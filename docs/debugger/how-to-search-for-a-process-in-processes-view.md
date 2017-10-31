---
title: "How to: Search for a Process in Processes View | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Processes view"
  - "processes, searching for"
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# How to: Search for a Process in Processes View
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

프로세스 ID나 모듈 문자열을 검색 조건으로 사용하여 프로세스 뷰에서 특정 프로세스를 검색할 수 있으며,  검색의 초기 방향을 지정할 수도 있습니다.  이 대화 상자의 필드에는 프로세스 트리에서 선택한 프로세스의 특성이 표시됩니다.  
  
### 프로세스 뷰에서 프로세스를 검색하려면  
  
1.  Spy\+\+와 활성 [프로세스 뷰](../debugger/processes-view.md) 창이 보이도록 창을 정렬합니다.  
  
2.  **검색** 메뉴에서 **프로세스 찾기**를 선택합니다.  
  
     [프로세스 검색 대화 상자](../debugger/process-search-dialog-box.md)가 열립니다.  
  
3.  프로세스 ID나 모듈 문자열을 검색 조건으로 입력합니다.  
  
4.  값을 지정하지 않을 모든 필드를 지웁니다.  
  
    > [!TIP]
    >  모듈이 소유하고 있는 모든 프로세스를 찾으려면 **프로세스** 상자를 지우고 **모듈** 상자에 모듈 이름을 입력합니다.  그런 후 **다음 찾기**를 사용하여 프로세스를 계속 검색합니다.  
  
5.  검색의 초기 방향으로 **위로** 또는 **아래로**를 선택합니다.  
  
6.  **확인**을 클릭합니다.  
  
 일치하는 프로세스가 발견되면 **프로세스 뷰** 창에서 강조 표시됩니다.