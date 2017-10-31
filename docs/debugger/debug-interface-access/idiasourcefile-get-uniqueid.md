---
title: "IDiaSourceFile::get_uniqueId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSourceFile::get_uniqueId 메서드"
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

이 이미지에 대 한 고유 하는 간단한 정수 키 값을 검색 합니다.  
  
## 구문  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### 매개 변수  
 `pRetVal`  
 \[out\] 이 이미지에 대 한 고유 하는 간단한 정수 키 값을 반환 합니다.  
  
## 반환 값  
 성공 하면 반환 `S_OK`. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## 설명  
 문자열 줄 번호 처리 속도 높일 수 있는 것이 아니라 키를 비교 합니다.  
  
## 참고 항목  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)