---
title: IDebugProgramHost2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b0161e2dd978b82eb5b09780a3fc07c25d15667
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119079"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
이 인터페이스는 프로그램에 대 한 호스트 (process) 정보를 제공합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 디버그 엔진으로 동일한 개체에서이 인터페이스를 구현 하는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 호스팅 프로세스에 대 한 정보를 제공 하는 인터페이스입니다. 선택적 인터페이스입니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 참고 사항  
 호출 [QueryInterface](/cpp/atl/queryinterface) 에 `IDebugProgram2` 인터페이스가이 인터페이스를 가져올 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugProgramHost2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|제목, 이름, 또는이 프로그램의 호스팅 프로세스의 파일 이름을 가져옵니다.|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|이 프로그램의 호스팅 프로세스의 프로세스 식별자를 가져옵니다.|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|이 프로그램의 호스팅 프로세스가 실행 중인 컴퓨터의 이름을 가져옵니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [코어 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)