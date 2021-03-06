---
title: BP_FLAGS90 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f8153f3fb2419e26f7e7d3a741ae4c79c9272a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100350"
---
# <a name="bpflags90"></a>BP_FLAGS90
선택적 플래그에 대 한 유효한 값을 열거합니다. 중단점을 설정할 때 추가 정보를 지정 하는 선택적 플래그를 사용할 수 있습니다. 이 열거형 확장는 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 열거 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 BP90_FLAG_NONE  
 중단점 플래그가 지정합니다.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 디버그 엔진 (DE) 문서 위치를 사용 하 여 중단점을 매핑하는 것을 지정 합니다. 스크립트 지향 소스 파일 등 ASP Active Server Pages ()에서 설정 된 중단점에만 적용 됩니다.  
  
 BP90_FLAG_DONT_STOP  
 지정 중단점 디버그 엔진에서 처리 되어야 한다는 하지만 디버그 엔진 궁극적으로 중지 해야 함이 없습니다. 즉, 한 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 이벤트 개체를 보내지 않아야 합니다. 이 플래그는 주로 추적 지점에서 사용 되는 설계 되었습니다.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 네이티브 디버그 엔진에서 단계별 실행 상태를 선택 취소 해야 하는지 여부를 결정 하는 데 사용 합니다. BP90_FLAG_DONT_STOP 추적 지점에 매크로 실행 하는 경우 설정 되어 있지 않으므로 BP90_FLAG_DONT_STOP에서 다릅니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)