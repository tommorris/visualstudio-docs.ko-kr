---
title: IDebugPropertyField::GetPropertyGetter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPropertyField::GetPropertyGetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertyGetter method
ms.assetid: ab9f861a-42ad-4a82-9ae6-2606176f755a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d58b9f6e390378f10ef08e70894eb7ea74fc8296
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120990"
---
# <a name="idebugpropertyfieldgetpropertygetter"></a>IDebugPropertyField::GetPropertyGetter
속성을 가져오는 메서드를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetPropertyGetter(   
   IDebugMethodField** ppField  
);  
```  
  
```cpp  
int GetPropertyGetter(  
   out IDebugMethodField ppField  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppField`  
 [out] 반환 된 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 속성을 가져오는 메서드를 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 s_ok이 고; 반환 그렇지 않은 경우 오류 코드를 반환합니다.  
  
## <a name="remarks"></a>설명  
 속성을 설정 하는 메서드를 가져올 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md) 메서드를 호출 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)   
 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)