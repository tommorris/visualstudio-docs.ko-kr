---
title: 'Walkthrough: Creating a Template By Using Content Controls | Microsoft Docs'
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
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
ms.assetid: 88fb9a60-dcc3-4a5f-a8c9-7aff01ca4b4b
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 3876ec91cb4872e2a08ee83b60aeca7ce974ad0d
ms.contentlocale: ko-kr
ms.lasthandoff: 08/30/2017

---
# <a name="walkthrough-creating-a-template-by-using-content-controls"></a>Walkthrough: Creating a Template By Using Content Controls
  This walkthrough demonstrates how to create a document-level customization that uses content controls to create structured and reusable content in a Microsoft Office Word template.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Word enables you to create a collection of reusable document parts, named *building blocks*. This walkthrough shows how to create two tables as building blocks. Each table contains several content controls that can hold different types of content, such as plain text or dates. One of the tables contains information about an employee, and the other table contains customer feedback.  
  
 After you create a document from the template, you can add either of the tables to the document by using several <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> objects, which display the available building blocks in the template.  
  
 This walkthrough illustrates the following tasks:  
  
-   Creating tables that contain content controls in a Word template at design time.  
  
-   Populating a combo box content control and a drop-down list content control programmatically.  
  
-   Preventing users from editing a specified table.  
  
-   Adding tables to the building block collection of a template.  
  
-   Creating a content control that displays the available building blocks in the template.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisites  
 You need the following components to complete this walkthrough:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="creating-a-new-word-template-project"></a>Creating a New Word Template Project  
 Create a Word template so that users can create their own copies easily.  
  
#### <a name="to-create-a-new-word-template-project"></a>To create a new Word template project  
  
1.  Create a Word template project with the name **MyBuildingBlockTemplate**. In the wizard, create a new document in the solution. For more information, see [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] opens the new Word template in the designer and adds the **MyBuildingBlockTemplate** project to **Solution Explorer**.  
  
## <a name="creating-the-employee-table"></a>Creating the Employee Table  
 Create a table that contains four different types of content controls where the user can enter information about an employee.  
  
#### <a name="to-create-the-employee-table"></a>To create the employee table  
  
1.  In the Word template that is hosted in the [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] designer, on the Ribbon, click the **Insert** tab.  
  
2.  In the **Tables** group, click **Table**, and insert a table with 2 columns and 4 rows.  
  
3.  Type text in the first column so that it resembles the following column:  
  
    ||  
    |-|  
    |**Employee Name**|  
    |**Hire Date**|  
    |**Title**|  
    |**Picture**|  
  
4.  Click in the first cell in the second column (next to **Employee Name**).  
  
5.  On the Ribbon, click the **Developer** tab.  
  
    > [!NOTE]  
    >  If the **Developer** tab is not visible, you must first show it. For more information, see [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  In the **Controls** group, click the **Text** button ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") to add a <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> to the first cell.  
  
7.  Click the second cell in the second column (next to **Hire Date**).  
  
8.  In the **Controls** group, click the **Date Picker** button ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") to add a <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> to the second cell.  
  
9. Click the third cell in the second column (next to **Title**).  
  
10. In the **Controls** group, click the **Combo Box** button ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") to add a <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> to the third cell.  
  
11. Click the last cell in the second column (next to **Picture**).  
  
12. In the **Controls** group, click the **Picture Content Control** button ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") to add a <xref:Microsoft.Office.Tools.Word.PictureContentControl> to the last cell.  
  
## <a name="creating-the-customer-feedback-table"></a>Creating the Customer Feedback Table  
 Create a table that contains three different types of content controls where the user can enter customer feedback information.  
  
#### <a name="to-create-the-customer-feedback-table"></a>To create the customer feedback table  
  
1.  In the Word template, click in the line after the employee table that you added earlier, and press ENTER to add a new paragraph.  
  
2.  On the Ribbon, click the **Insert** tab.  
  
3.  In the **Tables** group, click **Table**, and insert a table with 2 columns and 3 rows.  
  
4.  Type text in the first column so that it resembles the following column:  
  
    ||  
    |-|  
    |**Customer Name**|  
    |**Satisfaction Rating**|  
    |**Comments**|  
  
5.  Click in the first cell of the second column (next to **Customer Name**).  
  
6.  On the Ribbon, click the **Developer** tab.  
  
7.  In the **Controls** group, click the **Text** button ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") to add a <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> to the first cell.  
  
8.  Click in the second cell of the second column (next to **Satisfaction Rating**).  
  
9. In the **Controls** group, click the **Drop-Down List** button ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") to add a <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> to the second cell.  
  
10. Click in the last cell of the second column (next to **Comments**).  
  
11. In the **Controls** group, click the **Rich Text** button ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") to add a <xref:Microsoft.Office.Tools.Word.RichTextContentControl> to the last cell.  
  
## <a name="populating-the-combo-box-and-drop-down-list-programmatically"></a>Populating the Combo Box and Drop Down List Programmatically  
 You can initialize content controls at design time by using the **Properties** window in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. You can also initialize them at run time, which enables you to set their initial states dynamically. For this walkthrough, use code to populate the entries in the <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> and <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> at run time so that you can see how these objects work.  
  
#### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>To modify the UI of the content controls programmatically  
  
1.  In **Solution Explorer**, right-click **ThisDocument.cs** or **ThisDocument.vb**, and then click **View Code**.  
  
2.  Add the following code to the `ThisDocument` class. This code declares several objects that you will use later in this walkthrough.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]  [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Add the following code to the `ThisDocument_Startup` method of the `ThisDocument` class. This code adds entries to the <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> and <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> in the tables, and sets the placeholder text that is displayed in each of these controls before the user edits them.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]  [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="preventing-users-from-editing-the-employee-table"></a>Preventing Users from Editing the Employee Table  
 Use the <xref:Microsoft.Office.Tools.Word.GroupContentControl> object that you declared earlier to protect the employee table. After protecting the table, users can still edit the content controls in the table. However, they cannot edit text in the first column or modify the table in other ways, such as adding or deleting rows and columns. For more information about how to use a <xref:Microsoft.Office.Tools.Word.GroupContentControl> to protect a part of a document, see [Content Controls](../vsto/content-controls.md).  
  
#### <a name="to-prevent-users-from-editing-the-employee-table"></a>To prevent users from editing the employee table  
  
1.  Add the following code to the `ThisDocument_Startup` method of the `ThisDocument` class, after the code that you added in the previous step. This code prevents users from editing the employee table by putting the table inside the <xref:Microsoft.Office.Tools.Word.GroupContentControl> object that you declared earlier.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]  [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="adding-the-tables-to-the-building-block-collection"></a>Adding the Tables to the Building Block Collection  
 Add the tables to a collection of document building blocks in the template so that users can insert the tables that you have created into the document. For more information about document building blocks, see [Content Controls](../vsto/content-controls.md).  
  
#### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>To add the tables to the building blocks in the template  
  
1.  Add the following code to the `ThisDocument_Startup` method of the `ThisDocument` class, after the code that you added in the previous step. This code adds new building blocks that contain the tables to the Microsoft.Office.Interop.Word.BuildingBlockEntries collection, which contains all the reusable building blocks in the template. The new building blocks are defined in a new category named **Employee and Customer Information** and are assigned the building block type Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]  [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Add the following code to the `ThisDocument_Startup` method of the `ThisDocument` class, after the code that you added in the previous step. This code deletes the tables from the template. The tables are no longer necessary, because you have added them to the gallery of reusable building blocks in the template. The code first puts the document into design mode so that the protected employee table can be deleted.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]  [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="creating-a-content-control-that-displays-the-building-blocks"></a>Creating a Content Control That Displays the Building Blocks  
 Create a content control that provides access to the building blocks (that is, the tables) that you created earlier. Users can click this control to add the tables to the document.  
  
#### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>To create a content control that displays the building blocks  
  
1.  Add the following code to the `ThisDocument_Startup` method of the `ThisDocument` class, after the code that you added in the previous step. This code initializes the <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> object that you declared earlier. The <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> displays all building blocks that are defined in the category **Employee and Customer Information** and that have the building block type Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]  [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="testing-the-project"></a>Testing the Project  
 Users can click the building block gallery controls in the document to insert the employee table or the customer feedback table. Users can type or select responses in the content controls in both of the tables. Users can modify other parts of the customer feedback table, but they should not be able to modify other parts of the employee table.  
  
#### <a name="to-test-the-employee-table"></a>To test the employee table  
  
1.  Press F5 to run the project.  
  
2.  Click **Choose your first building block** to display the first building block gallery content control.  
  
3.  Click the drop-down arrow next to the **Custom Gallery 1** heading in the control, and select **Employee Table**.  
  
4.  Click in the cell to the right of the **Employee Name** cell and type a name.  
  
     Verify that you can add only text to this cell. The <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> allows users to add only text, not other types of content such as art or a table.  
  
5.  Click in the cell to the right of the **Hire Date** cell and select a date in the date picker.  
  
6.  Click in the cell to the right of the **Title** cell and select one of the job titles in the combo box.  
  
     Optionally, type the name of a job title that is not in the list. This is possible because the <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> enables users to select from a list of entries or to type their own entries.  
  
7.  Click the icon in the cell to the right of the **Picture** cell and browse to an image to display it.  
  
8.  Try to add rows or columns to the table, and try to delete rows and columns from the table. Verify that you cannot modify the table. The <xref:Microsoft.Office.Tools.Word.GroupContentControl> prevents you from making any modifications.  
  
#### <a name="to-test-the-customer-feedback-table"></a>To test the customer feedback table  
  
1.  Click **Choose your second building block** to display the second building block gallery content control.  
  
2.  Click the drop-down arrow next to the **Custom Gallery 1** heading in the control, and select **Customer Table**.  
  
3.  Click in the cell to the right of the **Customer Name** cell and type a name.  
  
4.  Click in the cell to the right of the **Satisfaction Rating** cell and select one of the available options.  
  
     Verify that you cannot type your own entry. The <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> allows users only to select from a list of entries.  
  
5.  Click in the cell to the right of the **Comments** cell and type some comments.  
  
     Optionally, add some content other than text, such as art or an embedded table. This is possible because the <xref:Microsoft.Office.Tools.Word.RichTextContentControl> enables users to add content other than text.  
  
6.  Verify that you can add rows or columns to the table, and that you can delete rows and columns from the table. This is possible because you have not protected the table by putting it in a <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Close the template.  
  
## <a name="next-steps"></a>Next Steps  
 You can learn more about how to use content controls from this topic:  
  
-   Bind content controls to pieces of XML, also named custom XML parts, that are embedded in a document. For more information, see [Walkthrough: Binding Content Controls to Custom XML Parts](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>See Also  
 [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)   
 [Content Controls](../vsto/content-controls.md)   
 [How to: Add Content Controls to Word Documents](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [How to: Protect Parts of Documents by Using Content Controls](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  