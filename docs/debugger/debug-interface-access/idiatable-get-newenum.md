---
title: "IDiaTable::get__NewEnum | Microsoft Docs"
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
  - "IDiaTable::get__NewEnum 메서드"
ms.assetid: ee89bba8-5d5c-4a0b-aa0d-1aad56baa380
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaTable::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

검색은 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 이 열거자의 버전입니다.  
  
## 구문  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### 매개 변수  
 `pRetVal`  
 \[out\] 반환은 `IUnknown` 나타내는 인터페이스는 <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> 이 열거자의 버전입니다.  
  
## 반환 값  
 성공 하면 반환 `S_OK`. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## 참고 항목  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)