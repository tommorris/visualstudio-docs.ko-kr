---
title: '연습: 첫 번째에 VSTO 추가 기능 프로젝트 만들기'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bc935c50a00efea7d3124eb7d1fb3246248f0b91
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674375"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>연습: 첫 번째에 VSTO 추가 기능 프로젝트 만들기
  이 연습에서는 Microsoft Office Project 용 VSTO 추가 기능을 만드는 방법을 보여 줍니다. 이러한 종류의 솔루션에서 만드는 기능은 열려 있는 프로젝트에 관계없이 응용 프로그램 자체에서 사용할 수 있습니다. 자세한 내용은 [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)합니다.  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 이 연습에서는 다음 작업을 수행합니다.  
  
-   Project VSTO 추가 기능 프로젝트 만들기  
  
-   새 프로젝트에 작업을 추가하기 위해 Project의 개체 모델을 사용하는 코드 작성  
  
-   테스트를 위해 프로젝트 빌드 및 실행  
  
-   VSTO 추가 기능이 개발 컴퓨터에서 더 이상 자동으로 실행되지 않도록 하기 위해 완료된 프로젝트 정리  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] 또는 [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)]  
  
## <a name="create-the-project"></a>프로젝트를 만듭니다.  
  
### <a name="to-create-a-new-project-in-visual-studio"></a>Visual Studio에서 새 프로젝트를 만들려면  
  
1.  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.  
  
2.  **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.  
  
3.  템플릿 창에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음 **Office/SharePoint**를 확장합니다.  
  
4.  확장된 **Office/SharePoint** 노드 아래에서 **Office 추가 기능** 노드를 선택합니다.  
  
5.  프로젝트 템플릿 목록에서 **Project 2010 추가 기능** 또는 **Project 2013 추가 기능**을 선택합니다.  
  
6.  **이름** 상자에 **FirstProjectAddIn**을 입력합니다.  
  
7.  **확인**을 클릭합니다.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서는 **FirstProjectAddIn** 프로젝트를 만들고 **ThisAddIn** 코드 파일을 편집기에서 엽니다.  
  
## <a name="write-code-that-adds-a-new-task-to-a-project"></a>프로젝트에 새 태스크를 추가 하는 코드를 작성 합니다.  
 다음 작업으로, ThisAddIn 코드 파일에 코드를 추가합니다. 새 코드는 Project의 개체 모델을 사용하여 프로젝트에 새 작업을 추가합니다. 기본적으로 ThisAddIn 코드 파일에는 다음과 같은 생성된 코드가 포함되어 있습니다.  
  
-   `ThisAddIn` 클래스의 부분 정의. 이 클래스는 코드의 진입점을 제공하고 Project의 개체 모델에 대한 액세스를 제공합니다. 자세한 내용은 [프로그램 VSTO 추가 기능](../vsto/programming-vsto-add-ins.md)합니다. `ThisAddIn` 클래스의 나머지 부분은 수정해서는 안 되는 숨김 코드 파일에서 정의됩니다.  
  
-   `ThisAddIn_Startup` 및 `ThisAddIn_Shutdown` 이벤트 처리기. 이러한 이벤트 처리기는 Project에서 VSTO 추가 기능을 로드하고 언로드할 때 호출됩니다. 이러한 이벤트 처리기를 사용하여 VSTO 추가 기능이 로드될 때 VSTO 추가 기능을 초기화하고 VSTO 추가 기능이 언로드될 때 VSTO 추가 기능에서 사용하는 리소스를 정리할 수 있습니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)합니다.  
  
### <a name="to-add-a-task-to-a-new-project"></a>작업을 새 프로젝트에 추가하려면  
  
1.  ThisAddIn 코드 파일에서 다음 코드를 `ThisAddIn` 클래스에 추가합니다. 이 코드에 대 한 이벤트 처리기를 정의 합니다 `NewProject` 의 이벤트는 `Microsoft.Office.Interop.MSProject.Application` 클래스입니다.  
  
     사용자가 새 프로젝트를 만들 때 이 이벤트 처리기는 작업을 프로젝트에 추가합니다.  
  
     [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]  
  
 프로젝트를 수정 하려면이 코드 예제에서는 다음 개체를 사용 합니다.  
  
-   `Application` 클래스의 `ThisAddIn` 필드. 합니다 `Application` 반환 필드는 `Microsoft.Office.Interop.MSProject.Application` 프로젝트의 현재 인스턴스를 나타내는 개체입니다.  
  
-   `pj` NewProject 이벤트에 대 한 이벤트 처리기의 매개 변수입니다. 합니다 `pj` 매개 변수는 한 `Microsoft.Office.Interop.MSProject.Project` 프로젝트를 나타내는 개체입니다. 자세한 내용은 [솔루션 프로젝트](../vsto/project-solutions.md)합니다.  
  
1.  C#을 사용하는 경우 다음 코드를 `ThisAddIn_Startup` 이벤트 처리기에 추가합니다. 이 코드는 연결 된 `Application_Newproject` NewProject 이벤트와 이벤트 처리기입니다.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]  
  
  
## <a name="test-the-project"></a>프로젝트 테스트  
 프로젝트를 빌드하고 실행할 때 새 작업이 새 결과 프로젝트에 나타나는지 확인합니다.  
  
### <a name="to-test-the-project"></a>프로젝트를 테스트하려면  
  
1.  **F5** 키를 눌러 프로젝트를 빌드하고 실행합니다. Microsoft Project가 시작되고 새 빈 프로젝트가 자동으로 열립니다.  
  
     프로젝트를 빌드하면 코드가 프로젝트의 빌드 출력 폴더에 포함된 어셈블리로 컴파일됩니다. 또한 Visual Studio에서는 Project에서 VSTO 추가 기능을 검색하고 로드할 수 있도록 하는 레지스트리 항목 집합을 만들고 VSTO 추가 기능이 실행될 수 있도록 개발 컴퓨터에서 보안 설정을 구성합니다. 자세한 내용은 [Office 솔루션 빌드 프로세스 개요](http://msdn.microsoft.com/a9d12e4f-c9ea-4a62-a841-c42b91f831ee)합니다.  
  
2.  새 작업이 빈 프로젝트에 추가되었는지 확인합니다.  
  
3.  다음 텍스트가 해당 작업의 **작업 이름** 필드에 표시되는지 확인합니다.  
  
     **This text was added by using code.**  
  
4.  Microsoft Project를 닫습니다.  
  
## <a name="clean-up-the-project"></a>프로젝트 정리  
 프로젝트의 개발을 완료하면 VSTO 추가 기능 어셈블리, 레지스트리 항목 및 보안 설정을 개발 컴퓨터에서 제거합니다. 이렇게 하지 않으면 개발 컴퓨터에서 Microsoft Project를 열 때마다 VSTO 추가 기능이 실행됩니다.  
  
### <a name="to-clean-up-your-project"></a>프로젝트를 정리하려면  
  
1.  Visual Studio의 **빌드** 메뉴에서 **솔루션 정리**를 클릭합니다.  
  
## <a name="next-steps"></a>다음 단계  
 기본적인 Project용 VSTO 추가 기능을 만들었으므로 다음 항목에서 VSTO 추가 기능을 개발하는 방법에 대해 자세히 알아볼 수 있습니다.  
  
-   Project 용 VSTO 추가 기능에서 수행할 수 있는 일반적인 프로그래밍 작업: [프로그램 VSTO 추가 기능](../vsto/programming-vsto-add-ins.md)합니다.  
  
-   프로젝트의 개체 모델 사용: [솔루션 프로젝트](../vsto/project-solutions.md)합니다.  
  
-   빌드 및 VSTO 추가 기능 프로젝트에 대 한 디버깅: [빌드 Office 솔루션](../vsto/building-office-solutions.md)합니다.  
  
-   Project 용 VSTO 추가 기능 배포: [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)합니다.  
  
## <a name="see-also"></a>참고자료  
 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)   
 [프로젝트 솔루션](../vsto/project-solutions.md)   
 [Office 솔루션 빌드](../vsto/building-office-solutions.md)   
 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)   
 [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)  
  
  