---
title: Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time | Microsoft Docs
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
- GetVstoObject method
- application-level add-ins [Office development in Visual Studio], adding controls to documents
- host items [Office development in Visual Studio], creating at run time in add-ins
- application-level add-ins [Office development in Visual Studio], extending Word documents
- application-level add-ins [Office development in Visual Studio], extending Excel workbooks
- controls [Office development in Visual Studio], adding at run time
- HasVstoObject method
ms.assetid: c1607314-4cf8-439c-b4c5-709db8b71cff
caps.latest.revision: 61
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: ea574b32578479f6f1d775da284d552a003b6cd6
ms.contentlocale: ko-kr
ms.lasthandoff: 08/30/2017

---
# <a name="extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time"></a>Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time
  You can use a VSTO Add-in to customize Word documents and Excel workbooks in the following ways:  
  
-   Add managed controls to any open document or worksheet.  
  
-   Convert an existing list object on an Excel worksheet to an extended <xref:Microsoft.Office.Tools.Excel.ListObject> that exposes events and can be bound to data by using the Windows Forms data binding model.  
  
-   Access application-level events that are exposed by Word and Excel for specific documents, workbooks, and worksheets.  
  
 To use this functionality, you generate an object at run time that extends the document or workbook.  
  
 **Applies to:** The information in this topic applies to VSTO Add-in projects for the following applications: Excel and Word. For more information, see [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
## <a name="generating-extended-objects-in-vsto-add-ins"></a>Generating Extended Objects in VSTO Add-ins  
 *Extended objects* are instances of types provided by the Visual Studio Tools for Office runtime that add functionality to objects that exist natively in the Word or Excel object models (called *native Office objects*). To generate an extended object for a Word or Excel object, use the GetVstoObject method. The first time you call the GetVstoObject method for a specified Word or Excel object, it returns a new object that extends the specified object. Each time you call the method and specify the same Word or Excel object, it returns the same extended object.  
  
 The type of the extended object has the same name as the type of the native Office object, but the type is defined in the <xref:Microsoft.Office.Tools.Excel> or <xref:Microsoft.Office.Tools.Word> namespace. For example, if you call the GetVstoObject method to extend a <xref:Microsoft.Office.Interop.Word.Document> object, the method returns a <xref:Microsoft.Office.Tools.Word.Document> object.  
  
 The GetVstoObject methods are intended to be used primarily in VSTO Add-in projects. You can also use these methods in document-level projects, but they behave differently, and have fewer uses.  
  
 To determine whether an extended object has already been generated for a particular native Office object, use the HasVstoObject method. For more information, see [Determining Whether an Office Object Has Been Extended](#HasVstoObject).  
  
### <a name="generating-host-items"></a>Generating Host Items  
 When you use the GetVstoObject to extend a document-level object (that is, a <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, or <xref:Microsoft.Office.Interop.Word.Document>), the returned object is called a *host item*. A host item is a type that can contain other objects, including other extended objects and controls. It resembles the corresponding type in the Word or Excel primary interop assembly, but it has additional features. For more information about host items, see [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
 After you generate a host item, you can use it to add managed controls to the document, workbook, or worksheet. For more information, see [Adding Managed Controls to Documents and Worksheets](#AddControls).  
  
##### <a name="to-generate-a-host-item-for-a-word-document"></a>To generate a host item for a Word document  
  
-   The following code example demonstrates how to generate a host item for the active document.  
  
     [!code-vb[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#8)]  [!code-csharp[Trin_WordAddInDynamicControls#8](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#8)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-workbook"></a>To generate a host item for an Excel workbook  
  
-   The following code example demonstrates how to generate a host item for the active workbook.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#2)]  [!code-csharp[Trin_ExcelAddInDynamicControls#2](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#2)]  
  
##### <a name="to-generate-a-host-item-for-an-excel-worksheet"></a>To generate a host item for an Excel worksheet  
  
-   The following code example demonstrates how to generate a host item for the active worksheet in a project.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#1)]  [!code-csharp[Trin_ExcelAddInDynamicControls#1](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#1)]  
  
### <a name="generating-listobject-host-controls"></a>Generating ListObject Host Controls  
 When you use the GetVstoObject method to extend a <xref:Microsoft.Office.Interop.Excel.ListObject>, the method returns a <xref:Microsoft.Office.Tools.Excel.ListObject>. The <xref:Microsoft.Office.Tools.Excel.ListObject> has all of the features of the original <xref:Microsoft.Office.Interop.Excel.ListObject>, but it also has additional functionality, such as the ability to be bound to data by using the Windows Forms data binding model. For more information, see [ListObject Control](../vsto/listobject-control.md).  
  
##### <a name="to-generate-a-host-control-for-a-listobject"></a>To generate a host control for a ListObject  
  
-   The following code example demonstrates how to generate a <xref:Microsoft.Office.Tools.Excel.ListObject> for the first <xref:Microsoft.Office.Interop.Excel.ListObject> in the active worksheet in a project.  
  
     [!code-vb[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_exceladdindynamiccontrols4/ThisAddIn.vb#3)]  [!code-csharp[Trin_ExcelAddInDynamicControls#3](../vsto/codesnippet/CSharp/trin_exceladdindynamiccontrols4/ThisAddIn.cs#3)]  
  
##  <a name="AddControls"></a> Adding Managed Controls to Documents and Worksheets  
 After you generate a <xref:Microsoft.Office.Tools.Word.Document> or <xref:Microsoft.Office.Tools.Excel.Worksheet>, you can add controls to the document or worksheet that these extended objects represent. To do this, use the Controls property of the <xref:Microsoft.Office.Tools.Word.Document> or <xref:Microsoft.Office.Tools.Excel.Worksheet>. For more information, see [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 You can add Windows Forms controls or *host controls*. A host control is a control provided by the [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] that wraps a corresponding control in the Word or Excel primary interop assembly. A host control exposes all of the behavior of the underlying native Office object, but it also raises events and can be bound to data by using the Windows Forms data binding model. For more information, see [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md).  
  
> [!NOTE]  
>  You cannot add a <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> control to a worksheet, or a <xref:Microsoft.Office.Tools.Word.XMLNode> or <xref:Microsoft.Office.Tools.Word.XMLNodes> control to a document, by using a VSTO Add-in. These host controls cannot be added programmatically. For more information, see [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="persisting-and-removing-controls"></a>Persisting and Removing Controls  
 When you add managed controls to a document or worksheet, the controls are not persisted when the document is saved and then closed. All host controls are removed so that only the underlying native Office objects are left behind. For example, a <xref:Microsoft.Office.Tools.Excel.ListObject> becomes a <xref:Microsoft.Office.Interop.Excel.ListObject>. All Windows Forms controls are also removed, but ActiveX wrappers for the controls are left behind in the document. You must include code in your VSTO Add-in to clean up the controls, or to recreate the controls the next time the document is opened. For more information, see [Persisting Dynamic Controls in Office Documents](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
## <a name="accessing-application-level-events-on-documents-and-workbooks"></a>Accessing Application-Level Events on Documents and Workbooks  
 Some document, workbook, and worksheet events in the native Word and Excel object models are raised only at the application level. For example, the <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> event is raised when a document is opened in Word, but this event is defined in the <xref:Microsoft.Office.Interop.Word.Application> class, rather than the <xref:Microsoft.Office.Interop.Word.Document> class.  
  
 When you use only native Office objects in your VSTO Add-in, you must handle these application-level events and then write additional code to determine whether the document that raised the event is one that you have customized. Host items provide these events at the document level, so that it is easier to handle the events for a specific document. You can generate a host item and then handle the event for that host item.  
  
### <a name="example-that-uses-native-word-objects"></a>Example That Uses Native Word Objects  
 The following code example demonstrates how to handle an application-level event for Word documents. The `CreateDocument` method creates a new document, and then defines a <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> event handler that prevents this document from being saved. Because this is an application-level event that is raised for the <xref:Microsoft.Office.Interop.Word.Application> object, the event handler must compare the `Doc` parameter with the `document1` object to determine if `document1` represents the saved document.  
  
 [!code-vb[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#12)] [!code-csharp[Trin_WordAddInDynamicControls#12](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#12)]  
  
### <a name="examples-that-use-a-host-item"></a>Examples That Use a Host Item  
 The following code examples simplify this process by handling the <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> event of a <xref:Microsoft.Office.Tools.Word.Document> host item. The `CreateDocument2` method in these examples generate a <xref:Microsoft.Office.Tools.Word.Document> that extends the `document2` object, and then it defines a <xref:Microsoft.Office.Tools.Word.Document.BeforeSave> event handler that prevents the document from being saved. Because this event handler is called only when `document2` is saved, the event handler can cancel the save action without doing any extra work to verify which document was saved.  
  
 The following code example demonstrates this task.  
  
 [!code-vb[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#13)] [!code-csharp[Trin_WordAddInDynamicControls#13](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#13)]  
  
##  <a name="HasVstoObject"></a> Determining Whether an Office Object Has Been Extended  
 To determine whether an extended object has already been generated for a particular native Office object, use the HasVstoObject method. This method returns **true** if an extended object has already been generated; otherwise, it returns **false**.  
  
 Use the Globals.Factory.HasVstoMethod method. Pass in the native Word or Excel object, such as a <xref:Microsoft.Office.Interop.Word.Document> or <xref:Microsoft.Office.Interop.Excel.Worksheet>, that you want to test for an extended object.  
  
 The HasVstoObject method is useful when you want to run code only when a specified Office object has an extended object. For example, if you have a Word VSTO Add-in that handles the <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> event to remove managed controls from a document before it is saved, you can use the HasVstoObject method to determine whether the document has been extended. If the document has not been extended, it cannot contain managed controls, and therefore the event handler can simply return without trying to clean up controls on the document.  
  
## <a name="see-also"></a>See Also  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Office Development Samples and Walkthroughs](../vsto/office-development-samples-and-walkthroughs.md)  
  
  