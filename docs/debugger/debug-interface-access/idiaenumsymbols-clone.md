---
title: "IDiaEnumSymbols::Clone | Microsoft Docs"
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
  - "IDiaEnumSymbols::Clone 메서드"
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbols::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

현재 열거자와 열거 상태가 같은 포함 하는 열거자를 만듭니다.  
  
## 구문  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSymbols** ppenum  
);  
```  
  
#### 매개 변수  
 ppenum  
 \[out\] 반환 된 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 열거자의 복제본을 포함 하는 개체입니다.  기호가 중복 되지는 열거자입니다.  
  
## 반환 값  
 성공 하면 반환 `S_OK`. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## 참고 항목  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)