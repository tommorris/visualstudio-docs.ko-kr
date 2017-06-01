---
title: "연습: Outlook에서 전자 메일 메시지와 함께 사용자 지정 작업 창 표시"
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
  - "Outlook[Visual Studio에서 Office 개발], 사용자 지정 작업창"
  - "작업창[Visual Studio에서 Office 개발], 메일 메시지와 함께 표시"
  - "전자 메일에 사용자 지정 작업 창 표시"
  - "메일[Visual Studio에서 Office 개발], 표시된 사용자 지정 작업창"
  - "사용자 지정 작업창[Visual Studio에서 Office 개발], 메일 메시지와 함께 표시"
ms.assetid: 04943967-a7ef-4876-9584-84ada427e3f3
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 58
---
# 연습: Outlook에서 전자 메일 메시지와 함께 사용자 지정 작업 창 표시
  이 연습에서는 각 메일 메시지를 만들거나 열 때 사용자 지정 작업창의 고유 인스턴스를 함께 표시하는 방법을 보여 줍니다. 사용자는 각 메일 메시지의 리본에 있는 단추를 사용하여 사용자 지정 작업창을 표시하거나 숨길 수 있습니다.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 여러 탐색기 또는 검사기 창에서 사용자 지정 작업창을 함께 표시하려면 열리는 각 창에 대해 사용자 지정 작업창의 인스턴스를 만들어야 합니다. Outlook 창에서의 사용자 지정 작업창 동작에 대한 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)를 참조하세요.  
  
> [!NOTE]  
>  이 연습에서는 코드에 숨겨진 논리를 보다 쉽게 설명하기 위해 VSTO 추가 기능 코드를 여러 개의 작은 섹션으로 보여 줍니다.  
  
 이 연습에서는 다음 작업을 수행합니다.  
  
-   사용자 지정 작업창의 UI\(사용자 인터페이스\) 디자인  
  
-   사용자 지정 리본 UI 만들기  
  
-   메일 메시지와 함께 사용자 지정 리본 UI 표시  
  
-   검사기 창 및 사용자 지정 작업창을 관리하기 위한 클래스 만들기  
  
-   VSTO 추가 기능에서 사용되는 리소스 초기화 및 정리  
  
-   리본 토글 단추를 사용자 지정 작업창과 동기화  
  
> [!NOTE]  
>  일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](http://msdn.microsoft.com/ko-kr/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
## 사전 요구 사항  
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] 또는 Microsoft Outlook 2010  
  
 ![비디오에 링크](../vsto/media/playvideo.png "비디오에 링크") 관련 동영상 데모는 [어떻게 할까요?: Outlook에서 작업창 사용](http://go.microsoft.com/fwlink/?LinkID=130309)을 참조하세요.  
  
## 프로젝트 만들기  
 사용자 지정 작업창은 VSTO 추가 기능에서 구현됩니다. 우선 Outlook용 VSTO 추가 기능 프로젝트를 만들어야 합니다.  
  
#### 새 프로젝트를 만들려면  
  
1.  이름이 **OutlookMailItemTaskPane**인 **Outlook 추가 기능** 프로젝트를 만듭니다.**Outlook 추가 기능** 프로젝트 템플릿을 사용합니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)을 참조하십시오.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서는 **ThisAddIn.cs** 또는 **ThisAddIn.vb** 코드 파일을 열고 **OutlookMailItemTaskPane** 프로젝트를 **솔루션 탐색기**에 추가합니다.  
  
## 사용자 지정 작업창의 사용자 인터페이스 디자인  
 사용자 지정 작업창을 위한 비주얼 디자이너는 없지만 원하는 UI를 사용하여 사용자 정의 컨트롤을 디자인할 수 있습니다.  이 VSTO 추가 기능의 사용자 지정 작업창에는 <xref:System.Windows.Forms.TextBox> 컨트롤이 포함된 간단한 UI가 있습니다. 이 연습 뒷부분에서는 사용자 지정 작업창에 사용자 정의 컨트롤을 추가합니다.  
  
#### 사용자 지정 작업창의 사용자 인터페이스를 디자인하려면  
  
1.  **솔루션 탐색기**에서 **OutlookMailItemTaskPane** 프로젝트를 클릭합니다.  
  
2.  **프로젝트** 메뉴에서 **사용자 정의 컨트롤 추가**를 클릭합니다.  
  
3.  **새 항목 추가** 대화 상자에서 새 사용자 정의 컨트롤의 이름을 **TaskPaneControl**로 변경하고 **추가**를 클릭합니다.  
  
     사용자 정의 컨트롤이 디자이너에서 열립니다.  
  
4.  **도구 상자**의 **공용 컨트롤** 탭에서 **TextBox** 컨트롤을 사용자 정의 컨트롤로 끌어 놓습니다.  
  
## 리본의 사용자 인터페이스 정의  
 이 VSTO 추가 기능의 목표 중 하나는 사용자가 각 메일 메시지의 리본에서 사용자 지정 작업창을 숨기거나 표시할 수 있도록 하는 것입니다. 사용자 인터페이스를 제공하려면 사용자가 클릭하면 사용자 지정 작업창을 표시하거나 숨길 수 있는 토글 단추를 표시하는 사용자 지정 리본 UI를 만듭니다.  
  
#### 사용자 지정 리본 UI를 만들려면  
  
1.  **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.  
  
2.  **새 항목 추가** 대화 상자에서 **리본\(비주얼 디자이너\)**을 선택합니다.  
  
3.  새 리본의 이름을 **ManageTaskPaneRibbon**으로 변경하고 **추가**를 클릭합니다.  
  
     **ManageTaskPaneRibbon.cs** 또는 **ManageTaskPaneRibbon.vb** 파일이 리본 디자이너에서 열리고 기본 탭 및 그룹이 표시됩니다.  
  
4.  리본 디자이너에서 **group1**을 클릭합니다.  
  
5.  **속성** 창에서 **Label** 속성을 **작업창 관리자**로 설정합니다.  
  
6.  **도구 상자**의 **Office 리본 컨트롤** 탭에서 ToggleButton 컨트롤을 **작업창 관리자** 그룹으로 끌어 놓습니다.  
  
7.  **toggleButton1**을 클릭합니다.  
  
8.  **속성** 창에서 **Label** 속성을 **작업창 표시**로 설정합니다.  
  
## 메일 메시지와 함께 사용자 지정 리본 사용자 인터페이스 표시  
 이 연습에서 만드는 사용자 지정 작업창은 메일 메시지가 포함된 검사기 창과 함께만 나타나도록 디자인되었습니다. 따라서 사용자 지정 리본 UI가 이 창과 함께만 표시되도록 해당 속성을 설정합니다.  
  
#### 메일 메시지와 함께 사용자 지정 리본 UI를 표시하려면  
  
1.  리본 디자이너에서 **ManageTaskPaneRibbon** 리본을 클릭합니다.  
  
2.  **속성** 창에서 **RibbonType** 옆의 드롭다운 목록을 클릭하고 **Microsoft.Outlook.Mail.Compose** 및 **Microsoft.Outlook.Mail.Read**를 선택합니다.  
  
## 검사기 창 및 사용자 지정 작업창을 관리하기 위한 클래스 만들기  
 VSTO 추가 기능에서 특정 메일 메시지와 연결된 사용자 지정 작업창을 식별해야 하는 경우가 있습니다. 이러한 경우는 다음과 같습니다.  
  
-   사용자가 메일 메시지를 닫은 경우. 이 경우 VSTO 추가 기능에서는 VSTO 추가 기능이 사용한 리소스가 올바르게 정리되도록 해당 사용자 지정 작업창을 제거해야 합니다.  
  
-   사용자가 사용자 지정 작업창을 닫은 경우. 이 경우 VSTO 추가 기능에서는 메일 메시지의 리본에 있는 토글 단추의 상태를 업데이트해야 합니다.  
  
-   사용자가 리본의 토글 단추를 클릭한 경우. 이 경우 VSTO 추가 기능에서는 해당 작업창을 숨기거나 표시해야 합니다.  
  
 VSTO 추가 기능에서 열려 있는 각 메일 메시지와 연결된 사용자 지정 작업창을 추적할 수 있도록 하려면 <xref:Microsoft.Office.Interop.Outlook.Inspector> 및 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체 쌍을 래핑하는 사용자 지정 클래스를 만듭니다. 이 클래스는 각 메일 메시지에 대해 새 사용자 지정 작업창 개체를 만들고 해당 메일 메시지가 닫히면 사용자 지정 작업창을 삭제합니다.  
  
#### 검사기 창 및 사용자 지정 작업창을 관리하기 위한 클래스를 만들려면  
  
1.  **솔루션 탐색기**에서 **ThisAddIn.cs** 또는 **ThisAddIn.vb** 파일을 마우스 오른쪽 단추로 클릭한 다음 **코드 보기**를 클릭합니다.  
  
2.  파일 맨 위에 다음 문을 추가합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#2)]  
  
3.  다음 코드를 **ThisAddIn.cs** 또는 **ThisAddIn.vb** 파일의 `ThisAddIn` 클래스 외부에 추가합니다. Visual C\#의 경우에는 이 코드를 `OutlookMailItemTaskPane` 네임스페이스 내에 추가합니다.`InspectorWrapper` 클래스는 <xref:Microsoft.Office.Interop.Outlook.Inspector> 및 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체 쌍을 관리합니다. 다음 단계에서는 이 클래스의 정의를 완료합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#3)]  
  
4.  이전 단계에서 추가한 코드 뒤에 다음 생성자를 추가합니다. 이 생성자는 전달된 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체와 연결된 새 사용자 지정 작업창을 만들고 초기화합니다. C\#에서는 이 생성자가 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체의 <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> 이벤트와 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체의 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 이벤트에 이벤트 처리기를 연결합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#4)]  
  
5.  이전 단계에서 추가한 코드 뒤에 다음 메서드를 추가합니다. 이 메서드는 `InspectorWrapper` 클래스에 포함된 <xref:Microsoft.Office.Tools.CustomTaskPane> 개체의 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 이벤트에 대한 이벤트 처리기입니다.  이 코드는 사용자가 사용자 지정 작업창을 열거나 닫을 때마다 토글 단추의 상태를 업데이트합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#5)]  
  
6.  이전 단계에서 추가한 코드 뒤에 다음 메서드를 추가합니다. 이 메서드는 현재 메일 메시지가 포함된 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체의 <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> 이벤트에 대한 이벤트 처리기입니다. 이벤트 처리기에서는 메일 메시지가 닫힐 때 리소스를 해제합니다. 또한 `CustomTaskPanes` 컬렉션에서 현재 사용자 지정 작업창을 제거합니다. 이렇게 하면 다음 메일 메시지가 열릴 때 사용자 지정 작업창의 인스턴스가 여러 개가 되지 않습니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#6)]  
  
7.  이전 단계에서 추가한 코드 뒤에 다음 코드를 추가합니다. 이 연습의 뒷부분에서는 사용자 지정 리본 UI의 메서드에서 이 속성을 호출하여 사용자 지정 작업창을 표시하거나 숨깁니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#7)]  
  
## 추가 기능에서 사용되는 리소스 초기화 및 정리  
 `ThisAddIn` 클래스에 코드를 추가하여 VSTO 추가 기능이 로드될 때 VSTO 추가 기능을 초기화하고 VSTO 추가 기능이 언로드될 때 VSTO 추가 기능에서 사용하는 리소스를 정리할 수 있습니다.<xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 이벤트에 대한 이벤트 처리기를 설정하고 기존의 모든 메일 메시지를 이 이벤트 처리기에 전달하여 VSTO 추가 기능을 초기화합니다. VSTO 추가 기능이 언로드될 때는 이벤트 처리기를 분리하고 VSTO 추가 기능에서 사용한 개체를 정리합니다.  
  
#### VSTO 추가 기능에서 사용되는 리소스를 초기화하고 정리하려면  
  
1.  **ThisAddIn.cs** 또는 **ThisAddIn.vb** 파일에서 `ThisAddIn` 클래스의 정의를 찾습니다.  
  
2.  `ThisAddIn` 클래스에 다음 선언을 추가합니다.  
  
    -   `inspectorWrappersValue` 필드에는 VSTO 추가 기능에서 관리되는 모든 <xref:Microsoft.Office.Interop.Outlook.Inspector> 및 `InspectorWrapper` 개체가 포함됩니다.  
  
    -   `inspectors` 필드는 현재 Outlook 인스턴스의 검사기 창 컬렉션에 대한 참조를 유지 관리합니다. 이 참조는 가비지 수집기가 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 이벤트\(다음 단계에서 선언\)에 대한 이벤트 처리기가 포함된 메모리를 해제할 수 없게 합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#8)]  
  
3.  `ThisAddIn_Startup` 메서드를 다음 코드로 바꿉니다. 이 코드에서 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 이벤트에 이벤트 처리기를 연결하고 기존의 모든 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체를 이벤트 처리기에 전달합니다. Outlook이 이미 실행 중일 때 사용자가 VSTO 추가 기능을 로드하면 VSTO 추가 기능에서는 이 정보를 사용하여 이미 열려 있는 모든 메일 메시지에 대해 사용자 지정 작업창을 만듭니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_OutlookMailItemTaskPane#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#9)]  
  
4.  `ThisAddIn_ShutDown` 메서드를 다음 코드로 바꿉니다. 이 코드에서는 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 이벤트 처리기를 분리하고 VSTO 추가 기능에서 사용한 개체를 정리합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_OutlookMailItemTaskPane#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#10)]  
  
5.  `ThisAddIn` 클래스에 다음 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 이벤트 처리기를 추가합니다. 새 <xref:Microsoft.Office.Interop.Outlook.Inspector>에 메일 메시지가 들어 있으면 이 메서드에서 새 `InspectorWrapper` 개체의 인스턴스를 만들어 메일 메시지와 해당 작업창 간의 관계를 관리합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_OutlookMailItemTaskPane#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#11)]  
  
6.  다음 속성을 `ThisAddIn` 클래스에 추가합니다. 이 속성은 `ThisAddIn` 클래스 외부의 코드에 전용 `inspectorWrappersValue` 필드를 노출합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_OutlookMailItemTaskPane#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ThisAddIn.vb#12)]  
  
## 검사점  
 프로젝트를 빌드하여 프로젝트가 오류 없이 컴파일되는지 확인합니다.  
  
#### 프로젝트를 빌드하려면  
  
1.  **솔루션 탐색기**에서 **OutlookMailItemTaskPane** 프로젝트를 마우스 오른쪽 단추로 클릭한 다음 **빌드**를 클릭합니다. 프로젝트가 오류 없이 컴파일되는지 확인합니다.  
  
## 리본 토글 단추를 사용자 지정 작업창과 동기화  
 토글 단추는 작업창이 표시될 때 누른 상태로 표시되고 작업창이 숨겨져 있을 때는 누르지 않은 상태로 표시됩니다. 단추의 상태를 사용자 지정 작업창과 동기화하려면 토글 단추의 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 이벤트 처리기를 수정합니다.  
  
#### 사용자 지정 작업창을 토글 단추와 동기화하려면  
  
1.  리본 디자이너에서 **작업창 표시** 토글 단추를 두 번 클릭합니다.  
  
     Visual Studio에서 이 토글 단추의 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 이벤트를 처리하는 `toggleButton1_Click`이라는 이벤트 처리기가 자동으로 생성됩니다. 또한 **ManageTaskPaneRibbon.cs** 또는 **ManageTaskPaneRibbon.vb** 파일이 코드 편집기에서 열립니다.  
  
2.  **ManageTaskPaneRibbon.cs** 또는 **ManageTaskPaneRibbon.vb** 파일 맨 위에 다음 문을 추가합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ManageTaskPaneRibbon.vb#14)]  
  
3.  `toggleButton1_Click` 이벤트 처리기를 다음 코드로 바꿉니다. 사용자가 토글 단추를 클릭하면 이 메서드는 현재 검사기 창과 연결된 사용자 지정 작업창을 숨기거나 표시합니다.  
  
     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/CS/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookMailItemTaskPane/VB/ManageTaskPaneRibbon.vb#15)]  
  
## 프로젝트 테스트  
 프로젝트를 디버깅하면 Outlook이 열리고 VSTO 추가 기능이 로드됩니다. VSTO 추가 기능에서는 열려 있는 각 메일 메시지와 함께 사용자 지정 작업창의 고유 인스턴스를 표시합니다. 여러 개의 새 메일 메시지를 만들어 코드를 테스트합니다.  
  
#### VSTO 추가 기능을 테스트하려면  
  
1.  F5 키를 누릅니다.  
  
2.  Outlook에서 **새로 만들기**를 클릭하여 새 메일 메시지를 만듭니다.  
  
3.  메일 메시지의 리본에서 **추가 기능** 탭을 클릭하고 **작업창 표시** 단추를 클릭합니다.  
  
     **내 작업창**이라는 제목의 작업창이 메일 메시지와 함께 표시되는지 확인합니다.  
  
4.  작업창의 텍스트 상자에 **첫 번째 작업창**을 입력합니다.  
  
5.  작업창을 닫습니다.  
  
     **작업창 표시** 단추의 상태가 누르지 않은 상태로 변경되는지 확인합니다.  
  
6.  **작업창 표시** 단추를 다시 클릭합니다.  
  
     작업창이 열리고 텍스트 상자에 여전히 **첫 번째 작업창**이라는 문자열이 들어 있는지 확인합니다.  
  
7.  Outlook에서 **새로 만들기**를 클릭하여 두 번째 메일 메시지를 만듭니다.  
  
8.  메일 메시지의 리본에서 **추가 기능** 탭을 클릭하고 **작업창 표시** 단추를 클릭합니다.  
  
     **내 작업창**이라는 제목의 작업창이 메일 메시지와 함께 표시되고 이 작업창의 텍스트 상자가 비어 있는지 확인합니다.  
  
9. 작업창의 텍스트 상자에 **두 번째 작업창**을 입력합니다.  
  
10. 포커스를 첫 번째 메일 메시지로 이동합니다.  
  
     이 메일 메시지와 연결된 작업창의 텍스트 상자에 여전히 **첫 번째 작업창**이 표시되는지 확인합니다.  
  
 이 VSTO 추가 기능에서는 보다 고급 시나리오도 처리하며 이를 테스트해 볼 수도 있습니다. 예를 들어 **다음 항목** 및 **이전 항목** 단추를 사용하여 메일을 볼 때의 동작을 테스트할 수 있습니다. VSTO 추가 기능을 언로드하고 여러 개의 메일 메시지를 연 다음 VSTO 추가 기능을 다시 로드할 때의 동작을 테스트할 수도 있습니다.  
  
## 다음 단계  
 다음 항목에서는 사용자 지정 작업창을 만드는 방법에 대해 더 자세히 설명합니다.  
  
-   다른 응용 프로그램용 VSTO 추가 기능의 사용자 지정 작업창을 만듭니다. 사용자 지정 작업창을 지원하는 응용 프로그램에 대한 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)를 참조하세요.  
  
-   사용자 지정 작업창을 사용하여 Microsoft Office 응용 프로그램을 자동화합니다. 자세한 내용은 [연습: 사용자 지정 작업 창을 사용하여 응용 프로그램 자동화](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)을 참조하세요.  
  
-   Excel에서 사용자 지정 작업창을 숨기거나 표시하는 데 사용할 수 있는 리본 단추를 만듭니다. 자세한 내용은 [연습: 사용자 지정 작업 창과 리본 단추 동기화](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)을 참조하세요.  
  
## 참고 항목  
 [사용자 지정 작업 창](../vsto/custom-task-panes.md)   
 [방법: 응용 프로그램에 사용자 지정 작업 창 추가](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [연습: 사용자 지정 작업 창을 사용하여 응용 프로그램 자동화](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [연습: 사용자 지정 작업 창과 리본 단추 동기화](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)   
 [리본 개요](../vsto/ribbon-overview.md)   
 [Outlook 개체 모델 개요](../vsto/outlook-object-model-overview.md)   
 [런타임에 리본 메뉴에 액세스](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  