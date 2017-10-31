---
title: "계층 상호 작용 뷰 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.tierinteraction"
helpviewer_keywords: 
  - "계층 상호 작용 뷰"
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# 계층 상호 작용 뷰
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

계층 상호 작용 프로파일링에서는 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]을 통해 데이터베이스와 통신하는 다중 계층 응용 프로그램의 함수 실행 시간에 대한 추가 정보를 제공합니다.  동기 함수 호출에 대한 데이터만 수집됩니다.  
  
 **요구 사항**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 상호 작용 뷰에서는 계층 상호 작용 데이터가 두 개의 창에 표시됩니다.  
  
-   주 창은 계층 트리로 표시됩니다.  최상위 행에는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 페이지나 프로세스의 응용 프로그램 연결에 대한 집계된 데이터가 들어 있습니다.  자식 노드에는 부모의 데이터베이스 호출에 대한 집계된 데이터가 들어 있습니다.  
  
-   주 창에서 데이터베이스 호출 노드를 클릭하면 해당 데이터베이스 호출 인스턴스에 대한 데이터가 세부 정보 창에 표시됩니다.  
  
 시간은 밀리초 또는 CPU 클록 틱 수로 표시됩니다.  표시되는 시간 단위를 변경하려면 **도구** 메뉴를 클릭하고 **옵션**을 클릭한 다음 **시간 값 표시** 옵션 중 하나를 선택합니다.  
  
## 주 창  
  
|열|설명|  
|-------|--------|  
|**Name**|-   최상위 행의 경우, 프로파일링된 프로세스 또는 웹 페이지의 이름입니다.<br />-   데이터베이스 연결 행의 경우, 해당 데이터베이스를 호스팅하는 서버의 이름입니다.|  
|**데이터베이스**|데이터베이스의 이름입니다\(데이터베이스 연결 행에만 해당\).|  
|**개수**|프로세스, 웹 페이지 또는 데이터베이스 연결에 의해 생성된 총 요청 수입니다.|  
|**총 경과 시간**|프로세스, 웹 페이지 또는 데이터베이스 연결에서 하나의 요청을 실행하는 데 소요된 총 시간입니다.|  
|**최대 경과 시간**|해당 프로세스, 웹 페이지 또는 데이터베이스 연결에서 하나의 요청을 실행하는 데 소요된 최대 시간입니다.|  
|**최소 경과 시간**|프로세스, 웹 페이지 또는 데이터베이스 연결에서 하나의 요청을 실행하는 데 소요된 최소 시간입니다.|  
|**평균 경과 시간**|해당 프로세스, 웹 페이지 또는 데이터베이스 연결에서 하나의 요청을 실행하는 데 소요된 평균 시간입니다.|  
  
## 데이터베이스 연결 정보 창  
  
|열|설명|  
|-------|--------|  
|**명령 텍스트**|요청의 SQL 쿼리입니다.|  
|**쿼리 수**|쿼리가 실행된 횟수입니다.|  
|**총 경과 시간**|해당 쿼리 인스턴스를 실행하는 데 소요된 총 시간입니다.|  
|**최대 경과 시간**|하나의 쿼리 인스턴스를 실행하는 데 소요된 최대 시간입니다.|  
|**최소 경과 시간**|하나의 쿼리 인스턴스를 실행하는 데 소요된 최소 시간입니다.|  
|**평균 경과 시간**|하나의 쿼리 인스턴스를 실행하는 데 소요된 평균 시간입니다.|