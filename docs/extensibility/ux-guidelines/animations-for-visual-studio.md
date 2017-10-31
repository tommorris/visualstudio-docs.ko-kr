---
title: "Visual Studio에 대 한 애니메이션 | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 446773a9-e6f7-4c0c-8dbc-9e303bf32eb1
caps.latest.revision: 2
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
ms.openlocfilehash: b36b5e35758ad10109328d6f001e043ad7dcbe15
ms.contentlocale: ko-kr
ms.lasthandoff: 05/04/2017

---
# <a name="animations-for-visual-studio"></a>Visual Studio에 대 한 애니메이션
## <a name="animation-fundamentals"></a>애니메이션의 기본 사항  
  
### <a name="animation-best-practices-in-visual-studio"></a>Visual Studio에서 애니메이션 모범 사례  
Visual Studio IDE에서 일관 되 고 사용자에 게 친숙 하는 애니메이션 스타일을 유지 하기 위해 이러한 규칙을 따릅니다.  
  
-   **주의 기울여야 합니다.** 애니메이션 특정 용도로 사용 되는 것을 제한 합니다.  
  
-   **타이밍 및 속도 중요 한** 전환 느낌을 신속 하 고 자연 스러운 있는지 확인 하려면:  
  
    -   1/2 초 (500 밀리초) 내에서 애니메이션된 전환을 완료 합니다.  
  
    -   애니메이션 자주 발생 하는 사용자의 워크플로 중단 하지 않는 시킬 만큼 빠른 있어야 합니다. 루프에서 애니메이션을 시청 하 고 오른쪽 느낌 될 때까지 타이밍을 조정 합니다. 
  
    -   따라서 빠르거나 하지 너무 느려 수행 하는 하나 끝나기를 전환에 대해 느리게만 할 뿐 아니라, 이해 하기 어렵더라도 임을 jarring 애니메이션이 아니어야 합니다.  
  
    -   변수 타이밍 중요도 강조 하기 위해 사용 합니다. 예를 들어 클래스 다이어그램에 있는 항목의 시퀀스를 탐색 하는 경우 항목 간 전환을 통해 속도가 다음 중요 한 항목에 초점을 느리게 합니다.  
  
-   **점진적 비선형 감속/가속을 사용 하 여** 다른 한 상태에서 잡고 자연 이동의 의미를 제공 합니다.  
  
-   가능 하면 **가리키기 미묘한 애니메이션을 사용 하 여** 마우스 아래 대화형 요소를 나타냅니다.  
  
-   경우 있습니다에 크게 의존 애니메이션 기능을에서 다음 **를 해제 하는 방법을 제공** 로컬로 (기능에 대 한 모든 사용자)에 옵션으로는 **도구 > 옵션** 대화 상자.  
  
-   **한 번에 하나의 애니메이션 수행할지** 하나만 부분의 정보 알아볼 수 있습니다. 둘 이상의 개체가 이동 하거나 여러 사항을 전달 하기 위해 시도 하는 혼동 될 수 있습니다. 
  
-   **주의 해야 하는 것이 중요 합니다.** 대부분의 경우에서 애니메이션의 목적에 따라 요청 시 사용자 주의 필요가 없습니다. 타이밍, 순서 지정 기능 및 동작에 미묘한 변화 인식에 크게 영향을 줄 수 있으며 효율적이 고 비효율적인 애니메이션 차이 수 있습니다.  
  
-   항목에 주목 하도록 애니메이션을 사용 하는 경우 **가치가 사용자 중단을 반드시**의 한 사고의 흐름.  
  
-   **진행률 또는 상태를 표시할 때** 애니메이션을 통해:  
  
    -   기본 프로세스 진행 되지 않습니다는 경우 진행률 이동 표시를 중지 합니다. 
  
    -   비활성화 프로세스에서 확인할 수 없는 프로세스를 구별할 수 있습니다.  
  
    -   애니메이션 식별이 가능한 완성 및 오류 상태에 있는지 확인 합니다.  
  
    -   상태를 보여 주는 실제 사용의 추가 정보를 제공 하 여 실제 값을 갖는지 확인 효과 애니메이션 사용을 최소화 합니다. 예로 임시 상태가 변경 되 고 응급 상황  
  
#### <a name="animation-donts"></a>애니메이션 수행:
  
-   작은 움직임 (적에서 이동)을 사용 하지 마십시오. 페이드 선호 하 고 이동 하는 개체를 통해 변경 합니다.  
  
-   화면 자원을의 큰 영역을 통해 수행 하는 애니메이션을 사용 하지 마십시오. 크기에 관계 없이 애니메이션의이 스타일은 사용자에 게 혼란 합니다.  
  
-   사용자는 방법에 대해 현재 개체와 관련 없는 하거나 상호 작용 하는 애니메이션을 사용 하지 마십시오.  
  
-   깜박임을 중지할 수 있도록 깜박이 알림에 응답 하도록 사용자와 같은 상태를 다시 설정 하려면 사용자가 개입 해야 하는 애니메이션을 사용 하지 마십시오. 어떤 방식으로 상호 작용 하는 해제 하려면 충분 해야 합니다.  
  
이들 모범 사례에 대 한 응용 프로그램에 대 한 자세한 내용은 참조 하십시오. [애니메이션 패턴](../../extensibility/ux-guidelines/animations-for-visual-studio.md#BKMK_AnimationPatterns)합니다.  
  
### <a name="animation-metrics"></a>애니메이션 메트릭  
  
-   시스템 10 밀리초 미만에 사용자 제스처에 응답 하는 시각적으로 표시 합니다.  
  
-   애니메이션된 전환을 끝나기를 500 밀리초 보다 오래 걸리는 하지 않아야 합니다.  
  
-   긴 시간을 필요로 하는 전환에 대 한 보정을 위해 한 가지 방법은 두 부분으로 분리 하는 것입니다. 예를 들어 애니메이션의 첫 번째 부분에 다음 콘텐츠 페이드 컨테이너 (최대 500 밀리초)를 빈 콘텐츠 컨테이너 (최대 500 밀리초)을 수 있습니다.  
  
-   계산할 수 있는 로드 시간에 대 한 결정 진행률 표시기 (%-완료 진행률 표시기) 선호 됩니다.  
  
-   계산할 수 없습니다 로드 시간에 대 한 커서 또는 포함 된 회전 애니메이션 (로드 또는 작업 표시기)와 같은 사용 중인 표시기는 적합 합니다.  
  
### <a name="animation-as-communicator"></a>Communicator로 애니메이션  
Visual Studio UI에서 애니메이션 통신 도구로 작동합니다.  다양 한 정보 (예: 메뉴 열리거나 닫힐 때) UI의 구조 변경 같은 통신에 사용 됩니다. 애니메이션 설치 진행률 시각화와 같은 복잡 한 시스템의 시간에 따라 변하는 동작을 시각화 하는 데 도움이 됩니다. 경고 및 알림의 관심을 갖게 하기 위한 애니메이션을 사용할 수도 있습니다.  
  
 UI 애니메이션 네 가지 방법으로 일반적으로 함수: 시각화, 관심을 갖게, 시뮬레이션 및 응답 시간/진행률 표시기입니다.  
  
#### <a name="visualize"></a>시각화  
애니메이션 개체의 3 차원 특성을 강조할 수도 있고 해당 공간 구조를 시각화 하는 사용자가 보다 쉽게 확인 됩니다. 이를 위해 애니메이션 수 있습니다 할 전체 원에 개체를 회전 하는 데 느린 주고받는 설정 또는 곧 제공 될 개체 가져오며 약간 롤오버 또는 포커스 강조 크기를 늘리거나.  
  
3d 개체에 (프로그래밍 방식으로 또는 수동으로) 디자이너 미리 결정 해야 하는 사용자 컨트롤로 이동할 수 수 있지만 어떻게 최적의 애니메이션 효과 줄 개체의 최적 이해를 제공 하는 이동 합니다. 이 애니메이션 수 프로그래밍 다음 있어도 되지만 대부분의 사용자 제어 이동을 사용자 개체를 조작 하는 방법을 이해 하는 개체에 대해 커서를 배치 하 여 사용자가 활성화할 수 있습니다. 제한 단일 축 또는; 한 번에 한 방향으로 이동 크기를 조정, 회전 또는 중를 하나만 하나 이상를 동시에 수행 하지 마십시오.  
  
시각화 범주에는 데이터, 관계, 상태의 측면에는 구조, 시퀀스 및 시간입니다.  
  
##### <a name="data"></a>데이터  
복잡 하 고 변수 정보를 보여 줍니다.  
  
-   차트와 그래프와 같은 정보 시각화를 통해 이동  
  
-   순서를 통해 단계별 실행, 둘러보기, 및 페이징  
  
-   세부 정보를 파악해을 특정 정보를 강조 표시  
  
-   세부 정보 및 추가 정보는 포커스가 있는 요소를 기반으로 오버레이
  
-   다른 한 구조적 또는 조직 표현에서 변형  
  
-   시간 슬라이더, 작업 셔틀 바퀴 및 전송 컨트롤 (재생, 중지 및 일시 중지)를 사용 하 여 시간이 지남에 따라 변경에 따라 
  
##### <a name="relationships"></a>관계  
  
-   어떤 항목 관련 지정된 된 항목 또는 항목 간의 관련 방식을 보여 줍니다.
  
-   계층 및 부모-자식 또는 형제 관계 표시
  
-   하나의 요소가 다른를 생성합니다.
  
-   하나의 요소가 다른 요소에 최소화
  
-   하나의 요소가 다른 테더 링 된
  
##### <a name="state"></a>상태  
  
-   콘텐츠 업데이트
  
-   사용자 포커스 및 선택  
  
-   진행률  
  
-   오류  
  
##### <a name="structure"></a>구조체  
  
-   한 노드에서 구조 피벗  
  
-   방향을 새로 설정  
  
-   최소화 및 최대화 또는 확장 및 축소  
  
##### <a name="sequence"></a>Sequence  
  
-   슬라이드 쇼 시퀀스  
  
-   그림을 통해 대칭 이동  
  
##### <a name="time"></a>시간  
  
-   시간, 시간 경과 및 캐스트에 대 한 표시 변경  
  
-   휴지통, 실행 취소 및 다시 실행으로 이동  
  
-   기록 상태를 복원 합니다.  
  
#### <a name="attract-attention"></a>관심을 갖게  
목표가 여러에서 단일 요소에 대 한 사용자의 주목 하도록 또는 업데이트 된 정보를 사용자에 게 경고할 경우 애니메이션 적합할 수 있습니다. 예를 들어 응용 프로그램 시작 페이지 페이지가 로드 된 후에 슬라이드 시작 단추를 사용할 수 있습니다.  
  
일반적으로 화면에서 이동 마지막 요소 동안 사용자의 주의 유도 합니다.  일련의 애니메이션된 요소에 사용자의 주의 마지막 개체가 이동 될 예정입니다.  
  
##### <a name="alert"></a>경고  
  
-   사용자 알림, 주의 진행률 표시  
  
-   문제가 되 고 했는지 올바르게 또는 잘못 표시 또는 진행 중이거나 진행 중인 변경  
  
-   온라인 추가 정보 찾기 또는 현재 작업에 대 한 학습와 같은 작업 중 사용자에 게 확인  
  
##### <a name="notifications"></a>알림  
  
-   오류 조건에 대 한 다음과 같은 경으십시오  
  
-   사용자에 게 다른 항목에 참석 하 전환할지 표시를 중단 합니다.  
  
-   조심 스럽게 프로세스가 완료 된 사용자에 게 알리는 또는 다운로드가 완료 되 면 like 변경 합니다.  
  
#### <a name="simulate"></a>시뮬레이션  
이 범주에서는 여실히 및 차원성을 다룹니다.  
  
-   개체에서 발생 한 위치 또는 위치로 이동 하는지를 설명합니다  
  
-   확장 및 축소 또는 열기 및 닫기  
  
-   이동, 스크롤, 및 페이지 설정  
  
-   스택 및 z 순서 지정  
  
-   회전식 및 accordion  
  
-   대칭 이동 및 UI를 회전  
  
#### <a name="response-and-progress-indicators"></a>응답 및 진행률 표시기  
진행률 표시기 큰 장점은 몇을 가지 있습니다.  
  
-   모두 비활성화 하 고 확인할 수 없는 진행률 표시기 시스템에서 반복적인 충돌이 발생 하 고 문제에 작동 하는 사용자를 원할 것입니다.  
  
-   비활성화 상태 표시기의 마침 수 있 느낌 뿐만 아니라 작업 얼마나 진행의 의미 진행 되 사용자에 게 제공 합니다.  
  
##  <a name="BKMK_AnimationPatterns"></a>애니메이션 패턴  
  
### <a name="overview"></a>개요  
Visual Studio에서 애니메이션 사용자 생산성을 방해 하지 않고 특정 기능을 제공 되어야 합니다. 일반적으로 Visual Studio에서 애니메이션 여야 합니다.  
  
-   작고 비간섭  
  
-   자연스럽 고 현실적인  
  
-   정교 하 고 게 당한 후  
  
-   신속 하 고 효율적인  
  
-   완화 되지 hurried  
  
이 그림에서는 Visual Studio에 대 한 것이 좋습니다 애니메이션 스타일을 보여 줍니다. 페이드 인 / 페이드 아웃 처럼 미묘한 애니메이션 없음이나 애니메이션 가장 자주 사용 됩니다. 확장 / 축소와 같은 이동 애니메이션의 제한 된 응용 프로그램이, X 및 Y 위치가 변경 및 회전 합니다. 
  
![Visual Studio에 대 한 권장 되는 애니메이션 스타일](../../extensibility/ux-guidelines/media/1202-a_vsanimstyles.png "1202-a_VSAnimStyles")<br />Visual Studio에 권장되는 애니메이션 스타일
  
#### <a name="appear-and-disappear"></a>표시 되거나 사라집니다  
이러한 패턴에서는 요소 보기 아웃 하 고 전환 애니메이션 없이 다시 표시에서 전환합니다.  
  
![표시 되 고 애니메이션 사라집니다.](../../extensibility/ux-guidelines/media/1202-b_appearanddisappear.png "1202-b_AppearAndDisappear")<br />표시 하거나 숨길 애니메이션  
  
##### <a name="correct-usage"></a>올바른 사용  
즉시 나타나거나 사라질 사용자 신경 아니고 방해 필요로 하는 새 UI 요소. 또한 천천히 움직이는 애니메이션 및 사라집니다 표시 스타일으로도 발생 하지 않습니다 성능 끌어 옵니다도 인식 될 수 있습니다.  
  
##### <a name="incorrect-usage"></a>잘못 된 사용  
UI 무슨 상황이, 나타납니다 갑자기 사용자에 게 어떠한 정보도 표시 하 고 상황에 맞는 이해에 도움이 될 애니메이션 추가 없는 경우.  
  
##### <a name="animation-properties"></a>애니메이션 속성  
시간 지연을 일반적으로 0 초입니다.  
  
##### <a name="examples"></a>예제    
-   도구 창 자동 숨기기  
  
-   바로 활성화 편집기 UI, IntelliSense 및 매개 변수 도움말와 같은  
  
-   확장-축소 코드 영역  
  
#### <a name="fade-in-and-fade-out"></a>전파가  
이 패턴으로 UI 요소는 표시 되지 않습니다 (불투명도 0%)에서 전환 표시 (100% 불투명도) 하거나 반대로 변경 합니다.  
  
![전파가 애니메이션](../../extensibility/ux-guidelines/media/1202-c_fadeinfadeout.png "1202-c_FadeInFadeOut")<br />전파가 애니메이션  
  
##### <a name="correct-usage"></a>올바른 사용  
가장 일반적으로 UI 애니메이션에 권장 됩니다. 이 흐름을 중단 하지 않고 관심을 추가 하는 미묘한 나타납니다. 경우에 따라 사용자 수 조차 모를 애니메이션는 부드러운 스트리밍 그 특수 하 고 UI 시스템 이동 합니다.  
  
##### <a name="animation-properties"></a>애니메이션 속성  
  
-   불투명도 시작: 페이드 인에 대 한 %0, 100% 페이드 아웃에 대 한  
  
-   끝 불투명도: 페이드 인 100%, 페이드 아웃에 대 한 %0  
  
-   기간: 200 밀리초 독립 실행형으로 100 밀리초 조합 애니메이션 시퀀스의 일부로 사용 될 때  
  
-   스타일 감속/가속: 사인 InOut  
  
##### <a name="examples"></a>예제  
  
-   도구 창 자동 숨기기  
  
-   메뉴 열기 및 닫기  
  
-   배경 및 전경 탭 전환  
  
#### <a name="color-blend-from-a-to-b"></a>B A에서 색 혼합  
이 패턴을 사용 UI 요소에서 A 색을 색으로 변경 2.  
  
![색 혼합 애니메이션](../../extensibility/ux-guidelines/media/1202-d_colorblend.png "1202-d_ColorBlend")<br />색 혼합 애니메이션  
  
##### <a name="correct-usage"></a>올바른 사용  
으로 UI 요소를 하나의 컨텍스트 또는 상태에서 다른 색이 변경 될 때 애니메이션 효과 준된 전환입니다.  
  
##### <a name="animation-properties"></a>애니메이션 속성  
  
-   시작 색: 특정 UI  
  
-   끝 색: 특정 UI  
  
-   기간: 200 밀리초 독립 실행형으로 100 밀리초 조합 애니메이션 시퀀스의 일부로 사용 될 때  
  
-   스타일 감속/가속: 사인 InOut  
  
##### <a name="examples"></a>예제  
  
-   문서 창 상태 전환 (활성, 활성 및 비활성 마지막)  
  
-   도구 창 상태 전환 (포커스가 및 포커스 없음)  
  
#### <a name="expand-and-contract"></a>확장 / 축소  
이 패턴을 사용 X, Y, 또는 두 방향에서 UI 요소를 확장합니다.  
  
![확장 / 축소 애니메이션](../../extensibility/ux-guidelines/media/1202-e_expandcontract.png "1202-e_ExpandContract")<br />확장 / 축소 애니메이션  
  
##### <a name="correct-usage"></a>올바른 사용  
으로 UI 요소를 다른 특정 컨텍스트에서 크기가 변경 될 때 애니메이션 효과 준된 전환입니다.  
  
##### <a name="animation-properties"></a>애니메이션 속성  
  
-   X 배율: % 또는 특정 차원 (픽셀 단위)  
  
-   Y 비율: % 또는 특정 차원 (픽셀 단위)  
  
-   앵커 위치: 일반적으로 (왼쪽에서 오른쪽 언어용) 왼쪽 위 또는 (오른쪽에서 왼쪽 언어)에 대 한 오른쪽 위  
  
-   기간: 200 밀리초 독립 실행형으로 100 밀리초 조합 애니메이션 시퀀스의 일부로 사용 될 때  
  
##### <a name="examples"></a>예제  
  
-   아키텍처 탐색기 패널 확장 및 축소  
  
-   시작 페이지 항목 확장 및 축소  
  
#### <a name="x-y-position-change"></a>X, Y 위치 변경  
UI 요소에는이 패턴을 사용의 X 또는 Y 위치 또는 둘 다 변경합니다.  
  
![X, Y 위치 변경 애니메이션](~/extensibility/ux-guidelines/media/1202-f_xypositionchange.png "1202-f_XYPositionChange")<br />X, Y 위치 변경 애니메이션  
  
##### <a name="correct-usage"></a>올바른 사용  
UI 요소 한 컨텍스트를 다른 위치를 변경 하는 경우에 애니메이션 효과 준된 전환으로 합니다.  
  
##### <a name="animation-properties"></a>애니메이션 속성  
  
-   시작 X 및 Y 위치: 특정 UI  
  
-   종료 X 및 Y 위치: 특정 UI  
  
-   이동 패스로: 없음  
  
-   기간: 200 밀리초 독립 실행형으로 100 밀리초 조합 애니메이션 시퀀스의 일부로 사용 될 때  
  
-   스타일 감속/가속: 사인 InOut  
  
##### <a name="example"></a>예제  
탭 순서 변경  
  
#### <a name="rotate"></a>회전  
이 패턴으로 UI 요소를 회전합니다.  
  
![UI 요소 회전 애니메이션](~/extensibility/ux-guidelines/media/1202-g_rotate.png "1202-g_Rotate")<br />UI 요소 회전 애니메이션  
  
##### <a name="correct-usage"></a>올바른 사용  
비활성화 상태 회전 진행률 표시기에 대해서만입니다.  
  
##### <a name="animation-properties"></a>애니메이션 속성  
  
-   회전 각도: 360  
  
-   회전 중심: 개체의 중간  
  
-   Duration: 연속  
  
##### <a name="example"></a>예제  
비활성화 상태의 진행률 표시기 (회전)  
  
### <a name="common-shell-ui-actions-and-recommended-animations"></a>일반적인 셸 UI 작업 및 권장된 애니메이션  
  
#### <a name="tab-open"></a>탭 열기  
![탭 열기 애니메이션](../../extensibility/ux-guidelines/media/1202-h_tabopen.png "1202-h_TabOpen")<br />탭 열기 애니메이션  
    
-   스타일: 표시  
  
-   0 초 기간:  

#### <a name="tab-close"></a>탭 닫기  
![탭 닫기 애니메이션](../../extensibility/ux-guidelines/media/1202-i_tabclose.png "1202-i_TabClose")<br />탭 닫기 애니메이션  
  
-   Style: X 위치 변경  
  
-   200 밀리초 기간:  
  
#### <a name="tab-reorder"></a>탭 순서 변경  
![Visual Studio에서 탭 순서 바꾸기 애니메이션](../../extensibility/ux-guidelines/media/1202-j_tabreorder.png "1202-j_TabReorder")<br />탭 순서 바꾸기 애니메이션

-   Style: X 위치 변경  
  
-   200 밀리초 기간:  
    
#### <a name="close-floating-document"></a>부동 문서 닫기  
![부동 문서의 닫기 애니메이션](../../extensibility/ux-guidelines/media/1202-k_closefloatingdocument.png "1202-k_CloseFloatingDocument")<br />닫기 부동 문서 애니메이션  
   
-   스타일: 표시  
  
-   200 밀리초 기간:   
 
#### <a name="window-state-transition"></a>창 상태 전환  
![창 상태 전환 애니메이션](../../extensibility/ux-guidelines/media/1202-l_windowstatetransition.png "1202-l_WindowStateTransition")<br />창 상태 전환 애니메이션  
    
-   Style: 다른 windows와 일치 하도록 문서 닫기 애니메이션을 정의 하는 현재 운영 체제를 사용 합니다.  
  
-   200 밀리초 기간:  
  
#### <a name="menu-open"></a>메뉴 열기  
![메뉴 열기 애니메이션](../../extensibility/ux-guidelines/media/1202-m_menuopen.png "1202-m_MenuOpen")<br />메뉴 열기 애니메이션  
    
-   스타일: 페이드 인  
  
-   200 밀리초 기간:  
  
#### <a name="menu-close"></a>메뉴 닫기  
![메뉴 닫기 애니메이션](../../extensibility/ux-guidelines/media/1202-n_menuclose.png "1202-n_MenuClose")<br />메뉴 닫기 애니메이션  
    
-   스타일: 페이드 아웃  
  
-   200 밀리초 기간:  
  
#### <a name="auto-hide-tool-window-reveal"></a>자동 숨기기 도구 창 표시  
![자동 숨기기 도구 창 표시 애니메이션](../../extensibility/ux-guidelines/media/1202-o_autohidetoolwindowreveal.png "1202-o_AutoHideToolWindowReveal")<br />자동 숨기기 도구 창 표시 애니메이션  

-   스타일: 표시  
  
-   0 초 기간: