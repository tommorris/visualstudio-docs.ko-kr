---
title: METADATA_ADDRESS_FIELD | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 384966b842db1ed685f365b2bead228e5dadd23f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125647"
---
# <a name="metadataaddressfield"></a>METADATA_ADDRESS_FIELD
이 구조체는 클래스 또는 구조체의 필드의 주소를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_FIELD {  
   _mdToken tokField;  
} METADATA_ADDRESS_FIELD  
```  
  
```csharp  
public struct METADATA_ADDRESS_FIELD {  
   public int tokField;  
}  
```  
  
## <a name="terms"></a>용어  
 tokField  
 Field 토큰의 ID입니다.  
  
 [C + +] `_mdToken` 는 `typedef` 32 비트 `int`합니다.  
  
## <a name="remarks"></a>설명  
 이 구조체의 공용 구조체의 일부인는 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 때 구조는 `dwKind` 필드는 `DEBUG_ADDRESS_UNION` 구조로 설정 되어 `ADDRESS_KIND_FIELD` (의 값은 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형)입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)