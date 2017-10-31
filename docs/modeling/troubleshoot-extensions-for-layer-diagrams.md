---
title: "종속성 다이어그램의 확장 문제 해결 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 25
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
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
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 26a1992fb9c49c670740a8d4a9a992df3d0a86db
ms.lasthandoff: 02/22/2017

---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>종속성 다이어그램의 확장 문제 해결
이 항목에서는 레이어 모델 확장을 만들 때 발생할 수 있는 몇 가지 문제를 해결합니다.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>My 확장을 디버깅 하려면 f5 키를 누를 때 내 명령, 제스처 처리기, 유효성 검사 확장 또는 사용자 지정 속성에 나타나지 않습니다의 실험적 인스턴스에서 종속성 다이어그램[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  실험적 인스턴스에서 확장 솔루션을 열고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 및는 **빌드** 메뉴를 클릭 하 여 **솔루션 다시 빌드**합니다.  
  
2.  키를 눌러 **F5** 또는 **CTRL + f&5;** 의 실험적 인스턴스를 시작 하려면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다. 종속성 다이어그램을 열고 확장 프로그램을 테스트 합니다.  
  
 필요한 경우 다음 절차를 계속 진행합니다.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>이전 버전의 확장이 실행됩니다.  
  
1.  실행 중인 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 실험적 인스턴스가 없는지 확인합니다.  
  
2.  다음 폴더를 삭제: %LocalAppData%\Microsoft\VisualStudio\\[version] \ComponentModelCache  
  
    > [!NOTE]
    >  % LocalAppData %는 일반적으로 *DriveName*: \Users\\*UserName*\AppData\Local입니다.  
  
 필요한 경우 다음 절차를 계속 진행합니다.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>이전 버전의 유효성 검사 결과가 나타나거나, 내 유효성 검사 메서드가 호출되지 않습니다.  
  
1.  실험적 인스턴스에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 **빌드** 메뉴를 클릭 하 여 **솔루션 정리**합니다. 캐시된 이전 유효성 검사 분석 결과가 지워집니다.  
  
2.  모델의 레이어가 코드 요소와 연결되었는지, 그리고 모델에 종속성 링크가 하나 이상 있는지 확인합니다. 유효성을 검사할 항목이 없는 경우에는 유효성 검사가 호출되지 않습니다.  
  
3.  일반 중단점은 별도 프로세스로 실행되기 때문에 유효성 검사 메서드에서 작동하지 않습니다. 메서드를 단계별로 실행하려는 경우 `System.Diagnostics.Debugger.Launch()` 호출을 삽입해야 합니다.  
  
4.  **source.extension.vsixmanifest** 레이어 유효성 검사 프로젝트에 추가한 모두 있는지 확인 한 **MEF 구성 요소** 항목 및 **사용자 지정 확장 형식** 항목 아래 **콘텐츠**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [종속성 다이어그램을 확장 합니다.](../modeling/extend-layer-diagrams.md)
