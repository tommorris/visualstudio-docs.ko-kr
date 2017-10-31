---
title: "모듈 뷰 - .NET 메모리 계측 데이터 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Modules view
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f3a04d34191f336c8f92c215c7ce064eb6513210

---
# <a name="modules-view---net-memory-instrumentation-data"></a>모듈 뷰 - .NET 메모리 계측 데이터
계측 방법을 사용하여 수집되는 .NET 메모리 할당 데이터의 모듈 뷰에서는 프로파일링 실행에서 실행된 모듈을 기준으로 메모리 및 타이밍 데이터를 그룹화합니다. 모듈의 함수에 대한 프로파일링 데이터는 모듈 노드 아래에 나열됩니다.  
  
## <a name="general"></a>일반  
  
|열|설명|  
|------------|-----------------|  
|**Name**|함수 또는 모듈의 이름입니다.|  
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|  
|**호출 수**|이 함수 또는 모듈에 대해 수행한 총 호출 수입니다.|  
|**소스 파일**|이 함수의 정의가 포함된 소스 파일입니다.|  
|**모듈 이름**|함수가 포함된 모듈의 이름입니다.|  
|**모듈 경로**|함수가 포함된 모듈의 경로입니다.|  
|**프로세스 ID**|프로파일링 실행의 PID(프로세스 ID)입니다.|  
|**프로세스 이름**|모듈이나 함수를 실행 중이었던 프로세스의 이름입니다.|  
|**시간 제외 프로브 오버헤드**|계측으로 인한 이 함수 또는 모듈의 시간 오버헤드입니다.|  
|**시간 포괄 프로브 오버헤드**|계측으로 인한 이 함수 또는 모듈과 해당 자식 함수의 시간 오버헤드입니다.|  
  
## <a name="net-memory-values"></a>.NET 메모리 값  
 함수의 포괄 .NET 메모리 값은 함수 및 해당 자식 함수에 의해 생성된 개체의 수(할당) 및 크기(바이트)를 나타냅니다.  
  
 제외 메모리 값은 자식 함수가 아닌 해당 함수에 의해 생성된 개체의 수와 크기를 나타냅니다.  
  
 모듈의 포괄 및 제외 메모리 값은 모듈 내 함수의 포괄 및 제외 메모리 값 합계입니다.  
  
|열|설명|  
|------------|-----------------|  
|**포함 할당**|-   함수의 경우 함수에 의해 생성된 개체의 총 수입니다. 이 수에는 함수가 호출한 함수에 생성된 개체가 포함됩니다.<br />-   모듈의 경우 모듈의 함수 중 하나 이상이 실행 중일 때 할당된 프로파일링 실행의 개체 수입니다. 이 수에는 모듈 함수의 호출에 의해 생성된 함수에서 할당된 개체가 포함됩니다.|  
|**포함 할당 비율(%)**|모듈 또는 함수의 포함 할당인 프로파일링 실행에서 할당된 모든 개체의 비율입니다.|  
|**제외 할당**|-   함수의 경우 함수가 함수 본문의 코드를 실행하고 있을 때(즉, 함수가 호출 스택의 맨 위에 있을 때) 생성된 개체의 수입니다. 이 수에는 함수가 호출한 함수에 생성된 개체는 포함되지 않습니다.<br />-   모듈의 경우 모듈 내 함수의 제외 할당 합계입니다.|  
|**제외 할당 비율(%)**|모듈 또는 함수의 제외 할당인 프로파일링 실행에서 할당된 모든 개체의 비율입니다.|  
|**제외 바이트**|-   함수의 경우 함수가 함수 본문의 코드를 실행하고 있을 때(즉, 함수가 호출 스택의 맨 위에 있을 때) 할당된 메모리의 총 바이트 수입니다. 이 수에는 함수가 호출한 함수에서 할당된 바이트는 포함되지 않습니다.<br />-   모듈의 경우 모듈 내 함수에 의해 할당된 제외 바이트의 합계입니다.|  
|**제외 바이트(%)**|모듈, 함수, 줄 또는 명령의 제외 바이트인 프로파일링 실행에서 할당된 모든 바이트의 비율입니다.|  
|**포함 바이트**|-   함수의 경우 함수에 의해 할당된 바이트 수입니다. 이 수에는 함수가 호출한 함수에서 할당된 바이트가 포함됩니다.<br />-   모듈의 경우 프로파일링 실행에서 할당되었으며 모듈의 함수 중 하나 이상이 실행 중일 때 할당된 바이트 수입니다. 이 수에는 모듈 함수가 호출한 모든 함수에 생성된 개체가 포함됩니다.|  
|**포함 바이트 비율(%)**|모듈 또는 함수의 포함 바이트인 프로파일링 실행에서 할당된 모든 바이트의 비율입니다.|  
  
## <a name="elapsed-inclusive-values"></a>경과된 포괄 시간값  
 경과된 포괄 시간값은 함수가 호출 스택에 있던 시간을 나타냅니다. 시간에는 자식 함수에서 소요된 시간과 컨텍스트 전환 및 입/출력 작업처럼 운영 체제에 대한 호출에 소요된 시간이 포함됩니다.  
  
|열|설명|  
|------------|-----------------|  
|**경과된 포괄 시간**|-   함수의 경우 함수에서 소요된 시간입니다. 이 시간에는 자식 함수에서 소요된 시간과 컨텍스트 전환 및 입/출력 작업처럼 운영 체제에 대한 호출에 소요된 시간이 포함됩니다.<br />-   모듈의 경우 모듈의 함수 하나 이상이 호출 스택에 있었던 기간입니다.|  
|**경과된 포괄 시간 %**|이 모듈이나 이 함수의 총 경과된 포괄 시간에서 소요된 프로파일링 실행의 총 경과된 포괄 시간 비율입니다.|  
|**경과된 평균 포괄 시간**|-   함수의 경우 이 함수에 대한 호출의 평균 경과된 포괄 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 평균 경과된 포괄 시간입니다.|  
|**경과된 최대 포괄 시간**|-   함수의 경우 이 함수에 대한 호출의 최대 경과된 포괄 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 최대 경과된 포괄 시간입니다.|  
|**경과된 최소 포괄 시간**|-   함수의 경우 이 모듈 또는 함수에 대한 호출의 최소 경과된 포괄 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 최소 경과된 포괄 시간입니다.|  
  
## <a name="elapsed-exclusive-values"></a>경과된 전용 시간값  
 경과된 전용 값은 함수가 호출 스택의 맨 위에서 직접 실행 중이던 시간을 나타냅니다. 시간에는 컨텍스트 전환 및 입/출력 작업처럼 운영 체제에 대한 호출 시간이 포함됩니다. 그러나 자식 함수에서 소요된 시간은 포함되지 않습니다.  
  
|열|설명|  
|------------|-----------------|  
|**경과된 전용 시간**|-   함수의 경우 모듈이나 함수에서 소요된 시간입니다. 여기에는 컨텍스트 전환 및 입/출력 작업처럼 운영 체제에 대한 호출은 포함되지만 자식 함수에서 소요된 시간은 제외됩니다.<br />-   모듈의 경우 모듈 내 함수의 경과된 전용 시간 합계입니다.|  
|**경과된 전용 시간 %**|이 모듈이나 함수의 총 경과된 전용 시간에서 소요된 프로파일링 실행의 총 경과된 전용 시간 비율입니다.|  
|**경과된 평균 전용 시간**|-   함수의 경우 이 함수에 대한 호출의 평균 경과된 전용 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 평균 경과된 전용 시간입니다.|  
|**최대 경과된 전용 시간**|-   함수의 경우 이 함수에 대한 호출의 최대 경과된 전용 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 최대 경과된 전용 시간입니다.|  
|**경과된 최소 전용 시간**|-   함수의 경우 이 모듈 또는 함수에 대한 호출의 최소 경과된 전용 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 최소 경과된 전용 시간입니다.|  
  
## <a name="application-inclusive-values"></a>응용 프로그램 포괄 시간값  
 응용 프로그램 포괄 값은 함수가 호출 스택에 있던 시간을 나타냅니다. 시간에는 컨텍스트 전환 및 입/출력 작업처럼 운영 체제에 대한 호출에 소요된 시간이 포함되지 않습니다. 그러나 자식 함수에서 소요된 시간은 포함됩니다.  
  
|열|설명|  
|------------|-----------------|  
|**응용 프로그램 포괄 시간**|-   함수의 경우 함수 호출에서 소요된 시간입니다. 여기에는 자식 함수에서 소요된 시간은 포함되지만 컨텍스트 전환 및 입/출력 작업처럼 운영 체제에 대한 호출은 제외됩니다.<br />-   모듈의 경우 운영 체제에 대한 호출에서 소요된 시간을 제외하고 모듈의 함수 하나 이상이 호출 스택에 있었던 기간입니다.|  
|**응용 프로그램 포괄 시간 비율(%)**|이 모듈이나 함수의 응용 프로그램 포괄 시간에서 소요된 프로파일링 실행의 총 경과된 포괄 시간 비율입니다.|  
|**평균 응용 프로그램 포괄 시간**|-   함수의 경우 이 함수에 대한 호출의 평균 응용 프로그램 포괄 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 평균 응용 프로그램 포괄 시간입니다.|  
|**최대 응용 프로그램 포괄 시간**|-   함수의 경우 이 함수에 대한 호출의 최대 응용 프로그램 포괄 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 최대 응용 프로그램 포괄 시간입니다.|  
|**최소 응용 프로그램 포괄 시간**|-   함수의 경우 이 모듈이나 함수에 대한 호출의 최소 응용 프로그램 포괄 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 최소 응용 프로그램 포괄 시간입니다.|  
  
## <a name="application-exclusive-values"></a>응용 프로그램 전용 값  
 응용 프로그램 전용 값은 자식 함수에서 소요된 시간을 제외하고 모듈이나 함수에서 소요된 시간을 나타냅니다. 표시된 값에는 컨텍스트 전환 및 입/출력 작업처럼 운영 체제에 대한 호출도 제외됩니다.  
  
|열|설명|  
|------------|-----------------|  
|**응용 프로그램 전용 시간**|-   함수의 경우 이 함수에 대한 호출의 총 응용 프로그램 전용 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 총 응용 프로그램 전용 시간입니다.|  
|**응용 프로그램 전용 시간 비율(%)**|프로파일링 실행에서 경과된 총 전용 시간에서 이 모듈이나 함수의 응용 프로그램 전용 시간에 소요된 시간의 백분율입니다.|  
|**평균 응용 프로그램 전용 시간**|-   함수의 경우 이 함수에 대한 호출의 평균 응용 프로그램 전용 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 평균 응용 프로그램 전용 시간입니다.|  
|**최대 응용 프로그램 전용 시간**|-   함수의 경우 이 함수에 대한 호출의 최대 응용 프로그램 전용 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 최대 응용 프로그램 전용 시간입니다.|  
|**최소 응용 프로그램 전용 시간**|-   함수의 경우 이 모듈이나 함수에 대한 호출의 최소 응용 프로그램 전용 시간입니다.<br />-   모듈의 경우 모듈 내 함수에 대한 모든 호출의 최소 응용 프로그램 전용 시간입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [모듈 뷰 - 샘플링](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [모듈 뷰](../profiling/modules-view-instrumentation-data.md)   
 [모듈 뷰](../profiling/modules-view-sampling-data.md)


<!--HONumber=Feb17_HO4-->

