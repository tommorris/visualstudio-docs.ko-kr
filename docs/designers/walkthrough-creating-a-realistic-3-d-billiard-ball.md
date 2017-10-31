---
title: "연습: 사실적인 3차원 당구공 만들기 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af8eb0f3-bf6a-4d1c-ab47-dcd88ab04efa
caps.latest.revision: 9
author: BrianPeek
ms.author: brpeek
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: e6ee75cded8cefe4f2e46c4e53edd0f050273a5d
ms.contentlocale: ko-kr
ms.lasthandoff: 05/13/2017

---
# <a name="walkthrough-creating-a-realistic-3-d-billiard-ball"></a>연습: 사실적인 3차원 당구공 만들기
이 연습에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 셰이더 디자이너 및 이미지 편집기를 사용하여 사실적인 3차원 당구공을 만드는 방법을 보여 줍니다. 당구공의 3차원 모양을 만들려면 여러 셰이더 기술을 적절한 질감 리소스와 결합합니다.  
  
 이 문서는 다음 활동을 보여 줍니다.  
  
-   도형 및 질감을 사용하여 당구공의 기본 모양 만들기.  
  
-   램버트 조명 모델을 사용하여 깊이 추가.  
  
-   반사 하이라이트를 사용하여 기본 모양 개선.  
  
-   환경을 반영하여 공간감 만들기.  
  
## <a name="prerequisites"></a>필수 조건  
 이 연습을 완료하려면 다음 구성 요소와 기술이 필요합니다.  
  
-   질감을 큐브 맵으로 어셈블하는 도구(예: June 2010 DirectX SDK에 포함된 DirectX Texture Tool).  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]의 이미지 편집기에 대한 지식.  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]의 셰이더 디자이너에 대한 지식.  
  
## <a name="creating-the-basic-appearance-with-shape-and-texture"></a>도형 및 질감을 사용하여 기본 모양 만들기  
 컴퓨터 그래픽에서 모양의 가장 기본적인 요소는 도형과 색입니다. 컴퓨터 시뮬레이션에서는 일반적으로 3차원 모델을 사용하여 사실적인 개체의 모양을 표현합니다. 색 세부 정보는 질감 맵을 통해 모델의 표면에 적용됩니다.  
  
 일반적으로 아티스트에게 사용할 수 있는 3차원 모델을 만들 것인지 물어야 하지만 당구공은 일반적인 도형(구)이므로 셰이더 디자이너에 적합한 모델이 기본 제공됩니다.  
  
 구는 셰이더 디자이너의 기본 미리 보기 도형입니다. 현재 다른 도형을 사용하여 셰이더를 미리 보는 경우 다시 구로 전환하세요.  
  
#### <a name="to-preview-the-shader-by-using-a-sphere"></a>구를 사용하여 셰이더를 미리 보려면  
  
-   셰이더 디자이너 도구 모음에서 **구로 미리 봅니다.**를 선택합니다.  
  
 다음 단계에서 모델에 질감을 적용하는 셰이더 프로그램을 만들지만, 먼저 사용할 수 있는 질감을 만들어야 합니다. 이 연습에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 포함된 이미지 편집기를 사용하여 질문을 만드는 방법을 보여 주지만, 질감을 적합한 형식으로 저장할 수 있는 모든 이미지 편집기를 사용할 수 있습니다.  
  
 **속성** 창과 **도구 상자**가 표시되는지 확인하세요.  
  
#### <a name="to-create-a-billiard-ball-texture-by-using-the-image-editor"></a>이미지 편집기를 사용하여 당구공 질감을 만들려면  
  
1.  사용할 질감을 만듭니다. 질감을 프로젝트에 추가하는 방법에 대한 내용은 [이미지 편집기](../designers/image-editor.md)의 시작 섹션을 참조하세요.  
  
2.  너비가 높이의 두 배가 되도록 이미지 크기를 설정합니다. 질감이 당구공의 구 표면에 매핑되므로 이 작업이 필요합니다. 이미지 크기를 조정하려면 **속성** 창에서 **너비** 및 **높이** 속성에 대한 새 값을 지정합니다. 예를 들어 너비를 512로 설정하고 높이를 256으로 설정합니다.  
  
3.  질감이 구에 매핑되는 방식을 주의해서 당구공의 질감을 그립니다.  
  
     질감은 다음과 같이 표시됩니다.  
  
     ![당구공 질감](~/designers/media/gfx_shader_demo_billiard_art_ball_texture.png "gfx_shader_demo_billiard_art_ball_texture")  
  
4.  필요한 경우 이 질감의 저장소 요구 사항을 줄여야 할 수 있습니다. 질감의 너비를 높이에 맞게 줄이면 됩니다. 그러면 너비에 따라 질감이 압축되지만 질감이 구에 매핑된 방식으로 인해 당구공이 렌더링될 때 질감이 확장됩니다. 크기를 조정한 후 질감은 다음과 같이 표시됩니다.  
  
     ![사각형으로 압축된 당구공 질감](~/designers/media/gfx_shader_demo_billiard_art_ball_texture_square.png "gfx_shader_demo_billiard_art_ball_texture_square")  
  
 이제 이 질감을 모델에 적용하는 셰이더를 만들 수 있습니다.  
  
#### <a name="to-create-a-basic-texture-shader"></a>기본 질감 셰이더를 만들려면  
  
1.  사용할 DGSL 셰이더를 만듭니다. DGSL 셰이더를 프로젝트에 추가하는 방법에 대한 내용은 [셰이더 디자이너](../designers/shader-designer.md)의 시작 섹션을 참조하세요.  
  
     기본적으로 셰이더 그래프는 다음과 같이 표시됩니다.  
  
     ![기본 셰이더 그래프](../designers/media/gfx_shader_demo_billiard_step_0.png "gfx_shader_demo_billiard_step_0")  
  
2.  질감 샘플 값을 현재 픽셀에 적용하도록 기본 셰이더를 수정합니다. 셰이더 그래프는 다음과 같이 표시됩니다.  
  
     ![질감을 개체에 적용한 셰이더 그래프](../designers/media/gfx_shader_demo_billiard_step_1.png "gfx_shader_demo_billiard_step_1")  
  
3.  질감 속성을 구성하여 이전 절차에서 만든 질감을 적용합니다. **질감 샘플** 노드의 **질감** 속성 값을 **Texture1**로 설정하고 같은 속성 창에서 **Texture1** 속성 그룹의 **파일 이름** 속성을 사용하여 질감 파일을 지정합니다.  
  
 셰이더에서 질감을 적용하는 방법에 대한 자세한 내용은 [방법: 기본 질감 셰이더 만들기](../designers/how-to-create-a-basic-texture-shader.md)를 참조하세요.  
  
 이제 당구공이 다음과 같이 표시됩니다.  
  
 ![질감이 있는 당구공 클로즈업](~/designers/media/gfx_shader_demo_.png "gfx_shader_demo_")  
  
## <a name="creating-depth-with-the-lambert-lighting-model"></a>램버트 조명 모델을 사용하여 깊이 만들기  
 지금까지 쉽게 인식할 수 있는 당구공을 만들었습니다. 그러나 이 당구공은 실제 당구공의 사실적인 모사라기보다는 만화같이 평면적이고 잘 눈에 띄지 않습니다. 평면적으로 보이는 이유는 셰이더가 당구공 표면의 각 픽셀이 같은 양의 빛을 받는 것처럼 동작하는 너무 단순한 셰이더이기 때문입니다.  
  
 실제 환경에서 빛은 광원을 직접 접하는 표면에서 가장 밝게 나타나고 광원의 사각 지대에 있는 표면에서는 가장 어둡게 나타납니다. 그 이유는 표면이 광원을 직접 접할 때 광선의 에너지가 가장 작은 표면 영역에서 분산되기 때문입니다. 표면이 광원에서 멀어질수록 같은 양의 에너지가 점점 더 큰 표면 영역에 분산됩니다. 광원을 외면하는 표면은 빛 에너지를 전혀 받지 않으므로 완전히 어두운 모양이 생성됩니다. 개체 표면에 적용되는 이런 밝기 차이는 개체의 모양을 나타나는 데 도움이 되는 중요한 시각적 단서입니다. 이 밝기 차이가 없으면 개체가 평면적으로 보이게 됩니다.  
  
 컴퓨터 그래픽에서 *조명 모델*(복잡하고 사실적인 조명 상호 작용의 간소화된 근사치)은 사실적인 조명의 모양을 복제하는 데 사용됩니다. 램버트 조명 모델은 앞 문단에서 설명한 대로 개체 표면에 확산 반사되는 빛의 양을 다르게 적용합니다. 램버트 조명 모델을 셰이더에 추가하여 당구공을 더 사실적인 3차원 모양으로 표현할 수 있습니다.  
  
#### <a name="to-add-lambert-lighting-to-your-shader"></a>셰이더에 램버트 조명을 추가하려면  
  
-   램버트 조명 값으로 질감 샘플 값을 조정하도록 셰이더를 수정합니다. 셰이더 그래프는 다음과 같이 표시됩니다.  
  
     ![램버트 조명이 추가된 셰이더 그래프](../designers/media/gfx_shader_demo_billiard_step_2.png "gfx_shader_demo_billiard_step_2")  
  
-   선택적으로 셰이더 그래프의 **MaterialDiffuse** 속성을 구성하여 조명 동작 방식을 조정할 수 있습니다. 셰이더 그래프의 속성에 액세스하려면 디자인 화면의 빈 영역을 선택하고 **속성** 창에서 액세스할 속성을 찾습니다.  
  
 셰이더에서 램버트 조명을 적용하는 방법에 대한 자세한 내용은 [방법: 기본 램버트 셰이더 만들기](../designers/how-to-create-a-basic-lambert-shader.md)를 참조하세요.  
  
 램버트 조명이 적용되면 당구공이 다음과 같이 표시됩니다.  
  
 ![질감이 있고 빛나는 당구공 클로즈업](~/designers/media/gfx_shader_demo_billiard_ball_2.png "gfx_shader_demo_billiard_ball_2")  
  
## <a name="enhancing-the-basic-appearance-with-specular-highlights"></a>반사 하이라이트를 사용하여 기본 모양 개선  
 램버트 조명 모델은 질감 전용 셰이더에 없는 모양 및 차원 감각을 제공합니다. 하지만 당구공의 모양이 약간 흐릿합니다.  
  
 실물 당구공은 보통 광택이 나는 마감재를 적용해서 당구공으로 떨어지는 빛의 일부를 반사합니다. 이 반사광의 일부가 반사 하이라이트를 생성하여, 공 표면의 반사 속성을 시뮬레이트합니다. 마감재의 속성에 따라 하이라이트가 국소적이거나 넓어지거나, 진하거나 옅어질 수 있습니다. 이러한 거울 반사는 광원, 표면 방향 및 카메라 위치 간 관계를 사용하여 모델링됩니다. 즉, 하이라이트는 표면 방향이 카메라에 직접 광원을 반사할 경우 가장 진하고 반사가 덜 직접적일 경우 덜 진합니다.  
  
 퐁 조명 모델은 램버트 조명 모델을 기반으로 빌드되고 이전 단락의 설명대로 반사 하이라이트를 포함합니다. 퐁 조명 모델을 셰이더에 추가하여 당구공을 더 눈에 띄는 모양으로 표현되는 시뮬레이트된 마감으로 표현할 수 있습니다.  
  
#### <a name="to-add-specular-highlights-to-your-shader"></a>셰이더에 반사 하이라이트를 추가하려면  
  
1.  추가 혼합을 사용하여 반사 기여도를 포함하도록 셰이더를 수정합니다. 셰이더 그래프는 다음과 같이 표시됩니다.  
  
     ![반사광이 추가된 셰이더 그래프](../designers/media/gfx_shader_demo_billiard_step_3.png "gfx_shader_demo_billiard_step_3")  
  
2.  필요한 경우 셰이더 그래프의 반사 속성(**MaterialSpecular** 및 **MaterialSpecularPower**)을 구성하여 반사 하이라이트 동작 방식을 조정할 수 있습니다. 셰이더 그래프의 속성에 액세스하려면 디자인 화면의 빈 영역을 선택하고 **속성** 창에서 액세스할 속성을 찾습니다.  
  
 셰이더에서 반사광을 적용하는 방법에 대한 자세한 내용은 [방법: 기본 퐁 셰이더 만들기](../designers/how-to-create-a-basic-phong-shader.md)를 참조하세요.  
  
 반사광이 적용되면 당구공이 다음과 같이 표시됩니다.  
  
 ![반사광이 추가된 당구공 클로즈업](~/designers/media/gfx_shader_demo_billiard_ball_3.png "gfx_shader_demo_billiard_ball_3")  
  
## <a name="creating-a-sense-of-space-by-reflecting-the-environment"></a>환경을 반영하여 공간감 만들기  
 반사광이 적용되면 당구공이 약간 사실적으로 보입니다. 올바른 모양, 올바른 그리기 작업 및 올바른 마감을 얻었습니다. 하지만 당구공이 더욱 사실적으로 보이도록 만드는 기술이 하나 더 있습니다.  
  
 실제 당구공을 가까이 살펴보면 윤이 나는 표면이 반사광을 드러낼 뿐 아니라 희미하게 주위 환경의 이미지를 반사하는 것을 확인할 수 있습니다. 환경 이미지를 질감으로 사용하고 이미지를 모델 자체 질감과 결합하여 각 픽셀의 최종 색을 결정하는 방식으로 이 반사를 시뮬레이트할 수 있습니다. 원하는 마감 종류에 따라 나머지 셰이더와 반사 질감의 결합 정도를 조절할 수 있습니다. 예를 들어 거울과 같은 고반사 표면을 시뮬레이트하는 셰이더는 반사 질감만 사용할 수 있지만, 당구공에 있는 반사와 같이 더 희미한 반사를 시뮬레이트하는 셰이더는 반사 질감 값의 작은 부분만 나머지 셰이더 계산과 결합할 수 있습니다.  
  
 물론 모델의 질감 맵을 적용하는 것과 같은 방식으로 반사 이미지를 모델에 적용할 수는 없습니다. 이렇게 하면 반사가 당구공에 붙은 것처럼 환경의 반사가 당구공과 함께 이동합니다. 반사는 모든 방향에서 생길 수 있으므로 모든 각도에 대한 반사 맵 값을 제공하는 방법과 반사 맵을 환경에 따라 방향이 지정되도록 유지하는 방법이 필요합니다. 이러한 요구 사항을 충족하기 위해 큐브의 면을 형성하도록 배열된 6개의 질감을 제공하는 *큐브 맵*이라는 특별한 종류의 질감 맵을 사용할 수 있습니다. 이 큐브 내부에서 모든 방향을 향하여 질감 값을 찾을 수 있습니다. 각 큐브 면의 질감에 환경 이미지가 포함된 경우 큐브 표면에서 올바른 위치를 샘플링하여 반사를 시뮬레이트할 수 있습니다. 큐브를 환경에 맞춰지도록 유지하면 환경의 정확한 반사를 얻게 됩니다. 큐브를 샘플링해야 하는 위치를 결정하려면 개체 표면부터 카메라 벡터의 반사를 계산하고 이 반사를 3차원 질감 좌표로 사용하면 됩니다. 큐브 맵을 이 방법으로 사용하는 것은 *환경 매핑*으로 알려진 일반적인 기술입니다.  
  
 환경 매핑은 이전 단락에 설명된 대로 실제 반사의 효율적인 근사치를 제공합니다. 환경에 매핑된 반사를 셰이더에 혼합하여 당구공이 화면에서 더 사실적으로 보이도록 당구공을 시뮬레이트된 마감으로 표현할 수 있습니다.  
  
 첫 번째 단계에서는 큐브 맵 질감을 만듭니다. 다양한 종류의 앱에서 특히 반사가 희미하거나 화면에서 눈에 띄는 공간을 차지하지 않는 경우 큐브 맵 콘텐츠의 효과가 완벽하게 나타날 필요는 없습니다. 예를 들어 많은 게임에서는 반사가 정확하지 않더라도 환경 매핑에 미리 계산된 큐브 맵을 사용하고 각 반사 개체에 가장 가까운 큐브 맵을 사용합니다. 오히려 대충의 근사치가 사실적인 효과에 적합한 경우가 많습니다.  
  
#### <a name="to-create-textures-for-an-environment-map-by-using-the-image-editor"></a>이미지 편집기를 사용하여 환경 맵의 질감을 만들려면  
  
1.  사용할 질감을 만듭니다. 질감을 프로젝트에 추가하는 방법에 대한 내용은 [이미지 편집기](../designers/image-editor.md)의 시작 섹션을 참조하세요.  
  
2.  너비가 높이와 같고 제곱 크기가 되도록 이미지 크기를 설정합니다. 큐브 맵이 인덱싱되는 방법 때문에 이 작업이 필요합니다. 이미지 크기를 조정하려면 **속성** 창에서 **너비** 및 **높이** 속성에 대한 새 값을 지정합니다. 예를 들어 **너비** 및 **높이** 속성을 256으로 설정합니다.  
  
3.  단색으로 질감을 채웁니다. 이 질감은 당구대의 표면에 해당하는 큐브 맵의 아래쪽이 됩니다. 다음 질감에 사용한 색을 기억해 두세요.  
  
4.  첫 번째와 같은 크기로 두 번째 질감을 만듭니다. 이 질감은 당구대의 표면 및 측면과 당구대 주변 영역에 해당하는 큐브 맵의 4개 측면에서 반복됩니다. 아래쪽 질감과 같은 색을 사용하여 이 질감으로 당구대 표면을 그려야 합니다. 질감은 다음과 같이 표시됩니다.  
  
     ![큐브 맵 측면의 질감](~/designers/media/gfx_shader_demo_billiard_art_env_texture_side.png "gfx_shader_demo_billiard_art_env_texture_side")  
  
     반사 맵의 효과는 사진처럼 정확할 필요가 없습니다. 예를 들어 이 문서에서 이미지를 만드는 데 사용된 큐브 맵에는 6개가 아닌 4개 포켓만 포함됩니다.  
  
5.  다른 질감과 크기가 같은 세 번째 질감을 만듭니다. 이 질감은 당구대 위의 천장에 해당하는 큐브 맵의 상단이 됩니다. 이 반사 부분을 더 눈에 띄게 만들려면 위쪽 조명을 그려 이전 절차의 셰이더에 추가한 반사 하이라이트를 강화합니다. 질감은 다음과 같이 표시됩니다.  
  
     ![큐브 맵 위쪽의 질감](~/designers/media/gfx_shader_demo_billiard_art_env_texture_top2.png "gfx_shader_demo_billiard_art_env_texture_top2")  
  
 이제 큐브 맵 측면의 개별 질감을 만들었으므로 도구를 사용하여 단일 .dds 질감에 저장될 수 있는 큐브 맵으로 질감을 어셈블할 수 있습니다. 프로그램이 큐브 맵을 .dds 질감 형식으로 저장할 수 있다면 큐브 맵을 만드는 데 원하는 모든 프로그램을 사용할 수 있습니다. 이 연습에서는 June 2010 DirectX SDK에 포함된 DirectX Texture Tool을 사용하여 질감을 만드는 방법을 보여 줍니다.  
  
#### <a name="to-assemble-a-cube-map-by-using-the-directx-texture-tool"></a>DirectX Texture Tool을 사용하여 큐브 맵을 어셈블하려면  
  
1.  DirectX Texture Tool의 주 메뉴에서 **파일**, **New Texture**(새 질감)를 선택합니다. **New Texture**(새 질감) 대화 상자가 표시됩니다.  
  
2.  **Texture Type**(질감 형식) 그룹에서 **Cubemap Texture**(큐브 맵 질감)를 선택합니다.  
  
3.  **차원** 그룹에서 **너비** 및 **높이**에 올바른 값을 입력하고 **확인**을 선택합니다. 새 질감 문서가 나타납니다. 기본적으로 질감 문서에 표시된 첫 번째 질감은 **양의 X** 큐브 면에 해당합니다.  
  
4.  질감 큐브의 측면용으로 만든 질감을 큐브 면으로 로드합니다. 주 메뉴에서 **파일**, **Open Onto This Cubemap Face**(이 큐브 맵 면으로 열기)를 선택하고, 큐브 측면용으로 만든 질감을 선택하고, **열기**를 선택합니다.  
  
5.  **음의 X**, **양의 Z** 및 **음의 Z** 큐브 면에 대해 4단계를 반복합니다. 이 작업을 하려면 로드할 면을 표시해야 합니다. 다른 큐브 맵 면을 보려면 주 메뉴에서 **보기**, **Cube Map Face**(큐브 맵 면)를 선택하고 보려는 면을 선택합니다.  
  
6.  **양의 Y** 큐브 면의 경우 질감 큐브의 위쪽용으로 만든 질감을 로드합니다.  
  
7.  **음의 Y** 큐브 면의 경우 질감 큐브의 아래쪽용으로 만든 질감을 로드합니다.  
  
8.  질감을 저장합니다.  
  
 큐브 맵 레이아웃이 다음과 같다고 가정할 수 있습니다.  
  
 ![환경 큐브 맵의 레이아웃](~/designers/media/gfx_shader_demo_billiard_art_env_texture_top.png "gfx_shader_demo_billiard_art_env_texture_top")  
  
 위쪽의 이미지는 양의 Y(+Y) 큐브 면이고, 중간에, 왼쪽에서 오른쪽까지 이미지는 -X, +Z, +X 및 -Z 큐브 면이고, 아래쪽의 이미지는 -Y 큐브 면입니다.  
  
 이제 큐브 맵 샘플을 나머지 셰이더로 혼합하도록 셰이더를 수정할 수 있습니다.  
  
#### <a name="to-add-environment-mapping-to-your-shader"></a>셰이터에 환경 매핑을 추가하려면  
  
1.  추가 혼합을 사용하여 환경 매핑 기여도를 포함하도록 셰이더를 수정합니다. 셰이더 그래프는 다음과 같이 표시됩니다.  
  
     ![두 종류의 반사 셰이더 노드 클로즈업](../designers/media/gfx_shader_demo_billiard_step_4b.png "gfx_shader_demo_billiard_step_4b")  
  
     **곱셈-덧셈** 노드를 사용하여 셰이더 그래프를 단순화할 수 있습니다.  
  
     다음은 환경 매핑을 구현하는 셰이더 노드의 더 자세한 보기입니다.  
  
     ![환경 매핑이 추가된 셰이더 그래프](../designers/media/gfx_shader_demo_billiard_step_4a.png "gfx_shader_demo_billiard_step_4a")  
  
2.  큐브 맵의 질감 속성을 구성하여 이전 절차에서 만든 질감을 적용합니다. **Cubemap Sample**(큐브 맵 샘플) 노드의 **질감** 값을 **Texture2**로 설정하고, **Texture2** 속성 그룹의 **파일 이름** 속성을 사용하여 질감 파일을 지정합니다.  
  
3.  경우에 따라 **상수** 노드의 **출력** 속성을 구성하여 당구공의 반사도를 조정할 수 있습니다. 노드 속성에 액세스하려면 노드를 선택하고 **속성** 창에서 액세스할 속성을 찾습니다.  
  
 환경 매핑이 적용되면 당구공이 다음과 같이 표시됩니다.  
  
 ![환경에 매핑된 당구공의 클로즈업](~/designers/media/gfx_shader_demo_billiard_ball_4.png "gfx_shader_demo_billiard_ball_4")  
  
 이 마지막 이미지에서 추가한 효과가 어떻게 결합되어 매우 사실적인 당구공을 만드는지 알 수 있습니다. 도형, 질감 및 조명은 3차원 개체의 기본 모양을 만들고 반사 하이라이트 및 반사는 당구공을 더 눈에 띠고 환경의 일부처럼 보이게 만듭니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 셰이더 내보내기](../designers/how-to-export-a-shader.md)   
 [방법: 3D 모델에 셰이더 적용](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [셰이더 디자이너](../designers/shader-designer.md)   
 [이미지 편집기](../designers/image-editor.md)   
 [셰이더 디자이너 노드](../designers/shader-designer-nodes.md)