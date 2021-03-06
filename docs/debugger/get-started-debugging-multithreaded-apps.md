---
title: 다중 스레드 응용 프로그램을 디버그 하는 방법을 알아봅니다
description: Visual Studio에서 병렬 스택 및 병렬 조사식 창을 사용 하 여 디버깅
ms.custom: H1HackMay2017
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11cb05ea81f086cf8c26e3058850968a909b84e3
ms.sourcegitcommit: 0cf1e63b6e0e6a0130668278489b21a6e5038084
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39468685"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Visual Studio에서 다중 스레드 응용 프로그램 디버깅 시작
Visual Studio는 여러 도구와 다중 스레드 응용 프로그램을 디버깅할 수 있도록 사용자 인터페이스 요소를 제공 합니다. 이 자습서에서는 스레드 마커를 사용 하는 방법을 보여 줍니다.는 **병렬 스택** 창에는 **병렬 조사식** 창과 조건부 중단점, 중단점 필터. 이 자습서는 몇 분 정도 걸리지만 완료 익힐 수 다중 스레드 응용 프로그램 디버깅에 대 한 기능을 사용 하 여.

|         |         |
|---------|---------|
|  ![비디오에 대한 비디오 카메라 아이콘](../install/media/video-icon.png "비디오 보기")  |    [비디오를 시청](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) 비슷한 단계를 보여 주는 다중 스레드 디버깅 합니다. |

다른 항목 다른 다중 스레드 디버깅 도구를 사용 하 여 추가 정보를 제공 합니다.

- 사용 하는 방법을 보여 주는 유사한 항목에 대 한 합니다 **디버그 위치** 도구 모음 및 **스레드** 창 참조 [연습: 다중 스레드 응용 프로그램을 디버그](../debugger/how-to-use-the-threads-window.md)합니다.

- 사용 하는 샘플을 사용 하 여 유사한 항목에 대 한 <xref:System.Threading.Tasks.Task> (관리 코드) (c + +), 동시성 런타임에서 확인할 [연습: 병렬 응용 프로그램을 디버깅](../debugger/walkthrough-debugging-a-parallel-application.md)합니다. 대부분의 다중 스레드 응용 프로그램 형식에 적용 되는 일반적인 디버깅 팁이 항목과 연결 된 항목을 참조 하세요.
  
이 자습서를 시작 하려면 다중 스레드 응용 프로그램 프로젝트를 해야 합니다. 여기에 나열된 단계에 따라 프로젝트를 만드십시오.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>다중 스레드 앱 프로젝트를 만들려면  
  
1.  에 **파일** 메뉴에서 선택 **새로 만들기** 을 클릭 한 다음 **프로젝트**합니다.  
  
     **새 프로젝트** 대화 상자가 나타납니다.  
  
2.  사용자가 선택한 언어를 클릭 합니다. **Visual C#**, **Visual c + +**, 또는 **Visual Basic**합니다.  
  
3.  아래 **Windows 바탕 화면**, 선택 **콘솔 앱**합니다.  
  
4.  에 **이름을** 상자에 MyThreadWalkthroughApp 라는 이름을 입력 합니다.  
  
5.  **확인**을 클릭합니다.  
  
     새 콘솔 프로젝트가 나타납니다. 프로젝트가 만들어지면 소스 파일이 나타납니다. 선택한 언어에 따라 Program.cs, MyThreadWalkthroughApp.cpp, 또는 Module1.vb 소스 파일을 호출할 수 있습니다.  
  
6.  소스 파일에 표시 되는 코드를 삭제 하 고 여기에 표시 된 예제 코드를 사용 합니다.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "stdafx.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```
  
7.  에 **파일** 메뉴에서 클릭 **모두 저장**합니다.  
  
#### <a name="to-begin-the-tutorial"></a>이 자습서를 시작 하려면  
  
-   소스 코드 편집기에서 다음 코드를 찾습니다. 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>디버깅을 시작하려면  
  
1.  왼쪽된 여백을 클릭 합니다 `Thread.Sleep` 또는 `this_thread::sleep_for` 문을 새 중단점을 삽입 합니다.  
  
     소스 코드 편집기의 왼쪽에 여백에 빨간색 원이 나타납니다. 이 공은 이 위치에 중단점이 설정되었음을 나타냅니다. 
  
2.  에 **디버그** 메뉴에서 클릭 **디버깅 시작** (**F5**).  
  
     Visual Studio 솔루션을 빌드합니다, 그리고 앱, 연결 된 디버거와 함께 실행을 시작 및 앱 중단점에서 멈춥니다.  
  
    > [!NOTE]
    > 콘솔 창에 포커스를 전환 하는 경우 클릭 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 창에 포커스를 돌리는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]합니다.  
  
4.  소스 코드 편집기에서 중단점을 포함 하는 줄을 찾습니다.  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3)); 
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>스레드 마커를 검색 하려면  

1.  디버그 도구 모음에서 클릭 합니다 **소스의 스레드 표시** 단추 ![소스의 스레드 표시](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")합니다.

2. 키를 눌러 **F11** 디버거를 한 줄 코드를 한 번입니다.
  
3.  창 왼쪽의 여백을 확인합니다. 이 줄에 표시 됩니다는 *스레드 마커* 아이콘 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker") 두 가닥의 실와 유사한 합니다. 스레드 마커는 이 위치에서 스레드가 중지되었음을 나타냅니다.

    스레드 마커 중단점에서 부분적으로 숨겨진 수를 확인 합니다. 
  
4.  스레드 마커에 포인터를 올려 놓습니다. DataTips가 나타납니다. DataTip을 통해 중지된 각 스레드의 이름과 스레드 ID 번호를 알 수 있습니다. 이 경우 이름의 되었을 `<noname>`합니다. 
  
5.  바로 가기 메뉴에서 사용할 수 있는 옵션을 보려면 스레드 마커를 마우스 오른쪽 단추로 클릭 합니다.
    
## <a name="ParallelStacks"></a>스레드 위치를 확인 합니다.

에 **병렬 스택** 전환할 수 있습니다 창 작업 보기 및 있습니다 각 스레드에 대 한 호출 스택 정보를 볼 수 있습니다 (작업 기반 프로그래밍)에 대 한 스레드 뷰 사이입니다. 이 앱의 경우 스레드 뷰에 사용할 수 있습니다.

1. 엽니다는 **병렬 스택** 를 선택 하 여 창 **디버그 > Windows > 병렬 스택**합니다. 다음과 유사한 결과가 표시 됩니다 (정확한 정보를 각 스레드, 하드웨어 및 프로그래밍 언어의 현재 위치에 따라 다를 수 됩니다).

    ![병렬 스택 창](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    이 예제에서는 왼쪽에서 오른쪽 얻게 관리 코드에 대 한이 정보:
    
    - 주 스레드 (왼쪽)에서 중지 되었습니다 `Thread.Start` (중지 지점 스레드 마커 아이콘으로 표시 됩니다 ![스레드 마커](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - 입력 한 두 개의 스레드를 `ServerClass.InstanceMethod`, 그 중 하나는 현재 스레드 (노란색 화살표)을에서 다른 스레드를 중지 하는 동안 `Thread.Sleep`합니다.
    - (오른쪽) 새 스레드 시작 (중지 `ThreadHelper.ThreadStart`).

2.  항목을 마우스 오른쪽 단추로 클릭 합니다 **병렬 스택** 창 바로 가기 메뉴에서 사용할 수 있는 옵션을 확인 합니다.

    이러한 오른쪽 클릭 메뉴에서 다양 한 조치를 취할 수 있지만이 자습서에서 이러한 세부 사항을 자세히 표시 됩니다 것를 **병렬 조사식** 창 (다음 섹션).

    > [!NOTE]
    > 각 스레드에 대 한 정보 보기에서 사용 하 여 목록에 더 관심이 있는 경우는 **스레드** 창 대신 합니다. 참조 [연습: 다중 스레드 응용 프로그램을 디버그](../debugger/how-to-use-the-threads-window.md)합니다.

## <a name="set-a-watch-on-a-variable"></a>변수에 조사식 설정

1. 엽니다는 **병렬 조사식** 를 선택 하 여 창 **디버그 > Windows > 병렬 조사식 > 병렬 조사식 1**합니다.

2. 표시 되는 셀을 클릭 합니다 `<Add Watch>` 텍스트, 네 번째 열에서 빈 머리글 셀 형식 `data`, Enter 키를 누릅니다.

    각 스레드에 대 한 데이터 변수 값 창에 나타납니다.

3. 다시 표시 셀을 클릭 합니다 `<Add Watch>` 텍스트, 다섯 번째 열에서 빈 머리글 셀을 형식 `count`, Enter 키를 누릅니다.

    각 스레드에 대해 개수 변수에 대 한 값 창에 나타납니다. (아직 없는 경우이 많은 정보를 참조 하세요, 디버거에서 스레드의 실행을 이동 하는 몇 번 더 F11 키를 시도 하세요.)

    ![병렬 조사식 창](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. 사용 가능한 옵션을 보려면 창의 행 중 하나를 마우스 오른쪽 단추로 클릭 합니다.

## <a name="flagging-and-unflagging-threads"></a>스레드에 플래그 지정 및 해제  
특별 한 주의가 원하는 스레드 플래그를 지정할 수 있습니다. 스레드에 플래그를 지정 하는 것이 중요 한 스레드를 추적 하 고에 대 한 중요 하지 않은 스레드를 무시 하도록 좋습니다.  
  
#### <a name="to-flag-threads"></a>스레드에 플래그를 지정하려면  

1. 에 **병렬 조사식** 창 SHIFT 키를 누른 채 여러 행을 선택 합니다.

2. 마우스 오른쪽 단추로 **플래그**합니다.

    이제 선택한 모든 스레드에 플래그가 지정 됩니다. 이제 플래그가 지정 된 스레드만 표시 하도록 필터링 할 수 있습니다.
  
3.  에 **병렬 조사식** 창 찾기 합니다 **플래그가 지정 된 스레드만 표시** 단추 ![플래그가 지정 된 스레드 표시](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker")합니다.  
  
4.  클릭 합니다 **플래그가 지정 된 스레드만 표시** 단추입니다.  
  
    플래그가 지정된 스레드만 목록에 나타납니다.

    > [!TIP]
    > 일부 스레드를 플래그를 지정한 경우 코드 편집기에서 코드 줄을 마우스 오른쪽 단추로 클릭 하 고 선택할 수 **커서 플래그가 지정 된 스레드가 실행** (선택 했는지 확인 하는 모든 플래그가 지정 된 스레드만 코드에 도달). 이 선택한 코드 줄을 쉽게 실행 하 여 순서를 제어 하에서 스레드 일시 중지 [스레드 중지 및 재개](#bkmk_freeze)합니다.

5.  클릭 합니다 **플래그가 지정 된 스레드만 표시** 다시 전환 하려면 단추 **모든 스레드 표시** 모드입니다.
    
#### <a name="to-unflag-threads"></a>스레드의 플래그를 해제하려면

스레드의 있습니다 수 마우스 오른쪽 단추로 클릭의 하나 이상의 플래그가 지정 된 스레드는 **병렬 조사식** 창을 선택한 **플래그 해제**합니다.

## <a name="bkmk_freeze"></a> 중지 및 재개 스레드 실행 

> [!TIP]
> 고정 및 고정 해제 수 있습니다 (일시 중단 및 다시 시작) 스레드를 스레드 작업을 수행 하는 순서를 제어 합니다. 이 교착 상태 같은 동시성 문제를 해결 하 고 경합 조건을 수 있습니다.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>스레드를 중지 및 해제하려면  
  
1.  에 **병렬 조사식** 창에 선택 된 모든 행을 마우스 오른쪽 단추로 **Freeze**합니다.

    두 번째 열, 일시 중지 아이콘 이제 각 행에 대해 나타납니다. 일시 중지 아이콘은 스레드를 고정 하는 것을 나타냅니다.

2.  하나의 행을 클릭 하 여 행을 선택 취소 합니다.

3.  선택한 행을 마우스 오른쪽 단추로 클릭 **재개**합니다.

    일시 중지 아이콘 스레드를 더 이상 고정 나타내는이 행에서 사라집니다.

4.  코드 편집기로 전환 하 고 클릭 **F11**합니다. 고정 되지 않은 스레드만 실행 됩니다.

    앱 몇 가지 새 스레드를 인스턴스화할 수도 수 있습니다. 새 스레드를 플래그 지정 된 않으며 고정 되지 않은 확인 합니다.

## <a name="bkmk_follow_a_thread"></a> 조건부 중단점을 사용 하 여 단일 스레드를 수행 합니다.

경우에 따라 디버거에서 단일 스레드로 실행을 추적할 수 유용할 수 있습니다. 원하는 않은 스레드를 동결 하 여 수행할 수 있는 한 가지 방법은 이지만 일부 시나리오에서는 하고자 할 수 있습니다 (예를 들어 특정 버그 재현)를 다른 스레드를 고정 하지 않고 단일 스레드를 수행 합니다. 다른 스레드를 고정 하지 않고 스레드를 수행 하려면 관심 있는 스레드에서 제외 하 고 코드를 중단 하면 하면 안 됩니다. 설정 하 여이 수행할 수는 [조건부 중단점](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)합니다.

스레드 이름 또는 스레드 ID와 같은 다양 한 조건에 중단점을 설정할 수 있습니다. 유용할 수 있는 또 다른 방법은 각 스레드에 고유 하 게 표시 하는 것이 알고 있는 데이터의 조건을 설정 하는 것입니다. 특정 스레드에 보다 몇 가지 특정 데이터 값에 더 관심이 되는 일반적인 디버깅 시나리오입니다.

#### <a name="to-follow-a-single-thread"></a>단일 스레드를 수행 합니다.

1. 이전에 만든 중단점을 마우스 오른쪽 단추로 클릭 하 고 선택 **조건을**합니다.

2. 에 **중단점 설정** 창, 형식 `data == 5` 조건 식에 대 한 합니다.

    ![조건부 중단점](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > 특정 스레드에 더 많은 관심 인 경우 스레드 이름이 나 스레드 ID 조건에 사용 합니다. 이를 수행 하는 **중단점 설정** 창에서 **필터** 대신 **조건식**, 필터 팁을 따릅니다. 앱 코드에서 스레드 (스레드 Id는 디버거를 다시 시작할 때 변경) 때문에 이름을 지정 하려고 합니다.

3. 닫기 합니다 **중단점 설정** 창입니다.

4. 다시 시작을 클릭 ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 디버깅 세션을 다시 시작 하는 단추입니다.

    데이터 변수 5는는 스레드에서 코드로 중단 됩니다. 노란색 화살표 (현재 디버거 컨텍스트)에 대 한 확인 합니다 **병렬 조사식** 되었는지 확인 하는 창입니다.

5. 이제 코드 (F10) 및 (F11) 코드를 한 단계씩 하는 단일 스레드 실행을 수행 합니다.

    중단점 조건은 스레드를 고유 하 고 디버거 (비활성화 해야 할) 다른 스레드에서 다른 중단점을 적중 하지 않습니다, 코드 수 있으며 다른 스레드를 전환 하지 않고 코드를 한 단계씩 수 있습니다.

    > [!NOTE]
    > 디버거를 진행 하면 모든 스레드가 실행 됩니다. 그러나 다른 스레드 중 하나는 중단점에 도달 하지 않는 한 다른 스레드에서 코드에 디버거를 중단 하지 않습니다. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>다중 스레드 디버깅 창에 대 한 자세한 정보 

#### <a name="to-switch-to-another-thread"></a>다른 스레드로 전환 

- 참조를 다른 스레드로 전환 하려면 [방법: 다른 스레드가 디버그 하는 동안 전환](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>병렬 스택 및 병렬 조사식 창에 자세히 알아보려면  
  
- 참조 [방법: 병렬 스택 창 사용](../debugger/using-the-parallel-stacks-window.md) 

- 참조 [방법: 병렬 조사식 창 사용](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>참고 항목  
 [다중 스레드 응용 프로그램 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [방법: 디버그 중 다른 스레드로 전환](../debugger/how-to-switch-to-another-thread-while-debugging.md)
