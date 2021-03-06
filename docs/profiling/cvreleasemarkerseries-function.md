---
title: CvReleaseMarkerSeries 함수 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27c5bbc5d47972a4829c4e46f6aafdcf8ee76fad
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749361"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries 함수
표식 계열을 해제합니다. 해제한 후에 표식 계열 개체를 사용하지 마세요. 해당 개체를 사용하는 경우 응용 프로그램 작동이 중단될 수 있습니다. 표식 계열을 해제하지 못하면 메모리 누수가 발생합니다.  
  
## <a name="syntax"></a>구문  
  
```C  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pMarkerSeries`  
 공급자 개체 변수의 주소입니다. 주소는 NULL일 수 없으며, 변수는 임의의 값을 포함할 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 표식 계열이 성공적으로 해제된 경우 S_OK이고, 오류가 발생한 경우 오류 코드입니다. SUCCEEDED/FAILED 매크로를 사용하여 오류 조건을 확인할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** *cvmarkers.h*  
  
## <a name="see-also"></a>참고 항목  
 [C++ 라이브러리 참조](../profiling/cpp-library-reference.md)