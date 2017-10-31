---
title: "Workflow Designer로 응용 프로그램 개발 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DefaultWorkflowDesigner"
  - "DefaultWorkflowDesigner.UI"
helpviewer_keywords: 
  - "Visual Studio 2010 Workflow Designer [WFD]"
  - "Visual Studio 2010 Workflow Designer [WFD], 개요"
  - "Workflow Designer [WFD]"
  - "Workflow Designer [WFD], 개요"
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
caps.handback.revision: 17
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Workflow Designer로 응용 프로그램 개발
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]는 [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] 개발 환경에 호스팅되는 [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)]에서 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 응용 프로그램을 디버깅하고 그래픽을 생성하는 비주얼 디자이너 겸 디버거입니다.여기서 템플릿 및 활동 디자이너를 사용하여 복합 워크플로 응용 프로그램, 활동 라이브러리 또는 [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 서비스를 생성할 수 있습니다.워크플로 [!INCLUDE[crabout](../test/includes/crabout_md.md)][Windows Workflow Foundation](../Topic/Windows%20Workflow%20Foundation.md)를 참조하십시오.  
  
 새 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 버전에서 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 이전 버전과 달라진 몇 가지 디자인 기능은 다음과 같습니다.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]는 [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)]로 제작되었습니다.따라서 활동 디자이너의 사용 경험과 대형 복합 워크플로에 대한 성능이 향상되었습니다.  
  
-   이제 XAML을 사용하여 [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)]로 사용자 지정 활동을 설계할 수 있으며 활동 디자이너를 생성하는 프로그래밍 모델이 간소화되었습니다.  
  
-   익숙한 순서도 모델링 스타일을 사용하여 프로그램 흐름을 시각화할 수 있도록 순서도 활동을 구현했습니다.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]에는 워크플로 내에서 변수를 선언하고 범위를 지정하여 활동에 바인딩할 수 있도록 하는 새로운 변수 디자이너가 있습니다.  
  
-   [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)]에서 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]는 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 워크플로 내에 Visual Basic 식을 작성할 때 완전한 IntelliSense 기능을 제공합니다.  
  
-   이제 디버깅 환경이 XAML까지 확장되어 XAML 워크플로 정의에 중단점을 설정하고 런타임 시 XAML 코드를 한 단계씩 실행할 수 있으므로 관리 코드와 비슷한 사용 경험을 얻을 수 있습니다.  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 외부에서 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]를 재호스팅하는 작업이 이전 버전과 비교할 때 훨씬 간소화되어 이제는 코드 몇 줄만 있으면 됩니다.  
  
-   새로운 <xref:System.Activities.Statements.Flowchart> 활동 및 [순서도](../workflow-designer/flowchart-activity-designer.md)를 통해 익숙한 순서도 모델링 스타일로 프로그램 흐름을 시각화할 수 있습니다.  
  
-   메시징 활동도 향상되어 완전 선언적\(코드 없음\) [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] 서비스를 작성할 수 있습니다.  
  
-   **서비스 참조 추가…** 기능을 사용하면 웹 서비스에 액세스하는 활동을 자동으로 생성할 수 있습니다.  
  
## 단원 내용  
 [Workflow Designer 사용](../workflow-designer/using-the-workflow-designer.md)  
 기본 제공 디자이너를 사용하여 새 활동 및 워크플로 프로젝트를 만드는 방법과 디자이너에서 제공하는 다른 도구를 사용하여 인수, 변수, 식, 가져오기 및 이동 경로 탐색을 처리하는 방법을 보여 줍니다.  
  
 [활동 디자이너 사용](../workflow-designer/using-the-activity-designers.md)  
 시스템 제공 활동 및 템플릿과 해당 디자이너의 범주에 대해 설명합니다.  
  
 [Workflow Designer로 워크플로 디버깅](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 기존 디버깅 절차는 물론 XAML 및 식 디버깅을 수행하는 방법에 대해 설명합니다.  
  
 [Workflow Designer UI 도움말](../workflow-designer/workflow-designer-ui-help.md)  
 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]에서 제공되는 대화 상자에 대한 상황에 맞는 도움말 항목과 디자이너 셸 기능, 바로 가기 키 및 오류 메시지에 대한 지침이 들어 있습니다.  
  
 [.NET 3.0 또는 .NET 3.5 Framework를 대상으로 하는 워크플로 응용 프로그램 개발](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 또는 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]를 대상으로 하는 레거시 디자이너의 사용 지침이 들어 있습니다.  
  
 [디자이너 재호스팅 &#91;WF 샘플&#93;](../Topic/Designer%20ReHosting.md)  
 이를 위해 디자이너를 포함하도록 적절한 WPF 레이아웃을 만드는 방법을 보여줍니다.  
  
 [사용자 지정 활동 디자이너](../Topic/Custom%20Activity%20Designers.md)  
 이 단원에는 워크플로 디자이너에 표시할 사용자 지정 디자이너를 사용하는 활동 샘플이 포함되어 있습니다.