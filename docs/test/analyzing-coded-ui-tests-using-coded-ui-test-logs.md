---
title: "코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트 분석 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 13
ms.author: douge
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 5f32c2bc9f289a69a5ef9e7acfc1a973017fec0f
ms.contentlocale: ko-kr
ms.lasthandoff: 05/13/2017

---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>코딩된 UI 테스트 로그를 사용하여 코딩된 UI 테스트 분석
코딩된 UI 테스트 로그는 코딩된 UI 테스트 실행에 대한 중요한 정보를 필터링하고 기록합니다.  
  
 **Requirements**  
  
-   Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>이 작업을 수행해야 하는 이유  
 로그는 문제를 신속하게 디버깅할 수 있는 형식으로 표시됩니다.  
  
## <a name="how-do-i-do-this"></a>문제 해결 방법  
  
### <a name="step-1-enable-logging"></a>1단계: 로깅 사용  
 시나리오에 따라 다음 방법 중 하나를 사용하여 로그를 사용하도록 설정할 수 있습니다.  
  
-   테스트 프로젝트에 App.config 파일이 없는 .NET Framework 버전 4를 대상으로 지정하는 경우  
  
    -   **QTAgent32_40.exe.config** 파일을 엽니다.  
  
         기본적으로 이 파일은 **\<drive>:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE**에 있습니다.  
  
         EqtTraceLevel의 값을 원하는 로그 수준으로 수정합니다.  
  
         파일을 저장합니다.  
  
-   테스트 프로젝트에 App.config 파일이 없는 .NET Framework 버전 4.5를 대상으로 지정하는 경우  
  
    -   **QTAgent32.exe.config** 파일을 엽니다.  
  
         기본적으로 이 파일은 **\<drive>:\Program Files (x86)\Microsoft Visual Studio 12.0\Common7\IDE**에 있습니다.  
  
         EqtTraceLevel의 값을 원하는 로그 수준으로 수정합니다.  
  
         파일을 저장합니다.  
  
-   테스트 프로젝트에 App.config 파일이 있는 경우  
  
    -   프로젝트에서 App.config 파일을 엽니다.  
  
         구성 노드 아래에 다음 코드를 추가합니다.  
  
         `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`  
  
-   테스트 코드 자체에서 로깅을 사용하는 경우  
  
    -   <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;  
  
### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>2단계: 코딩된 UI 테스트를 실행하고 로그 보기  
 현재 위치에서 **QTAgent32.exe.config** 파일을 적절하게 수정한 코딩된 UI 테스트를 실행하는 경우 테스트 탐색기 결과에 출력 링크가 표시됩니다. 로그 파일은 테스트에 실패한 경우뿐만 아니라 추적 수준이 “verbose”로 설정되었을 때 성공한 테스트의 경우에도 생성됩니다.  
  
1.  **테스트** 메뉴에서 **창**을 선택한 다음 **테스트 탐색기**를 선택합니다.  
  
2.  **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.  
  
3.  테스트 탐색기에서 실행하려는 코딩된 UI 테스트를 선택하고 해당 테스트의 바로 가기 메뉴를 연 다음 **선택한 테스트 실행**을 선택합니다.  
  
     자동화된 테스트가 실행되고 성공 또는 실패 여부를 나타냅니다.  
  
    > [!TIP]
    >  테스트 탐색기를 보려면 **테스트 메뉴**에서 **Windows**를 가리킨 다음 **테스트 탐색기**를 선택합니다.  
  
4.  테스트 탐색기 결과에서 **출력** 링크를 선택합니다.  
  
     ![테스트 탐색기의 출력 링크](../test/media/cuit_htmlactionlog1.png "CUIT_HTMLActionLog1")  
  
     그러면 작업 로그에 대한 링크가 포함되는 테스트에 대한 출력이 표시됩니다.  
  
     ![코딩된 UI 테스트의 결과 및 출력 링크](../test/media/cuit_htmlactionlog2.png "CUIT_HTMLActionLog2")  
  
5.  UITestActionLog.html 링크를 선택합니다.  
  
     웹 브라우저에 로그가 표시됩니다.  
  
     ![코딩된 UI 테스트 로그 파일](../test/media/cuit_htmlactionlog3.png "CUIT_HTMLActionLog3")  
  
## <a name="q--a"></a>Q & A  
  
### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>Q: EnableHtmlLogger 키는 어떻게 되나요?  
 이전 버전의 Visual Studio에는 코딩된 UI 테스트에서 HtmlLogger를 사용하도록 설정하는 다음과 같은 구성 설정이 두 개 더 있었습니다.  
  
```  
  
<add key="EnableHtmlLogger" value="true"/>  
  
<add key="EnableSnapshotInfo" value="true"/>  
  
```  
  
 그러나 이러한 설정은 둘 다 Visual Studio 2012 이후부터 사용되지 않습니다. EqtTraceLevel이 HtmlLogger를 사용하기 위해 수정해야 하는 유일한 설정입니다.  
  
## <a name="see-also"></a>참고 항목  
 [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)   
 [방법: Microsoft Visual Studio에서 테스트 실행](http://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
