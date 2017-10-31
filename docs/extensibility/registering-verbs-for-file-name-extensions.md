---
title: "파일 이름 확장명에 대 한 동사를 등록 하는 중 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "동사를 등록 하는 중"
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# 파일 이름 확장명에 대 한 동사를 등록 하는 중
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

응용 프로그램 파일 이름 확장명의 연결에는 일반적으로 사용자 파일을 두 번 클릭할 때 발생 하는 기본 동작을 있습니다. 이 기본 동작 동사, 예를 들어 열기 작업에 해당 하는에 연결 됩니다.  
  
 중이지에 있는 셸 키를 사용 하 여 한 ProgID \(프로그래밍 식별자\)는 확장에 대 한와 연결 된 동사를 등록할 수 있습니다*progid*\\shell 합니다. 자세한 내용은 참조 [파일 형식](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)합니다.  
  
## 표준 동사를 등록 하는 중  
 운영 체제는 다음과 같은 표준 동사를 인식합니다.  
  
-   열기  
  
-   편집  
  
-   재생  
  
-   인쇄  
  
-   미리 보기  
  
 가능 하면 표준 동사를 등록 합니다. 가장 일반적인 선택은 Open 동사입니다. 분명 한 차이가 간에 파일을 열고 파일을 편집 하는 경우에 편집 동사를 사용 합니다. 예를 들어.htm 파일을 열면 표시 브라우저에서 HTML 편집기를 시작 하는.htm 파일을 편집 하는 반면 합니다. 표준 동사는 운영 체제 로캘로 지역화 됩니다.  
  
> [!NOTE]
>  표준 동사를 등록할 때 열린 키에 대 한 기본값을 설정 하지 마십시오. 메뉴에서 표시 문자열을 포함 하는 기본값입니다. 운영 체제 표준 동사에 대 한이 문자열을 제공합니다.  
  
 프로젝트 파일의 새 인스턴스를 시작 하려면 등록 해야 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 사용자가 파일을 열 때. 다음 예제에 대 한 표준 동사 등록 한 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 프로젝트입니다.  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 파일을 열려면의 기존 인스턴스에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], DDEEXEC 키를 등록 합니다. 다음 예제에 대 한 표준 동사 등록 한 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .cs 파일입니다.  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## 기본 동사를 설정합니다.  
 기본 동사는 사용자가 Windows 탐색기에서 파일을 두 번 클릭할 때 실행 되는 작업입니다. 기본 동사는 중이지에 대 한 기본 값으로 지정 된 동사는*progid*\\Shell 키입니다. 기본 동사는 중이지에 지정 된 첫 번째 동사는 없는 값을 지정 하는 경우*progid*\\Shell 키 목록입니다.  
  
> [!NOTE]
>  병렬\-배포의 확장 프로그램에 대 한 기본 동사를 변경 하려는 경우 설치 및 제거에 영향을 고려해 야 합니다. 설치 하는 동안 원래 기본 값을 덮어씁니다.  
  
## 참고 항목  
 [Creating a File Association](_win32_file_associations)   
 [Side by Side 파일 연결 관리](../extensibility/managing-side-by-side-file-associations.md)