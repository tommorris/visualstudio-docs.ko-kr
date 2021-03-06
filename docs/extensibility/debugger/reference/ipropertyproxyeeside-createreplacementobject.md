---
title: IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56e5001d7abd498982361a51d0386db4b2624cf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135609"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
식 계산기 (EE)에 특정 데이터 개체의 복사본을 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dataIn`  
 [in] [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 개체를 복사할 데이터를 보유 합니다.  
  
 `dataOut`  
 [out] 새 반환 `IEEDataStorage` 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`, 그러지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드에 제공 되는 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 바이트 배열을 나타내는 개체입니다. 이 들어오는 데이터 개체 일반적으로 EE에서 구현 되지 않습니다. 그러나이 메서드에서 반환 된 개체는 항상 EE 구현 수 있도록 하는 EE에서 구현 된 `IEEDataStorage` 어떤 클래스가 필요한 경우에 인터페이스입니다.  
  
 데이터는 들어오는에서 제공 됨을 유의 `IEEDataStorage` 개체는 나가는의 동일한 데이터 이어야 `IEEDataStorage` 개체입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)