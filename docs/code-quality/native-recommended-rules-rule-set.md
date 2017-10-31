---
title: "네이티브 권장 규칙 규칙 집합 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d845b5a-1b75-4e9d-861a-7c59cb7752af
caps.latest.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 3
---
# 네이티브 권장 규칙 규칙 집합
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

이러한 규칙들은 잠재적 보안 허점 및 응용 프로그램 충돌을 포함하여 네이티브 코드의 가장 중요하고 일반적인 문제에 초점을 맞춥니다.  네이티브 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에 이 규칙 집합을 포함해야 합니다.  이 규칙 집합은 Visual Studio Professional 이상 버전에서 사용하도록 디자인되었습니다.  
  
|규칙|설명|  
|--------|--------|  
|[C6001](../code-quality/c6001.md)|초기화되지 않은 메모리 사용|  
|[C6011](../code-quality/c6011.md)|Null 포인터 역참조|  
|[C6029](../code-quality/c6029.md)|확인되지 않은 값 사용|  
|[C6031](../code-quality/c6031.md)|반환 값이 무시되었습니다.|  
|[C6053](../code-quality/c6053.md)|호출의 0 종료|  
|[C6054](../code-quality/c6054.md)|0 종료 없음|  
|[C6059](../code-quality/c6059.md)|잘못된 연결|  
|[C6063](../code-quality/c6063.md)|Format 함수에 문자열 인수 없음|  
|[C6064](../code-quality/c6064.md)|Format 함수에 정수 인수 없음|  
|[C6066](../code-quality/c6066.md)|Format 함수에 포인터 인수 없음|  
|[C6067](../code-quality/c6067.md)|Format 함수에 문자열 포인터 인수 없음|  
|[C6101](../code-quality/c6101.md)|초기화되지 않은 메모리 반환 중입니다.|  
|[C6200](../code-quality/c6200.md)|인덱스가 버퍼 최대값을 초과함|  
|[C6201](../code-quality/c6201.md)|인덱스가 스택 버퍼 최대값을 초과함|  
|[C6214](../code-quality/c6214.md)|BOOL에 대한 잘못된 캐스팅 HRESULT|  
|[C6215](../code-quality/c6215.md)|BOOL에 대한 잘못된 캐스팅 HRESULT|  
|[C6216](../code-quality/c6216.md)|HRESULT에 대한 잘못된 컴파일러 삽입 캐스팅 BOOL|  
|[C6217](../code-quality/c6217.md)|NOT을 포함하는 잘못된 HRESULT 테스트|  
|[C6220](../code-quality/c6220.md)|1과 비교할 때 잘못된 HRESULT|  
|[C6226](../code-quality/c6226.md)|1에 대한 잘못된 HRESULT 할당|  
|[C6230](../code-quality/c6230.md)|HRESULT를 부울로 잘못 사용|  
|[C6235](../code-quality/c6235.md)|논리합의 0이 아닌 상수|  
|[C6236](../code-quality/c6236.md)|논리합의 0이 아닌 상수|  
|[C6237](../code-quality/c6237.md)|논리적으로 0에 대한\-부작용을 잃습니다.|  
|[C6242](../code-quality/c6242.md)|강제 로컬 해제|  
|[C6248](../code-quality/c6248.md)|Null DACL 작성|  
|[C6250](../code-quality/c6250.md)|해제되지 않은 주소 설명자|  
|[C6255](../code-quality/c6255.md)|보호되지 않은 Alloca 사용|  
|[C6258](../code-quality/c6258.md)|스레드 종료를 사용|  
|[C6259](../code-quality/c6259.md)|비트 OR 제한 스위치에 데드 코드가 있음|  
|[C6260](../code-quality/c6260.md)|바이트 산술 사용|  
|[C6262](../code-quality/c6262.md)|과도한 스택 사용|  
|[C6263](../code-quality/c6263.md)|루프에 Alloca 사용|  
|[C6268](../code-quality/c6268.md)|캐스팅에 괄호 없음|  
|[C6269](../code-quality/c6269.md)|포인터 역참조 무시됨|  
|[C6270](../code-quality/c6270.md)|Format 함수에 부동 인수 없음|  
|[C6271](../code-quality/c6271.md)|Format 함수의 추가 인수|  
|[C6272](../code-quality/c6272.md)|Format 함수의 비부동 인수|  
|[C6273](../code-quality/c6273.md)|Format 함수의 비정수 인수|  
|[C6274](../code-quality/c6274.md)|Format 함수의 비문자 인수|  
|[C6276](../code-quality/c6276.md)|잘못된 문자열 캐스팅|  
|[C6277](../code-quality/c6277.md)|잘못된 CreateProcess 호출|  
|[C6278](../code-quality/c6278.md)|배열\-새 스칼라\-삭제 불일치|  
|[C6279](../code-quality/c6279.md)|배열\-새 스칼라\-삭제 불일치|  
|[C6280](../code-quality/c6280.md)|메모리 할당\-할당 해제 불일치|  
|[C6281](../code-quality/c6281.md)|비트 관계 우선 순위|  
|[C6282](../code-quality/c6282.md)|할당에서 테스트 교체|  
|[C6283](../code-quality/c6283.md)|기본 배열\-새 스칼라\-삭제 불일치|  
|[C6284](../code-quality/c6284.md)|Format 함수의 개체 인수 잘못됨|  
|[C6285](../code-quality/c6285.md)|상수의 논리합|  
|[C6286](../code-quality/c6286.md)|논리합이 0이 아니므로 의도하지 않은 결과 발생|  
|[C6287](../code-quality/c6287.md)|중복 테스트|  
|[C6288](../code-quality/c6288.md)|논리로 상호를 포하고\-False 입니다.|  
|[C6289](../code-quality/c6289.md)|논리합에 대한 상호 제외가 true임|  
|[C6290](../code-quality/c6290.md)|비트 논리 부정\-및 우선 순위|  
|[C6291](../code-quality/c6291.md)|비트 논리 부정\-또는 우선 순위|  
|[C6292](../code-quality/c6292.md)|루프가 최대값부터 위로 계산됨|  
|[C6293](../code-quality/c6293.md)|루프가 최소값부터 아래로 계산됨|  
|[C6294](../code-quality/c6294.md)|루프 본문이 실행되지 않음|  
|[C6295](../code-quality/c6295.md)|무한 루프|  
|[C6296](../code-quality/c6296.md)|루프가 한 번만 실행됨|  
|[C6297](../code-quality/c6297.md)|더 큰 크기로의 시프트 캐스팅 결과|  
|[C6299](../code-quality/c6299.md)|부울 비교에 대한 비트 필드|  
|[C6302](../code-quality/c6302.md)|Format 함수에 대한 잘못된 문자열 인수|  
|[C6303](../code-quality/c6303.md)|Format 함수에 대한 잘못된 와이드 문자열 인수|  
|[C6305](../code-quality/c6305.md)|크기 및 개수 사용 불일치|  
|[C6306](../code-quality/c6306.md)|잘못된 변수 인수 함수 호출|  
|[C6308](../code-quality/c6308.md)|Realloc 누수|  
|[C6310](../code-quality/c6310.md)|잘못된 예외 필터 상수|  
|[C6312](../code-quality/c6312.md)|예외 실행 루프 계속|  
|[C6314](../code-quality/c6314.md)|비트 OR 우선 순위|  
|[C6317](../code-quality/c6317.md)|하지 하지 보수|  
|[C6318](../code-quality/c6318.md)|예외 계속 검색|  
|[C6319](../code-quality/c6319.md)|쉼표로 무시됨|  
|[C6324](../code-quality/c6324.md)|문자열 비교 대신 문자열 복사|  
|[C6328](../code-quality/c6328.md)|잠재적 인수 형식 불일치|  
|[C6331](../code-quality/c6331.md)|VirtualFree 플래그 잘못됨|  
|[C6332](../code-quality/c6332.md)|VirtualFree 매개 변수 잘못됨|  
|[C6333](../code-quality/c6333.md)|VirtualFree 크기 잘못됨|  
|[C6335](../code-quality/c6335.md)|프로세스 핸들 누수|  
|[C6381](../code-quality/c6381.md)|종료 정보 없음|  
|[C6383](../code-quality/c6383.md)|Element\-Count Byte\-Count 버퍼 오버런|  
|[C6384](../code-quality/c6384.md)|포인터 크기 분할|  
|[C6385](../code-quality/c6385.md)|읽기 오버런|  
|[C6386](../code-quality/c6386.md)|쓰기 오버런|  
|[C6387](../code-quality/c6387.md)|잘못된 매개 변수 값|  
|[C6388](../code-quality/c6388.md)|잘못된 매개 변수 값|  
|[C6500](../code-quality/c6500.md)|잘못된 특성 속성|  
|[C6501](../code-quality/c6501.md)|특성 속성 값 충돌|  
|[C6503](../code-quality/c6503.md)|참조는 Null일 수 없음|  
|[C6504](../code-quality/c6504.md)|비포인터에 대한 Null|  
|[C6505](../code-quality/c6505.md)|Void에 대한 MustCheck|  
|[C6506](../code-quality/c6506.md)|비포인터 또는 배열에 대한 버퍼 크기|  
|[C6507](http://msdn.microsoft.com/ko-kr/18f88cd1-d035-4403-a6a4-12dd0affcf21)|Null 역참조 0에서 불일치|  
|[C6508](../code-quality/c6508.md)|상수에 대한 쓰기 액세스|  
|[C6509](../code-quality/c6509.md)|사전 조건에서 반환이 사용됨|  
|[C6510](../code-quality/c6510.md)|비포인터에 대한 Null 종료|  
|[C6511](../code-quality/c6511.md)|MustCheck는 Yes 또는 No여야 함|  
|[C6513](../code-quality/c6513.md)|버퍼 크기가 없는 요소 크기|  
|[C6514](../code-quality/c6514.md)|버퍼 크기가 배열 크기를 초과함|  
|[C6515](../code-quality/c6515.md)|비포인터에 대한 버퍼 크기|  
|[C6516](../code-quality/c6516.md)|특성에 대한 속성 없음|  
|[C6517](../code-quality/c6517.md)|읽기 불가능 버퍼에 대한 유효 크기|  
|[C6518](../code-quality/c6518.md)|쓰기 불가능 버퍼에 대한 쓰기 가능 크기|  
|[C6519](http://msdn.microsoft.com/ko-kr/2b6326b0-0539-4d26-8fb1-720114933232)|주석이 잘못 되었습니다: 'NeedsRelease' 속성의 값이 예 또는 아니요이어야 합니다.|  
|[C6521](http://msdn.microsoft.com/ko-kr/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|역참조 문자열 크기가 잘못 되었습니다.|  
|[C6522](../code-quality/c6522.md)|잘못된 크기 문자열 형식|  
|[C6523](http://msdn.microsoft.com/ko-kr/11397a31-b224-46b0-afb7-d49ca576a3bb)|문자열 매개 변수의 크기가 잘못 되었습니다.|  
|[C6525](../code-quality/c6525.md)|잘못된 크기 문자열 접근할 수 없는 위치|  
|[C6526](http://msdn.microsoft.com/ko-kr/59c590c7-0098-4166-a1ac-87f324596002)|잘못된 크기를 문자열 버퍼 형식입니다.|  
|[C6527](../code-quality/c6527.md)|경고 C6527: 주석이 잘못되었습니다. NeedsRelease 속성은 void 형식의 값에 사용할 수 없습니다.|  
|[C6530](../code-quality/c6530.md)|인식할 수 없는 형식 문자열 스타일|  
|[C6540](../code-quality/c6540.md)|이 함수에 특성 주석을 사용하면 기존의 모든 주석이 무효화됩니다.|  
|[C6551](../code-quality/c6551.md)|크기 사양이 잘못되었습니다. 식을 구문 분석할 수 없습니다.|  
|[C6552](../code-quality/c6552.md)|Deref\= 또는 Notref\=가 잘못되었습니다. 식을 구문 분석할 수 없습니다.|  
|[C6701](../code-quality/c6701.md)|값이 올바른 Yes\/No\/Maybe 값이 아닙니다.|  
|[C6702](../code-quality/c6702.md)|값이 문자열 값이 아닙니다.|  
|[C6703](../code-quality/c6703.md)|값이 숫자가 아닙니다.|  
|[C6704](../code-quality/c6704.md)|예기치 않은 주석 식 오류가 발생했습니다.|  
|[C6705](../code-quality/c6705.md)|주석 인수 개수가 예상 된 주석에 대한 인수의 실제 수가 맞지 않습니다.|  
|[C6706](../code-quality/c6706.md)|주석에 대해 예기치 않은 주석 오류가 발생했습니다.|  
|[C6995](../code-quality/c6995.md)|XML 로그 파일을 저장하지 못했습니다.|  
|[C26100](../code-quality/c26100.md)|경합 상태\(race condition\).|  
|[C26101](../code-quality/c26101.md)|연관 작업을 적절하게 사용할 수 없습니다.|  
|[C26110](../code-quality/c26110.md)|호출자가 잠금 유지에 실패했습니다.|  
|[C26111](../code-quality/c26111.md)|호출자가 잠금 해제에 실패했습니다.|  
|[C26112](../code-quality/c26112.md)|호출자가 잠금을 유지할 수 없습니다.|  
|[C26115](../code-quality/c26115.md)|잠금 해제에 실패했습니다.|  
|[C26116](../code-quality/c26116.md)|잠금 획득 또는 유지에 실패했습니다.|  
|[C26117](../code-quality/c26117.md)|유지되지 않은 잠금을 해제합니다.|  
|[C26140](../code-quality/c26140.md)|SAL 주석 동시성 오류|  
|[C28020](../code-quality/c28020.md)|이 식은 이 호출에 대해 True가 아닙니다.|  
|[C28021](../code-quality/c28021.md)|주석이 추가된 매개 변수는 포인터여야 합니다.|  
|[C28022](../code-quality/c28022.md)|이 함수의 함수 클래스\(들\)은 함수를 정의하는 데 사용된 typedef의 함수 클래스\(들\)와 일치하지 않습니다.|  
|[C28023](../code-quality/c28023.md)|할당 중이거나 전달 중인 함수는 하나 이상의 클래스에 대한 함수 클래스 주석을 갖고 있어야만 합니다.|  
|[C28024](../code-quality/c28024.md)|할당 중인 함수 포인터에 함수 클래스\(들\)로 주석이 추가되었는데 이 클래스는 함수 클래스\(들\) 목록에 포함되지 않습니다.|  
|[C28039](../code-quality/c28039.md)|실제 매개 변수의 형식은 형식과 정확히 일치해야 합니다.|  
|[C28112](../code-quality/c28112.md)|Interlocked 함수를 통해 액세스되는 변수는 항상 Interlocked 함수를 통해 액세스해야 합니다.|  
|[C28113](../code-quality/c28113.md)|interlocked 함수를 통해 로컬 변수에 액세스합니다.|  
|[C28125](../code-quality/c28125.md)|함수는 try\/except 블록 내에서 호출해야 합니다.|  
|[C28137](../code-quality/c28137.md)|변수 인수가 대신 \(리터럴\) 상수여야 합니다.|  
|[C28138](../code-quality/c28138.md)|그 대신 상수 인수는 변수여야 합니다.|  
|[C28159](../code-quality/c28159.md)|다른 함수를 대신 사용하십시오.|  
|[C28160](../code-quality/c28160.md)|Error 주석|  
|[C28163](../code-quality/c28163.md)|함수를 try\/except 블록 내에서 호출할 수 없습니다.|  
|[C28164](../code-quality/c28164.md)|인수가 포인터에 대한 포인터가 아니라 개체에 대한 포인터가 필요한 함수로 전달되고 있습니다.|  
|[C28182](../code-quality/c28182.md)|NULL 포인터를 역참조하고 있습니다.  다른 포인터와 포인터가 NULL 값을 포함 합니다.|  
|[C28183](../code-quality/c28183.md)|인수의 값은 하나일 수 있으며 포인터에서 찾은 값의 복사본입니다.|  
|[C28193](../code-quality/c28193.md)|변수가 검사해야 하는 값을 보유하고 있습니다.|  
|[C28196](../code-quality/c28196.md)|충족하지 않은 요구 사항입니다. \(이 식은 true가 아닙니다.\)|  
|[C28202](../code-quality/c28202.md)|비정적 멤버에 대한 잘못된 참조입니다.|  
|[C28203](../code-quality/c28203.md)|클래스 멤버에 대한 모호한 참조입니다.|  
|[C28205](../code-quality/c28205.md)|\_Success\_ 또는 \_On\_failure\_가 잘못된 컨텍스트에서 사용되었습니다.|  
|[C28206](../code-quality/c28206.md)|'\-\>': 왼쪽 피연산자가 구조체를 가리킵니다.|  
|[C28207](../code-quality/c28207.md)|왼쪽 피연산자가 구조체를 가리킵니다. '.'를 사용하십시오.|  
|[C28209](../code-quality/c28209.md)|기호의 선언에 충돌하는 선언이 있습니다.|  
|[C28210](../code-quality/c28210.md)|\_On\_failure\_ 컨텍스트에 대한 주석이 명시적 사전 컨텍스트에 없어야 합니다.|  
|[C28211](../code-quality/c28211.md)|SAL\_context에 대해 정적 컨텍스트 이름이 필요합니다.|  
|[C28212](../code-quality/c28212.md)|주석에 대한 포인터 식이 있어야 합니다.|  
|[C28213](../code-quality/c28213.md)|이전 선언을 수정하지 않고 참조하려면 \_Use\_decl\_annotations\_ 주석을 사용해야 합니다.|  
|[C28214](../code-quality/c28214.md)|특성 매개 변수 이름은 p1...p9여야 합니다.|  
|[C28215](../code-quality/c28215.md)|이미 typefix가 있는 매개 변수에 typefix를 적용할 수 없습니다.|  
|[C28216](../code-quality/c28216.md)|주석은 특정 함수 매개 변수에 대한 사전 조건에만 적용됩니다.|  
|[C28217](../code-quality/c28217.md)|함수의 경우 주석에 대한 매개 변수 개수가 파일에 있는 개수와 일치하지 않습니다.|  
|[C28218](../code-quality/c28218.md)|함수에 대해 매개 변수의 경우 주석 매개 변수 개수가 파일에 있는 개수와 일치하지 않습니다.|  
|[C28219](../code-quality/c28219.md)|주석에 있는 매개 변수 주석에 열거의 멤버가 필요합니다.|  
|[C28220](../code-quality/c28220.md)|주석에 있는 매개 변수 주석에 정수 식이 필요합니다.|  
|[C28221](../code-quality/c28221.md)|주석에 있는 매개 변수에 문자열 식이 필요합니다.|  
|[C28222](../code-quality/c28222.md)|주석에 \_\_yes, \_\_no 또는 \_\_maybe가 필요합니다.|  
|[C28223](../code-quality/c28223.md)|주석, 매개 변수에 대해 토큰\/식별자가 필요한데 없습니다.|  
|[C28224](../code-quality/c28224.md)|주석에 매개 변수가 필요합니다.|  
|[C28225](../code-quality/c28225.md)|주석에서 필요한 수의 매개 변수를 찾을 수 없습니다.|  
|[C28226](../code-quality/c28226.md)|또한 주석은 현재 선언에서 PrimOp일 수 없습니다.|  
|[C28227](../code-quality/c28227.md)|또한 주석은 PrimOp일 수 없습니다\(이전 선언 참조\).|  
|[C28228](../code-quality/c28228.md)|주석 매개 변수: 주석에서 형식을 사용할 수 없습니다.|  
|[C28229](../code-quality/c28229.md)|주석에서 매개 변수를 지원하지 않습니다.|  
|[C28230](../code-quality/c28230.md)|매개 변수 형식에 멤버가 없습니다.|  
|[C28231](../code-quality/c28231.md)|주석은 배열에서만 유효합니다.|  
|[C28232](../code-quality/c28232.md)|Pre, post 또는 deref가 주석에 적용되지 않았습니다.|  
|[C28233](../code-quality/c28233.md)|Pre, post 또는 deref가 블록에 적용되었습니다.|  
|[C28234](../code-quality/c28234.md)|\_\_at\_ 식이 현재 함수에 적용되지 않습니다.|  
|[C28235](../code-quality/c28235.md)|함수는 단독으로 주석으로 사용할 수 없습니다.|  
|[C28236](../code-quality/c28236.md)|주석은 식에서 사용할 수 없습니다.|  
|[C28237](../code-quality/c28237.md)|매개 변수의 주석은 더 이상 지원되지 않습니다.|  
|[C28238](../code-quality/c28238.md)|매개 변수의 주석에 value, stringValue 및 longValue가 두 개 이상 있습니다.  paramn\=xxx를 사용하십시오.|  
|[C28239](../code-quality/c28239.md)|경고 28239: 매개 변수의 주석에 value, stringValue 또는 longValue와 paramn\=xxx가 모두 있습니다.  paramn\=xxx만 사용하십시오.|  
|[C28240](../code-quality/c28240.md)|매개 변수의 주석에 param2는 있는데 param1이 없습니다.|  
|[C28241](../code-quality/c28241.md)|매개 변수의 함수에 대한 주석을 인식할 수 없습니다.|  
|[C28243](../code-quality/c28243.md)|매개 변수의 함수에 대한 주석에 실제 형식 주석이 허용하는 것보다 많은 역참조가 필요합니다.|  
|[C28244](../code-quality/c28244.md)|함수에 대한 주석에 구문 분석할 수 없는 매개 변수\/외부 주석이 있습니다.|  
|[C28245](../code-quality/c28245.md)|함수에 대한 주석에서 멤버가 아닌 함수에 'this'를 주석으로 추가합니다.|  
|[C28246](../code-quality/c28246.md)|함수 매개 변수에 주석을 매개 변수 형식이 일치 하지 않습니다.|  
|[C28250](../code-quality/c28250.md)|함수에 대한 주석이 일치하지 않습니다. 이전 인스턴스에 오류가 있습니다.|  
|[C28251](../code-quality/c28251.md)|함수에 대한 주석이 일치하지 않습니다. 이 인스턴스에 오류가 있습니다.|  
|[C28252](../code-quality/c28252.md)|경고 C28253: 함수에 대한 주석이 일치하지 않습니다. 매개 변수의 이 인스턴스에 다른 주석이 있습니다.|  
|[C28253](../code-quality/c28253.md)|경고 C28253: 함수에 대한 주석이 일치하지 않습니다. 매개 변수의 이 인스턴스에 다른 주석이 있습니다.|  
|[C28254](../code-quality/c28254.md)|dynamic\_cast\<\>\(\)는 주석에서 지원되지 않습니다.|  
|[C28262](../code-quality/c28262.md)|함수에 주석에 대한 주석 구문 오류가 있습니다.|  
|[C28263](../code-quality/c28263.md)|내장 주석에 대한 조건부 주석에 구문 오류가 있습니다.|  
|[C28264](http://msdn.microsoft.com/ko-kr/bf6ea983-a06e-4752-a042-747a7dbf338c)|결과 목록 값은 상수여야 합니다.|  
|[C28267](../code-quality/c28267.md)|함수에 주석에 대한 주석 구문 오류가 있습니다.|  
|[C28272](../code-quality/c28272.md)|함수, 매개 변수에 대한 주석이 검사 시 함수 선언과 일치하지 않습니다.|  
|[C28273](../code-quality/c28273.md)|함수의 암시가 함수 선언과 일치하지 않습니다.|  
|[C28275](../code-quality/c28275.md)|\_Macro\_value\_에 대한 매개 변수가 null입니다.|  
|[C28279](../code-quality/c28279.md)|기호의 경우 일치하는 'end'가 없는 'begin'이 있습니다.|  
|[C28280](../code-quality/c28280.md)|기호의 경우 일치하는 'begin'이 없는 'end'가 있습니다.|  
|[C28282](../code-quality/c28282.md)|형식 문자열이 사전 조건에 있어야 합니다.|  
|[C28285](../code-quality/c28285.md)|함수의 경우 매개 변수에 구문 오류가 있습니다.|  
|[C28286](../code-quality/c28286.md)|함수의 경우 끝에 구문 오류가 있습니다.|  
|[C28287](../code-quality/c28287.md)|함수의 경우 \_At\_\(\) 주석에 구문 오류가 있습니다\(인식할 수 없는 매개 변수 이름\).|  
|[C28288](../code-quality/c28288.md)|함수의 경우 \_At\_\(\) 주석에 구문 오류가 있습니다\(잘못된 매개 변수 이름\).|  
|[C28289](../code-quality/c28289.md)|함수의 경우: ReadableTo 또는 WritableTo에 limit\-spec가 매개 변수로 포함되지 않았습니다.|  
|[C28290](../code-quality/c28290.md)|함수에 대한 주석에 실제 매개 변수 개수보다 많은 외부 참조가 있습니다.|  
|[C28291](../code-quality/c28291.md)|게시물에 null\/notnull deref 수준 0은 함수에 대한 의미가 없습니다.|  
|[C28300](../code-quality/c28300.md)|연산자에 대한 호환되지 않는 형식의 식 피연산자입니다.|  
|[C28301](../code-quality/c28301.md)|함수의 첫 번째 선언에 대한 주석이 없습니다.|  
|[C28302](../code-quality/c28302.md)|주석에 추가 \_Deref\_ 연산자가 있습니다.|  
|[C28303](../code-quality/c28303.md)|주석에 모호한 \_Deref\_ 연산자가 있습니다.|  
|[C28304](../code-quality/c28304.md)|토큰에 부적절하게 배치된 \_Notref\_ 연산자가 적용되었습니다.|  
|[C28305](../code-quality/c28305.md)|token을\(를\) 구문 분석하는 동안 오류가 발생했습니다.|  
|[C28306](../code-quality/c28306.md)|매개 변수의 주석이 사용되지 않습니다.|  
|[C28307](../code-quality/c28307.md)|매개 변수의 주석이 사용되지 않습니다.|  
|[C28350](../code-quality/c28350.md)|주석이 조건부로 적용할 수 없는 상황을 설명합니다.|  
|[C28351](../code-quality/c28351.md)|주석은 동적 값\(변수\)을 조건에 사용할 수 없는 위치를 설명합니다.|