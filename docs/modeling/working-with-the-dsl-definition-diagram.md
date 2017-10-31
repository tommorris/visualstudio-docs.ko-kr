---
title: "DSL 정의 다이어그램 작업 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.diagram"
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "도메인별 언어 도구, Bring Tree Here"
  - "도메인별 언어 도구, 다이어그램"
  - "도메인별 언어 도구, Show As Class"
  - "도메인별 언어 도구, Show Map Lines"
  - "도메인별 언어 도구, Split Tree"
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# DSL 정의 다이어그램 작업
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 정의의 다이어그램은 DSL을 정의하는 중요한 도구입니다.  도메인 모델에 요소를 추가하고 다이어그램에 대해 관계를 정의할 수 있으며 보다 읽기 쉽도록 다이어그램의 레이아웃을 수정할 수 있습니다.  
  
## 다이어그램 레이아웃  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 정의 다이어그램에는 **클래스 및 관계** 파티션과 **다이어그램 요소** 파티션의 두 파티션이 있습니다.  **클래스 및 관계** 파티션에는 도메인 클래스, 도메인 관계 및 상속이 표시되고 **다이어그램 요소** 파티션에는 모양 클래스, 연결선 클래스, 스윔 레인 클래스 및 생성된 디자이너 다이어그램이 표시됩니다.  
  
 도메인 클래스는 **클래스 및 관계** 파티션의 여러 위치에 표시될 수 있습니다.  도메인 클래스 정의는 다른 도메인 클래스의 기본 클래스인 경우 상속 트리를 표시하고 포함\/참조 관계의 소스인 경우에는 관계 트리를 표시합니다.  포함 또는 참조 관계의 대상으로는 도메인 클래스 자리 표시자가 표시됩니다.  기본적으로 자리 표시자 요소는 **도메인 속성** 구획이 축소된 상태로 표시되며  상속 또는 포함\/참조 관계는 표시하지 않습니다.  
  
 도메인 클래스를 추가하면 **클래스 및 관계** 파티션 아래쪽에 해당 클래스가 표시됩니다.  포함 또는 참조 관계를 추가하면 소스 도메인 클래스 오른쪽 아래에 관계가 그려집니다.  
  
 도메인 클래스와 관계를 추가할 때는 특정 도메인 클래스를 찾기가 어려울 수도 있습니다.  **DSL 탐색기**에서 도메인 클래스를 마우스 오른쪽 단추로 클릭하고 **다이어그램에서 찾기**를 클릭하여 도메인 클래스를 찾을 수 있습니다.  
  
 다음 섹션에서는 보다 쉽게 읽을 수 있도록 다이어그램의 모양을 변경하는 방법을 설명합니다.  
  
## 요소 복사  
 DSL 정의 다이어그램의 요소에 대해 복사, 잘라내기 및 붙여넣기를 사용할 수 있습니다.  
  
## 다이어그램 확대\/축소  
 **DSL Designer** 도구 모음을 사용해 확대\/축소 수준을 설정하여 다이어그램을 확대하거나 축소할 수 있습니다.  
  
## 지도 선 숨기기  
 지도 선은 도메인 클래스 또는 도메인 관계와 해당 클래스\/관계가 매핑되는 모양 또는 연결선 간에 그려지는 선입니다.  **DSL Designer** 도구 모음에서 **지도 선 표시** 단추를 클릭하여 지도 선을 숨길 수 있습니다.  선을 표시하려면 단추를 다시 클릭합니다.  
  
## 다이어그램 레이아웃 변경  
 다음과 같이 **클래스 및 관계** 파티션의 레이아웃을 변경할 수 있습니다.  
  
### 확장\/축소  
 도메인 클래스 또는 모양을 나타내는 구획 모양 요소를 마우스 오른쪽 단추로 클릭한 다음 **축소**를 클릭하여 해당 크기를 줄일 수 있습니다.  그러면 모양의 **도메인 속성** 구획이 숨겨집니다.  **도메인 속성** 구획을 다시 표시하려면 모양을 마우스 오른쪽 단추로 클릭하고 **확장**을 클릭합니다.  
  
### 위\/아래로 이동  
 도메인 클래스 또는 다이어그램 요소를 마우스 오른쪽 단추로 클릭하고 **위로 이동** 또는 **아래로 이동**을 클릭하여 해당 요소를 파티션에서 위나 아래로 이동할 수 있습니다.  포함 또는 참조 관계의 대상으로 표시된 자리 표시자 요소를 이동하면 관계도 함께 이동됩니다.  
  
### 관계 트리 확장\/축소  
 도메인 클래스가 다른 도메인 클래스와의 포함 또는 참조 관계에서 소스 역할을 하는 경우 도메인 클래스 정의를 마우스 오른쪽 단추로 클릭하고 **관계 트리 축소**를 클릭하여 관계를 숨길 수 있습니다.  관계를 표시하려면 정의 요소를 마우스 오른쪽 단추로 클릭하고 **관계 트리 확장**을 클릭합니다.  
  
### 상속 트리 확장\/축소  
 도메인 클래스가 다른 도메인 클래스의 기본 클래스인 경우 도메인 클래스 정의를 마우스 오른쪽 단추로 클릭하고 **상속 트리 축소**를 클릭하여 상속 트리를 숨길 수 있습니다.  상속 트리를 표시하려면 정의 요소를 마우스 오른쪽 단추로 클릭하고 **상속 트리 확장**을 클릭합니다.  
  
### 여기로 트리 가져오기  
 자리 표시자 도메인 클래스를 마우스 오른쪽 단추로 클릭하고 **여기로 트리 가져오기**를 클릭하여 다이어그램을 통합할 수 있습니다.  그러면 자리 표시자 도메인 클래스가 정의 요소가 되고 상속 및 관계 트리가 표시됩니다.  이전 정의 요소는 관계의 대상이거나 상속 관계의 자식인 경우 자리 표시자 요소가 되고 그렇지 않으면 사라집니다.  
  
### 트리 분할  
 상속 또는 관계 트리가 표시되는 도메인 클래스 정의를 마우스 오른쪽 단추로 클릭하고 **트리 분할**을 클릭하여 해당 트리를 분할할 수 있습니다.  그러면 정의 요소가 자리 표시자 요소가 되고 정의 도메인 클래스는 상속 및 관계 트리와 함께 파티션 아래쪽에 표시됩니다.  
  
### 클래스로 표시  
 도메인 관계에서 관계가 파생되었거나 해당 관계와 다른 도메인 관계 간에 포함\/참조 관계가 설정되어 있으면 관계를 마우스 오른쪽 단추로 클릭하고 **클래스로 표시**를 클릭하여 관계를 클래스로 표시할 수 있습니다.  관계는 **도메인 속성** 구획과 함께 표시되며 상속 및 관계 트리를 보여줍니다.  
  
## 참고 항목  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/ko-kr/ca5e84cb-a315-465c-be24-76aa3df276aa)