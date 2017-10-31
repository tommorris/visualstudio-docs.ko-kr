---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 17
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
ms.openlocfilehash: c9441dc96ca5c090f246d4b27842afa6270e1ffb
ms.contentlocale: ko-kr
ms.lasthandoff: 09/26/2017

---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
이 메서드는 서버에 대 한 시스템 유틸리티를 가져옵니다.  
  
> [!NOTE]
>  이 메서드는 사용 되지 않습니다:를 사용 하지 마십시오 ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 항상 반환 `E_NOTIMPL` 이 메서드를 호출 하는 경우). 이유 때문에 보존 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppUtil`  
 [out] 반환 된 `IDebugMDMUtil2_V7` 컴퓨터 유틸리티 정보를 나타내는 인터페이스입니다.  
  
## <a name="return-value"></a>반환 값  
 항상 반환 `E_NOTIMPL`, 나타내는 메서드가 구현 되지 않았습니다.  
  
## <a name="remarks"></a>설명  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]항상 반환 `E_NOTIMPL` 이 메서드를 호출 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)