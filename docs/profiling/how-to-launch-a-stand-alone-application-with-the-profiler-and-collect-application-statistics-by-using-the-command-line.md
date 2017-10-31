---
title: "방법: 명령줄을 통해 프로파일러와 함께 독립 실행형 응용 프로그램을 시작하여 응용 프로그램 통계 수집 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 방법: 명령줄을 통해 프로파일러와 함께 독립 실행형 응용 프로그램을 시작하여 응용 프로그램 통계 수집
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

이 항목에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구의 명령줄 도구를 사용하여 독립 실행형\(클라이언트\) 응용 프로그램을 시작하고 샘플링 방법을 사용하여 성능 통계를 수집하는 방법에 대해 설명합니다.  
  
> [!NOTE]
>  Windows 8 및 Windows Server 2012의 강화된 보안 기능으로 Visual Studio 프로파일러가 해당 플랫폼에서 데이터를 수집하는 방식에 중요한 변경 사항이 발생합니다.  Windows 스토어 응용 프로그램에는 또한 새 컬렉션 기술이 필요합니다.  [Windows 8 및 Windows Server 2012 응용 프로그램 프로파일링](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하십시오.  
>   
>  계층 상호 작용을 프로파일링 실행에 추가하는 것은, 데이터 명령줄 프로 파일링 도구를 사용하는 특정 프로시저가 필요 합니다.  [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)을 참조하십시오.  
  
 프로파일러 명령줄 도구를 사용하려면 해당 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.  Visual Studio 명령 창에서 Visual Studio가 설치된 컴퓨터에서 프로 파일링 도구를 실행할 수 있습니다.  
  
1.  Visual Studio 명령 창이 올바른 경로에 Visual Studio를 설치한 Visual Studio 컴퓨터에 프로파일링 도구를 실행한다면.  **도구** 메뉴에서, **VS 명령 프롬프트**를 선택합니다.  
  
> [!NOTE]
>  프로파일링 도구의 명령줄 도구는 Visual Studio 설치 디렉터리의 \\Team Tools\\Performance Tools 하위 디렉터리에 있습니다.  64비트 컴퓨터에서는 64비트 및 32비트 버전의 도구를 모두 사용할 수 있습니다.  프로파일러 명령줄 도구를 사용하려면 해당 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.  자세한 내용은 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하십시오.  
  
## 프로파일러를 사용하여 응용 프로그램 시작  
 프로파일러를 사용하여 대상 응용 프로그램을 시작하려면 VSPerfCmd **\/start** 및 **\/launch** 옵션을 사용하여 프로파일러를 초기화하고 응용 프로그램을 시작합니다.  단일 명령줄에서 **\/start** 및 **\/launch**와 각각에 해당하는 옵션을 지정할 수 있습니다.  
  
 **\/globaloff** 옵션을 추가하여 대상 응용 프로그램이 시작될 때 데이터 수집을 일시 중지할 수도 있습니다.  그런 다음 **\/globalon**을 사용하여 데이터 수집을 시작합니다.  
  
#### 프로파일러를 사용하여 응용 프로그램을 시작하려면  
  
1.  명령 프롬프트 창을 엽니다.  
  
2.  프로파일러를 시작합니다.  다음을 입력합니다.  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   [\/start](../profiling/start.md) **:sample** 옵션은 프로파일러를 초기화합니다.  
  
    -   **\/start**와 함께 [\/output](../profiling/output.md)**:**`OutputFile` 옵션을 사용해야 합니다.  `OutputFile`은 프로파일링 데이터 파일\(.vsp\)의 이름과 위치를 지정합니다.  
  
     다음 옵션을 **\/start:sample** 옵션과 함께 사용할 수 있습니다.  
  
    |옵션|설명|  
    |--------|--------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|프로파일링 중 수집할 Windows 성능 카운터를 지정합니다.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|**\/wincounter**에만 사용합니다.  Windows 성능 카운터 수집 이벤트의 시간 간격\(밀리초\)을 지정합니다.  기본값은 500밀리초입니다.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|프로파일링 중 수집할 ETW\(Windows용 이벤트 추적\) 이벤트를 지정합니다.  ETW 이벤트는 별도의 파일\(.etl\)에 수집됩니다.|  
  
3.  대상 응용 프로그램을 시작합니다.  **VSPerfCmd \/launch:**`appName` \[`Options`\] \[`Sample Event`\]를 입력합니다.  
  
     다음 중 하나 이상의 옵션을 **\/launch** 옵션과 함께 사용할 수 있습니다.  
  
    |옵션|설명|  
    |--------|--------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|대상 응용 프로그램에 전달할 명령줄 인수가 들어 있는 문자열을 지정합니다.|  
    |[\/console](../profiling/console.md)|대상 명령줄 응용 프로그램을 별도의 창에서 시작합니다.|  
  
     기본적으로 성능 데이터는 중단되지 않은 프로세서 클록 주기 수가 10,000,000개가 될 때마다 샘플링됩니다.  1GHz 프로세서에서 이 값은 대략 10초당 1회에 해당합니다.  다음 옵션 중 하나를 지정하여 클록 주기 간격을 변경하거나 다른 샘플링 이벤트를 지정할 수 있습니다.  
  
    |샘플 이벤트|설명|  
    |------------|--------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|샘플링 간격을 `Interval`에 지정된 중단되지 않은 클록 주기 수로 변경합니다.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|샘플링 이벤트를 페이지 폴트로 변경합니다.  `Interval`이 지정된 경우 샘플 간의 페이지 폴트 수를 설정합니다.  기본값은 10입니다.|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[**:**`Interval`\]|샘플링 이벤트를 해당 프로세스에서 운영 체제 커널로의 시스템 호출\(syscall\)로 변경합니다.  `Interval`이 지정된 경우 샘플 간의 호출 수를 설정합니다.  기본값은 10입니다.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|샘플링 이벤트와 간격을 각각 `Config`에 지정된 프로세서 성능 카운터와 간격으로 변경합니다.|  
  
## 데이터 수집 제어  
 대상 응용 프로그램이 실행 중일 때 **VSPerfCmd.exe** 옵션을 사용하여 프로파일러 데이터 파일에 데이터를 기록하는 작업을 시작하고 중지하는 방법으로 데이터 수집을 제어할 수 있습니다.  데이터 수집을 제어하면 응용 프로그램의 시작 또는 종료와 같은 프로그램 실행의 특정 부분에 대해 데이터를 수집할 수 있습니다.  
  
#### 데이터 수집을 시작 및 중지하려면  
  
-   다음 옵션 쌍으로 데이터 수집을 시작하고 중지할 수 있습니다.  각 옵션을 별도의 명령줄에 지정합니다.  데이터 수집을 여러 번 설정하거나 해제할 수 있습니다.  
  
    |옵션|설명|  
    |--------|--------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|모든 프로세스에 대해 데이터 수집을 시작\(**\/globalon**\)하거나 중지\(**\/globaloff**\)합니다.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|프로세스 ID\(`PID`\)로 지정된 프로세스에 대해 데이터 수집을 시작\(**\/processon**\)하거나 중지\(**\/processoff**\)합니다.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|**\/attach**는 `PID` 또는 프로세스 이름\(ProcName\)으로 지정된 프로세스에 대해 데이터 수집을 시작합니다.  **\/detach**는 지정된 프로세스 또는 모든 프로세스\(특정 프로세스가 지정되지 않은 경우\)에 대해 데이터 수집을 중지합니다.|  
  
## 프로파일링 세션 종료  
 프로파일링 세션을 종료하려면 프로파일링된 모든 프로세스에서 프로파일러를 분리해야 하며 프로파일러를 명시적으로 종료해야 합니다.  응용 프로그램을 닫거나 **VSPerfCmd \/detach** 옵션을 호출하여 샘플링 방법으로 프로파일링된 응용 프로그램에서 프로파일러를 분리할 수 있습니다.  그런 다음 **VSPerfCmd \/shutdown** 옵션을 호출하여 프로파일러를 해제하고 프로파일링 데이터 파일을 닫을 수 있습니다.  **VSPerfClrEnv \/off** 명령은 프로파일링 환경 변수를 지웁니다.  
  
#### 프로파일링 세션을 종료하려면  
  
1.  다음 단계 중 하나를 수행하여 대상 응용 프로그램에서 프로파일러를 분리합니다.  
  
    -   대상 응용 프로그램을 닫습니다.  
  
         또는  
  
    -   **VSPerfCmd \/detach**를 입력합니다.  
  
2.  프로파일러를 종료합니다.  다음을 입력합니다.  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## 참고 항목  
 [독립 실행형 응용 프로그램 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)