---
title: "Excel 솔루션"
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
  - "응용 프로그램 수준 추가 기능[Visual Studio에서 Office 개발], Excel"
  - "Excel[Visual Studio에서 Office 개발], 응용 프로그램 수준 추가 기능"
  - "Office 솔루션[Visual Studio에서 Office 개발], Excel"
  - "솔루션[Visual Studio에서 Office 개발], Excel"
  - "추가 기능[Visual Studio에서 Office 개발], Excel"
  - "Excel[Visual Studio에서 Office 개발], Excel 솔루션 정보"
  - "Excel[Visual Studio에서 Office 개발]"
  - "문서[Visual Studio에서 Office 개발], Excel"
  - "Office 문서[Visual Studio에서 Office 개발], Excel"
  - "프로젝트[Visual Studio에서 Office 개발], Excel"
  - "Excel [Visual Studio에서 Office 개발], 문서 수준 사용자 지정"
  - "사용자 인터페이스[Visual Studio에서 Office 개발], Excel"
  - "Visual Studio에서 Office 개발, Excel 솔루션"
  - "문서 수준 사용자 지정[Visual Studio에서 Office 개발], Excel"
  - "Office 프로젝트[Visual Studio에서 Office 개발], Excel"
ms.assetid: 34444d54-d7b6-479a-b5b7-a946267081e9
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Excel 솔루션
  Visual Studio에서는 Microsoft Office Excel용 VSTO 추가 기능 및 문서 수준 사용자 지정을 만드는 데 사용할 수 있는 프로젝트 템플릿을 제공합니다. 이러한 솔루션을 사용하여 Excel을 자동화하고, Excel 기능을 확장한 다음 Excel UI\(사용자 인터페이스\)를 사용자 지정할 수 있습니다. 문서 수준 사용자 지정과 VSTO 추가 기능 간의 차이점에 대한 자세한 내용은 [Office 솔루션 개발 개요&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)를 참조하세요.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 이 항목에서는 다음 내용에 대해 설명합니다.  
  
-   [Excel 자동화](#automating)  
  
-   [Excel용 문서 수준 사용자 지정 개발](#doclevel)  
  
-   [Excel용 VSTO 추가 기능 개발](#applevel)  
  
-   [Excel의 사용자 인터페이스 사용자 지정](#UI)  
  
##  <a name="automating"></a> Excel 자동화  
 Excel 개체 모델은 Excel 자동화에 사용할 수 있는 다양한 형식을 노출합니다. 예를 들어 프로그래밍 방식으로 차트를 만들고, 워크시트의 서식을 지정하고, 범위 및 셀의 값을 설정할 수 있습니다. 자세한 내용은 [Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)을 참조하세요.  
  
 Visual Studio에서 Excel 솔루션을 개발하는 경우 솔루션에서 *호스트 항목* 및 *호스트 컨트롤*을 사용할 수도 있습니다. Excel 개체 모델에서 일반적으로 사용되는 특정 개체\(예: <xref:Microsoft.Office.Interop.Excel.Worksheet> 및 <xref:Microsoft.Office.Interop.Excel.Range>\)를 확장하는 개체입니다. 확장된 개체는 기반이 되는 Excel 개체처럼 동작하지만 개체에 이벤트 및 데이터 바인딩 기능을 더 추가합니다. 자세한 내용은 [확장된 개체를 사용하여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)을 참조하세요.  
  
##  <a name="doclevel"></a> Excel 용 문서 수준 사용자 지정 개발  
 Microsoft Office Excel용 문서 수준 사용자 지정은 특정 통합 문서와 연결된 어셈블리로 구성됩니다. 어셈블리는 일반적으로 UI를 사용자 지정하고 Excel을 자동화하여 통합 문서를 확장합니다. Excel 자체와 연결된 VSTO 추가 기능과 달리 사용자 지정에 구현하는 기능은 연결된 통합 문서가 Excel에서 열려 있는 경우에만 사용할 수 있습니다.  
  
 Excel용 문서 수준 사용자 지정 프로젝트를 만들려면 Visual Studio의 **새 프로젝트** 대화 상자에서 Excel 통합 문서 또는 Excel 서식 파일 프로젝트 템플릿을 사용합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)을 참조하십시오.  
  
 문서 수준 사용자 지정 작업에 대한 자세한 내용은 [문서 수준 사용자 지정 아키텍처](../vsto/architecture-of-document-level-customizations.md)를 참조하세요.  
  
### Excel 사용자 지정 프로그래밍 모델  
 Excel용 문서 수준 프로젝트를 만드는 경우 Visual Studio는 솔루션의 기초가 되는 여러 클래스\(예: `ThisWorkbook`, `Sheet1`, `Sheet2` 및 `Sheet3`\)를 생성합니다. 이러한 클래스는 솔루션과 연결된 통합 문서 및 워크시트를 나타내고 코드를 작성하기 위한 시작점을 제공합니다.  
  
 이 생성된 클래스 및 문서 수준 프로젝트에서 사용할 수 있는 기타 기능에 대한 자세한 내용은 [문서 수준 사용자 지정 프로그래밍](../vsto/programming-document-level-customizations.md)을 참조하세요.  
  
##  <a name="applevel"></a> Excel용 VSTO 추가 기능 개발  
 Microsoft Office Excel용 VSTO 추가 기능은 Excel에서 로드되는 어셈블리로 구성됩니다. 어셈블리는 일반적으로 UI를 사용자 지정하고 Excel을 자동화하여 Excel을 확장합니다. 특정 통합 문서와 연결된 문서 수준 사용자 지정과 달리 VSTO 추가 기능에서 구현하는 기능은 단일 통합 문서로 제한되지 않습니다.  
  
 Excel용 VSTO 추가 기능 프로젝트를 만들려면 Visual Studio의 **새 프로젝트** 대화 상자에서 Excel 통합 문서 또는 Excel 서식 파일 프로젝트 템플릿을 사용합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)을 참조하십시오.  
  
 VSTO 추가 기능이 작동하는 방법에 대한 일반적인 내용은 [VSTO 추가 기능의 아키텍처](../vsto/architecture-of-vsto-add-ins.md)를 참조하세요.  
  
 ![비디오에 링크](~/data-tools/media/playvideo.gif "비디오에 링크") 관련 동영상 데모는 [어떻게 할까요?: Excel 추가 기능에서 PowerPoint 자동화](http://go.microsoft.com/fwlink/?LinkID=130300)를 참조하세요.  
  
### Excel 추가 기능 프로그래밍 모델  
 Excel VSTO 추가 기능 프로젝트를 만드는 경우 Visual Studio는 솔루션의 기초가 되는 `ThisAddIn`이라는 클래스를 생성합니다. 이 클래스는 코드를 작성하기 위한 시작점을 제공하고 VSTO 추가 기능에 Excel의 개체 모델도 노출합니다.  
  
 `ThisAddIn` 클래스 및 VSTO 추가 기능에서 사용할 수 있는 기타 Visual Studio 기능에 대한 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조하세요.  
  
##  <a name="UI"></a> Excel의 사용자 인터페이스 사용자 지정  
 Excel의 사용자 인터페이스를 사용자 지정하는 여러 가지 방법이 있습니다. 모든 프로젝트 형식에서 사용할 수 있는 옵션도 있고, VSTO 추가 기능 또는 문서 수준 사용자 지정에만 사용할 수 있는 옵션도 있습니다.  
  
### 모든 프로젝트 형식에 대한 옵션  
 다음 표에서는 문서 수준 사용자 지정과 VSTO 추가 기능에서 모두 사용할 수 있는 사용자 지정 옵션을 보여 줍니다.  
  
|작업|추가 정보|  
|--------|-----------|  
|리본 메뉴 사용자 지정|[리본 개요](../vsto/ribbon-overview.md)|  
|문서 수준 사용자 지정에 대한 사용자 지정 통합 문서 또는 VSTO 추가 기능에 대한 열려 있는 통합 문서에서 워크시트에 Windows Forms 컨트롤 또는 확장된 Excel 컨트롤 추가|[방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [방법: 워크시트에 Chart 컨트롤 추가](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [방법: 워크시트에 ListObject 컨트롤 추가](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### 문서 수준 사용자 지정에 대한 옵션  
 다음 표에서는 문서 수준 사용자 지정에만 사용할 수 있는 사용자 지정 옵션을 보여 줍니다.  
  
|작업|추가 정보|  
|--------|-----------|  
|통합 문서에 작업 창 추가|[작업 창 개요](../vsto/actions-pane-overview.md)<br /><br /> [방법: Word 문서 또는 Excel 통합 문서에 작업 창 추가](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|워크시트에 XML 노드에 매핑된 확장된 범위 컨트롤 추가|[방법: 워크시트에 XMLMappedRange 컨트롤 추가](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### VSTO 추가 기능에 대한 옵션  
 다음 표에서는 VSTO 추가 기능에만 사용할 수 있는 사용자 지정 옵션을 보여 줍니다.  
  
|작업|추가 정보|  
|--------|-----------|  
|사용자 지정 작업창을 만듭니다.|[사용자 지정 작업 창](../vsto/custom-task-panes.md)|  
  
### 관련 항목  
  
|제목|설명|  
|--------|--------|  
|[Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)|Excel 개체 모델에서 제공하는 주요 형식에 대해 설명합니다.|  
|[확장된 개체를 사용하여 Excel 자동화](../vsto/automating-excel-by-using-extended-objects.md)|Excel 솔루션에서 사용할 수 있는 확장된 개체\([!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]에서 제공\)에 대한 정보를 제공합니다.|  
|[Excel 솔루션 전역화 및 지역화](../vsto/globalization-and-localization-of-excel-solutions.md)|영어 이외의 Windows 언어 설정이 있는 컴퓨터에서 실행되는 Excel 솔루션의 특수 고려 사항에 대한 정보를 포함합니다.|  
|[Office 문서의 Windows Forms 컨트롤 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)|Excel 워크시트에 Windows Forms 컨트롤을 추가할 수 있는 방법을 설명합니다.|  
|[연습: Excel용 첫 문서 수준 사용자 지정 만들기](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Excel용 기본 문서 수준 사용자 지정을 만드는 방법을 보여 줍니다.|  
|[연습: Excel용 첫 VSTO 추가 기능 만들기](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Excel용 기본 VSTO 추가 기능을 만드는 방법을 보여 줍니다.|  
|[연습: 런타임에 VSTO 추가 기능 프로젝트에서 워크시트에 컨트롤 추가](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|VSTO 추가 기능을 사용하여 런타임에 Windows Forms 단추, <xref:Microsoft.Office.Tools.Excel.NamedRange> 및 <xref:Microsoft.Office.Tools.Excel.ListObject>를 워크시트에 추가하는 방법을 설명합니다.|  
|[Office 개발에서 Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199011)|Excel 솔루션 개발에 대한 문서 및 참조 설명서의 링크를 제공합니다. Visual Studio를 사용한 Office 개발과는 관련이 없습니다.|  
  
  