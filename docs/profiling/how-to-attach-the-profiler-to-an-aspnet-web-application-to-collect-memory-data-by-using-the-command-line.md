---
title: "방법: 명령줄을 통해 ASP.NET 웹 응용 프로그램에 프로파일러를 연결하여 메모리 데이터 수집 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 방법: 명령줄을 통해 ASP.NET 웹 응용 프로그램에 프로파일러를 연결하여 메모리 데이터 수집
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

이 항목에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구의 명령줄 도구를 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 응용 프로그램에 프로파일러를 연결하고 .NET Framework 메모리 할당의 수 및 크기에 대한 데이터를 수집하는 방법에 대해 설명합니다.  .NET Framework 메모리 개체의 수명에 대한 데이터도 수집할 수 있습니다.  
  
> [!NOTE]
>  프로파일링 도구의 명령줄 도구는 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 설치 디렉터리의 \\Team Tools\\Performance Tools 하위 디렉터리에 있습니다.  64비트 컴퓨터에서는 64비트 및 32비트 버전의 도구를 모두 사용할 수 있습니다.  프로파일러 명령줄 도구를 사용하려면 해당 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.  자세한 내용은 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하십시오.  
  
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 응용 프로그램 으로 부터 데이터를 수집하려면, [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) 도구 를 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 응용 프로그램을 호스팅하는 컴퓨터의 적절한 환경 변수를 초기화해야 합니다.  프로 파일링을 위한 웹 서버를 구성하기 위해 컴퓨터를 다시 시작해야 합니다.  
  
 다음에는 [VSPerfCmd.exe](../profiling/vsperfcmd.md) 도구를 사용하여 웹 사이트를 호스팅하는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스에 프로파일러를 연결합니다.  응용 프로그램에 프로파일러가 연결되어 있을 때 데이터 수집을 일시 중지했다가 다시 시작할 수 있습니다.  
  
 프로파일링 세션을 종료하려면 프로파일러가 응용 프로그램에 더 이상 연결되어 있지 않아야 하며 프로파일러를 명시적으로 종료해야 합니다.  대부분의 경우 세션을 종료할 때 프로파일링 환경 변수를 지우는 것이 좋습니다.  
  
## 프로파일러 연결  
  
#### ASP.NET 웹 응용 프로그램에 프로파일러를 연결하려면  
  
1.  명령 프롬프트 창을 엽니다.  
  
2.  프로파일링 환경 변수를 초기화합니다.  다음을 입력합니다.  
  
     **VSPerfClrEnv** {**\/globalsamplegc** &#124; **\/globalsamplegclife**} \[**\/samplelineoff**\]  
  
    -   **\/globalsamplegc** 및 **\/globalsamplegclife** 옵션은 수집할 메모리 데이터의 종류를 지정합니다.  
  
         다음 옵션 중 하나만 지정합니다.  
  
        |옵션|설명|  
        |--------|--------|  
        |**\/globalsamplegc**|메모리 할당 데이터를 수집할 수 있도록 합니다.|  
        |**\/globalsamplegclife**|메모리 할당 데이터와 개체 수명 데이터를 모두 수집할 수 있도록 합니다.|  
  
    -   **\/samplelineoff** 옵션은 특정 소스 코드 줄에 수집된 데이터를 할당할 수 없도록 합니다.  이 옵션을 지정하면 데이터가 함수 수준에서만 할당됩니다.  
  
3.  컴퓨터를 다시 시작하여 새 환경 구성을 설정합니다.  
  
4.  명령 프롬프트 창을 엽니다.  필요한 경우 프로파일러 경로 환경 변수를 설정합니다.  
  
5.  프로파일러를 시작합니다.  다음을 입력합니다.  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   **\/start:sample** 옵션은 프로파일러를 초기화합니다.  
  
    -   **\/start**와 함께 **\/output:**`OutputFile` 옵션을 사용해야 합니다.  `OutputFile`은 프로파일링 데이터 파일\(.vsp\)의 이름과 위치를 지정합니다.  
  
     다음 옵션을 **\/start:sample** 옵션과 함께 사용할 수 있습니다.  
  
    > [!NOTE]
    >  **\/user** 및 **\/crosssession** 옵션은 대개 ASP.NET 응용 프로그램에 필요합니다.  
  
    |옵션|설명|  
    |--------|--------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|ASP.NET 작업자 프로세스를 소유하는 계정의 도메인 및 사용자 이름을 지정합니다.  이 옵션은 로그온한 사용자 이외의 사용자 권한으로 프로세스가 실행되는 경우에 필요합니다.  해당 프로세스 소유자는 Windows 작업 관리자에서 프로세스 탭의 사용자 이름 열에 표시됩니다.|  
    |[\/crosssession](../profiling/crosssession.md)|다른 로그온 세션에서 프로세스를 프로파일링할 수 있도록 합니다.  이 옵션은 ASP.NET 응용 프로그램이 다른 세션에서 실행되고 있는 경우에 필요합니다.  세션 식별자는 Windows 작업 관리자에서 프로세스 탭의 세션 ID 열에 표시됩니다.  **\/crosssession**의 약식 표현으로 **\/CS**를 지정해도 됩니다.|  
    |[\/waitstart](../profiling/waitstart.md) \[**:**`Interval`\]|프로파일러가 초기화될 때까지 기다릴 수 있는 시간\(초\)을 지정합니다. 이 시간이 지나면 오류가 반환됩니다.  `Interval`을 지정하지 않으면 프로파일러는 무기한 기다립니다.  기본적으로 **\/start**는 즉시 반환됩니다.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|프로파일링 중 수집할 Windows 성능 카운터를 지정합니다.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|**\/wincounter**에만 사용합니다.  Windows 성능 카운터 수집 이벤트의 시간 간격\(밀리초\)을 지정합니다.  기본값은 500밀리초입니다.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|프로파일링 중 수집할 ETW\(Windows용 이벤트 추적\) 이벤트를 지정합니다.  ETW 이벤트는 별도의 파일\(.etl\)에 수집됩니다.|  
  
6.  일반적인 방식으로 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 응용 프로그램을 시작합니다.  
  
7.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스에 프로파일러를 연결합니다.  다음을 입력합니다.  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   프로세스 ID `(PID)`는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스의 프로세스 ID 또는 프로세스 이름을 지정합니다.  Windows 작업 관리자에서 실행 중인 모든 프로세스의 프로세스 ID를 볼 수 있습니다.  
  
    -   **\/targetclr:** `Version`은 응용 프로그램에 둘 이상의 CLR\(공용 언어 런타임\) 버전이 로드될 때 프로파일링할 런타임 버전을 지정합니다.  
  
## 데이터 수집 제어  
 응용 프로그램이 실행 중일 때는 **VSPerfCmd.exe** 옵션을 사용하여 프로파일러 데이터 파일에 데이터를 기록하는 작업을 시작하고 중지하는 방법으로 데이터 수집을 제어할 수 있습니다.  데이터 수집을 제어하면 응용 프로그램의 시작 또는 종료와 같은 프로그램 실행의 특정 부분에 대해 데이터를 수집할 수 있습니다.  
  
#### 데이터 수집을 시작 및 중지하려면  
  
-   다음과 같은 **VSPerfCmd** 옵션 쌍으로 데이터 수집을 시작하고 중지할 수 있습니다.  각 옵션을 별도의 명령줄에 지정합니다.  데이터 수집을 여러 번 설정하거나 해제할 수 있습니다.  
  
    |옵션|설명|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대해 데이터 수집을 시작\(**\/globalon**\)하거나 중지\(**\/globaloff**\)합니다.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|`PID`로 지정된 프로세스에 대해 데이터 수집을 시작\(**\/processon**\)하거나 중지\(**\/processoff**\)합니다.|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;:`ProcName`}\]|**\/attach**는 프로세스 ID 또는 프로세스 이름으로 지정된 프로세스에 대해 데이터 수집을 시작합니다.  **\/detach**는 지정된 프로세스 또는 모든 프로세스\(특정 프로세스가 지정되지 않은 경우\)에 대해 데이터 수집을 중지합니다.|  
  
## 프로파일링 세션 종료  
 프로파일링 세션을 종료하려면 웹 응용 프로그램에서 프로파일러를 분리해야 합니다.  [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 다시 시작하거나 **VSPerfCmd \/detach** 옵션을 호출하여 샘플링 방법으로 프로파일링되는 응용 프로그램에서 데이터 수집을 중지할 수 있습니다.  그런 다음 **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) 옵션을 호출하여 프로파일러를 해제하고 프로파일링 데이터 파일을 닫을 수 있습니다.  **VSPerfClrEnv \/globaloff** 명령은 프로파일링 환경 변수를 지우지만 컴퓨터가 다시 시작되기 전까지 시스템 구성은 다시 설정되지 않습니다.  
  
#### 프로파일링 세션을 종료하려면  
  
1.  다음 단계 중 하나를 수행하여 대상 응용 프로그램에서 프로파일러를 분리합니다.  
  
    -   **VSPerfCmd**  [\/detach](../profiling/detach.md)를 입력합니다.  
  
         또는  
  
    -   [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 작업자 프로세스를 닫습니다.  다음을 입력합니다.  
  
     **IISReset \/stop**  
  
2.  프로파일러를 종료합니다.  다음을 입력합니다.  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(선택 사항\) 프로파일링 환경 변수를 지웁니다.  다음을 입력합니다.  
  
     **VSPerfCmd \/globaloff**  
  
4.  컴퓨터를 다시 시작합니다.  필요하면 인터넷 정보 서비스\(IIS\)를 다시 시작합니다.  다음을 입력합니다.  
  
     **IISReset \/start**  
  
## 참고 항목  
 [ASP.NET 웹 응용 프로그램 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET 메모리 데이터 뷰](../profiling/dotnet-memory-data-views.md)