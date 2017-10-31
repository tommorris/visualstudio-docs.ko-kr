---
title: "방법: Direct2D 또는 Javascript 앱과 함께 사용하기 위해 질감 내보내기 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 77f610f9bf40cbd1ff840832203a78ccbaa3eeb2
ms.contentlocale: ko-kr
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>방법: Direct2D 또는 Javascript 앱과 함께 사용하기 위해 질감 내보내기
이미지 콘텐츠 파이프라인은 Direct2D의 내부 렌더링 규칙에 부합되는 질감을 생성할 수 있습니다. 이 종류의 질감은 Direct2D를 사용하는 앱 및 JavaScript를 통해 생성된 Windows 스토어 앱에서 사용하기에 적합합니다.  
  
 이 문서는 다음 활동을 보여 줍니다.  
  
-   이미지 콘텐츠 파이프라인에서 처리할 소스 이미지 구성.  
  
-   Direct2D 또는 JavaScript 앱에서 사용할 수 있는 질감을 생성하도록 이미지 콘텐츠 파이프라인 구성.  
  
    -   블록 압축 .dds 파일을 생성합니다.  
  
    -   미리 곱한 알파를 생성합니다.  
  
    -   MIP 맵 생성을 사용하지 않도록 설정합니다.  
  
## <a name="rendering-conventions-in-direct2d"></a>Direct2D의 렌더링 규칙  
 Direct2D의 컨텍스트에서 사용되는 질감은 이러한 Direct2D 내부 렌더링 규칙을 따릅니다.  
  
-   Direct2D는 미리 곱한 알파를 사용하여 투명도 및 반투명도를 구현합니다. 질감에 투명도 또는 반투명도를 사용하지 않는 경우에도 Direct2D에서 사용되는 질감은 미리 곱한 알파를 포함해야 합니다. 미리 곱한 알파에 대한 자세한 내용은 [방법: 미리 증가된 알파를 사용하는 질감 내보내기](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)를 참조하세요.  
  
-   다음 블록 압축 형식 중 하나를 사용하여 질감을 .dds 형식으로 제공해야 합니다.  
  
    -   BC1_UNORM 압축  
  
    -   BC2_UNORM 압축  
  
    -   BC3_UNORM 압축  
  
-   MIP 맵은 지원되지 않습니다.  
  
#### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Direct2D 렌더링 규칙에 부합되는 질감을 만들려면  
  
1.  기본 질감으로 시작합니다. 기존 이미지를 로드하거나 [방법: 기본 질감 만들기](../designers/how-to-create-a-basic-texture.md)의 설명대로 새 질감을 만듭니다. .dds 형식의 블록 압축을 지원하려면 너비 및 높이가 4의 배수인 크기(예: 100x100, 128x128 또는 256x192)의 질감을 지정합니다. MIP 매핑은 지원되지 않으므로 질감은 정사각형일 필요가 없고 크기가 2의 제곱일 필요가 없습니다.  
  
2.  이미지 콘텐츠 파이프라인에서 처리되도록 질감 파일을 구성합니다. **솔루션 탐색기**에서 방금 만든 질감 파일에 대한 바로 가기 메뉴를 열고 **속성**을 선택합니다. **구성 속성**, **일반** 페이지에서 **항목 종류** 속성을 **이미지 콘텐츠 파이프라인**으로 설정합니다. **콘텐츠** 속성이 **예**로 설정되고 **빌드에서 제외**가 **아니요**로 설정되어 있는지 확인하고 **적용** 단추를 선택합니다. **이미지 콘텐츠 파이프라인** 구성 속성 페이지가 표시됩니다.  
  
3.  출력 형식을 블록 압축 형식 중 하나로 설정합니다. **구성 속성**, **이미지 콘텐츠 파이프라인**, **일반** 페이지에서 **압축** 속성을 **BC3_UNORM 압축(/compress:BC3_UNORM)**으로 설정합니다. 요구 사항에 따라 기타 BC1, BC2 또는 BC3 형식 중에서 선택할 수 있습니다. Direct2D는 현재 BC4, BC5, BC6 또는 BC7 질감을 지원하지 않습니다. 다른 BC 형식에 대한 자세한 내용은 [Block Compression (Direct3D 10)](http://msdn.microsoft.com/library/windows/desktop/bb694531.aspx)(블록 압축(Direct3D 10))을 참조하세요.  
  
    > [!NOTE]
    >  지정된 압축 형식은 이미지 콘텐츠 파이프라인에서 생성되는 파일의 형식을 결정합니다. 이 형식은 이미지 편집기에 있는 소스 이미지의 **형식** 속성과 다릅니다. 이 속성은 디스크에 저장된 소스 이미지 파일의 형식(*작업 형식*)을 결정합니다. 일반적으로 압축된 작업 형식은 필요하지 않습니다.  
  
4.  미리 곱한 알파를 사용하는 출력을 생성하도록 이미지 콘텐츠 파이프라인을 구성합니다. **구성 속성**, **이미지 콘텐츠 파이프라인**, **일반** 페이지에서 **미리 곱한 알파 형식으로 변환** 속성을 **예(/generatepremultipliedalpha)**로 설정합니다.  
  
5.  MIP 맵을 생성하지 않도록 이미지 콘텐츠 파이프라인을 구성합니다. **구성 속성**, **이미지 콘텐츠 파이프라인**, **일반** 페이지에서 **Mip 생성** 속성을 **아니요**로 설정합니다.  
  
6.  **확인** 단추를 선택합니다.  
  
 프로젝트를 빌드할 때 이미지 콘텐츠 파이프라인은 소스 이미지를 작업 형식에서 지정한 출력 형식으로 변환하고(변환에는 미리 곱한 알파 생성이 포함됨) 결과는 프로젝트의 출력 디렉터리로 복사됩니다.