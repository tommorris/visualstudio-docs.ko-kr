---
title: IDebugObject::IsEqual | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 9
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
ms.openlocfilehash: 9780a18ff72058a90739c421061fabd9ce8520e1
ms.contentlocale: ko-kr
ms.lasthandoff: 09/26/2017

---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
이 개체와 개체를 비교합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pObject`  
 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 비교할 개체를 나타내는 개체입니다.  
  
 `pfIsEqual`  
 [out] 0이 아닌 반환 (`TRUE`) 개체의 값은 같고, 그렇지 않으면 0이 반환 (`FALSE`).  
  
## <a name="return-value"></a>반환 값  
 성공 하면 s_ok이 고; 반환 그렇지 않은 경우 오류 코드를 반환합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드 주소를 나타내는 값을 비교할 수는 일반적으로 `pObject` 매개 변수 및이 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체; 주소가 같으면 개체 취급 될 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)