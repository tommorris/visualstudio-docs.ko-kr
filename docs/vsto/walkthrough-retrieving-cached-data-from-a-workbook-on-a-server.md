---
title: 'Walkthrough: Retrieving Cached Data from a Workbook on a Server | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks [Office development in Visual Studio], retrieving data
- datasets [Office development in Visual Studio], accessing on server
- server-side data access [Office development in Visual Studio]
- data [Office development in Visual Studio], accessing on server
- documents [Office development in Visual Studio], server-side data access
ms.assetid: ef6d61e5-a498-4b38-8e2e-2e80706d854b
caps.latest.revision: 35
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: ec1e9c72991bdfded96cb53907f5dd3d4fb87dca
ms.contentlocale: ko-kr
ms.lasthandoff: 08/30/2017

---
# <a name="walkthrough-retrieving-cached-data-from-a-workbook-on-a-server"></a>Walkthrough: Retrieving Cached Data from a Workbook on a Server
  This walkthrough demonstrates how to retrieve data from a dataset that is cached in a Microsoft Office Excel workbook without starting Excel by using the <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> class.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 This walkthrough illustrates the following tasks:  
  
-   Defining a dataset that contains data from the AdventureWorksLT database.  
  
-   Creating instances of the dataset in an Excel workbook project and a console application project.  
  
-   Creating a <xref:Microsoft.Office.Tools.Excel.ListObject> that is bound to the dataset in the workbook, and populating the <xref:Microsoft.Office.Tools.Excel.ListObject> with data when the workbook is opened.  
  
-   Adding the dataset in the workbook to the data cache.  
  
-   Reading data from the cached dataset into the dataset in the console application, without starting Excel.  
  
 Although this walkthrough assumes that you are running the code on your development computer, the code demonstrated by this walkthrough can be used on a server that does not have Excel installed.  
  
> [!NOTE]  
>  Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions. The Visual Studio edition that you have and the settings that you use determine these elements. For more information, see [Personalize the Visual Studio IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] or [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Access to a running instance of Microsoft SQL Server or Microsoft SQL Server Express that has the AdventureWorksLT sample database attached to it. You can download the AdventureWorksLT database from the [CodePlex Web site](http://go.microsoft.com/fwlink/?linkid=87843). For more information about attaching a database, see the following topics:  
  
    -   To attach a database by using SQL Server Management Studio or SQL Server Management Studio Express, see [How to: Attach a Database (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   To attach a database by using the command line, see [How to: Attach a Database File to SQL Server Express](http://msdn.microsoft.com/en-us/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## <a name="creating-a-class-library-project-that-defines-a-dataset"></a>Creating a Class Library Project That Defines a Dataset  
 To use the same dataset in an Excel workbook project and a console application, you must define the dataset in a separate assembly that is referenced by both of these projects. For this walkthrough, define the dataset in a class library project.  
  
#### <a name="to-create-the-class-library-project"></a>To create the class library project  
  
1.  Start [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  On the **File** menu, point to **New**, and then click **Project**.  
  
3.  In the templates pane, expand **Visual C#** or **Visual Basic**, and then click **Windows**.  
  
4.  In the list of project templates, select **Class Library**.  
  
5.  In the **Name** box, type **AdventureWorksDataSet**.  
  
6.  Click **Browse**, navigate to your %UserProfile%\My Documents (for Windows XP and earlier) or %UserProfile%\Documents (for Windows Vista) folder, and then click **Select Folder**.  
  
7.  In the **New Project** dialog box, ensure that the **Create directory for solution** check box is not selected.  
  
8.  Click **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adds the **AdventureWorksDataSet** project to **Solution Explorer** and opens the **Class1.cs** or **Class1.vb** code file.  
  
9. In **Solution Explorer**, right-click **Class1.cs** or **Class1.vb**, and then click **Delete**. You do not need this file for this walkthrough.  
  
## <a name="defining-a-dataset-in-the-class-library-project"></a>Defining a Dataset in the Class Library Project  
 Define a typed dataset that contains data from the AdventureWorksLT database for SQL Server 2005. Later in this walkthrough, you will reference this dataset from an Excel workbook project and a console application project.  
  
 The dataset is a *typed dataset* that represents the data in the Product table of the AdventureWorksLT database. For more information about typed datasets, see [Dataset tools in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).  
  
#### <a name="to-define-a-typed-dataset-in-the-class-library-project"></a>To define a typed dataset in the class library project  
  
1.  In **Solution Explorer**, click the **AdventureWorksDataSet** project.  
  
2.  If the **Data Sources** window is not visible, display it by, on the menu bar, choosing **View**, **Other Windows**, **Data Sources**.  
  
3.  Choose **Add New Data Source** to start the **Data Source Configuration Wizard**.  
  
4.  Click **Database**, and then click **Next**.  
  
5.  If you have an existing connection to the AdventureWorksLT database, choose this connection and click **Next**.  
  
     Otherwise, click **New Connection**, and use the **Add Connection** dialog box to create the new connection. For more information, see [Add new connections](../data-tools/add-new-connections.md).  
  
6.  In the **Save the Connection String to the Application Configuration File** page, click **Next**.  
  
7.  In the **Choose Your Database Objects** page, expand **Tables** and select **Product (SalesLT)**.  
  
8.  Click **Finish**.  
  
     The AdventureWorksLTDataSet.xsd file is added to the **AdventureWorksDataSet** project. This file defines the following items:  
  
    -   A typed dataset named `AdventureWorksLTDataSet`. This dataset represents the contents of the Product table in the AdventureWorksLT database.  
  
    -   A TableAdapter named `ProductTableAdapter`. This TableAdapter can be used to read and write data in the `AdventureWorksLTDataSet`. For more information, see [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     You will use both of these objects later in this walkthrough.  
  
9. In **Solution Explorer**, right-click **AdventureWorksDataSet** and click **Build**.  
  
     Verify that the project builds without errors.  
  
## <a name="creating-an-excel-workbook-project"></a>Creating an Excel Workbook Project  
 Create an Excel workbook project for the interface to the data. Later in this walkthrough, you will create a <xref:Microsoft.Office.Tools.Excel.ListObject> that displays the data, and you will add an instance of the dataset to the data cache in the workbook.  
  
#### <a name="to-create-the-excel-workbook-project"></a>To create the Excel workbook project  
  
1.  In **Solution Explorer**, right-click the **AdventureWorksDataSet** solution, point to **Add**, and then click **New Project**.  
  
2.  In the templates pane, expand **Visual C#** or **Visual Basic**, and then expand **Office/SharePoint**.  
  
3.  Under the expanded **Office/SharePoint** node, select the **Office Add-ins** node.  
  
4.  In the list of project templates, select the **Excel 2010 Workbook** or **Excel 2013 Workbook** project.  
  
5.  In the **Name** box, type **AdventureWorksReport**. Do not modify the location.  
  
6.  Click **OK**.  
  
     The **Visual Studio Tools for Office Project Wizard** opens.  
  
7.  Ensure that **Create a new document** is selected, and click **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] opens the **AdventureWorksReport** workbook in the designer and adds the **AdventureWorksReport** project to **Solution Explorer**.  
  
## <a name="adding-the-dataset-to-data-sources-in-the-excel-workbook-project"></a>Adding the Dataset to Data Sources in the Excel Workbook Project  
 Before you can display the dataset in the Excel workbook, you must first add the dataset to data sources in the Excel workbook project.  
  
#### <a name="to-add-the-dataset-to-the-data-sources-in-the-excel-workbook-project"></a>To add the dataset to the data sources in the Excel workbook project  
  
1.  In **Solution Explorer**, double-click **Sheet1.cs** or **Sheet1.vb** under the **AdventureWorksReport** project.  
  
     The workbook opens in the designer.  
  
2.  On the **Data** menu, click **Add New Data Source**.  
  
     The **Data Source Configuration Wizard** opens.  
  
3.  Click **Object**, and then click **Next**.  
  
4.  In the **Select the Object You Wish to Bind** to page, click **Add Reference**.  
  
5.  On the **Projects** tab, click **AdventureWorksDataSet** and then click **OK**.  
  
6.  Under the **AdventureWorksDataSet** namespace of the **AdventureWorksDataSet** assembly, click **AdventureWorksLTDataSet** and then click **Finish**.  
  
     The **Data Sources** window opens, and **AdventureWorksLTDataSet** is added to the list of data sources.  
  
## <a name="creating-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>Creating a ListObject That Is Bound to an Instance of the Dataset  
 To display the dataset in the workbook, create a <xref:Microsoft.Office.Tools.Excel.ListObject> that is bound to an instance of the dataset. For more information about binding controls to data, see [Binding Data to Controls in Office Solutions](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### <a name="to-create-a-listobject-that-is-bound-to-an-instance-of-the-dataset"></a>To create a ListObject that is bound to an instance of the dataset  
  
1.  In the **Data Sources** window, expand the **AdventureWorksLTDataSet** node under **AdventureWorksDataSet**.  
  
2.  Select the **Product** node, click the drop-down arrow that appears, and select **ListObject** in the drop-down list.  
  
     If the drop-down arrow does not appear, confirm that the workbook is open in the designer.  
  
3.  Drag the **Product** table to cell A1.  
  
     A <xref:Microsoft.Office.Tools.Excel.ListObject> control named `productListObject` is created on the worksheet, starting in cell A1. At the same time, a dataset object named `adventureWorksLTDataSet` and a <xref:System.Windows.Forms.BindingSource> named `productBindingSource` are added to the project. The <xref:Microsoft.Office.Tools.Excel.ListObject> is bound to the <xref:System.Windows.Forms.BindingSource>, which in turn is bound to the dataset object.  
  
## <a name="adding-the-dataset-to-the-data-cache"></a>Adding the Dataset to the Data Cache  
 To enable code outside the Excel workbook project to access the dataset in the workbook, you must add the dataset to the data cache. For more information about the data cache, see [Cached Data in Document-Level Customizations](../vsto/cached-data-in-document-level-customizations.md) and [Caching Data](../vsto/caching-data.md).  
  
#### <a name="to-add-the-dataset-to-the-data-cache"></a>To add the dataset to the data cache  
  
1.  In the designer, click **adventureWorksLTDataSet**.  
  
2.  In the **Properties** window, set the **Modifiers** property to **Public**.  
  
3.  Set the **CacheInDocument** property to **True**.  
  
## <a name="initializing-the-dataset-in-the-workbook"></a>Initializing the Dataset in the Workbook  
 Before you can retrieve the data from the cached dataset by using the console application, you must first populate the cached dataset with data.  
  
#### <a name="to-initialize-the-dataset-in-the-workbook"></a>To initialize the dataset in the workbook  
  
1.  In **Solution Explorer**, right-click the **Sheet1.cs** or **Sheet1.vb** file and click **View Code**.  
  
2.  Replace the `Sheet1_Startup` event handler with the following code. This code uses an instance of the `ProductTableAdapter` class that is defined in the **AdventureWorksDataSet** project to fill the cached dataset with data, if it is currently empty.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/CSharp/AdventureWorksDataSet/AdventureWorksReport/Sheet1.cs#8)]  [!code-vb[Trin_CachedDataWalkthroughs#8](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/AdventureWorksReport/Sheet1.vb#8)]  
  
## <a name="checkpoint"></a>Checkpoint  
 Build and run the Excel workbook project to ensure that it compiles and runs without errors. This operation also fills the cached dataset and saves the data in the workbook.  
  
#### <a name="to-build-and-run-the-project"></a>To build and run the project  
  
1.  In **Solution Explorer**, right-click the **AdventureWorksReport** project, choose **Debug**, and then click **Start new instance**.  
  
     The project is built, and the workbook opens in Excel. Verify the following:  
  
    -   The <xref:Microsoft.Office.Tools.Excel.ListObject> fills with data.  
  
    -   The value in the **ListPrice** column for the first row of the <xref:Microsoft.Office.Tools.Excel.ListObject> is 1431.5. Later in this walkthrough, you will use a console application to modify the values in the **ListPrice** column.  
  
2.  Save the workbook. Do not modify the file name or the location of the workbook.  
  
3.  Close Excel.  
  
## <a name="creating-a-console-application-project"></a>Creating a Console Application Project  
 Create a console application project to use to modify data in the cached dataset in the workbook.  
  
#### <a name="to-create-the-console-application-project"></a>To create the console application project  
  
1.  In **Solution Explorer**, right-click the **AdventureWorksDataSet** solution, point to **Add**, and then click **New Project**.  
  
2.  In the **Project Types** pane, expand **Visual C#** or **Visual Basic**, and then click **Windows**.  
  
3.  In the **Templates** pane, select **Console Application**.  
  
4.  In the **Name** box, type **DataReader**. Do not modify the location.  
  
5.  Click **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] adds the **DataReader** project to **Solution Explorer** and opens the **Program.cs** or **Module1.vb** code file.  
  
## <a name="retrieving-data-from-the-cached-dataset-by-using-the-console-application"></a>Retrieving Data from the Cached Dataset by Using the Console Application  
 Use the <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> class in the console application to read the data into a local `AdventureWorksLTDataSet` object. To confirm that the local dataset was initialized with data from the cached dataset, the application displays the number of rows in the local dataset.  
  
#### <a name="to-retrieve-data-from-the-cached-dataset"></a>To retrieve data from the cached dataset  
  
1.  In **Solution Explorer**, right-click the **DataReader** project and click **Add Reference**.  
  
2.  On the **.NET** tab, select Microsoft.VisualStudio.Tools.Applications.ServerDocument.  
  
3.  Click **OK**.  
  
4.  In **Solution Explorer**, right-click the **DataReader** project and click **Add Reference**.  
  
5.  On the **Projects** tab, select **AdventureWorksDataSet**, and click **OK**.  
  
6.  Open the Program.cs or Module1.vb file in the Code Editor.  
  
7.  Add the following **using** (for C#) or **Imports** (for Visual Basic) statement to the top of the code file.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#1)]  [!code-vb[Trin_CachedDataWalkthroughs#1](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#1)]  
  
8.  Add the following code to the `Main` method. This code declares the following objects:  
  
    -   An instance of the `AdventureWorksLTDataSet` type that is defined in the **AdventureWorksDataSet** project.  
  
    -   The path to the AdventureWorksReport workbook in the build folder of the **AdventureWorksReport** project.  
  
    -   A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> object to use to access the data cache in the workbook.  
  
        > [!NOTE]  
        >  The following code assumes that the workbook is saved using the .xlsx extension. If the workbook in your project has a different extension, modify the path as necessary.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#10)] [!code-vb[Trin_CachedDataWalkthroughs#10](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#10)]  
  
9. Add the following code to the `Main` method, after the code you added in the previous step. This code performs the following tasks:  
  
    -   It uses the <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> property of the <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> class to access the cached dataset in the workbook.  
  
    -   It reads the data from the cached dataset into the local dataset.  
  
    -   It displays the number of rows in the local dataset, to confirm that it has data.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/CSharp/AdventureWorksDataSet/DataWriter/Program.cs#11)] [!code-vb[Trin_CachedDataWalkthroughs#11](../vsto/codesnippet/VisualBasic/AdventureWorksDataSet/DataWriter/Module1.vb#11)]  
  
10. On the **Build** menu, click **Build DataReader**.  
  
## <a name="testing-the-project"></a>Testing the Project  
 When you run the console application, it displays the number of rows in the local dataset.  
  
#### <a name="to-test-the-workbook"></a>To test the workbook  
  
1.  In **Solution Explorer**, right-click the **DataReader** project, point to **Debug**, and then click **Start new instance**.  
  
     Verify that the application reports that the local dataset has 295 rows.  
  
2.  Press ENTER to close the application.  
  
## <a name="next-steps"></a>Next Steps  
 You can learn more about working with cached data from these topics:  
  
-   Changing the data in a cached dataset without starting Excel. For more information, see [Walkthrough: Changing Cached Data in a Workbook on a Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## <a name="see-also"></a>See Also  
 [Walkthrough: Inserting Data into a Workbook on a Server](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md)   
 [Walkthrough: Changing Cached Data in a Workbook on a Server](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Connecting to Data in Windows Forms Applications](/visualstudio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  