---
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f5be75214e9ab112cc3af17bd8bdcfae00083661
ms.contentlocale: ko-kr
ms.lasthandoff: 09/26/2017

---
# <a name="bpresolutiondata"></a>BP_RESOLUTION_DATA
데이터 중단점을 바인딩한 결과를 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```csharp  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## <a name="members"></a>멤버  
 `bstrDataExpr`  
 바인딩된 데이터 식입니다.  
  
 `bstrFunc`  
 함수의 이름 데이터 중단점에 바인딩하지 (있는 경우).  
  
 `bstrImage`  
 데이터 중단점에 바인딩하지 모듈 (예: MyModule.dll)의 이름입니다.  
  
 `dwFlags`  
 값은 [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) 데이터 중단점을 구현 하는 방법을 설명 하는 열거형입니다.  
  
## <a name="remarks"></a>설명  
 이 구조체의 멤버는는 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) 구조체에는 설정의 멤버는 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 에서 반환 된 구조는 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)메서드.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)