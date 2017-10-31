---
title: "TransactedReceiveScope 활동 디자이너 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# TransactedReceiveScope 활동 디자이너
**TransactedReceiveScope** 디자이너는 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동을 만들고 구성하는 데 사용됩니다.  
  
## TransactedReceiveScope 활동  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동을 통해 트랜잭션을 워크플로 또는 디스패처에 의해 만들어진 서버 트랜잭션으로 이동할 수 있습니다.  
  
### TransactedReceiveScope 활동 디자이너 사용  
 **TransactedReceiveScope** 활동 디자이너는 **도구 상자**의 **메시징** 범주에 있습니다. 이 범주에 액세스하려면 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]의 **도구 상자** 탭을 클릭하거나, **보기** 메뉴에서 **도구 모음**을 선택하거나, Ctrl\+Alt\+X를 누릅니다.  
  
 **TransactedReceiveScope** 활동 디자이너를 **도구 상자**에서 끌어다가 일반적으로 활동을 배치하는 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 화면의 아무 곳에나 놓을 수 있습니다.그러면 기본 **DisplayName**인 TransactedReceiveScope라는 이름의 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동이 만들어집니다.**TransactedReceiveScope** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 <xref:System.Activities.Activity.DisplayName%2A>을 편집할 수 있습니다.  
  
 **TransactedReceiveScope** 디자이너는 **요청** 및 **본문** 상자를 포함합니다.이 상자는 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> 속성을 구성하는 데 사용되고, 이 속성은 <xref:System.ServiceModel.Activities.Receive> 활동과 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 속성을 지정하며, 이 속성은 다시 몇 가지 다른 <xref:System.Activities.Activity>를 지정합니다.<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>는 트랜잭션을 만듭니다.그러면 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> 범위의 트랜잭션이 앰비언트 트랜잭션이 되어 이 범위의 모든 활동이 이 트랜잭션 내에서 실행됩니다.  
  
### TransactedReceiveScope 속성  
 다음 표에서는 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.이러한 <xref:System.Activities.Activity.DisplayName%2A> 속성은 속성 표 또는 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 화면에서 편집할 수 있지만 나머지 속성은 반드시 디자이너 화면에서 편집해야 합니다.  
  
|속성 이름|필수|사용법|  
|-----------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> 활동의 선택적 이름입니다.기본값은 TransactedReceiveScope입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> 이름이 꼭 필요하지 않더라도 표시 이름을 사용하는 것이 좋습니다.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|<xref:System.ServiceModel.Activities.Receive> 활동을 활동 디자이너 화면의 **요청** 블록에 놓습니다.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|<xref:System.Activities.Activity>를 활동 디자이너 화면의 **본문** 블록에 놓습니다.|  
  
## 참고 항목  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)