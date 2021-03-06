---
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c1598ec8a6e5fca5275384c00433d74d22ce3505
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107896"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
이 인터페이스는 명령의 스트림을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진 프로그램의 코드의 디스어셈블리를 지원 하기 위해이 인터페이스를 구현 합니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 참고 사항  
 에 대 한 호출에서 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) 메서드가이 인터페이스를 반환 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugDisassemblyStream2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|디스어셈블리 스트림 내의 현재 위치에서 시작 하는 지침을 읽습니다.|  
|[검색](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|디스어셈블리 스트림에서 지정된 된 수의 지정된 된 위치에 상대적인 지침 읽기 포인터를 이동합니다.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|특정 코드 컨텍스트에 대 한 코드 위치 식별자를 반환합니다.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|지정한 코드 위치 id에 해당 하는 코드 컨텍스트 개체를 반환 합니다.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|현재 코드 위치를 나타내는 코드 위치 식별자를 반환 합니다.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|이 디스어셈블리 스트림과 연결 된 원본 문서를 가져옵니다.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|디스어셈블리 스트림에이 범위를 가져옵니다.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|이 디스어셈블리 스트림의 크기를 가져옵니다.|  
  
## <a name="remarks"></a>설명  
 또는 표시 하 여 전체 주소 공간 또는는 함수 내 공간에서 모듈이 디스어셈블리 스트림을 만들 수 있습니다. 각 명령으로 표시 됩니다는 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 구조에 대 한 호출에서 반환 되는 [읽기](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 메서드.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [코어 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)