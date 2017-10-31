---
title: "메시지 표식 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.markers.message
ms.assetid: 721f40ca-5af2-4a01-b8b6-2b90f6cb7f89
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 0fa95a9a7ff262f03608d5b076a45220d2b56fec
ms.contentlocale: ko-kr
ms.lasthandoff: 05/13/2017

---
# <a name="message-markers"></a>메시지 표식
메시지 표식은 로그 출력을 나타냅니다. 메시지는 특정 시간에 특정 스레드에서 생성되는 문자열입니다. 다른 도구에 사용할 수 있도록 메시지를 텍스트 파일로 내보낼 수 있습니다. 동시성 시각화 도우미에서 메시지에 포인터를 두면 메시지 문자열을 볼 수 있습니다. 또한 [표식 보고서](../profiling/markers-report.md)에서 모든 메시지 표식을 볼 수 있습니다.  다음 그림은 메시지 표식을 보여줍니다.  
  
## <a name="message-aggregation-markers"></a>메시지 집계 표식  
 일부 경우에는 동시성 시각화 도우미에서 여러 메시지가 서로 너무 가깝게 표시되어 개별적으로 그리지 못할 수 있습니다. 이 경우에는 기본 메시지를 나타내는 *메시지 집계 표식*이 표시됩니다. 이러한 아이콘 중 하나에 포인터를 놓으면 안에 있는 메시지 수가 도구 설명에 표시됩니다. 메시지를 보려면 확대합니다.  끝까지 확대해도 집계 표식이 나타나면 [표식 보고서](../profiling/markers-report.md)에서 기본 메시지를 볼 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [동시성 시각화 도우미 표식](../profiling/concurrency-visualizer-markers.md)   
 [동시성 시각화 도우미 SDK](../profiling/concurrency-visualizer-sdk.md)