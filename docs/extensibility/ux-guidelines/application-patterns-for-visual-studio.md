---
title: "Visual Studio에 대 한 응용 프로그램 패턴 | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 7c2612cb537a6f3197cf9f99a0dc11981dfc73e1
ms.contentlocale: ko-kr
ms.lasthandoff: 05/04/2017

---
# <a name="application-patterns-for-visual-studio"></a>Visual Studio에 대 한 응용 프로그램 패턴
##  <a name="BKMK_WindowInteractions"></a>창 상호 작용  
  
### <a name="overview"></a>개요  
Visual Studio에서 사용 되는 두 개의 주 창 형식을 문서 편집기 및 도구 창입니다. 드물지만 가능한 모덜리스 대화 상자를 큰 됩니다. 이러한 옵션은 모든 모덜리스 셸에서 해당 패턴은 근본적으로 다릅니다. 이 섹션에서는 문서 창과 도구 창, 모덜리스 대화 상자 간의 차이 설명 합니다. 모달 대화 패턴에 대해서는 설명 [대화 상자의](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)합니다.  
  
### <a name="comparing-window-usage-patterns"></a>창 사용 패턴을 비교합니다.  
**문서** 잘 표시 문서 내에서 거의 항상 됩니다. "가운데 단계" 문서 편집기 제공 주위 추가 도구 창 정렬 합니다.  
  
A **도구 창** 가장 자주 IDE의 가장자리에 대해이 축소 보다 작은 경우 별도 창으로 표시 됩니다. 이 표시, 숨김, 또는 자동으로 숨길 수 있습니다. 그러나 경우에 따라 도구 창을 표시 됩니다는 물론 문서 내에서 선택을 취소 하 여는 **창/도킹** 속성 창에서. 이 인해 더 많은 부동산 하지만 또한 공통 설계 결정 사항: Visual Studio로 통합을 시도할 때 기능 도구 창이 나 문서 창에 표시 되는지 여부를 결정 해야 합니다.  
  
**모덜리스 대화 상자** Visual Studio에서 해서는 안 됩니다. 가장 모덜리스 대화 상자 부동 정의 따르면 인 도구 창 및 이런 방식으로 구현 해야 합니다. 모덜리스 대화 상자는 경우 셸의 측면에 도킹 일반 도구 창의 크기는 너무 제한에 허용 됩니다. 사용자는 보조 모니터에 대화 상자를 이동할 수 수 없는 경우에 사용할 수 있습니다.  
  
신중 하 게 컨테이너 유형에 대 한 필요한 생각 하면 됩니다. UI 디자인에 대 한 일반적인 사용 패턴 고려 사항 다음 테이블에 있습니다.  
  
||문서 창|도구 창|모덜리스 대화 상자|  
|-|---------------------|-----------------|---------------------|  
| **위치** | 항상 문서 내에 함께 배치 하 고 IDE의 가장자리에 도킹 하지 않습니다. 그 끌어올 수 있습니다 "off" 주 셸에서 별도로 부동 합니다. | 일반적으로 탭-도킹 IDE의 가장자리 주위 하지만 부동 수에 맞게 사용자 지정, 자동 숨김 (고정 해제 됨), 또는 수 잘 문서 내에서 도킹 합니다.|IDE에서 별도 큰 부동 창 |  
| **모델을 커밋** | *지연 된 커밋*<br /><br /> 사용자는 문서에 데이터를 저장 하기 위해 실행 해야 합니다는 **파일 &gt; 저장**, **다른 이름으로 저장**, 또는 **모두 저장** 명령 합니다. 문서 창에 다음 저장 중 하나에 커밋되기 되 고 "정리" 그 내부의 데이터가 개념이 명령입니다. 문서 창을 닫으면이 모든 콘텐츠는 디스크에 저장 되거나 손실 합니다. | *즉시 커밋*<br /><br /> 저장 하지는 모델입니다. 파일 편집에 도움이 되는 검사기 도구 창, 파일 활성 편집기 또는 디자이너에 열려 있어야 하며 편집기 또는 디자이너 소유 하 고 저장 합니다. | *연기 또는 즉시 커밋*<br /><br /> 대부분의 경우 큰 모덜리스 대화 변경 내용을 커밋하기 위해 조치를 취해야 하 고 대화 세션 내에서 모든 변경 내용을 롤백합니다 "취소" 작업을 허용 합니다.  이 도구 창에는 항상 즉시 커밋 모델 포함 한다는 점에서 도구 창에서 모덜리스 대화 상자를 구별 합니다. |  
| **표시 유형** | *열기/만들기 (파일) 및 닫기*<br /><br /> 문서 창을 열어 기존 문서 열기 또는 서식 파일을 사용 하 여 새 문서를 통해 수행 됩니다. 없습니다 "열기 \<특정 편집기 >" 명령입니다. | *숨기기 및 표시*<br /><br /> 단일 인스턴스 도구 창 숨겨지거나 표시 될 수 있습니다. 내용 및 도구 창 상태 유지 여부를 표시 또는 숨김 합니다. 다중 인스턴스 도구 창 수 수 닫혀으로 숨겨집니다. 다중 인스턴스 도구 창이 닫히면 내용과 상태 도구 창 내에서 삭제 됩니다. | *명령에서 시작*<br /><br /> 작업 기반 명령에서 대화 상자가 시작 됩니다. |  
| **인스턴스** | *다중 인스턴스*<br /><br /> 일부 편집기에도 동일한 파일을 둘 이상의 편집기에서 열려 있을 수 여러 편집기 같은 시간 및 다른 파일을 편집한에 열 수 있습니다 (사용 하는 **창 &gt; 새 창** 명령).<br /><br /> 단일 편집기가 편집 하 고 하나 또는 여러 개의 파일 (프로젝트 디자이너) 동시에 합니다. | *단일 또는 다중 instance*<br /><br /> 내용 (예: 속성 브라우저) 컨텍스트를 반영 합니다. 또는 다른 창 (작업 목록, 솔루션 탐색기)에 포커스/컨텍스트 푸시를 변경 합니다.<br /><br /> 단일 인스턴스와 다중 인스턴스 도구 창 모두 있으면 불가피 한 하지에 현재 문서 창에 연결 해야 합니다. | *단일 인스턴스* |  
| **예제** | **텍스트 편집기**, 코드 편집기와 같은<br /><br /> **디자인 화면**모델링 화면 또는 폼 디자이너와 같은<br /><br /> **대화 상자와 유사한 레이아웃을 제어**, 매니페스트 디자이너와 같은 | **솔루션 탐색기** 솔루션과 솔루션 내에 포함 된 프로젝트를 제공 합니다.<br /><br /> **서버 탐색기** 창에서 열려는 사용자가 선택 하는 서버 및 데이터 연결의 계층적 뷰를 제공 합니다. 한 쿼리와 데이터베이스 계층 구조에서 개체를 열기 문서 창이 열리고 쿼리를 편집할 수 있습니다.<br /><br /> **속성 브라우저** 문서 창 또는 다른 도구 창에 선택한 개체에 대 한 속성이 표시 됩니다. 계층적 그리드 보기 또는 복잡 한 대화 상자와 비슷한 컨트롤에 표시 됩니다 속성과 이러한 속성에 대 한 값을 설정 하는 데 사용할 수입니다. | |  
  
##  <a name="BKMK_ToolWindows"></a>도구 창  
  
### <a name="overview"></a>개요  
도구 창은 문서 창에서 발생 하는 사용자의 작업을 지원 합니다. Visual Studio를 제공 하 고 조작할 수 있는 기본 루트 개체를 나타내는 계층을 표시 하려면 사용할 수 있습니다.  
  
IDE에서 요소를 고려 하는 경우 만든이 수행 해야 합니다.  
  
-   작업에 적합 한 기존 도구 창을 사용 하 여 유사한 기능을 가진 새 캠페인을 만들지 않으며 와 비슷한 "도구" 또는 유사한 창이 나 기존 창을 피벗 허브로 설정 하 여 통합 될 수 없는 기능을 제공 하는 경우에 새 도구 창은 만들 해야 합니다.  
  
-   도구 창의 위쪽에 필요한 경우 표준 명령 모음을 사용 합니다.  
  
-   컨트롤 프레젠테이션 및 키보드 탐색을 위한 다른 도구 창은에 이미 있는 패턴으로 일관 되어야 합니다.  
  
-   다른 도구 창에서 컨트롤 표시와 일관 되어야 합니다.  
  
-   확인 문서 관련 도구 창 자동 표시 가능한 경우 부모 문서를 활성화 하는 경우에 표시 되도록 합니다.  
  
-   창 콘텐츠를 탐색할 수 키보드 (지원 화살표 키)를 확인 합니다.  
  
#### <a name="tool-window-states"></a>도구 창 상태  
Visual Studio 도구 창은 일부 (예: 자동 숨기기 기능) 사용자 활성화는 다양 한 상태의 있어야 합니다. 기타 상태와 같은 자동 표시, 도구 창을 올바른 컨텍스트에서 표시 되 고 필요 하지 않은 경우 숨기기를 허용 합니다. 총에서 5 개의 도구 창 상태 있습니다.  
  
-   **고정/고정** 도구 창을 문서 영역의 네 면 중 하나에 연결할 수 있습니다. 도구 창 제목 표시줄에 압정 아이콘으로 표시 됩니다. 도구 창을 셸 및 다른 도구 창은 가장자리를 따라 가로 또는 세로로 도킹 될 되었고 탭으로 연결할 수 있습니다.  
  
-   **자동으로 숨겨진** 도구 창은 고정이 해제 됩니다. 창을 보이지 문서 영역의 가장자리에는 tab (도구 창 및 아이콘의 이름)을 그대로 두고 슬라이드 수 있습니다. 사용자의 탭 위로 가져갈 때 도구 창을 아웃 슬라이드 합니다.  
  
-   **자동 표시** 도구 창은 편집기와 같은 UI 다른 조각 시작 되거나 포커스를 획득 하는 경우 자동으로 표시 합니다.  
  
-   **부동** 도구 창이 IDE 외부에서 마우스를 가져가고 합니다. 다중 모니터 구성에 유용합니다.  
  
-   **탭된 문서** 도구 창을 문서 내에서 잘 도킹 될 수 있습니다. 이것은 허용의 프레임 가장자리에 도킹 된 것 보다 더 많은 부동산 해야 하는 개체 브라우저와 같은 큰 도구 창, 적합 합니다.  
  
![Visual Studio의 도구 창 상태](~/extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Visual Studio의 도구 창 상태
  
#### <a name="single-instance-and-multi-instance"></a>단일 인스턴스 및 다중 인스턴스  
도구 창에는 단일 인스턴스 또는 다중 인스턴스입니다. 다중 인스턴스 도구 창 않을 수도 있습니다 하는 동안 일부 단일 인스턴스 도구 창은 현재 문서 창에 연결 수 있습니다. 다중 인스턴스 도구 창에 응답의 **창 &gt; 새 창** 명령을 실행 하 여 창의 새 인스턴스를 만들어야 합니다. 다음 그림에서는 창의 인스턴스 활성화 된 경우 새 창 명령을 사용 하도록 설정 하는 도구 창이 수행 합니다.  
  
![창의 인스턴스 활성화 되어 있을 때 ' 새 창 ' 명령을 사용 하도록 설정 하는 도구 창](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />창의 인스턴스 활성화 되어 있을 때 ' 새 창 ' 명령을 사용 하도록 설정 하는 도구 창  
  
단일 인스턴스 도구 창 숨김 또는 다중 인스턴스 도구 창 수 수 닫혀 뿐만 아니라 숨겨진 동안 표시 된 수 있습니다. 모든 도구 창 탭-연결 된, 부동 또는 다중 문서 MDI (인터페이스) 자식 창 (문서 창으로와 유사)으로 설정 도킹 될 수 있습니다. 모든 도구 창은 창 메뉴에서 적절 한 창 관리 명령에 응답 해야 합니다.  
  
![Visual Studio 창 메뉴의 창 관리 명령](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Visual Studio 창 메뉴의 창 관리 명령
  
#### <a name="document-specific-tool-windows"></a>문서 관련 도구 창  
일부 도구 창의 지정 된 유형의 문서를 기준으로 변경 하도록 설계 되었습니다. 이러한 창은 IDE에서 현재 문서 창에 적용할 수 있는 기능을 반영 하기 위해 지속적으로 업데이트 합니다.  
  
도구 창 내용이 선택한 편집기를 반영 하도록 변경의 예로 도구 상자 및 문서 개요. 이러한 창은 편집기 창에는 컨텍스트를 제공 하지 않는 포커스가 있을 때 워터 마크를 보여 줍니다.  
  
#### <a name="navigable-list-tool-windows"></a>탐색 가능한 목록 도구 창  
일부 도구 창의 상호 작용할 수 탐색 가능한 항목 목록을 표시 합니다. 이 유형의 창에 항상 있어야 목록에서 현재 항목에 대 한 피드백 창이 활성화 되어 있는 경우에 있습니다. 목록에 응답 하는 **GoToNextLocation** 및 **GoToPrevLocation** 또한 창에서 현재 선택 된 항목을 변경 하 여 명령  
  
탐색 가능한 목록 도구 창에는 솔루션 탐색기 및 찾기 결과 창 있습니다.  
  
### <a name="tool-window-types"></a>도구 창 유형  
  
#### <a name="common-tool-windows-and-their-functions"></a>공통 도구 창 및 해당 기능

**계층 구조 도구 창**
| 도구 창 | 함수 | 
| --- | --- | 
| 솔루션 탐색기 | 프로젝트, 기타 파일 및 솔루션 항목에 포함 된 문서의 목록을 표시 하는 계층적 트리. 프로젝트 내에 있는 항목의 표시는 프로젝트 형식 (예: 참조 기반, 디렉터리 기반 또는 혼합 모드 형식)를 소유 하는 패키지에 의해 정의 됩니다. | 
| 클래스 뷰 | 클래스 및 문서를 독립적으로 파일 자체의 작업 집합에 다양 한 요소는 계층적 트리. | 
| 서버 탐색기 | 솔루션에 있는 모든 서버 및 데이터 연결을 표시 하는 계층적 트리. | 
| 문서 개요 | 현재 문서의 계층 구조입니다. | 

**표 도구 창**
| 도구 창 | 함수 | 
| --- | --- | 
| 속성 | 이러한 속성을 편집 하려면 값 선택 함께 선택한 개체에 대 한 속성의 목록을 표시 하는 표입니다. | 
| 작업 목록 | 사용자 만들기/편집/삭제 작업 및 메모 수 있게 하는 표입니다. | 

**콘텐츠 도구 창**
| 도구 창 | 함수 | 
| --- | --- | 
| 도움말 | 사용자가 다양 한 "어떻게 할까요?"에서 도움말을 보는 방법에 대 한 액세스를 허용 하는 창 비디오 MSDN 포럼입니다. | 
| 동적 도움말 | 도움말 항목에 현재 선택 영역에 적용할 수 있는 링크를 표시 하는 도구 창입니다. | 
| 개체 브라우저 | 계층적 개체 및 구성 요소는 왼쪽된 창 개체의 속성 및 메서드의 오른쪽 열에서 목록 사용 하 여 두 개의 열 프레임셋 합니다. | 

**대화 상자 도구 창**
| 도구 창 | 함수 | 
| --- | --- | 
| Find | 사용자 찾기 또는에서 찾기 및 바꾸기 솔루션 내에서 다양 한 파일 수 있게 하는 대화 상자입니다. |
| 고급 찾기 | 사용자 찾기 또는에서 찾기 및 바꾸기 솔루션 내에서 다양 한 파일 수 있게 하는 대화 상자입니다. | 

**다른 도구 창은**
| 도구 창 | 함수 | 
| --- | --- | 
| 도구 상자 | 모든 디자이너에 대 한 일관성 있는 끌기 소스를 제공 하는 디자인 화면에 끌어 놓을 수는 요소를 저장 하는 데 사용 되는 도구 창입니다. |
| 시작 페이지 | 개발자 뉴스, Visual Studio 도움말 및 최근에 사용한 프로젝트 피드에 액세스할 수 있는 Visual Studio로 사용자의 포털입니다. 사용자에서 StartPage.xaml 파일을 복사 하 여 사용자 지정 시작 페이지를 만들 수도 있습니다는 "Common7\IDE\StartPages\" StartPages 폴더에 Visual Studio 문서 디렉터리 XAML을 직접 편집 하거나 Visual Studio 또는 다른 코드 편집기에서 열거나 Visual Studio 프로그램 파일 디렉터리입니다. | 

**디버거 도구 창**
| 도구 창 | 함수 | 
| --- | --- |
| 자동 ||  
| 직접 실행 ||  
| 출력 | 출력 창 텍스트 이벤트 또는 상태 선언할 수 있을 때마다 사용할 수 있습니다. |  
| 메모리 ||  
| 중단점 ||  
| 실행 중 ||  
| 문서 ||  
| 호출 스택 ||  
| 로컬 ||  
| 조사식 ||  
| 디스어셈블리 ||  
| 레지스터 ||  
| 스레드 ||  
  
##  <a name="BKMK_DocumentEditorConventions"></a>편집기 도움말 표기법  
  
### <a name="document-interactions"></a>문서 상호 작용  
"문서 well" IDE 내에서 가장 큰 공간 이며 여기서 사용자 일반적으로 집중적 주의 지원 추가 도구 창으로 해당 작업을 완료 해야 합니다. 문서 편집기에는 사용자가 열리고 Visual Studio 내에서 저장 하는 작업의 기본 단위를 나타냅니다. 솔루션 탐색기 또는 다른 활성 계층 구조 창에 연결 된 선택의 강력한 개념이 유지 됩니다. 사용자는 이러한 계층 구조 창 중 하나를 가리키고 솔루션, 프로젝트 또는 Visual Studio 패키지에서 제공 하는 다른 루트 개체에 문서의 포함 된 활동 및 활동과 관계를 알 수 있어야 합니다.  
  
문서를 편집 하려면 일관 된 사용자 환경이 필요 합니다. 사용자 작업 대신 찾기 명령 및 창 관리에 집중할 수 있도록 해당 문서 유형을 편집을 위해 사용자 작업에 가장 잘 맞는 문서 보기 전략을 선택 합니다.  
  
#### <a name="common-interactions-for-the-document-well"></a>문서 저장소에 대 한 일반적인 상호 작용  
  
-   에 공통 일관성 있는 상호 작용 모델을 유지 관리 **새 파일** 및 **열려 있는 파일** 발생 합니다.  
  
-   문서 창이 열릴 때 관련된 창 및 메뉴의 관련된 기능을 업데이트 합니다.  
  
-   메뉴 명령을 같은 일반적인 메뉴에 적절 하 게 통합 되어 **편집**, **형식**, 및 **보기** 메뉴. 상당한 양의 특수 명령을 사용할 수 있으면 새 메뉴 만들 수 있습니다. 이 새 메뉴는 문서에 포커스가 있을 때만 표시 되어야 합니다.  
  
-   포함된 된 도구 모음 편집기의 맨 위쪽에 배치 될 수 있습니다. 이 편집기 외부에서 표시 되는 별도 도구 모음을 지정 하는 것이 좋습니다.  
  
-   솔루션 탐색기 또는 유사한 활성 선택 영역을 항상 유지 계층 구조 창.  
  
-   솔루션 탐색기에서 문서를 두 번 클릭 하면 동일한 작업을 수행 해야 **열려**합니다.  
  
-   사용자를 재정의 하거나 사용 하 여 특정된 문서 형식을 대 한 기본 작업을 다시 설정할 수 있어야 문서 종류에 둘 이상의 편집기를 사용할 수 있는 경우는 **프로그램** 파일을 마우스 오른쪽 단추로 클릭 하 고 선택 하 여 대화 상자 **연결 프로그램** 바로 가기 메뉴에서.  
  
-   문서에는 마법사를 제대로 작성 하지 않아도 합니다.  
  
### <a name="user-expectations-for-specific-document-types"></a>특정 문서 유형에 대 한 사용자 기대  
각 보안 개체 집합의 동일한 형식의 다른 항목과 일치 하는 상호 작용와 문서 편집기 여러 가지 기본 유형이 있습니다.  
  
-   **텍스트 기반 편집기:** 코드 편집기, 로그 파일  
  
-   **디자인 화면:** WPF 폼 디자이너, Windows forms  
  
-   **대화 상자 스타일 편집기:** 매니페스트 디자이너, 프로젝트 속성  
  
-   **모델 디자이너:** 워크플로 디자이너, codemap, 아키텍처 다이어그램, 진행  
  
문서를 함께 사용 하는 비 편집기 유형은 여러 가지가 있습니다. 문서 자체를 편집 하지 않는, 문서 창에 대 한 표준 상호 작용에 따라 필요가 있습니다.  
  
-   **보고서:** IntelliTrace 보고서, Hyper-v 보고서 프로파일러 보고서  
  
-   **대시보드:** 진단 허브  
  
#### <a name="text-based-editors"></a>텍스트 기반 편집기  
  
-   문서에 문서를 열지 않고도 미리 볼 수 있도록 미리 보기 탭 모델에 참여 합니다.  
  
-   문서 구조는 문서 개요와 같은 도우미 도구 창으로 표시할 수 있습니다.  
  
-   IntelliSense (필요한 경우)는 다른 코드 편집기와 일관성 있게 동작 합니다.  
  
-   팝업 또는 보조 UI CodeLens 같은 기존 유사한 UI에 대 한 유사한 스타일 및 패턴을 따릅니다.  
  
-   상태 표시줄 또는 문서 위쪽에 있는 정보 표시줄 컨트롤에서 문서 상태에 대 한 메시지가 표시 됩니다.  
  
-   사용자의 글꼴 및 색을 사용 하 여 모양을 사용자 지정할 수 있어야는 **도구 > 옵션** 공유 글꼴 및 색 페이지 또는 특정 편집기 페이지입니다.  
  
#### <a name="design-surfaces"></a>디자인 화면  
  
-   빈 디자이너 시작 하는 방법을 나타내는 화면에 워터 마크를 사용 해야 합니다.  
  
-   보기 전환 메커니즘은 코드 편집기 또는 창 모두와 상호 작용을 허용 하 여 문서 창 내에서 탭을 열려면 두 번 클릭과 같은 기존 패턴을 따릅니다.  
  
-   디자인 화면에 요소를 추가 해야 도구 상자를 통해 매우 특정 도구 창을 필요한 경우를 제외 합니다.  
  
-   화면에서 항목을 일관 된 선택 모델 될 예정입니다.  
  
-   포함 된 도구 모음 문서 관련 명령을, 일반적으로 해당 되지 명령의와 같은 포함 **저장**합니다.  
  
#### <a name="dialog-style-editors"></a>편집기 대화 상자 스타일  
  
-   컨트롤 레이아웃 일반 대화 상자 레이아웃 규칙을 따라야 합니다.  
  
-   편집기 내에서 탭 문서 탭의 모양을 일치 해서는 안, 두 개의 내부 탭 허용 된 스타일 중 하나를 일치 해야 합니다.  
  
-   사용자가 해당 하며 키보드를 사용 하 여 컨트롤과 상호 작용할 수 있어야 사용 하거나 표준 니모닉을 사용 하 여 편집기를 활성화 및 컨트롤을 통해 또는 탭 이동 합니다.  
  
-   디자이너는 일반 모델 저장을 사용 해야 합니다. 다른 단추는 적절 한 수도 있지만 없음 전반적인 저장 또는 커밋 단추는 화면에 배치 해야 합니다.  
  
#### <a name="model-designers"></a>모델 디자이너  
  
-   빈 디자이너 시작 하는 방법을 나타내는 화면에 워터 마크를 사용 해야 합니다.  
  
-   디자인 화면에 요소를 추가 하는 도구 상자를 통해 수행 되어야 합니다.  
  
-   화면에서 항목을 일관 된 선택 모델 될 예정입니다.  
  
-   포함 된 도구 모음 문서 관련 명령을, 일반적으로 해당 되지 명령의와 같은 포함 **저장**합니다.  
  
-   범례는 암시적 또는 워터 마크는 화면에 나타날 수 있습니다.  
  
-   사용자를 사용 하 여 글꼴 및 색의 모양을 사용자 지정할 수 있어야는 **도구 > 옵션** 공유 글꼴 및 색 페이지 또는 특정 편집기 페이지입니다.  
  
#### <a name="reports"></a>보고서  
  
-   보고서는 일반적으로 정보 전용 및 모델 저장에에서 참여 하지 않습니다. 그러나 다른 관련 정보 또는 확장 및 축소 된 섹션에는 링크와 같은 상호 작용을 포함 될 수 있습니다.  
  
-   화면에서 대부분의 명령은 하이퍼링크, 단추 하지 이어야 합니다.  
  
-   레이아웃은 헤더를 포함 하 고 표준 보고서 레이아웃 지침을 따라 해야 합니다.  
  
#### <a name="dashboards"></a>대시보드  
  
-   대시보드 상호 작용 모델 자체에 필요는 없지만 여러 가지 다른 도구를 제공 하는 수단으로 사용 합니다.  
  
-   모델 저장에에서 참여 하지 않습니다.  
  
-   사용자가 편집기를 활성화 하 고 컨트롤 tab 키를 사용 하거나 표준 니모닉을 사용 하 여 키보드만 사용 하 여 컨트롤과 상호 작용할 수 있어야 합니다.  
  
##  <a name="BKMK_Dialogs"></a>대화 상자  
  
### <a name="introduction"></a>소개  
Visual Studio에서 대화 상자 일반적으로 하나의 개별 사용자의 작업 단위를 지원 해야 및 다음 해제할 수 있습니다.  
  
대화가 필요를 확인 한 순서 대로 세 개의 선택 사용할 수 있습니다.  
  
1.  Visual Studio의 공유 대화 상자 중 하나에 해당 기능을 통합 합니다.  
  
2.  기존 비슷한 대화에서 발견 되는 패턴을 사용 하 여 사용자 고유의 대화 상자를 만듭니다.  
  
3.  새 대화 상자, 다음과 같은 상호 작용 및 레이아웃 지침을 만듭니다.  
  
이 섹션에서는 Visual Studio 워크플로 내에서 해당 대화 패턴 및 대화 상자 디자인에 대 한 일반적인 규칙을 선택 하는 방법에 설명 합니다.  
  
### <a name="themes"></a>테마  
Visual Studio의 대화 상자는 두 가지 기본 스타일 중 하나를 따르십시오.  
  
#### <a name="standard-unthemed"></a>표준 (unthemed)  
대화 상자는 대부분 표준 유틸리티 대화 상자 되며 unthemed 이어야 합니다. "최신" 단추 스타일된 또는 컨트롤 만들려고 하거나 템플릿을 다시 만들면 공용 컨트롤 하지 마십시오. 컨트롤 및 chrome 모양에 따라 [대화 상자에 대 한 표준 Windows 데스크톱 상호 작용 지침](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)합니다.  
  
#### <a name="themed"></a>테마  
Specialty "서명" 대화 상자는 테마를 적용할 수 있습니다. 테마가 지정 된 대화 상자에 고유한 모양을 제공 하는 스타일와 관련 된 몇 가지 특별 한 상호 작용 패턴에는 합니다. 테마 대화 상자에 이러한 요구 사항을 충족 하는 경우에:  
  
-   대화 상자는 표시 되 고 자주 또는 많은 사용자가 사용 하는 일반적인 환경을 (예를 들어는 **새 프로젝트** 대화 상자.  
  
-   두드러진 제품 브랜드 요소를 포함 하는 대화 상자 (예를 들어는 **계정 설정** 대화).  
  
-   테마가 지정 된 다른 대화 상자를 포함 하는 큰 흐름의 필수적인 부분으로 된 대화 상자가 나타납니다 (예를 들어는 **연결 된 서비스 추가** 대화).  
  
-   대화 상자에 역할을 전략적 수준을 높이 거 나 제품 버전이 구별 되는 상태로의 중요 한 부분입니다.  
  
테마가 지정 된 대화를 만들 때 적절 한 환경 색을 사용 하 고 올바른 레이아웃 및 상호 작용 패턴을 따릅니다. (참조 [Visual Studio에 대 한 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)  
  
### <a name="dialog-design"></a>대화 상자 디자인  
다음 요소를 고려해 설정 하는 잘 설계 된 대화 상자:  
  
-   지원 되는 사용자 작업  
  
-   대화 상자 텍스트의 스타일, 언어 및 용어  
  
-   컨트롤 선택 및 UI 규칙  
  
-   시각적 레이아웃 사양 및 컨트롤 맞춤  
  
-   키보드 액세스  
  
#### <a name="content-organization"></a>콘텐츠 구성  
대화의 이러한 기본 형식 간의 차이점을 고려해 야 합니다.  
  
-   [간단한 대화 상자](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) 단일 모달 창에서 컨트롤을 제공 합니다. 프레젠테이션의 필드 선택 또는 아이콘 표시줄을 포함 하 여 복잡 한 컨트롤 패턴의 변형을 포함 될 수 있습니다.  
  
-   [대화 상자를 계층화](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) 는 단일 UI 컨트롤의 여러 그룹을 구성 하는 경우 화면 자원을 최대한 활용 하기 위해 사용 됩니다. 대화의 그룹을 "계층" 탭 컨트롤, 탐색 목록 컨트롤 또는 단추를 통해 사용자 지정된 된 순간에 볼 수는 그룹화를 선택할 수 있도록 합니다.  
  
-   [마법사](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) 논리는 일련의 작업의 완료 될 때까지 단계를 통해 사용자를 전송 하는 데 유용 합니다. 여러 선택 항목은 다른 워크플로 ("분기") 이전 패널에서 선택에 종속 된 경우에 따라 소개 하는 순차적 패널에 제공 됩니다.  
  
####  <a name="BKMK_SimpleDialogs"></a>간단한 대화 상자  
간단한 대화 항목이 단일 모달 창에서 컨트롤의 표시 합니다. 이 프레젠테이션 필드 선택과 같은 복잡 한 컨트롤 패턴, 변형 포함 될 수 있습니다. 간단한 대화 상자에 대 한 복잡 한 제어 그룹화 하는 데 필요한 모든 특정 레이아웃 뿐만 아니라 표준 일반적인 레이아웃을 따릅니다.
  
![> 만들 강력한 이름 키는 Visual Studio에서 간단한 대화의 예입니다.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />만들 강력한 이름 키는 Visual Studio에서 간단한 대화의 예입니다.
  
####  <a name="BKMK_LayeredDialogs"></a>계층화 된 대화 상자  
계층화 된 대화 상자 탭, 대시보드 및 포함 된 트리를 포함 합니다. UI의 한 부분에 제공 되는 컨트롤의 여러 그룹에 있는 경우 공간을 최대화 하기 위해 사용 됩니다. 사용자는 한 번에 볼 수는 그룹화를 선택할 수 있도록 필드 그룹은 계층적입니다.  
  
가장 간단한 경우 그룹화 사이의 전환을 위한 메커니즘 탭 컨트롤입니다. 사용 가능한 여러 대체 있습니다. Prioritizing 및 가장 적합 한 스타일을 선택 하는 방법에 대 한 레이어 참조 하십시오.  
  
**도구 &gt; 옵션** 대화 상자는 포함 된 트리를 사용 하 여 계층화 된 대화 상자:  
  
![도구 > 옵션은 Visual Studio의 계층화 된 대화의 예입니다.](~/extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />도구 > 옵션은 Visual Studio의 계층화 된 대화의 예입니다.
  
####  <a name="BKMK_Wizards"></a>마법사  
마법사는 논리는 일련의 단계를 통해 사용자는 작업의 완료에 전송 하는 데 유용 합니다. 여러 선택 항목 순차적 패널에 제공 되 고 사용자는 다음 단계로 진행 하기 전에 각 단계를 계속 해야 합니다. 충분 한 기본값 사용을 한 번의 **마침** 단추를 사용할 수 있습니다.  
  
 모달 마법사를 사용 하 여 작업에 대 한입니다.  
  
-   사용자의 선택에 따라 다양 한 경로 제공 하는 분기가 포함  
  
-   이후 단계 위의 단계에서 사용자 입력에 따라 달라 집니다 단계 간의 종속성을 포함  
  
-   제공 된 선택 사항 각 단계에서 가능한 결과 설명 하기 위해 UI를 사용 해야 함을 충분히 복잡  
  
-   일련의 단계에 변경한 내용이 커밋되기 전에 전체에서 완료 하는 데 필요한 트랜잭션  
  
### <a name="common-conventions"></a>공통 규칙  
최적의 디자인과 기능을 대화 상자를 얻기 위해 대화 크기, 위치, 표준, 제어 구성 및 맞춤, UI 텍스트, 제목 표시줄, 컨트롤 단추 및 선택 키에 이러한 규칙을 따릅니다.  
  
레이아웃 관련 지침을 참조 하십시오. [Visual Studio에 대 한 레이아웃](../../extensibility/ux-guidelines/layout-for-visual-studio.md)합니다.  
  
#### <a name="size"></a>크기  
대화 상자는 최소 1024 x 768 화면 해상도 맞도록 해야 하 고 초기 대화 상자 크기가 900 x 700 픽셀을 넘지 않아야 합니다. 대화 상자, 크기 조정 가능한 있지만 필요 하지 않습니다.  
  
크기 조정 가능한 대화 상자에 대 한 두 가지 권장 사항 가지가 있습니다.  
  
1.  최소 크기는 대화 상자 컨트롤에 대 한 최적화에 대 한 정의 클리핑 없이 설정 하 고 적절 한 지역화 성장에 맞게 조정 합니다.  
  
2.  사용자 확장할 크기 세션 간에 유지 됩니다. 예를 들어 사용자 150% 수 있는 대화 상자를 확장 하는 경우 대화 상자의 이후 시작 150%로 표시 됩니다.  
  
#### <a name="position"></a>위치  
대화 상자를 처음 시작할 대 IDE 내에서 가운데에 맞출지 나타나야 합니다. 크기 조정이 불가능 대화의 마지막 위치 이후에 시작에 집중 나타납니다 유지 될 필요 하지 않습니다. 

크기 조정 가능한 대화 상자에 대 한 크기 이후에 시작에 유지 되어야 합니다. 크기 조정 가능한 모달 대화 상자에 대 한 위치 유지 될 필요가 없습니다. IDE 내에서 가운데에 표시 하면 사용자의 디스플레이 구성 변경 될 때 예기치 않은 또는 사용할 수 없는 위치에 표시 되는 대화의 가능성 수 없습니다. 

변경 될 수 있는 모덜리스 대화 상자에 대 한 큰 워크플로의 필수적인 요소로 서 대화 상자를 자주 사용 될 수 이후에 시작에 사용자의 위치를 유지 해야 합니다.  
  
오른쪽 맨 위에 있는 대화 상자를 중첩할 해야 대화 상자 해야 다른 대화 상자를 생성 하는 경우와 한다는 새 위치로 이동 했으므로 사용자에 게 명확 하도록 부모에서 아래쪽입니다.  
  
#### <a name="modality"></a>형식  
Modal 되 고 완료 하거나 계속 하기 전에 대화 상자를 취소 하는 데 필요한 사용자를 의미 합니다. 모달 대화 상자에 환경의 다른 부분과 상호 작용에서 사용자를 차단 하므로 기능의 작업 흐름 해야 같이 너무 많이 사용 가능한 합니다. 모달 작업이 필요한 경우 Visual Studio에 다양 한 공유 대화 상자에 기능을 통합할 수 있습니다. 새 대화 상자를 만들어야 하는 경우 유사한 기능을 가진 기존 대화의 상호 작용 패턴을 따릅니다.  
  
사용자가 한 번에 두 개의 작업을 수행 해야 하는 경우와 같은 **찾을** 및 **대체** 새 코드를 작성 하는 동안 대화 상자 해야 모덜리스 사용자 서로 쉽게 전환할 수 있도록 합니다. 일반적으로 visual Studio 도구 창을 사용 하 여 이러한 종류의 편집기를 지 원하는 연결 된 작업에 대 한 합니다.  
  
#### <a name="control-configuration"></a>제어 구성  
Visual Studio에서 같은 작업을 수행 하는 기존 컨트롤 구성으로 일관 되어야 합니다.  
  
#### <a name="title-bars"></a>제목 표시줄  
  
-   제목 표시줄의 텍스트를 실행 하는 명령 이름을 반영 해야 합니다.  
  
-   대화 상자 제목 표시줄에 아이콘이 없는 사용 해야 합니다. 하나는 시스템 필요 하는 경우에는 Visual Studio 로고를 사용 합니다.  
  
-   대화 상자를 사용 해야 최소화 나 최대화 단추입니다.  
  
-   제목 표시줄에 도움말 단추는 더 이상 사용 되지 않습니다. 이러한 새 대화 상자에 추가 하지 마십시오. 존재 않도록 하는 경우 개념적으로 작업에 관련 된 도움말 항목을 시작 해야 합니다.  
  
 ![Visual Studio 대화 상자에 제목 표시줄에 대 한 지침 사양](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Visual Studio 대화 상자에 제목 표시줄에 대 한 지침 사양
  
#### <a name="control-buttons"></a>컨트롤 단추  
일반적으로 **확인**, **취소**, 및 **도움말** 대화 상자의 오른쪽 아래에 단추를 가로로 정렬 해야 합니다. 대화 상자에 컨트롤 단추와 visual 혼동을 발생 하 게 되는 대화 상자 아래쪽에 있는 여러 단추를 포함 하는 경우 대체 세로 스택을 허용 됩니다.  
  
![Visual Studio 대화 상자에서 단추 컨트롤에 대 한 허용 가능한 구성](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Visual Studio 대화 상자에서 단추 컨트롤에 대 한 허용 가능한 구성
  
대화 상자에는 기본 컨트롤 단추를 포함 해야 합니다. 기본적으로 사용 하도록 최상의 명령을 확인 하려면 (우선 순위 대로 나열) 다음 옵션 중에서 선택 합니다.  
  
-   기본적으로 안전 하 고 가장 안전한 명령을 선택 합니다. 즉, 데이터 손실을 방지 하 고 의도 하지 않은 시스템 액세스를 방지 하는 가능성이 가장 높은 명령을 선택 합니다.  
  
-   데이터가 손실 되 고 보안 요인 하지 않으면 편의에 따라 기본 명령을 선택 합니다. 기본적으로 가능성이 가장 높은 명령을 포함 하 여 대화 상자에서 자주 또는 반복 작업을 지 원하는 경우 사용자의 워크플로 향상 됩니다.  
  
기본 명령에 대 한 영구적으로 삭제 작업을 선택 하지 마십시오. 이러한 명령을 있는 경우 더 안전 하 게 명령을 대신 기본으로 선택 합니다.  
  
#### <a name="access-keys"></a>선택 키  
에 대 한 선택 키를 사용 하지 마십시오 **확인**, **취소**, 또는 **도움말** 단추입니다. 기본적으로 이러한 단추 바로 가기 키에 매핑됩니다.  
  
| 단추 이름 | 키보드 바로 가기 키 |  
| --- | --- |  
| 확인 | Enter 키 |  
| 취소 | Esc |  
| 도움말 | F1 |  
  
#### <a name="imagery"></a>이미지  
대화 상자에서 이미지를 제한적으로 사용 합니다. 대화 상자에서 공간을 사용 하 여 단순히 큰 아이콘을 사용 하지 마십시오. 경고 아이콘이 또는 애니메이션 상태와 같은 사용자에 게 메시지를 전달의 중요 한 부분이 있는 경우에 이미지를 사용 합니다.  
  
###  <a name="BKMK_PrioritizingAndLayering"></a>우선 순위 지정 및 레이어로 표시  
  
#### <a name="prioritizing-your-ui"></a>UI를 우선 순위 지정  
forefront를 특정 UI 요소를 가져와서 고급 동작 및 대화 상자에 옵션 (모호한 명령 포함)를 배치 해야 할 수도 있습니다. forefront,에 대 한 공간을 마련 하 고 있으므로 표시 텍스트 레이블이 있는 UI에서 기본적으로 대화 상자를 표시 하는 경우 일반적으로 사용 되는 기능을으로 가져옵니다.  
  
#### <a name="layering-your-ui"></a>UI를 레이어로 표시  
대화 상자는 필요 하지만 관련된 기능을 사용자에 게 표시 되 면 간단한 대화 상자에 표시할 수 있는 기능을 확인 한 경우 UI 레이어 해야 합니다. Visual Studio를 사용 하는 가장 일반적인 쌓기 메서드는 탭 및 hallways 또는 대시보드입니다. 경우에 따라 확장 하거나 축소할 수 있는 영역에 적합할 수 있습니다. 적응 UI 일반적으로 Visual Studio에서 권장 되지 않습니다.  
  
유사한 탭 컨트롤을 통해 UI를 계층화 하는 다양 한 방법 단점이 있습니다. 상황에 맞는 쌓기 기술을 선택 했는지 확인 하려면 아래 목록을 검토 합니다.  
  
##### <a name="tabbing"></a>탭 이동  
  
| 스위칭 메커니즘 | 장점 및 적절 한 사용 | 단점 및 부적절 한 사용 |  
| --- | --- | --- |  
| 탭 컨트롤 | 관련된 집합으로 대화 상자 페이지를 논리적으로 그룹화 합니다.<br /><br />5 보다 작은 (또는 탭 대화 상자에서 한 행 크기에 맞는 수)에 대 한 유용한 대화 상자에서 관련된 컨트롤의 페이지<br /><br />탭 레이블 짧아야: 콘텐츠를 쉽게 식별할 수 있는 단어 하나 또는 두 개의<br /><br />일반적인 시스템 대화 상자 스타일<br /><br />예: **파일 탐색기 &gt; 항목 속성** | 짧은 설명 레이블이 하기가 어려울 수 있습니다.<br /><br />일반적으로 지난 한 대화 상자에 5 개 탭 적절 하지 않습니다.<br /><br />부적절 한 행 (사용 하 여 대체 쌓기 기법에) 대해 너무 많은 탭이 있는 경우<br /><br />확장 가능 하지 않습니다 |  
| 사이드바 탐색 | 탭 보다 더 많은 범주를 수용할 수 있는 간단한 전환 장치<br /><br />범주 (계층 구조)의 단순 목록<br /><br />확장 가능<br /><br />예: **사용자 지정... &gt; 추가 명령** | 그룹이 세 대 보다 적은 경우 가로 공간의 좋은 사용 되지 않습니다<br /><br />작업을 드롭다운 목록에 적합 한 더 잘 수 있습니다. |  
| 트리 컨트롤 | 무제한 범주에 대 한 허용<br /><br />그룹화 및/또는 범주 계층 구조에 대 한 허용<br /><br />확장 가능<br /><br />예: **도구 &gt; 옵션** | 많이 중첩 된 계층 구조는 과도 한 가로 스크롤 발생할 수 있습니다.<br /><br />Visual Studio에 트리 보기는 과도할 정도로 사용 되는 |  
| 마법사 | 작업 완료 된 사용자, 순차적 작업 기반 단계를 안내 하는 여는 데 도움이 됩니다: 마법사는 상위 수준 작업 나타내고 개별 패널은 전반적인 작업을 수행 하는 데 필요한 하위 작업<br /><br />작업에는 경우 사용자 할 여러 명의 편집기를 사용 하 고 작업을 완료 하는 windows 도구으로 Ui 경계를 이동 하는 경우에 유용함<br /><br />분기 작업 해야 하는 경우에 유용함<br /><br />작업 단계 간에 종속성을 포함 하는 경우에 유용함<br /><br />결정 분기와 유사한 작업을 여러 개의 서로 다른 유사한 대화 상자 수를 줄이는 한 대화에 제공할 수 있는 경우에 유용함 | 순차 워크플로 필요 하지 않은 모든 작업에 대 한 부적절 한<br /><br />무력화 및 너무 많은 단계를 통해 마법사에 혼란 사용자 지정할 수 있습니다.<br /><br />기본적으로 마법사 화면 자원을 제한합니다 |  
  
##### <a name="hallways-or-dashboards"></a>Hallways 또는 대시보드  
Hallways 및 대시보드는 대화 상자 또는 역할을 가리키는 다른 대화 상자 및 창 시작 하는 패널입니다. 잘 디자인 된 "복도"만 가장 일반적인 옵션, 명령 및 사용자가 일반적인 작업을 쉽게 수행할 수 있도록 설정에 즉시 표시 합니다. 여기서 실제 복도 제공 입구 방 뒤에 액세스할 수와 같은 보다 덜 일반적인 UI 별도 "장소" (종종 다른 대화 상자)의 주 복도에서 액세스할 수 있는 관련된 기능에 수집 됩니다.  
  
또는 UI를 하지 않고 단순히 대시보드는 별도 위치에 대 한 보다 덜 일반적인 기능을 리팩터링 단일 컬렉션에서 모든 사용 가능한 기능을 제공 합니다.  
  
![Outlook에서 추가 UI를 노출 하기 위한 복도 개념](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Outlook에서 추가 UI를 노출 하기 위한 복도 개념
  
##### <a name="adaptive-ui"></a>적응 UI  
사용에 따라 표시 또는 숨기기 UI 또는 사용자 자체 보고 된 환경은 또 다른 방법의 다른 부분을 숨기 려 필요 UI를 표현 합니다. 이 권장 되지 않습니다 Visual Studio에서 표시 하거나 숨기려면 UI 시기를 결정 하는 것에 대 한 알고리즘은 까다로울 수, 하 고 규칙 일부 경우에 대 한 잘못 된 항상 됩니다.  
  
##  <a name="BKMK_Projects"></a>프로젝트  
  
### <a name="projects-in-the-solution-explorer"></a>솔루션 탐색기의 프로젝트  
대부분의 프로젝트와 참조 기반, 디렉터리 기반 또는 혼합 분류 됩니다. 솔루션 탐색기에서 세 가지 유형의 프로젝트를 모두 동시에 지원 됩니다. 프로젝트 작업에서 사용자 환경의 루트 창이 수행이 됩니다. 다른 프로젝트 노드 옵션은 참조, 디렉터리 또는 혼합 모드 형식 프로젝트에 프로젝트 관련 사용자 패턴으로 수렴 하기 전에 시작 지점으로 적용 해야 하는 일반적인 상호 작용 패턴이 있습니다.  
  
프로젝트 항상 수행 해야합니다.  
  
-   프로젝트 내용을 구성 하기 위해 프로젝트 폴더를 추가 하는 기능을 지원 합니다.  
  
-   프로젝트 지 속성에 대 한 일관 된 모델을 유지 관리  
  
프로젝트는 일관성 있는 상호 작용 모델에 대 한 유지 관리도 해야 합니다.  
  
-   프로젝트 항목 제거  
  
-   문서 저장  
  
-   프로젝트 속성 편집  
  
-   대체 보기에서 프로젝트를 편집합니다.  
  
-   끌어서 놓기 작업  
  
### <a name="drag-and-drop-interaction-model"></a>끌어서 놓기 상호 작용 모델  
프로젝트를 일반적으로 자체 기반 참조로 (지속할 수 저장소의 프로젝트 항목에 대 한 참조만), 분류 디렉터리 기반 (물리적으로 프로젝트 항목만 지속할 수 저장 프로젝트의 계층 구조 내에서) 또는 혼합 (참조 또는 실제 항목을 지속할 수)입니다. 모든 세 가지 유형의 프로젝트를 동시에 내 수용 IDE는 **솔루션 탐색기**합니다.  
  
끌어서 놓기 관점에서 볼 때 다음과 같은 특징이 프로젝트 내에서 각 형식에 적용 해야는 **솔루션 탐색기**:  
  
-   **프로젝트 기반 참조:** 중요 한 점은 주위 저장소에 있는 항목에 대 한 참조는 프로젝트를 끌어옵니다. 참조 기반 프로젝트 이동 작업에 대 한 소스로 역할을 하는 경우에 프로젝트에서 항목에 대 한 참조를 제거 해야 것. 항목 하드 드라이브에서 실제로 삭제 해야 합니다. 프로젝트 기반 참조 이동 (또는 복사) 작업에 대 한 대상으로 역할을 하는 경우 항목의 전용 복사본을 만들지 않고 원래 소스 항목에 대 한 참조를 추가 해야 합니다.  
  
-   **프로젝트 디렉터리 기반:** 는 끌어서 놓기 관점에서 프로젝트를 참조 하지 않고 실제 항목 주위 끌어옵니다. 이동 작업에 대 한 소스로 디렉터리 기반 프로젝트 역할을 하는 경우 프로젝트에서 제거할 수 있을 뿐만 아니라 하드 드라이브에서 실제 항목 삭제를 종료 해야 합니다. 이동 (또는 복사) 작업에 대 한 대상 디렉터리 기반 프로젝트 역할을 하는 경우 대상 위치에서 소스 항목의 복사본을 확인 해야 것입니다.  
  
-   **혼합 대상 프로젝트:** 는 끌어서 놓기 관점에서 이러한 유형의 프로젝트의 동작 (저장소에 있는 항목 참조) 또는 항목 자체 끌고 있는 항목의 특성에 기반 합니다. 실제 항목 및 참조에 대 한 올바른 동작 위에 설명 되어 있습니다.  
  
한 가지 유형의 프로젝트에 있는 경우는 **솔루션 탐색기**, 하면 끌어서 놓기 작업 간단 하 게 될 것입니다. 각 프로젝트 시스템 끌어서 놓기 동작을 정의 하는 기능을 사용 하므로 특정 지침 (Windows 탐색기 끌어서 놓기 동작에 따라) 사용자 환경을 예측할를 보장 하기 위해 수행 해야 합니다.  
  
-   는 수정 되지 않은 끌기 작업의 **솔루션 탐색기** 이동 작업을 유발 (때 Ctrl 또는 Shift 키 아닙니다는 누른 상태).  
  
-   Shift 드래그 작업 해야도 이동 작업이 생성 됩니다.  
  
-   Ctrl + 드래그 작업을 복사 작업을 생성 해야 합니다.  
  
-   프로젝트 기반 참조와 혼합 시스템 소스 항목에 링크 (또는 참조)를 추가 하는 개념을 지원 합니다. 이러한 프로젝트는 끌어서 놓기 작업의 대상이 되 면 (때 **Ctrl + Shift** 를 누르고), 프로젝트에 추가 되는 항목에 대 한 참조에서 발생 해야  
  
일부 끌어서 놓기 작업은 참조 기반, 디렉터리 기반 및 혼합 프로젝트의 조합에서 붙여 구분이 가능한. 특히,은 소스 디렉터리 기반 프로젝트를 이동 하는 완료 되 면 소스 항목을 삭제 해야 합니다 하기 때문에 소스 디렉터리 기반 프로젝트와 대상 참조 기반 프로젝트 간 이동 작업 수 있도록 자신 문제가 있습니다. 대상 프로젝트 기반 참조는 다음 삭제 된 항목에 대 한 참조로 남게 됩니다.  
  
대상 프로젝트 기반 참조 소스 항목의 독립 복사본을 사용 하지 않아야 하기 때문에 이러한 유형의 프로젝트 간에 복사 작업 수 있도록 자신 오해의 소지가 이기도 합니다. 마찬가지로, Ctrl + Shift 대상 디렉터리 기반 프로젝트에 끌어 허용 되지 디렉터리 기반 프로젝트에 대 한 참조를 지속할 수 없기 때문에 있습니다. 프로그램이 끌어서 놓기 작업이 지원 되지 않는 경우에 IDE의 삭제를 허용 하 고 (포인터 테이블 아래에 표시) 놓기 없음 커서 사용자에 게 표시 해야 합니다.  
  
끌어서 놓기 동작을 제대로 구현 하려면 끌기의 소스 프로젝트를 대상 프로젝트에 해당 특성을 통신 해야 합니다. (예를 들어 상태인 것 참조 또는 디렉터리 기반) 이 정보는 원본에서 제공 하는 클립보드 형식으로 표시 됩니다. 끌어서 (또는 클립보드로 복사 작업)의 원본으로 프로젝트를 제공 해야 하거나 `CF_VSREFPROJECTITEMS` 또는 `CF_VSSTGPROJECTITEMS` 각각 인지 여부에 따라 프로젝트 기반 참조 디렉터리 기반 합니다. Windows에서 비슷한 동일한 데이터 콘텐츠를 포함 하는 이러한 형식을 모두 `CF_HDROP` 의 서식을 지정 하는 파일 이름 대신 문자열의 목록이 이중-점을 제외 하 고`NULL` 목록이 종료 `Projref` 문자열 (에서 반환 된 `IVsSolution::GetProjrefOfItem` 또는 `::GetProjrefOfProject` 적절 하 게).  
  
Drop (또는 클립보드 붙여넣기 작업)의 대상으로 프로젝트를 둘 다 허용 `CF_VSREFPROJECTITEMS` 및 `CF_VSSTGPROJECTITEMS`경우에 끌어서 놓기 작업의 정확한 처리 대상 프로젝트 및 원본 프로젝트의 특성에 따라 달라 집니다. 원본 프로젝트의 제공 여부 하 여 해당 특성을 선언 `CF_VSREFPROJECTITEMS` 또는 `CF_VSSTGPROJECTITEMS`합니다. 놓기 대상 자체 특성을 이해 하 고 따라서에서 충분 한 정보가 이동, 복사, 여부를 결정을 내릴 수 또는 링크를 수행 해야 합니다. 또한 사용자는 Ctrl, Shift, 또는 둘 다 Ctrl 및 Shift 키를 눌러 끌어서 놓기 작업을 수행 해야 수정 합니다. 이 사전에 어떤 작업이 수행 되도록 있음을 제대로 표시 하기 위해 놓기 대상을 대 한 중요 해당 `DragEnter` 및 `DragOver` 메서드. **솔루션 탐색기** 소스 프로젝트와 대상 프로젝트 지 동일한 프로젝트를 자동으로 감지 합니다.  
  
(예를 들어의 한 인스턴스에서 다른 devenv.exe) Visual Studio의 인스턴스를 통해 프로젝트 항목을 끌어 구체적으로 사용할 수 없습니다. **솔루션 탐색기** 도 직접이 사용 하지 않습니다.  
  
항상 사용자 항목을 선택 하 여 대상 위치에 끌어 다음 마우스 포인터의 나타나는 항목을 삭제 하기 전에 관찰 끌어서 놓기 작업의 결과 확인할 수: 있습니다.  
  
| 마우스 포인터 | 명령 | 설명 |  
| :---: | --- | --- |  
| ![마우스 "끌어 놓기 없음" 아이콘](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 01_MouseNoDrop") | 끌어 놓기 없음 | 지정된 된 위치에 항목을 삭제할 수 없습니다. |  
| ![마우스 "복사" 아이콘](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706 02_MouseCopy") | 복사 | 항목 대상 위치에 복사 됩니다. |  
| ![마우스 "이동" 아이콘](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 03_MouseMove") | 이동 | 항목 대상 위치로 이동 됩니다. |  
| ![마우스 "참조 추가" 아이콘](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 04_MouseAddRef") | 참조 추가 | 선택한 항목에 대 한 참조를 대상 위치에 추가 됩니다. |

#### <a name="reference-based-projects"></a>프로젝트 기반 참조  
 다음 표에서 참조 기반 대상 프로젝트에 대 한 누른 원본 항목과 한정자 키 특성에 따라 (뿐만 아니라 잘라내기/복사/붙여넣기) 끌어서 놓기 작업을 수행 해야 하는 요약 되어 있습니다.  
  
| 한정자 | 범주 | 소스 항목: 참조/링크 | 소스 항목: 실제 항목이 나 파일 시스템 (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| 어떠한 한정자 | 작업 | 이동 | 링크 |  
| 어떠한 한정자 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 원래 항목에 대 한 참조를 추가합니다. |  
| 어떠한 한정자 | 소스 | 원래 항목에 대 한 참조를 삭제 | 원래 항목을 그대로 유지 |  
| 어떠한 한정자 | 결과 | `DROPEFFECT_MOVE`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | `DROPEFFECT_LINK`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. |  
| Shift + 드래그 | 작업 | 이동 | 끌어 놓기 없음 |  
| Shift + 드래그 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 끌어 놓기 없음 |  
| Shift + 드래그 | 소스 | 원래 항목에 대 한 참조를 삭제 | 끌어 놓기 없음 |  
| Shift + 드래그 | 결과 | `DROPEFFECT_MOVE`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | 끌어 놓기 없음 |  
| Ctrl + 끌어서 | 작업 | 복사 | 끌어 놓기 없음 |  
| Ctrl + 끌어서 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 끌어 놓기 없음 |  
| Ctrl + 끌어서 | 소스 | 원래 항목에 대 한 참조를 유지합니다. | 끌어 놓기 없음 |  
| Ctrl + 끌어서 | 결과 | `DROPEFFECT_COPY`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | 끌어 놓기 없음 |  
| Ctrl + Shift + 끌기 | 작업 | 링크 | 링크 |  
| Ctrl + Shift + 끌기 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 원래 항목에 대 한 참조를 추가합니다. |  
| Ctrl + Shift + 끌기 | 소스 | 원래 항목에 대 한 참조를 유지합니다. | 원래 항목을 그대로 유지 |  
| Ctrl + Shift + 끌기 | 결과 | `DROPEFFECT_LINK`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | `DROPEFFECT_LINK`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. |  
| Ctrl + Shift + 끌기 | 참고 | Windows 탐색기에서 바로 가기 키에 대 한 끌어서 놓기 동작와 동일 합니다. ||  
| 잘라내기/붙여넣기 | 작업 | 이동 | 링크 |  
| 잘라내기/붙여넣기 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 원래 항목에 대 한 참조를 추가합니다. |  
| 잘라내기/붙여넣기 | 소스 | 원래 항목에 대 한 참조를 유지합니다.|원래 항목을 그대로 유지 |  
| 잘라내기/붙여넣기 | 결과 | 항목은 저장소에서 원래 위치에 유지 됩니다. | 항목은 저장소에서 원래 위치에 유지 됩니다. |  
| 복사/붙여넣기 | 작업 | 복사 | 링크 |  
| 복사/붙여넣기 | 소스 | 원래 항목에 대 한 참조를 추가합니다. | 원래 항목에 대 한 참조를 추가합니다. |  
| 복사/붙여넣기 | 결과 | 원래 항목에 대 한 참조를 유지합니다. | 원래 항목을 그대로 유지 |  
| 복사/붙여넣기 | 작업 | 항목은 저장소에서 원래 위치에 유지 됩니다. | 항목은 저장소에서 원래 위치에 유지 됩니다. |  
  
#### <a name="directory-based-projects"></a>디렉터리 기반 프로젝트  
다음 표에서 대상 디렉터리 기반 프로젝트에 대 한 누른 원본 항목과 한정자 키 특성에 따라 끌어서 놓기 (뿐 아니라 잘라내기/복사/붙여넣기) 작업을 수행 해야 하는 요약 되어 있습니다.  
  
| 한정자 | 범주 | 소스 항목: 참조/링크 | 소스 항목: 실제 항목이 나 파일 시스템 (`CF_HDROP`) |  
| --- | --- | --- | --- |  
| 어떠한 한정자 | 작업 | 이동 | 이동 |  
| 어떠한 한정자 | 대상 | 대상 위치에 복사 항목 | 대상 위치에 복사 항목 |  
| 어떠한 한정자 | 소스 | 원래 항목에 대 한 참조를 삭제 | 원래 항목에 대 한 참조를 삭제 | | 어떠한 한정자 | 결과 | `DROPEFFECT_MOVE`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | `DROPEFFECT_MOVE`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. |  
| Shift + 드래그 | 작업 | 이동 | 이동 |  
| Shift + 드래그 | 대상 | 대상 위치에 복사 항목 | 대상 위치에 복사 항목 |  
| Shift + 드래그 | 소스 | 원래 항목에 대 한 참조를 삭제 | 원래 위치에서 항목을 삭제합니다. |
| Shift + 드래그 | 결과 | `DROPEFFECT_MOVE`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | `DROPEFFECT_MOVE`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. |  
| Ctrl + 끌어서 | 작업 | 복사 | 복사 |  
| Ctrl + 끌어서 | 대상 | 대상 위치에 복사 항목 | 대상 위치에 복사 항목 |  
| Ctrl + 끌어서 | 소스 | 원래 항목에 대 한 참조를 유지합니다. | 원래 항목에 대 한 참조를 유지합니다. |  
| Ctrl + 끌어서 | 결과 | `DROPEFFECT_COPY`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | `DROPEFFECT_COPY`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. |  
| Ctrl + Shift + 끌기 | | 끌어 놓기 없음 | 끌어 놓기 없음 |  
| 잘라내기/붙여넣기 | 작업 | 이동 | 이동 |  
| 잘라내기/붙여넣기 | 대상 | 대상 위치에 복사 항목 | 대상 위치에 복사 항목 |  
| 잘라내기/붙여넣기 | 소스 | 원래 항목에 대 한 참조를 삭제 | 원래 위치에서 항목을 삭제합니다. |  
| 잘라내기/붙여넣기 | 결과 | 항목은 저장소에서 원래 위치에 유지 됩니다. | 저장소에서 원래 위치에서 항목이 삭제 됩니다. |  
| 복사/붙여넣기 | 작업 | 복사 | 복사 |  
| 복사/붙여넣기 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 대상 위치에 복사 항목 |  
| 복사/붙여넣기 | 소스 | 원래 항목을 그대로 유지 | 원래 항목을 그대로 유지 |  
| 복사/붙여넣기 | 결과 | 항목은 저장소에서 원래 위치에 유지 됩니다. | 항목은 원래 위치 기능 저장소에 유지 됩니다. |
  
#### <a name="mixed-target-projects"></a>혼합 대상 프로젝트  
다음 표에서 혼합 대상 프로젝트에 대 한 누른 원본 항목과 한정자 키 특성에 따라 (뿐만 아니라 잘라내기/복사/붙여넣기) 끌어서 놓기 작업을 수행 해야 하는 요약 되어 있습니다.  
  
| 한정자 | 범주 | 소스 항목: 참조/링크 | 소스 항목: 실제 항목이 나 파일 시스템 (`CF_HDROP`) |  
| --- | --- | --- | --- |
| 어떠한 한정자 | 작업 | 이동 | 이동 |
| 어떠한 한정자 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 대상 위치에 복사 항목 |
| 어떠한 한정자 | 소스 | 원래 항목에 대 한 참조를 삭제 | 원래 항목에 대 한 참조를 삭제 |
| 어떠한 한정자 | 결과 | `DROPEFFECT_ MOVE`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | `DROPEFFECT_ MOVE`반환 `::Drop` 저장소의 원래 위치에서 항목이 삭제 되 고 |
| Shift + 드래그 | 작업 | 이동 | 이동 |
| Shift + 드래그 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 대상 위치에 복사 항목 |
| Shift + 드래그 | 소스 | 원래 항목에 대 한 참조를 삭제 | 원래 위치에서 항목을 삭제합니다. | 
| Shift + 드래그 | 결과 | `DROPEFFECT_ MOVE`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | `DROPEFFECT_ MOVE`반환 `::Drop` 저장소의 원래 위치에서 항목이 삭제 되 고 |
| Ctrl + 끌어서 | 작업 | 복사 | 복사 |
| Ctrl + 끌어서 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 대상 위치에 복사 항목 |
| Ctrl + 끌어서 | 소스 | 원래 항목에 대 한 참조를 유지합니다. | 원래 항목을 그대로 유지 |
| Ctrl + 끌어서 | 결과 | `DROPEFFECT_ COPY`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | `DROPEFFECT_ COPY`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. |
| Ctrl + Shift + 끌기 | 작업 | 링크 | 링크 |
| Ctrl + Shift + 끌기 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 원래 소스 항목에 대 한 참조를 추가합니다. |
| Ctrl + Shift + 끌기 | 소스 | 원래 항목에 대 한 참조를 유지합니다. | 원래 항목을 그대로 유지 |
| Ctrl + Shift + 끌기 | 결과 | `DROPEFFECT_ LINK`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. | `DROPEFFECT_ LINK`반환 `::Drop` 항목 저장소에 원래 위치에 유지 됩니다. |
| 잘라내기/붙여넣기 | 작업 | 이동 | 이동 |
| 잘라내기/붙여넣기 | 대상 | 대상 위치에 복사 항목 | 대상 위치에 복사 항목 |
| 잘라내기/붙여넣기 | 소스 | 원래 항목에 대 한 참조를 삭제 | 원래 위치에서 항목을 삭제합니다. |
| 잘라내기/붙여넣기 | 결과 | 항목은 저장소에서 원래 위치에 유지 됩니다. | 저장소에서 원래 위치에서 항목이 삭제 됩니다. |
| 복사/붙여넣기 | 작업 | 복사 | 복사 |
| 복사/붙여넣기 | 대상 | 원래 항목에 대 한 참조를 추가합니다. | 대상 위치에 복사 항목 |
| 복사/붙여넣기 | 소스 | 원래 항목을 그대로 유지 | 원래 항목을 그대로 유지 |
| 복사/붙여넣기 | 결과 | 항목은 저장소에서 원래 위치에 유지 됩니다. | 항목은 저장소에서 원래 위치에 유지 됩니다. |
  
이러한 세부 정보를 고려해 야 고려 사항에서 구현 하는 경우는 **솔루션 탐색기**:  
  
-   여러 선택 영역 시나리오에 대 한 디자인 합니다.  
  
-   파일 이름 (전체 경로) 대상 프로젝트에서 고유 해야 또는 삭제가 허용 되지 합니다.  
  
-   폴더 이름은 고유 해야 합니다. (대/소문자 구분) 손실 되는 수준입니다.  
  
-   파일 간에 개방형 또는 폐쇄형 끌어서 (위의 시나리오에서 언급 되지 않은) 시간에 동작 차이가 있습니다.  
  
-   최상위 파일 폴더에 있는 파일 보다 약간 다르게 동작 합니다.  
  
주의 해야 할 또 다른 문제는 열려 디자이너 또는 편집기에 있는 항목에 이동 작업을 처리 하는 방법입니다. (모든 프로젝트 형식에 적용) 다음과 같이 경우:  
  
1.  편집기/디자이너 열기에 변경 내용을 저장 하지 않은 경우 편집기/디자이너 창은 자동으로 닫을 수 해야 합니다.  
  
2.  편집기/디자이너 열기 변경 내용을 저장 하지 않은 경우, 끌기 소스를 수행 하 고 다음과 유사한 프롬프트 창을 닫기 전에 열려 있는 문서에서 커밋되지 않은 변경 내용을 저장 하 라는 요청 놓기에 대 한 대기 해야 합니다.  
  
    ```  
    ==========================================================   
         One or more open documents have unsaved changes.  
    Do you want to save uncommitted changes before proceeding?   
                      [Yes]  [No]  [Cancel]   
    ==========================================================  
    ```  
  
이렇게 하면 사용자를 대상이 사본과 하기 전에 진행 중인 작업을 저장할 수 있습니다. 새 메서드 `IVsHierarchyDropDataSource2::OnBeforeDropNotify` 이 처리를 사용 하도록 추가 되었습니다.  
  
저장소에 있는 것과 대상 항목의 상태를 다음 복사 합니다 (사용자가 경우 편집기에서 저장 되지 않은 변경 내용을 제외한 **아니요**). 대상의 복사 완료 된 후 (에서 `IVsHierarchyDropDataSource::Drop`), 소스 delete 부분의 이동 작업을 완료할 수 있는 기회를 제공 됩니다 (에서 `IVsHierarchyDropDataSource::OnDropNotify`).  
  
저장 되지 않은 변경 내용으로 모든 편집기 열린 채로 남아 해야 합니다. 저장 되지 않은 변경 내용으로 문서, 즉 이동 작업의 복사 단계가 수행 됩니다 있지만 delete 부분 중단 됩니다. 사용자가 선택 하는 여러 선택 영역 시나리오에서 **아니요**, 문서를 저장 하지 않은 변경 종료 되거나 제거 되지 않아야 하지만 저장 되지 않은 변경 내용이 없는 닫고 해야 제거 합니다.