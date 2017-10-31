---
title: "디버그 후크 함수 작성 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "디버그 후크 함수"
  - "디버깅[C++], CRT 디버그 지원"
  - "디버깅[CRT], 디버그 후크 함수"
  - "후크"
  - "후크, 디버그"
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 디버그 후크 함수 작성
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

이 단원에서는 디버거의 표준 처리 과정에서 미리 정의된 특정 지점에 코드를 삽입하기 위해 작성할 수 있는 여러 가지 사용자 지정 디버그 후크 함수에 대해 설명합니다.  
  
## 단원 내용  
 [클라이언트 블록 후크 함수](../debugger/client-block-hook-functions.md)  
 \_CLIENT\_BLOCK 블록에 저장되는 데이터의 내용을 보고하거나 그 유효성을 검사하는 함수의 프로토타입과 작성 지침을 제공합니다.  
  
 [할당 후크 함수](../debugger/allocation-hook-functions.md)  
 할당 후크 함수를 정의하고 여러 가지 용도를 파악하고 제한 사항을 알아 보며 프로토타입을 제공합니다.  
  
 [할당 후크 및 CRT 메모리 할당](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 내부 메모리를 할당하는 C 런타임 라이브러리 함수를 호출할 때 `_CRT_BLOCK` 블록을 명시적으로 무시하는 할당 후크 함수에 대한 제한 사항에 대해 설명합니다.  또한 할당 후크가 `_CRT_BLOCK` 블록\(예제\)을 무시하지 않을 경우에 발생하는 결과와 기본 할당 후크 함수 **CrtDefaultAllocHook**를 변경하는 방법도 소개합니다.  
  
 [보고서 후크 함수](../debugger/report-hook-functions.md)  
 특정 형식의 할당에 맞게 보고서를 필터링하는 데 사용할 수 있는 `_CrtSetReportHook` 함수에 대해 설명하고  프로토타입을 제공합니다.  
  
## 관련 단원  
 [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md)  
 CRT 디버그 라이브러리 사용, 보고서 매크로, `malloc`과 `_malloc_dbg`의 차이, 디버그 후크 함수 작성, CRT 디버그 힙 등과 같은 C 런타임 라이브러리의 디버깅 기술에 대해 설명합니다.