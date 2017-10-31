---
title: "질감 및 이미지 작업 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
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
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 2cb4836ae868d56147a82fcefa0c5546bfcf8cad
ms.contentlocale: ko-kr
ms.lasthandoff: 04/05/2017

---
# <a name="working-with-textures-and-images"></a>질감 및 이미지 작업
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 이미지 편집기를 사용하여 질감 및 이미지를 만들고 수정할 수 있습니다. 이미지 편집기는 DirectX 앱 개발에 사용되는 질감 및 이미지와 같은 풍부한 질감 및 이미지 형식을 지원합니다.  
  
> [!NOTE]
>  이미지 편집기는 아이콘이나 커서 같은 로우 컬러 이미지를 지원하지 않습니다. 이런 종류의 이미지를 만들거나 수정하려면 [아이콘에 대한 이미지 편집기](/cpp/windows/image-editor-for-icons)를 사용합니다.  
  
## <a name="textures-and-images"></a>질감 및 이미지  
 기본적인 수준의, 질감 및 이미지는 그래픽 앱에서 시각적인 세부 정보를 제공하는 데 사용되는 데이터 테이블입니다. 질감이나 이미지가 제공하는 세부 정보의 종류는 사용되는 방식에 따라 다르지만, 색상 샘플, 알파(투명도) 값, 표면 법선 및 높이 값이 일반적인 예입니다. 질감과 이미지의 주요 차이는 질감은 개체나 장면 전체를 나타내기 위한 모양의 표현(일반적으로 3D 모델)에 사용되는 반면, 이미지는 일반적으로 개체나 장면에 대한 독립적인 표현입니다.  
  
 질감의 일반적인 종류는 다음과 같습니다.  
  
 질감 맵  
 질감 맵은 1, 2 또는 3차원 행렬로 구성되는 색상값을 포함합니다. 영향을 받는 개체의 색 세부 정보를 제공하는 데 사용됩니다. 색상은 주로 RGB(빨강, 초록, 파랑) 색 채널을 사용하여 인코딩되며, 투명도를 나타내는 네 번째 채널 즉, 알파를 포함할 수 있습니다. 드물지만, 색상은 다른 색 구성표로 인코딩되거나 네 번째 채널에 알파가 아닌 데이터(예: 높이)가 포함될 수 있습니다.  
  
 법선 맵  
 법선 맵은 표면 법선을 포함합니다. 영향을 받는 개체의 조명 세부 정보를 제공하는 데 사용됩니다. 법선은 주로 빨강, 초록, 파랑 색의 구성 요소를 사용하여 인코딩되며, 벡터의 x, y 및 z 차원을 저장합니다. 하지만, 다른 인코딩(예: 극좌표를 기반으로 하는 인코딩)도 존재합니다.  
  
 높이 맵  
 높이 맵은 높이 필드 데이터를 포함합니다. 영향을 받는 개체의 기하학적 세부 정보의 형태를 제공하기 위해(원하는 효과를 계산하는 셰이더 코드를 사용하여) 또는 지형 생성 같은 용도를 위한 데이터 요소를 제공하기 위해 사용됩니다. 높이 값은 주로 질감의 한 가지 채널을 사용하여 인코딩됩니다.  
  
 큐브 맵  
 큐브 맵은 다양한 유형의 데이터(예: 색상 또는 법선)를 포함할 수 있지만 큐브 면은 6가지 질감으로 구성됩니다. 이로 인해 큐브 맵은 질감 좌표를 제공하여 샘플링되지 않고 큐브 중앙이 원점인 벡터를 제공하여 샘플링됩니다. 샘플링은 벡터가 큐브와 교차하는 지점에서 수행됩니다. 큐브 맵은 리플렉션 계산에 사용될 수 있는 환경의 근사값을 제공하는 데 사용되거나( *환경 매핑*이라고 함), 구면 개체에 2차원 질감이 제공할 수 있는 기본적인 수준보다 왜곡이 적은 질감을 제공하기 위해 사용됩니다.  
  
 모든 질감은 질감에 포함된 데이터 유형 또는 질감의 차원수나 "모양"과 직교하는 여러 가지 방법으로 인코딩하고 압축할 수 있습니다. 하지만, 다양한 인코딩 및 압축 방법은 다양한 종류의 데이터에 더 좋은 결과를 가져옵니다.  
  
 이미지 편집기를 사용하여 다른 이미지 편집기와 비슷한 방식으로 질감과 이미지를 만들고 수정할 수 있습니다. 이미지 편집기는 3D 그래픽에 사용할 수 있는 MIP 매핑 및 그 밖의 기능을 제공하고, DirectX가 지원하는 다수의 고도로 압축된, 하드웨어 가속 질감 형식을 지원합니다.  
  
## <a name="related-topics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[이미지 편집기](../designers/image-editor.md)|이미지 편집기를 사용하여 질감과 이미지 작업을 수행하는 방법을 설명합니다.|  
|[이미지 편집기 예제](../designers/image-editor-examples.md)|일반적인 이미지 처리 작업을 수행하기 위해 이미지 편집기 사용 방법을 보여주는 항목에 대한 링크를 제공합니다.|