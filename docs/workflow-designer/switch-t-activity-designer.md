---
title: "Switch&lt;T&gt; 활동 디자이너 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.ModelItemKeyValuePair.UI"
  - "System.Activities.Statements.Switch`1.UI"
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Switch&lt;T&gt; 활동 디자이너
<xref:System.Activities.Statements.Switch%601> 활동은 지정된 식을 계산하고 연관된 키가 계산에서 얻은 값과 일치하는 활동 컬렉션의 활동을 실행합니다.  
  
 **Switch\<T\>** 활동 디자이너는 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]에서 <xref:System.Activities.Statements.TryCatch> 활동을 만들고 구성하는 데 사용됩니다.  
  
## Switch\<T\>활동  
 <xref:System.Activities.Statements.Switch%601> 활동에는 <xref:System.Activities.Statements.Switch%601.Expression%2A> 및 <xref:System.Activities.Statements.Switch%601.Cases%2A> 사전이 포함되어 있습니다.사전의 각 case는 *key*와 그 *value* 역할을 하는 활동의 쌍으로 구성됩니다.<xref:System.Activities.Statements.Switch%601> 활동은 <xref:System.Activities.Statements.Switch%601.Expression%2A>을 계산한 후 각 키와 비교하고,일치하는 항목이 있으면 해당 활동을 실행합니다.사전 키는 사전의 같음 비교자로 정의된 같음 형식에 따라 고유해야 하므로 일치하는 항목은 하나만 존재할 수 있습니다.일치하는 항목이 없으면 <xref:System.Activities.Statements.Switch%601.Default%2A> 활동이 실행됩니다.  
  
## Switch\<T\> 활동 디자이너를 사용하는 방법  
 **Switch\<T\>** 활동 디자이너는 **도구 상자**의 **제어 흐름** 범주에 있습니다. 이 범주에 액세스하려면 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]의 **도구 상자** 탭을 클릭하거나, **보기** 메뉴에서 **도구 모음**을 선택하거나, Ctrl\+Alt\+X를 누릅니다. 활동 디자이너를 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]로 끌어 놓으면 **형식 선택** 대화 상자가 표시되어 사용자가 <xref:System.Activities.Statements.Switch%601> 활동에 사용된 제네릭 형식 *T*를 지정할 수 있습니다.기본값은 **Int32**입니다.제네릭 형식 *T*를 선택하면 **Switch\<T\>** 디자이너가 Workflow Designer에 추가됩니다.  
  
 다음은 **Switch\<T\>** 디자이너의 속성입니다.이러한 모든 속성을 속성 표에서 편집할 수 있습니다.일부 속성은 디자이너 화면에서도 편집할 수 있습니다.  
  
 다음 표에서는 가장 유용한 <xref:System.Activities.Statements.Switch%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.  
  
|속성 이름|필수|사용법|  
|-----------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Switch%601> 활동 디자이너의 이름을 지정합니다.기본값은 Switch\<Int32\>입니다.값은 **속성** 창에서 편집하거나 디자이너 머리글에서 직접 편집할 수 있습니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|실행할 case를 결정하기 위해 case 컬렉션의 키와 비교하는 데 사용할 식을 지정합니다.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||일치하는 항목이 없는 경우에 실행할 활동을 지정합니다.디자이너에서 **활동 추가** 단추를 클릭하여 **기본값** 상자를 열고 활동을 끌어 놓습니다.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||계산할 case를 지정합니다.case를 추가하려면 **Switch\<T\>** 디자이너 아래쪽에 있는 **새 case 추가** 단추를 클릭합니다.단추가 텍스트 상자\(Switch\<T\>를 추가할 때 String 또는 Enum 제네릭 형식을 선택한 경우 콤보 상자\)로 바뀝니다.**Case 값** 상자에 키를 추가하면 case 영역이 확장되고 "여기에 작업 놓기"라는 힌트 텍스트가 있는 곳으로 활동을 끌어서 해당 case의 실행 논리를 정의할 수 있습니다.|  
  
 case 키가 중복되지 않는 한 여러 case를 추가할 수 있습니다.키가 중복되는 경우 지정한 case 키가 이미 있으며 다른 키를 선택해야 한다는 메시지가 표시된 오류 대화 상자가 나타납니다.**Switch\<T\>** 디자이너의 확장된 보기에는 한 번에 한 case 영역만 표시할 수 있습니다.case 영역이 축소된 보기로 되어 있는 경우 case 영역을 클릭하면 보기가 확장됩니다.축소된 case는 디자이너에서 case 내 활동의 표시 이름\(있는 경우\)이 case 오른쪽에 표시됩니다.또는 **활동 추가** 단추가 표시되고 이를 클릭하면 case가 확장되어 활동을 추가할 수 있습니다.  
  
 기존 case의 키를 클릭하면 키 레이블이 텍스트 상자로 바뀌어 case 키를 편집할 수 있게 됩니다.  
  
 case를 삭제하는 방법은 두 가지입니다.  
  
1.  case를 선택하여 삭제합니다.  
  
2.  case를 선택하고 마우스 오른쪽 단추를 클릭하여 상황에 맞는 메뉴를 표시한 다음 **삭제**를 선택합니다.  
  
 삭제하려면 case 자체를 선택해야 합니다.case 내의 활동을 선택하여 삭제하는 경우 case가 아닌 활동만 삭제됩니다.  
  
## 참고 항목  
 [제어 흐름](../workflow-designer/control-flow-activity-designers.md)