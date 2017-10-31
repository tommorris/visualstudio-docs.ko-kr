---
title: "Error Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Error"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Error task [MSBuild]"
  - "MSBuild, Error task"
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Error Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

빌드를 중지하고 확인된 조건문에 따라 오류를 기록합니다.  
  
## 매개 변수  
 다음 표에서는 `Error` 작업의 매개 변수에 대해 설명합니다.  
  
|Parameter|설명|  
|---------------|--------|  
|`Code`|선택적 `String` 매개 변수입니다.<br /><br /> 오류에 연결할 오류 코드입니다.|  
|`File`|선택적 `String` 매개 변수입니다.<br /><br /> 오류가 들어 있는 파일의 이름입니다.  아무 파일도 제공하지 않으면 오류 작업이 들어 있는 파일이 사용됩니다.|  
|`HelpKeyword`|선택적 `String` 매개 변수입니다.<br /><br /> 오류와 연결할 도움말 키워드입니다.|  
|`Text`|선택적 `String` 매개 변수입니다.<br /><br /> `Condition` 매개 변수가 `true`로 확인되는 경우 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]에서 기록하는 오류 텍스트입니다.|  
  
## 설명  
 `Error` 작업을 사용하면 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 프로젝트에서 오류 텍스트를 로거에 기록하고 빌드 실행을 중지할 수 있습니다.  
  
 `Condition` 매개 변수가 `true`로 확인되면 빌드가 중지되고 오류가 기록됩니다.  `Condition` 매개 변수가 없으면 오류가 기록되고 빌드 실행이 중지됩니다.  기록에 대한 자세한 내용은 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)을 참조하십시오.  
  
 위에 나열된 매개 변수 외에도 이 작업은 <xref:Microsoft.Build.Utilities.Task> 클래스에서 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수를 상속합니다.  추가 매개 변수 목록과 해당 설명은 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)를 참조하십시오.  
  
## 예제  
 다음 코드 예제에서는 필요한 속성이 모두 설정되었는지 확인합니다.  속성이 설정되어 있지 않으면 프로젝트에서 오류 이벤트가 발생하고 `Error` 작업의 `Text` 매개 변수 값이 기록됩니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## 참고 항목  
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)