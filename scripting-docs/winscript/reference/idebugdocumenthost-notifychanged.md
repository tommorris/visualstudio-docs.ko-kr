---
title: IDebugDocumentHost::NotifyChanged | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.NotifyChanged
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::NotifyChanged
ms.assetid: 33a4a54f-3bcb-4422-b3c0-bdbf46590f34
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1890aeb64346994480a7e4ef452543107bd1544e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726263"
---
# <a name="idebugdocumenthostnotifychanged"></a>IDebugDocumentHost::NotifyChanged
문서의 원본 파일이 저장 된 및 해당 내용을 새로 고쳐야 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수가 없습니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 이 메서드는 문서의 원본 파일이 저장 된 및 해당 내용을 새로 고쳐야 호스트에 알립니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugDocumentHost 인터페이스](../../winscript/reference/idebugdocumenthost-interface.md)