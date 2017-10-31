---
title: "AspNetCompiler 작업을 사용하여 ASP.NET 응용 프로그램 미리 컴파일 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
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
translationtype: Human Translation
ms.sourcegitcommit: 26c3d46033a59f88e70b6afde25a25c1ef5e77e8
ms.openlocfilehash: 0227d24dda3ca6a94092361f70c7e699c2c79c71
ms.lasthandoff: 02/22/2017

---
# <a name="aspnetcompiler-task"></a>AspNetCompiler 작업
`AspNetCompiler` 작업은 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 응용 프로그램을 미리 컴파일하는 유틸리티인 aspnet_compiler.exe를 래핑합니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
 다음 표에서는 `AspNetCompiler` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 이 매개 변수가 `true`이면 강력한 이름의 어셈블리에서 부분적으로 신뢰할 수 있는 호출자를 사용할 수 있습니다.|  
|`Clean`|선택적 `Boolean` 매개 변수<br /><br /> 이 매개 변수가 `true`이면 미리 컴파일된 응용 프로그램이 클린 빌드됩니다. 이전에 컴파일된 구성 요소가 모두 다시 컴파일됩니다. 기본값은 `false`입니다. 이 매개 변수는 aspnet_compiler.exe의 **-c** 스위치에 해당합니다.|  
|`Debug`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 이 매개 변수가 `true`이면 컴파일 중 디버그 정보(.PDB 파일)가 내보내집니다. 기본값은 `false`입니다. 이 매개 변수는 aspnet_compiler.exe의 **-d** 스위치에 해당합니다.|  
|`DelaySign`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 이 매개 변수가 `true`이면 어셈블리를 만들 때 완전히 서명되지 않습니다.|  
|`FixedNames`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 이 매개 변수가 `true`이면 컴파일된 어셈블리에 고정 이름이 지정됩니다.|  
|`Force`|선택적 `Boolean` 매개 변수<br /><br /> 이 매개 변수가 `true`이면 대상 디렉터리가 이미 있는 경우 작업은 대상 디렉터리를 덮어씁니다. 기존 콘텐츠는 손실됩니다. 기본값은 `false`입니다. 이 매개 변수는 aspnet_compiler.exe의 **-f** 스위치에 해당합니다.|  
|`KeyContainer`|선택적 `String` 매개 변수입니다.<br /><br /> 강력한 이름의 키 컨테이너를 지정합니다.|  
|`KeyFile`|선택적 `String` 매개 변수입니다.<br /><br /> 강력한 이름 키 파일의 실제 경로를 지정합니다.|  
|`MetabasePath`|선택적 `String` 매개 변수입니다.<br /><br /> 응용 프로그램의 전체 IIS 메타베이스 경로를 지정합니다. 이 매개 변수는 `VirtualPath` 또는 `PhysicalPath` 매개 변수와 함께 사용할 수 없습니다. 이 매개 변수는 aspnet_compiler.exe의 **-m** 스위치에 해당합니다.|  
|`PhysicalPath`|선택적 `String` 매개 변수입니다.<br /><br /> 컴파일할 응용 프로그램의 실제 경로를 지정합니다. 이 매개 변수가 누락되면 IIS 메타데이터가 응용 프로그램을 찾는 데 사용됩니다. 이 매개 변수는 aspnet_compiler.exe의 **-p** 스위치에 해당합니다.|  
|`TargetFrameworkMoniker`|선택적 `String` 매개 변수입니다.<br /><br /> aspnet_compiler.exe의 .NET Framework 버전을 나타내는 TargetFrameworkMoniker가 사용되도록 지정합니다. .NET Framework 모니커만 허용합니다.|  
|`TargetPath`|선택적 `String` 매개 변수입니다.<br /><br /> 응용 프로그램이 컴파일되는 실제 경로를 지정합니다. 지정하지 않으면 응용 프로그램은 현재 위치에서 미리 컴파일됩니다.|  
|`Updateable`|선택적 `Boolean` 매개 변수입니다.<br /><br /> 이 매개 변수가 `true`이면 미리 컴파일된 응용 프로그램이 업데이트 가능합니다.  기본값은 `false`입니다. 이 매개 변수는 aspnet_compiler.exe의 **-u** 스위치에 해당합니다.|  
|`VirtualPath`|선택적 `String` 매개 변수입니다.<br /><br /> 컴파일할 응용 프로그램의 가상 경로입니다. `PhysicalPath`가 지정되면 실제 경로가 응용 프로그램을 찾는 데 사용됩니다. 그렇지 않으면 IIS 메타베이스가 사용되고 응용 프로그램은 기본 사이트에 있는 것으로 간주됩니다. 이 매개 변수는 aspnet_compiler.exe의 **-v** 스위치에 해당합니다.|  
  
## <a name="remarks"></a>설명  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Tasks.ToolTaskExtension> 클래스의 매개 변수를 상속합니다. 이 클래스는 <xref:Microsoft.Build.Utilities.ToolTask> 클래스에서 매개 변수를 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [ToolTaskExtension 기본 클래스](../msbuild/tooltaskextension-base-class.md)를 참조하세요.  
  
## <a name="example"></a>예제  
 다음 코드 예제에서는 `AspNetCompiler` 작업을 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 응용 프로그램을 미리 컴파일합니다.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>참고 항목  
 [작업](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
