---
title: Rethrow 활동 디자이너-워크플로 디자이너
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 24c13b629047b73b3f3ee15f2fc25a0120a2c177
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755257"
---
# <a name="rethrow-activity-designer"></a>Rethrow 활동 디자이너

**Rethrow** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.Rethrow> 활동입니다.

## <a name="the-rethrow-activity"></a>Rethrow 활동

<xref:System.Activities.Statements.Rethrow> 활동은 이전에 throw된 예외를 throw합니다. 이 활동은 <xref:System.Activities.Statements.Catch> 활동의 <xref:System.Activities.Statements.TryCatch> 처리기에서만 사용할 수 있습니다.

### <a name="use-the-rethrow-activity-designer"></a>ReThrow 활동 디자이너 사용

액세스는 **다시 Throw** 에서 활동 디자이너를 **오류 처리** 범주의 합니다 **도구 상자**합니다. **다시 Throw** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 작업은 일반적으로, 등 배치 위치는 워크플로 디자이너 화면에 끌어 놓 및는 <xref:System.Activities.Statements.Sequence>. Activity designer 만들어집니다를 <xref:System.Activities.Statements.Rethrow> 기본값을 사용 하 여 활동 **DisplayName** 인 Throw 합니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **다시 Throw** 활동 디자이너 또는 **DisplayName** 속성 그리드의 상자입니다.

### <a name="the-rethrow-properties"></a>Rethrow 속성

다음 표는 <xref:System.Activities.Statements.Rethrow> 속성을 디자이너에서 사용 하는 방법을 설명 합니다.

|속성 이름|필수|용도|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Rethrow> 활동의 선택적 이름을 지정합니다. 기본값은 Rethrow입니다.|

## <a name="see-also"></a>참고자료

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)