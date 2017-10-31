---
title: "프로세스 속성 대화 상자, 메모리 탭 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows NT의 프로세스 속성"
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# 프로세스 속성 대화 상자, 메모리 탭
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**메모리** 탭을 사용하여 프로세스가 메모리를 사용하는 방법을 표시할 수 있습니다.  [프로세스 속성 대화 상자](../debugger/process-properties-dialog-box.md)를 표시하려면 포커스를 [프로세스 뷰](../debugger/processes-view.md) 창으로 이동합니다.  그런 다음 트리에서 프로세스 노드를 선택하고 **보기** 메뉴에서 **속성**을 선택합니다.  
  
 **메모리** 탭에서 사용할 수 있는 설정은 다음과 같습니다.  
  
|Entry|설명|  
|-----------|--------|  
|**가상 바이트**|프로세스가 사용하고 있는 가상 주소 공간의 바이트 수입니다.  가상 주소 공간의 사용이 해당 디스크 또는 주 메모리 페이지를 반드시 사용함을 뜻하지는 않습니다.  그러나 가상 공간이 한정되어 있으므로 가상 공간을 너무 많이 사용하면 프로세스가 라이브러리를 로드하는 데 제한을 받을 수 있습니다.|  
|**최고 가상 바이트**|어느 한 시점에서 프로세스가 사용한 가상 주소 공간의 최대 바이트 수입니다.|  
|**작업 집합**|프로세스의 스레드가 최근에 작업한 메모리 페이지의 집합입니다.  컴퓨터에 있는 빈 메모리가 한계를 초과하면 페이지는 사용 중이 아니라도 프로세스의 작업 집합에 남아 있습니다.  빈 메모리가 한계 미만이면 페이지는 작업 집합에서 지워집니다.  이 페이지가 필요하면 주 메모리에서 없어지기 전에 소프트 오류 처리되어 다시 작업 집합에 있게 됩니다.|  
|**최고 작업 집합**|어느 한 시점에서 이 프로세스의 작업 집합에 포함된 최대 페이지 수입니다.|  
|**페이징 풀 바이트**|프로세스가 할당한 현재 페이징 풀의 양입니다.  페이징 풀은 운영 체제 구성 요소가 지정된 작업을 수행할 때 공간을 확보하는 시스템 메모리 영역입니다.  페이징 풀 페이지는 일정 기간 동안 시스템에 의해 액세스되지 않으면 페이징 파일로 페이징 아웃될 수 있습니다.|  
|**비페이징 풀 바이트**|프로세스가 할당한 비페이징 풀의 현재 바이트 수입니다.  비페이징 풀은 운영 체제 구성 요소가 지정된 작업을 수행할 때 공간을 확보하는 시스템 메모리 영역입니다.  비페이징 풀 페이지는 페이징 파일로 페이징 아웃될 수 없으므로 할당되어 있는 한 주 메모리에 그대로 유지됩니다.|  
|**전용 바이트**|이 프로세스가 할당한 현재 바이트 수로, 다른 프로세스와 공유될 수 없습니다.|  
|**사용 가능한 바이트**|이 프로세스에 의해 사용되지 않는 총 가상 주소 공간입니다.|  
|**예약된 바이트**|이 프로세스가 나중에 사용하기 위해 예약한 총 가상 메모리 양입니다.|  
|**사용 가능한 이미지 바이트**|이 프로세스 내의 이미지에 의해 사용되고 있지 않거나 예약되지 않은 가상 주소 공간의 양입니다.|  
|**예약된 이미지 바이트**|이 프로세스 내에서 실행되는 이미지에 의해 예약된 모든 가상 메모리의 합계입니다.|