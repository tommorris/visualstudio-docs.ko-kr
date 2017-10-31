---
title: "요약 뷰 - 프로파일러 계측 데이터 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "요약 뷰"
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 요약 뷰 - 프로파일러 계측 데이터
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

요약 뷰에는 프로파일링 실행 시 성능 부담이 가장 큰 함수에 대한 정보가 표시됩니다.  알림 링크 및 보고서 목록에 대한 설명을 비롯한 자세한 내용은 [요약 뷰](../profiling/summary-view.md)를 참조하십시오.  
  
## 시간 표시 그래프  
 요약 뷰의 시간 표시 그래프에서는 프로파일링이 발생한 시간 동안 프로파일링된 응용 프로그램에서의 프로세서\(CPU\) 사용률을 보여 줍니다.  시간 표시 그래프를 사용하여 선택한 시간 범위로 뷰를 필터링할 수 있습니다.  자세한 내용은 [방법: 요약 시간 표시 막대에서 보고서 뷰 필터링](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)을 참조하십시오.  
  
## 실행 부하 과다 경로  
 **실행 부하 과다 경로**에는 가장 많은 시간을 소모한 실행 경로가 표시됩니다.  함수를 클릭하여 해당 함수에 대한 함수 정보 뷰를 표시할 수 있습니다.  함수에 대한 다른 뷰를 표시하려면 함수를 마우스 오른쪽 단추로 클릭하고 목록에서 뷰를 클릭합니다.  
  
 **실행 부하 과다 경로**에는 각 함수에 대한 다음 데이터가 포함됩니다.  
  
|열|설명|  
|-------|--------|  
|**Name**|함수의 이름.|  
|**경과된 포괄 시간\(%\)**|프로파일링 데이터의 전체 시간 중 해당 함수가 함수 본문 및 해당 함수에 의해 호출된 함수의 코드를 실행하는 데 소요한 시간의 백분율입니다.|  
|**경과된 전용 시간\(%\)**|프로파일링 데이터의 전체 시간 중 해당 함수가 함수 본문의 코드를 실행하는 데 소요한 시간의 백분율입니다.  해당 함수가 호출한 함수에서 소요된 시간은 포함되지 않습니다.|  
  
## 개별 작업이 가장 많은 함수  
 함수 본문의 코드\(해당 함수가 호출한 함수의 코드는 제외\)를 실행하는 데 가장 많은 시간이 소요된 함수의 목록입니다.  
  
 **개별 작업이 가장 많은 함수**에는 각 함수에 대한 다음 데이터가 포함됩니다.  
  
|열|설명|  
|-------|--------|  
|**Name**|함수의 이름.|  
|**전용 시간\(Exclusive Time\) %**|프로파일링 데이터의 전체 시간 중 해당 함수가 함수 본문의 코드를 실행하는 데 소요한 시간의 백분율입니다.  해당 함수가 호출한 함수에서 소요된 시간은 포함되지 않습니다.|  
  
## 참고 항목  
 [요약 뷰](../profiling/summary-view-sampling-data.md)   
 [요약 뷰](../profiling/summary-view-dotnet-memory-data.md)