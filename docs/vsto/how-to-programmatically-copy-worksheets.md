---
title: 'How to: Programmatically Copy Worksheets | Microsoft Docs'
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
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
ms.assetid: e49e03f5-7b2f-416b-b5fe-0965336c47e1
caps.latest.revision: 31
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: cec0a7c0408205f187572c191c1335a21484da86
ms.contentlocale: ko-kr
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-copy-worksheets"></a>How to: Programmatically Copy Worksheets
  You can create a copy of a worksheet, and insert that worksheet before or after an existing worksheet in the workbook. If you do not specify where to insert the worksheet, Excel creates a new workbook to contain the new worksheet.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Whether you copy the worksheet programmatically, or the end user copies the worksheet manually, there is no code behind the new worksheet and controls on the new worksheet do not function. This is because the newly copied worksheet is a <xref:Microsoft.Office.Interop.Excel.Worksheet> object and not a <xref:Microsoft.Office.Tools.Excel.Worksheet> host item. Windows Forms controls and host controls can only be added to host items. For more information, see [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>To add a copied worksheet to a workbook in a document-level customization  
  
1.  Use the <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> method to copy the first worksheet in the current workbook and place the copy after the third sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]  [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>To add a copied worksheet to a workbook in a VSTO Add-in  
  
1.  Use the <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> method to copy the first worksheet in the current workbook and place the copy after the third sheet.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]  [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>See Also  
 [Working with Worksheets](../vsto/working-with-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [How to: Programmatically Add New Worksheets to Workbooks](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [How to: Programmatically Delete Worksheets from Workbooks](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [How to: Programmatically Select Worksheets](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)   
 [Global Access to Objects in Office Projects](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Optional Parameters in Office Solutions](../vsto/optional-parameters-in-office-solutions.md)  
  
  