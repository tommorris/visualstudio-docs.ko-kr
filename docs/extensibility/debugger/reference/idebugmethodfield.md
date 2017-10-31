---
title: IDebugMethodField | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 12
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
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 46d6173d2c015dc783bac0778b93419101d4c553
ms.lasthandoff: 04/05/2017

---
# <a name="idebugmethodfield"></a>IDebugMethodField
이 인터페이스는 방법을 설명 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 기호 공급자를 구현 하는 동일한 개체에서이 인터페이스를 구현 하는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스입니다. 이 인터페이스는 메서드를 제공 하는 특수화는 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 참고 사항  
 사용 하 여 [QueryInterface](/cpp/atl/queryinterface) 에서이 인터페이스를 가져올 수는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 반환 `FIELD_TYPE_METHOD`합니다. 메서드는 또한 [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md), 및 [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)모든 반환는 `IDebugMethodField` 인터페이스입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 메서드 외에도 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 경우이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|메서드의 매개 변수에 대 한 열거자를 만듭니다.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|메서드를 포함 하는 개체의 "this"이 포인터를 가져옵니다.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|메서드의 모든 지역 변수에 대 한 열거자를 만듭니다.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|메서드의 선택한 지역 변수에 대 한 열거자를 만듭니다.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|특정 사용자 지정 특성 정의 되었는지 여부를 결정 합니다.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|메서드는 정적 지역 변수에 대 한 열거자를 만듭니다.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|메서드의 글로벌 컨테이너를 가져옵니다.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|메서드를 호출 하는 데 필요한 각 인수의 형식에 대 한 열거자를 만듭니다.|  
  
## <a name="remarks"></a>주의  
 메서드 매개 변수 뿐만 아니라 지역 변수를 포함할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)