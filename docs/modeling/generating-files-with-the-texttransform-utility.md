---
title: "TextTransform 유틸리티를 사용 하 여 파일을 생성 합니다. | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 41
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7d54fba9b16b87122b78ec6157abdbf2a8aface1
ms.lasthandoff: 02/22/2017

---
# <a name="generating-files-with-the-texttransform-utility"></a>TextTransform 유틸리티 사용하여 파일 생성
TextTransform.exe는 텍스트 템플릿을 변환 하는 데 사용할 수 있는 명령줄 도구입니다. TextTransform.exe를 호출할 때 인수로 텍스트 템플릿 파일의 이름을 지정 합니다. TextTransform.exe는 텍스트 변환 엔진을 호출 하 고 텍스트 템플릿을 처리 합니다. TextTransform.exe은 일반적으로 스크립트에서 호출 됩니다. 그러나 되므로 하지 일반적으로 필요한 또는 Visual Studio에서 빌드 프로세스에서 텍스트 변환 작업을 수행할 수 있습니다.  
  
> [!NOTE]
>  빌드 프로세스의 일부로 텍스트 변환을 수행 하려는 경우에 MSBuild 텍스트 변환 작업을 사용 하는 것이 좋습니다. 자세한 내용은 참조 [는 빌드 프로세스에서 코드 생성](../modeling/code-generation-in-a-build-process.md)합니다. 않은 컴퓨터에서의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 가 설치 되어 응용 프로그램을 작성할 수도 있습니다 또는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 텍스트 템플릿을 변환할 수 있는 확장 합니다. 자세한 내용은 참조 [사용자 지정 호스트를 사용 하 여 텍스트 템플릿을 처리](../modeling/processing-text-templates-by-using-a-custom-host.md)합니다.  
  
 TextTransform.exe은 다음 디렉터리에 있습니다.  
  
 **\Program Files\Microsoft Shared\TextTemplating\11.0**  
  
## <a name="syntax"></a>구문  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>매개 변수  
  
|**인수**|**설명**|  
|------------------|---------------------|  
|`templateName`|변환 하려는 경우 템플릿 파일의 이름을 식별 합니다.|  
  
|**옵션**|**설명**|  
|----------------|---------------------|  
|**-out** \<파일 이름 >|변환의 출력을 쓸 파일입니다.|  
|**-r** \<어셈블리 >|컴파일 및 텍스트 템플릿을 실행에 사용 되는 어셈블리입니다.|  
|**-u** \<네임 스페이스 >|서식 파일을 컴파일하는 데 사용 되는 네임 스페이스입니다.|  
|**-I** \<includedirectory >|지정된 된 텍스트 템플릿을 포함 된 텍스트 템플릿을 포함 하는 디렉터리입니다.|  
|**-P** \<참조 경로 >|텍스트 템플릿 내에 지정 된 어셈블리 또는 사용 하 여 검색 하려면 디렉터리는 **-r** 옵션입니다.<br /><br /> 예를 들어 Visual Studio API에 대 한 사용 되는 어셈블리를 포함 하려면 사용<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName >!\< 응용 프로그램 이름 >! \<assemblyName | 코드 베이스 >|이름, 전체 형식 이름 및 텍스트 템플릿 내에서 사용자 지정 지시문을 처리 하는 데 사용할 수 있는 지시문 프로세서의 어셈블리입니다.|  
|**-a** [processorName]! [ directiveName]! \<parameterName >! \<parameterValue >|지시문 프로세서에 대 한 매개 변수 값을 지정 합니다. 매개 변수 이름 및 값을 지정 하면 매개 변수가 모든 지시문 프로세서에 제공 됩니다. 지시문 프로세서를 지정 하면 지정 된 프로세서 수입니다. 지시문 이름을 지정 하면 지정 된 지시문이 처리 될 때에 사용할 수는 매개 변수는.<br /><br /> 지시문 프로세서 또는 텍스트 템플릿에서 매개 변수 값에 액세스 하려면 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A>.</xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost.ResolveParameterValue%2A> 사용 텍스트 템플릿에 포함할 `hostspecific` 템플릿 지시문에에서 메시지를 호출 하 고 `this.Host`합니다. 예:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> 항상 입력의 '!' 옵션 프로세서 및 지시문 이름을 생략 하는 경우에 표시 합니다. 예:<br /><br /> `-a !!param!value`|  
|**-h**|도움말을 제공 합니다.|  
  
## <a name="related-topics"></a>관련 항목  
  
|작업|항목|  
|----------|-----------|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 솔루션에서 파일을 생성합니다.|[T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|고유한 데이터 소스를 변형하는 지시문 프로세서를 작성합니다.|[T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md)|  
|사용자의 응용 프로그램에서 텍스트 템플릿을 호출할 수 있도록 텍스트 템플릿 호스트를 작성 합니다.|[사용자 지정 호스트를 사용하여 텍스트 템플릿 처리](../modeling/processing-text-templates-by-using-a-custom-host.md)|