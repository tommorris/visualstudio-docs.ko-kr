---
title: "IEnumDebugAddresses::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses::Reset"
helpviewer_keywords: 
  - "IEnumDebugAddresses::Reset 메서드"
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugAddresses::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

이 메서드는 첫 번째 요소에 열거형을 다시 설정합니다.  
  
## 구문  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
#### 매개 변수  
 없음  
  
## 반환 값  
 성공 하면 반환 `S_OK`. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## 설명  
 이 메서드 호출 후 다음 호출을 [다음](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) 열거형의 첫 번째 요소를 반환 합니다.  
  
## 참고 항목  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [다음](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)