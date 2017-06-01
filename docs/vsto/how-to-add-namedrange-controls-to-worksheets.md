---
title: "방법: 워크시트에 NamedRange 컨트롤 추가"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "범위, 워크시트에 추가"
  - "NamedRange 컨트롤, 워크시트에 추가"
  - "컨트롤[Visual Studio에서 Office 개발], 워크시트에 추가"
ms.assetid: da7ec48f-92cb-4fa3-b3e2-447c238d17a8
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 방법: 워크시트에 NamedRange 컨트롤 추가
  디자인 타임 및 런타임에 문서 수준 프로젝트에서 Microsoft Office Excel 워크시트에 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 추가할 수 있습니다.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 런타임에 VSTO 추가 기능 프로젝트에서 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 추가할 수도 있습니다.  
  
 이 항목에서는 다음 작업에 대해 설명합니다.  
  
-   [디자인 타임에 NamedRange 컨트롤 추가](#designtime)  
  
-   [런타임에 문서 수준 프로젝트에서 NamedRange 컨트롤 추가](#runtimedoclevel)  
  
-   [런타임에 VSTO 추가 기능 프로젝트에서 NamedRange 컨트롤 추가](#runtimeaddin)  
  
 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤에 대한 자세한 내용은 [NamedRange 컨트롤](../vsto/namedrange-control.md)을 참조하세요.  
  
##  <a name="designtime"></a> 디자인 타임에 NamedRange 컨트롤 추가  
 디자인 타임에 문서 수준 프로젝트에서 워크시트에 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 추가하기 위한 여러 가지 방법이 있습니다. 즉, Excel, Visual Studio **도구 상자** 및 **데이터 원본** 창에서 추가할 수 있습니다.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Excel에서 이름 상자를 사용하여 워크시트에 NamedRange 컨트롤을 추가하려면  
  
1.  명명된 범위에 포함하려는 셀을 선택합니다.  
  
2.  **이름 상자**에 범위 이름을 입력한 다음 Enter 키를 누릅니다.  
  
     **이름 상자**는 워크시트의 **A** 열 바로 위에 수식 입력줄 옆에 있습니다.  
  
#### 도구 상자를 사용하여 워크시트에 NamedRange 컨트롤을 추가하려면  
  
1.  **도구 상자**를 열고 **Excel 컨트롤** 탭을 클릭합니다.  
  
2.  <xref:Microsoft.Office.Tools.Excel.NamedRange>를 클릭하고 워크시트에 끌어 놓습니다.  
  
     **명명된 범위 추가** 대화 상자가 나타납니다.  
  
3.  명명된 범위에 포함하려는 셀을 선택합니다.  
  
4.  **확인**을 클릭합니다.  
  
     컨트롤에 지정된 기본 이름을 원하지 않으면 **속성** 창에서 이름을 변경할 수 있습니다.  
  
#### 데이터 원본 창을 사용하여 워크시트에 NamedRange 컨트롤을 추가하려면  
  
1.  **데이터 원본** 창을 열고 데이터베이스에서 데이터 원본을 만듭니다. 자세한 내용은 [방법: 데이터베이스의 데이터에 연결](~/data-tools/how-to-connect-to-data-in-a-database.md)을 참조하세요.  
  
2.  **데이터 원본** 창에서 워크시트로 단일 필드를 끌어 놓습니다.  
  
     데이터 바인딩된 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 워크시트에 추가됩니다. 자세한 내용은 [데이터 바인딩 및 Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27)을 참조하세요.  
  
##  <a name="runtimedoclevel"></a> 런타임에 문서 수준 프로젝트에서 NamedRange 컨트롤 추가  
 런타임에 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 워크시트에 프로그래밍 방식으로 추가할 수 있습니다. 이를 통해 이벤트에 대한 응답으로 호스트 컨트롤을 만들 수 있습니다. 동적으로 생성된 명명된 범위는 워크시트를 닫을 때 워크시트에서 호스트 컨트롤로 유지되지 않습니다. 자세한 내용은 [런타임에 Office 문서에 컨트롤 추가](../vsto/adding-controls-to-office-documents-at-run-time.md)을 참조하세요.  
  
#### 프로그래밍 방식으로 워크시트에 NamedRange 컨트롤을 추가하려면  
  
1.  `Sheet1`의 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 이벤트 처리기에서 다음 코드를 삽입하여 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 **A1** 셀에 추가하고 해당 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 속성을 `Hello world!`로 설정합니다.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> 런타임에 VSTO 추가 기능 프로젝트에서 NamedRange 컨트롤 추가  
 VSTO 추가 기능 프로젝트에서 열려 있는 워크시트에 프로그래밍 방식으로 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 추가할 수 있습니다. 동적으로 생성된 명명된 범위는 워크시트를 닫을 때 워크시트에서 호스트 컨트롤로 유지되지 않습니다. 자세한 내용은 [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조하세요.  
  
#### 프로그래밍 방식으로 워크시트에 NamedRange 컨트롤을 추가하려면  
  
1.  다음 코드는 열려 있는 워크시트를 기반으로 하는 워크시트 호스트 항목을 생성하고 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 **A1** 셀에 추가하고 해당 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 속성을 `Hello world`로 설정합니다.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#7)]  
  
## 참고 항목  
 [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)   
 [NamedRange 컨트롤](../vsto/namedrange-control.md)   
 [확장된 개체를 사용하여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)   
 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)   
 [방법: NamedRange 컨트롤 크기 조정](../vsto/how-to-resize-namedrange-controls.md)   
 [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  