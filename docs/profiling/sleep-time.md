---
title: 중지 시간 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94b1695eb36aa8f55847c21a14d72357d51a405
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35669521"
---
# <a name="sleep-time"></a>중지 시간
타임라인의 이러한 세그먼트는 중지로 분류되는 차단 시간과 관련이 있습니다. 중지 범주는 스레드가 자발적으로 해당 논리 코어를 포기했고 아무 작업도 수행하지 않음을 의미입니다. 이 시간 동안 스레드는 동시성 시각화 도우미가 중지로 간주되는 API에서 차단되었습니다. `Sleep()` 및 `SwitchToThread()` 등의 API는 이 그룹에 속합니다.  
  
## <a name="see-also"></a>참고 항목  
 [스레드 뷰](../profiling/threads-view-parallel-performance.md)