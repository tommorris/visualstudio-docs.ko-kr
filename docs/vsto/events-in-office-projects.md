---
title: "Office 프로젝트의 이벤트"
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
  - "Sheet1_Startup"
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "응용 프로그램 수준 추가 기능[Visual Studio에서 Office 개발], 이벤트"
  - "이벤트 처리기[Visual Studio에서 Office 개발]"
  - "ThisWorkbook_Startup"
  - "Sheet2_Startup"
  - "ThisWorkbook_Shutdown"
  - "문서 수준 사용자 지정[Visual Studio에서 Office 개발], 이벤트"
  - "Sheet2_Shutdown"
  - "Startup 이벤트"
  - "Sheet3_Shutdown"
  - "추가 기능[Visual Studio에서 Office 개발], 이벤트"
  - "Shutdown 이벤트"
  - "ThisAddIn_Startup"
  - "Sheet3_Startup"
  - "Startup 메서드[Visual Studio에서 Office 개발]"
  - "Shutdown 메서드[Visual Studio에서 Office 개발]"
  - "Sheet1_Shutdown"
  - "이벤트[Visual Studio에서 Office 개발]"
  - "ThisAddIn_Shutdown"
ms.assetid: 666d7f23-ef85-4f2e-9cd3-258df5bdc6fd
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Office 프로젝트의 이벤트
  각 Office 프로젝트 템플릿은 몇 가지 이벤트 처리기를 자동으로 생성합니다. 문서 수준 사용자 지정의 이벤트 처리기는 VSTO 추가 기능의 이벤트 처리기와 약간 다릅니다.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 문서 수준 프로젝트  
 Visual Studio에서는 문서 수준 사용자 지정의 신규 또는 기존 문서나 워크시트 뒤에서 생성된 코드를 제공합니다. 이 코드에서는 두 가지 이벤트인 **Startup** 및 **Shutdown**을 발생시킵니다.  
  
### Startup 이벤트  
 **Startup** 이벤트는 문서가 실행 중이고 어셈블리의 모든 초기화 코드가 실행된 후 각 호스트 항목\(문서, 통합 문서 또는 워크시트\)에 대해 발생합니다. 이 이벤트는 코드가 실행되고 있는 클래스의 생성자에서 실행될 마지막 항목입니다. 호스트 항목에 대한 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조하세요.  
  
 문서 수준 프로젝트를 만드는 경우 Visual Studio에서는 생성된 코드 파일에서 **Startup** 이벤트에 대한 이벤트 처리기를 만듭니다.  
  
-   Microsoft Office Word 프로젝트에 대한 이벤트 처리기의 이름은 `ThisDocument_Startup`입니다.  
  
-   Microsoft Office Excel 프로젝트에 대한 이벤트 처리기의 이름은 다음과 같습니다.  
  
    -   `Sheet1_Startup`  
  
    -   `Sheet2_Startup`  
  
    -   `Sheet3_Startup`  
  
    -   `ThisWorkbook_Startup`  
  
### Shutdown 이벤트  
 **Shutdown**  이벤트는 코드가 로드된 응용 프로그램 도메인이 언로드되려고 할 때 각 호스트 항목\(문서 또는 워크시트\)에 대해 발생합니다. 이 이벤트는 언로드될 때 클래스에서 호출되는 마지막 항목입니다.  
  
 문서 수준 프로젝트를 만드는 경우 Visual Studio에서는 생성된 코드 파일에서  **Shutdown**  이벤트에 대한 이벤트 처리기를 만듭니다.  
  
-   Microsoft Office Word 프로젝트에 대한 이벤트 처리기의 이름은 `ThisDocument_Shutdown`입니다.  
  
-   Microsoft Office Excel 프로젝트에 대한 이벤트 처리기의 이름은 다음과 같습니다.  
  
    -   `Sheet1_Shutdown`  
  
    -   `Sheet2_Shutdown`  
  
    -   `Sheet3_Shutdown`  
  
    -   `ThisWorkbook_Shutdown`  
  
> [!NOTE]  
>  문서의 **Shutdown** 이벤트 처리기 중에 프로그래밍 방식으로 컨트롤을 제거하지 마세요. 문서의 UI 요소는 **Shutdown** 이벤트가 발생할 때 더 이상 사용할 수 없습니다. 응용 프로그램이 닫히기 전에 컨트롤을 제거하려면 **BeforeClose**, **BeforeSave** 등의 다른 이벤트 처리기에 코드를 추가합니다.  
  
### 이벤트 처리기 메서드 선언  
 모든 이벤트 처리기 메서드 선언에는 동일한 인수인 *sender* 및 *e*가 전달됩니다. Excel에서 *sender* 인수는 `Sheet1`, `Sheet2` 등의 시트를 참조하고, Word에서 *sender* 인수는 문서를 참조합니다.*e* 인수는 이벤트의 표준 인수를 참조합니다. 이 경우에는 표준 인수가 사용되지 않습니다.  
  
 다음 코드 예제에서는 Word용 문서 수준 프로젝트의 기본 이벤트 처리기를 보여 줍니다.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#121](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#121)]
 [!code-vb[Trin_VstcoreWordAutomation#121](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#121)]  
  
 다음 코드 예제에서는 Excel용 문서 수준 프로젝트의 기본 이벤트 처리기를 보여 줍니다.  
  
> [!NOTE]  
>  다음 코드 예제에서는 `Sheet1` 클래스의 이벤트 처리기를 보여 줍니다. 다른 호스트 항목 클래스의 이벤트 처리기 이름은 클래스 이름에 해당합니다. 예를 들어 `Sheet2` 클래스에서 **Startup** 이벤트 처리기의 이름은 `Sheet2_Startup`입니다.`ThisWorkbook` 클래스에서 **Startup** 이벤트 처리기의 이름은 `ThisWorkbook_Startup`입니다.  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#83](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#83)]  
  
### 문서 수준 Excel 프로젝트의 이벤트 순서  
 Excel 프로젝트의 **Startup** 이벤트 처리기는 다음 순서로 호출됩니다.  
  
1.  `ThisWorkbook_Startup`.  
  
2.  `Sheet1_Startup`.  
  
3.  `Sheet2_Startup`.  
  
4.  `Sheet3_Startup`.  
  
5.  순서에 있는 다른 시트  
  
 통합 문서 솔루션의  **Shutdown** 이벤트 처리기는 다음 순서로 호출됩니다.  
  
1.  `ThisWorkbook_Shutdown`.  
  
2.  `Sheet1_Shutdown`.  
  
3.  `Sheet2_Shutdown`.  
  
4.  `Sheet3_Shutdown`.  
  
5.  순서에 있는 다른 시트  
  
 순서는 프로젝트가 컴파일될 때 결정됩니다. 사용자가 런타임에 시트를 다시 정렬하는 경우 다음번에 통합 문서가 열리거나 닫힐 때 이벤트가 발생하는 순서는 변경되지 않습니다.  
  
## VSTO 추가 기능 프로젝트  
 Visual Studio에서는 VSTO 추가 기능에서 생성된 코드를 제공합니다. 이 코드에서는 두 가지 이벤트인 <xref:Microsoft.Office.Tools.AddInBase.Startup> 및 <xref:Microsoft.Office.Tools.AddInBase.Shutdown>을 발생시킵니다.  
  
### Startup 이벤트  
 <xref:Microsoft.Office.Tools.AddIn.Startup> 이벤트는 VSTO 추가 기능이 로드되고 어셈블리의 모든 초기화 코드가 실행된 후 발생합니다. 이 이벤트는 생성된 코드 파일의 `ThisAddIn_Startup` 메서드에서 처리됩니다.  
  
 VSTO 추가 기능이 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 메서드를 재정의하지 않는 한 `ThisAddIn_Startup` 이벤트 처리기의 코드는 실행할 첫 번째 사용자 코드입니다. 이 경우에 `ThisAddIn_Startup` 이벤트 처리기는 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 뒤에 호출됩니다.  
  
 코드를 실행하려면 문서가 열려 있어야 하는 경우 `ThisAdd-In_Startup` 이벤트 처리기에서 코드를 추가하면 안 됩니다. 대신 사용자가 문서를 만들거나 열 때 Office 응용 프로그램에서 발생하는 이벤트에 해당 코드를 추가합니다. 자세한 내용은 [Office 응용 프로그램이 시작될 때 문서 액세스](../vsto/programming-vsto-add-ins.md#AccessingDocuments)을 참조하세요.  
  
 VSTO 추가 기능의 시작 시퀀스에 대한 자세한 내용은 [VSTO 추가 기능의 아키텍처](../vsto/architecture-of-vsto-add-ins.md)를 참조하세요.  
  
### Shutdown 이벤트  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 이벤트는 코드가 로드된 응용 프로그램 도메인이 언로드되려고 할 때 발생합니다. 이 이벤트는 생성된 코드 파일의 `ThisAddIn_Shutdown` 메서드에서 처리됩니다. 이 이벤트 처리기는 VSTO 추가 기능이 언로드될 때 실행할 마지막 사용자 코드입니다.  
  
#### Outlook VSTO 추가 기능의 Shutdown 이벤트  
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 이벤트는 사용자가 Outlook에서 COM 추가 기능 대화 상자를 사용하여 VSTO 추가 기능을 사용하지 않도록 설정할 때만 발생합니다. 이 이벤트는 Outlook이 종료될 때 발생하지 않습니다. Outlook이 종료될 때 실행되어야 하는 코드가 있는 경우 다음 이벤트 중 하나를 처리합니다.  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application> 개체의 <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> 이벤트  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer> 개체의 <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> 이벤트  
  
> [!NOTE]  
>  레지스트리를 수정하여 Outlook이 종료될 때 Outlook에서 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> 이벤트를 강제로 발생시킬 수 있습니다. 그러나 관리자가 이 설정을 되돌리는 경우 `ThisAddIn_Shutdown` 메서드에 추가하는 모든 코드가 Outlook이 종료될 때 더 이상 실행되지 않습니다. 자세한 내용은 [Outlook 2010의 종료 변경 내용](http://go.microsoft.com/fwlink/?LinkID=184614)을 참조하세요.  
  
## 참고 항목  
 [Office 솔루션 개발](../vsto/developing-office-solutions.md)   
 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [문서 수준 사용자 지정 프로그래밍](../vsto/programming-document-level-customizations.md)   
 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)   
 [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)  
  
  