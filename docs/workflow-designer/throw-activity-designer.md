---
title: Throw 활동 디자이너-워크플로 디자이너
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Throw.UI
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71cf547a1ea3599de8926e40ca5a43f3bdea0f71
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758323"
---
# <a name="throw-activity-designer"></a>Throw 활동 디자이너

합니다 **Throw** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.Throw> 활동입니다.

## <a name="the-throw-activity"></a>Throw 활동

<xref:System.Activities.Statements.Throw> 활동은 예외를 throw합니다.

### <a name="using-the-throw-activity-designer"></a>Throw 활동 디자이너 사용

액세스는 **Throw** 활동 디자이너를 **오류 처리** 범주의 합니다 **도구 상자**.

**Throw** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 작업은 일반적으로, 등 배치 위치는 워크플로 디자이너 화면에 끌어 놓 및를 <xref:System.Activities.Statements.Sequence>합니다. 이렇게를 <xref:System.Activities.Statements.Throw> 기본값을 사용 하 여 활동 **DisplayName** Throw입니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **Throw** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자. <xref:System.Activities.Statements.Throw.Exception%2A> 속성은 속성 표에서 편집해야 합니다.

### <a name="the-throw-properties"></a>Throw 속성

다음 표에서는 <xref:System.Activities.Statements.Throw> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|용도|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Throw> 활동의 선택적 이름을 지정합니다. 기본값은 Throw입니다.|
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|throw할 예외입니다. 이 예외는 <xref:System.Exception>에서 파생되어야 합니다. 이 예외를 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|

## <a name="see-also"></a>참고자료

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [다시 throw](../workflow-designer/rethrow-activity-designer.md)
- [Throw 활동 디자이너](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)