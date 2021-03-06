---
title: METADATA_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66a1632198a0af5490e66a843458fc55bcad2d6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134723"
---
# <a name="metadatatype"></a>METADATA_TYPE
이 구조체는 메타 데이터에서 가져온 필드 형식에 대 한 정보를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>매개 변수  
 ulAppDomainID  
 기호를 가져온 응용 프로그램의 ID입니다. 이 응용 프로그램의 인스턴스를 고유 하 게 식별 하기 위해 사용 됩니다.  
  
 guidModule  
 이 필드를 포함 하는 모듈의 GUID입니다.  
  
 tokClass  
 이러한 종류의 메타 데이터 토큰 ID입니다.  
  
 [C + +] `_mdToken` 는 `typedef` 32 비트 `int`합니다.  
  
## <a name="remarks"></a>설명  
 이 구조체의 공용 구조체의 일부분으로 표시는 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 때 구조는 `dwKind` 필드는 `TYPE_INFO` 구조로 설정 되어 `TYPE_KIND_METADATA` (의 값은 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 열거형)입니다.  
  
 `tokClass` 값은 형식을 고유 하 게 식별 하는 메타 데이터 토큰입니다. 메타 데이터 토큰 ID의 상위 비트를 해석 하는 방법에 대 한 자세한 내용은 참조는 `CorTokenType` 열거형에서 corhdr.h 파일에는 [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)