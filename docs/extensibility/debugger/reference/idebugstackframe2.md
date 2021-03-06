---
title: IDebugStackFrame2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: efa6c917e5a59c291d07757b52fab4fe8aa7b0ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122095"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
이 인터페이스의 특정 스레드에서 호출 스택에 있는 단일 스택 프레임을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 (DE) 스택 프레임을 나타내기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 참고 사항  
 호출 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 검색 하는 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) 인터페이스입니다. 호출 [다음](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) 검색 하는 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 포함 된 구조는 `IDebugStackFrame2` 인터페이스입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugStackFrame2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|이 스택 프레임에 대 한 코드 컨텍스트를 가져옵니다.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|이 스택 프레임에 대 한 문서 컨텍스트를 가져옵니다.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|스택 프레임의 이름을 가져옵니다.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|스택 프레임에 대 한 설명을 가져옵니다.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|스택 프레임과 연결 된 물리적 주소 범위에 대 한 컴퓨터 종속 표현을 가져옵니다.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|스택 프레임 및 스레드는 현재 컨텍스트 내에서 식 평가 수행 하는 데는 평가 컨텍스트를 가져옵니다.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|스택 프레임와 관련 된 언어를 가져옵니다.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|스택 프레임와 연결 된 속성에 대 한 설명을 가져옵니다.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|프레임 속성 스택에 대 한 열거자를 만듭니다.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|스택 프레임과 연결 된 스레드를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 디버깅 중인 프로그램 (발생 한 사용자가 설정한 중단점 또는 예외) 중단점에서 중지 되었습니다 하는 경우에 가져옵니다. 이 인터페이스에서 식을 평가 하는 식 컨텍스트를 가져올 수 있습니다, 레지스터의 목록을 반환할 수 있습니다, 또는 호출 스택의 검사 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)