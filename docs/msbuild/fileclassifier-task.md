---
title: FileClassifier 작업 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eea3fbb882a2ed2b8036b6fe5bbb280d99c0f270
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177035"
---
# <a name="fileclassifier-task"></a>FileClassifier 작업
<xref:Microsoft.Build.Tasks.Windows.FileClassifier> 작업은 소스 리소스 집합을 어셈블리에 포함될 항목으로 분류합니다. 리소스를 지역화할 수 없는 경우 주 응용 프로그램 어셈블리에 포함되고, 그렇지 않으면 위성 어셈블리에 포함합니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`CLREmbeddedResource`|사용되지 않습니다.|  
|`CLRResourceFiles`|사용되지 않습니다.|  
|`CLRSatelliteEmbeddedResource`|사용되지 않습니다.|  
|`Culture`|선택적 **문자열** 매개 변수입니다.<br /><br /> 빌드에 대한 문화권을 지정합니다. 빌드를 지역화할 수 없는 경우 이 값은 **null**입니다. **null**인 경우 기본값은 **CultureInfo.InvariantCulture**가 반환하는 소문자 값입니다.|  
|`MainEmbeddedFiles`|선택적 **ITaskItem** 출력 매개 변수입니다.<br /><br /> 주 어셈블리에 포함되는 지역화할 수 없는 리소스를 지정합니다.|  
|`OutputType`|필수 **String** 매개 변수입니다.<br /><br /> 지정된 소스 파일을 포함할 파일의 형식을 지정합니다. 유효한 값은 **exe**, **winexe** 또는 **library**입니다.|  
|`SatelliteEmbeddedFiles`|선택적 **ITaskItem** 출력 매개 변수입니다.<br /><br /> **Culture** 매개 변수로 지정된 문화권에 대한 위성 어셈블리에 포함되는 지역화할 수 있는 파일을 지정합니다.|  
|`SourceFiles`|필수 **ITaskItem[]** 매개 변수입니다.<br /><br /> 분류할 파일의 목록을 지정합니다.|  
  
## <a name="remarks"></a>설명  
 **Culture** 매개 변수를 설정하지 않으면 **SourceFiles** 매개 변수를 사용하여 지정된 모든 리소스는 지역화할 수 없고, 그렇지 않고 이러한 리소스가 **false**로 설정된 **Localizable** 특성과 연결되어 있지 않는 한, 지역화할 수 있습니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 단일 소스 파일을 리소스로 분류한 다음 프랑스어-캐나다(fr-CA) 문화권에 대한 위성 어셈블리에 포함합니다.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>참고 항목  
 [WPF MSBuild 참조](../msbuild/wpf-msbuild-reference.md)   
 [작업 참조](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 참조](../msbuild/msbuild-reference.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)   
 [WPF 응용 프로그램 빌드(WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)