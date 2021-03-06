---
title: Just-In-Time 디버거를 사용 하 여 디버그 | Microsoft Docs
ms.custom: ''
ms.date: 09/24/18
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a2e6cfbd6d26d575bab5d7592f320779ffd8888
ms.sourcegitcommit: 000cdd1e95dd02e99a7c7c1a34c2f8fba6a632af
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47168398"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Just-In-Time 디버거를 사용 하 여 Visual Studio에서 디버그
Just-in-time 디버깅 Visual Studio 자동으로 시작 외부 Visual Studio를 실행 하는 응용 프로그램에서 예외 또는 충돌이 발생 합니다. 이 옵션을 사용 하면 Visual Studio 실행 중이지 않을 때 응용 프로그램을 테스트 하 고 문제가 발생 한 경우 Visual Studio를 사용 하 여 디버깅을 시작할 수 있습니다.

Just-in-time 디버깅은 Windows 데스크톱 앱에 대 한 작동합니다. 유니버설 Windows 앱의 경우 작동 하지 않습니다 하 고 시각화 도우미 같은 네이티브 응용 프로그램에서 호스트 되는 관리 코드에 대해 작동 하지 않습니다.

> [!TIP]
> 시간에 응답 하는 방법을 알고 싶으면 디버거 대화 상자, 참조 [이 항목에서는](../debugger/just-in-time-debugging-in-visual-studio.md)합니다.

##  <a name="BKMK_Enabling"></a> 사용 하지 않도록 설정 하면 시간에 디버깅 사용 또는 사용
Just In Time Visual Studio에서 디버깅을 사용 하지 않도록 설정 하거나 설정할 수 있습니다 **도구 > 옵션** 대화 상자.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Just-In-Time 디버깅을 활성화하거나 비활성화하려면

1.  관리자 권한으로 Visual Studio를 열고 (마우스 오른쪽 단추로 **관리자 권한으로 실행**).

    활성화 또는 비활성화 Just In Time 레지스트리 키를 설정 하는 디버깅 하 고 해당 키를 변경 하려면 관리자 권한이 필요할 수 있습니다.

2. **도구** 메뉴에서 **옵션**을 클릭합니다.

2.  에 **옵션** 대화 상자를 확장 합니다 **디버깅** 노드.

3.  에 **디버깅** 노드를 선택 **Just In Time**합니다.

    ![JIT 디버깅을 사용할지](../debugger/media/dbg-jit-enable-or-disable.png "JIT 디버깅을 사용할지")

4.  에 **Just-In-Time 디버깅 사용 이러한 유형의 코드** 상자에서 선택 하거나 해당 프로그램 형식 선택을 취소: **관리 되는**, **네이티브**, 또는 **스크립트**.

5.  **확인**을 클릭합니다.

    시간에만 사용 하도록 설정 하면 디버거, 하지만 표시 되지 않는 응용 프로그램 충돌 또는 예외를 참조 하십시오 [Just In Time 디버깅 오류](#jit_errors)합니다.

컴퓨터에 Visual Studio가 더 이상 설치되어 있지 않아도 Just-In-Time 디버깅은 계속 활성화되어 있습니다. Visual Studio 설치 되어 있지 않으면 Just In Time Visual Studio에서 디버깅을 비활성화할 수 없습니다 **옵션** 대화 상자. 이 경우 Windows 레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화할 수 있습니다.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화하려면

1.  에 **시작** 메뉴, 검색 및 실행 `regedit.exe`

2.  에 **레지스트리 편집기** 창 찾기 및 다음 레지스트리 항목을 삭제 합니다.

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\합니다. NETFramework\DbgManagedDebugger

    ![JIT 레지스트리 키](../debugger/media/dbg-jit-registry.png "JIT 레지스트리 키")

3.  컴퓨터는 64 비트 운영 체제를 실행 하는 경우 다음 레지스트리 항목을 삭제 합니다.

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\합니다. NETFramework\DbgManagedDebugger

4.  실수로 다른 레지스트리 키를 삭제하거나 변경하지 않도록 주의합니다.

5.  닫기 합니다 **레지스트리 편집기** 창입니다.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Windows Form에 Just-In-Time 디버깅을 사용하려면

1.  기본적으로 Windows Forms 응용 프로그램에는 복구할 수 있는 경우 프로그램을 계속 실행할 수 있도록 하는 최상위 예외 처리기가 있습니다. 예를 들어, Windows Forms 응용 프로그램에서 처리 되지 않은 예외를 throw 하는 경우 다음과 같은 대화 상자가 나타납니다.

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Windows Forms 응용 프로그램의 디버깅을 사용 하면 시간을에 다음과 같은 추가 단계를 수행 해야 합니다.

2.  설정 합니다 `jitDebugging` 값을 `true` 에 `system.windows.form` 합니다 machine.config 섹션 또는  *\<응용 프로그램 이름 >*. exe.config 파일:

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3.  C++ Windows Forms 응용 프로그램의 경우 .config 파일이나 코드에서 `DebuggableAttribute`도 설정해야 합니다. 사용 하 여 컴파일하면 [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) 하지 않고 [/Og](/cpp/build/reference/og-global-optimizations), 컴파일러를이 특성을 설정 합니다. 그러나 최적화되지 않은 릴리스 빌드를 디버깅하려면 이 특성을 직접 설정해야 합니다. 응용 프로그램의 AssemblyInfo.cpp 파일에 다음 줄을 추가하여 이 특성을 설정할 수 있습니다.

    ```cpp
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     자세한 내용은 <xref:System.Diagnostics.DebuggableAttribute>을 참조하세요.

## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Just-in-time 디버깅 사용
 이 섹션에서는 실행 예외를 throw 하는 경우 어떻게 되는지 보여 줍니다.

 Visual Studio를 설치 하려면 다음이 단계를 수행 해야 합니다. Visual Studio가 없는 경우 무료 다운로드할 수 있습니다 [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)합니다.

 Just In Time 있는지 확인은 디버깅 [사용](#BKMK_Enabling)합니다.

 이 섹션에서는 throw 하는 Visual Studio에서 C# 콘솔 앱을 확인 합니다는 [NullReferenceException](/dotnet/api/system.nullreferenceexception)합니다.

 Visual Studio에서 C# 콘솔 앱을 만듭니다 (**파일 > 새로 만들기 > 프로젝트 > Visual C# > 콘솔 응용 프로그램**) 이라는 **ThrowsNullException**합니다. Visual Studio에서 프로젝트를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [연습: 간단한 응용 프로그램](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)합니다.

 Visual Studio에서 프로젝트가 열리면 Program.cs 파일을 엽니다. 콘솔에 줄을 출력 하 고 다음 NullReferenceException을 throw 하는 다음 코드를 사용 하 여 main () 메서드를 바꿉니다.

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
>  이 절차에서 작동 하도록 하기 위해를 [릴리스 구성을](../debugger/how-to-set-debug-and-release-configurations.md)를 해제 해야 [Just My Code](../debugger/just-my-code.md)합니다. Visual Studio에서 클릭 **도구 > 옵션**합니다. 에 **옵션** 대화 상자에서 **디버깅**합니다. 검사를 제거 **내 코드만**합니다.

 솔루션을 빌드합니다 (Visual Studio에서 선택 **빌드 > 솔루션 다시 빌드**). 디버그 또는 릴리스 구성을 선택할 수 있습니다 (선택 **디버그** 완벽 한 디버깅 환경을 위해). 빌드 구성에 대한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조하세요.

 빌드 프로세스는 실행 ThrowsNullException.exe를 만듭니다. C# 프로젝트를 만든 폴더에서 찾을 수 있습니다: **...\ThrowsNullException\ThrowsNullException\bin\Debug** 하거나 **...\ThrowsNullException\ThrowsNullException\bin\Release**합니다.

 ThrowsNullException.exe를 두 번 클릭 합니다. 이 같은 명령 창이 표시 됩니다.

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 몇 초 후 오류 창이 나타납니다.

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 클릭 하지 마세요 **취소**! 두 개의 단추를 몇 초 후 표시 **디버그** 하 고 **프로그램을 닫아**합니다. 클릭 **디버그**합니다.

> [!CAUTION]
>  응용 프로그램에 신뢰할 수 없는 코드가 보안 경고 대화 상자가 나타납니다. 이 대화 상자에서 디버깅을 계속할지 여부를 결정할 수 있습니다. 디버깅을 계속하기 전에 코드를 신뢰할 수 있는지 확인해야 합니다. 직접 작성한 코드인지, 코드 작성자를 신뢰할 수 있는지, 응용 프로그램이 원격 컴퓨터에서 실행 중인 경우 프로세스 이름을 알 수 있는지 등을 확인합니다. 응용 프로그램이 로컬로 실행 중이라고 해서 반드시 신뢰할 수 있는 것은 아닙니다. 컴퓨터에서 악의적인 코드가 실행 될 가능성을 고려 합니다. 코드를 하려는 경우 디버그를 신뢰할 수, 클릭 **디버그**합니다. 그렇지 않은 경우 클릭 **디버깅 하지 마십시오**합니다.

 합니다 **Visual Studio Just-In-Time Debugger** 창이 나타납니다.

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 아래 **사용 가능한 디버거**, 것을 확인할 수는 **Microsoft Visual Studio의 새 인스턴스 <available version>**  줄을 선택 합니다. 이미 선택 되지 않은 경우 지금 선택할.

 창의 맨 아래 **선택한 디버거를 사용 하 여 디버깅 하 시겠습니까?**, 클릭 **예**합니다.

 Visual Studio의 새 인스턴스를에서 예외를 throw 하는 줄에서 중지 된 실행과 ThrowsNullException 프로젝트를 엽니다.

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 이 시점에서 디버깅을 시작할 수 있습니다. 실제 응용 프로그램의 경우 코드는 예외를 throw 하는 이유를 확인 해야 합니다.

## <a name="jit_errors"></a> Just-in-time 디버깅 오류
 프로그램 충돌 및 기능을 사용 하도록 설정 해야 하는 경우 대화 상자에 표시 되지이 컴퓨터에 Windows 오류 보고 설정으로 인해 있습니다. 추가 해야 합니다는 **사용 안 함** 다음 레지스트리 키 값 및 값 1로 설정 합니다.

* HKLM\Software\Microsoft\Windows\Windows 오류 보고
* HKLM\Software\WOW6432Node\Microsoft\Windows\Windows 오류 보고
 
이러한 설정에 대 한 자세한 내용은 참조 하세요. [합니다. WER 설정](https://docs.microsoft.com/windows/desktop/wer/wer-settings)합니다.

또한 Just In Time와 연관 된 다음 오류 메시지가 나타날 디버깅 합니다.

- **충돌 하는 프로세스에 연결할 수 없습니다. 지정된 된 프로그램을 Windows 또는 MS-DOS 프로그램이 아닙니다.**

    이 오류는 다른 사용자로 실행 되는 프로세스에 연결 하려고 할 때 발생 합니다.

    Visual Studio 시작이이 문제를 해결 하려면 엽니다는 **프로세스에 연결** 대화 상자를 **디버그** 메뉴 및 찾기 프로세스에서 디버그 하려는 **사용 가능한 프로세스**목록입니다. 프로세스의 이름을 모르는 경우 확인 합니다 **Visual Studio Just-In-Time Debugger** 대화 및 참고 프로세스 id입니다. 프로세스를 선택 합니다 **사용 가능한 프로세스** 나열 하 고 클릭 **연결**합니다. 에 **Visual Studio Just-In-Time Debugger** 대화 상자에서 클릭 **No** 대화 상자를 닫습니다.

- **사용자가 로그온 하기 때문에 디버거를 시작할 수 없습니다.**

    이 오류는 콘솔에 로그온한 사용자가 없는 컴퓨터에서 Just-In-Time 디버깅 시 Visual Studio를 시작하려고 할 때 발생합니다. 로그온한 사용자가 없으므로 Just-In-Time 디버깅 대화 상자를 표시할 사용자 세션이 없습니다.

    이 문제를 해결하려면 컴퓨터에 로그온합니다.

- **클래스가 등록 되지 않았습니다.**

    이 오류는 설치 문제 등으로 인해 등록되지 않은 COM 클래스를 디버거에서 만들려고 했음을 의미합니다.

    이 문제를 해결하려면 설치 디스크를 사용하여 Visual Studio를 다시 설치하거나 Visual Studio 설치를 복구합니다.

## <a name="see-also"></a>참고 항목
 [디버거 보안](../debugger/debugger-security.md) [디버거 기본 사항](../debugger/getting-started-with-the-debugger.md) [Just 시간, 디버깅, 옵션 대화 상자](../debugger/just-in-time-debugging-options-dialog-box.md) [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결 될 수 있습니다 위험 합니다. 아래의 정보가 의심스럽거나 잘 모르겠으면 이 프로세스에 연결하지 마세요.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
