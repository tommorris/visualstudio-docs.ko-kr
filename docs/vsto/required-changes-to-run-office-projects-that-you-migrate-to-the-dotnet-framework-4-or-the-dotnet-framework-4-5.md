---
title: ".NET Framework 4 또는 .NET Framework 4.5로 마이그레이션하는 Office 프로젝트를 실행하는 데 필요한 변경 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office 프로젝트[Visual Studio에서 Office 개발], .NET Framework 4로 마이그레이션"
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# .NET Framework 4 또는 .NET Framework 4.5로 마이그레이션하는 Office 프로젝트를 실행하는 데 필요한 변경
  Office 프로젝트의 대상 프레임워크가 이전 버전의 .NET Framework에서 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경된 경우 다음 작업을 수행하여 개발 컴퓨터와 최종 사용자 컴퓨터에서 솔루션을 실행할 수 있는지 확인해야 합니다.  
  
-   Visual Studio 2008에서 업그레이드한 경우 프로젝트에서 <xref:System.Security.SecurityTransparentAttribute>를 제거합니다.  
  
-   개발 컴퓨터에서 프로젝트를 실행하거나 디버그할 수 있도록 Visual Studio에서 **Clean** 명령을 수행합니다.  
  
-   프로젝트에 대한 .NET Framework 필수 조건을 업데이트합니다.  
  
-   또한 대상 프레임워크를 변경하기 전에 ClickOnce를 사용하여 이전에 배포한 경우 최종 사용자가 솔루션을 다시 설치해야 합니다.  
  
 이러한 각 작업에 대한 자세한 내용은 아래 해당 섹션을 참조하세요.  
  
## Visual Studio 2008에서 업그레이드하는 프로젝트에서 SecurityTransparent 특성 제거  
 Visual Studio 2008에서 Office 프로젝트를 업그레이드하고 프로젝트의 대상 프레임워크가 이후에 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경되는 경우 프로젝트에서 <xref:System.Security.SecurityTransparentAttribute>를 제거해야 합니다. Visual Studio에서 자동으로 이 특성을 제거하지 않습니다. 이 특성을 제거하지 않으면 프로젝트를 컴파일할 때 오류 메시지가 수신됩니다.  
  
 Visual Studio에서 업그레이드된 프로젝트의 대상 프레임워크를 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]로 변경할 수 있는 조건에 대한 자세한 내용은 [Office 솔루션 업그레이드 및 마이그레이션](../vsto/upgrading-and-migrating-office-solutions.md)을 참조하세요.  
  
#### SecurityTransparentAttribute를 제거하려면  
  
1.  Visual Studio에서 프로젝트를 열고 **솔루션 탐색기**를 엽니다.  
  
2.  **속성** 노드\(C\#의 경우\) 또는 **My Project** 노드\(Visual Basic의 경우\) 아래에서 AssemblyInfo 코드 파일을 두 번 클릭하여 코드 편집기에서 엽니다.  
  
    > [!NOTE]  
    >  Visual Basic 프로젝트에서 AssemblyInfo 코드 파일을 보려면 **솔루션 탐색기**에서 **모든 파일 표시** 단추를 클릭해야 합니다.  
  
3.  <xref:System.Security.SecurityTransparentAttribute>를 찾아 파일에서 제거하거나 주석으로 처리합니다.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## Clean 명령을 수행하여 개발 컴퓨터에서 프로젝트 디버그 또는 실행  
 프로젝트의 대상 프레임워크가 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경되기 전에 Office 프로젝트가 빌드된 경우 대상 프레임워크가 변경된 후 **Clean** 명령을 수행한 다음 프로젝트를 다시 빌드해야 합니다.  **Clean** 명령을 수행하지 않으면 대상이 변경된 프로젝트를 디버그 또는 실행하려고 할 때 <xref:System.Runtime.InteropServices.COMException>이 수신됩니다.  
  
 **Clean** 명령에 대한 자세한 내용은 [Office 솔루션 빌드](../vsto/building-office-solutions.md)를 참조하세요.  
  
## 배포를 위한 필수 조건 업데이트  
 Office 프로젝트 대상을 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경하는 경우 **필수 조건** 대화 상자에서 해당하는 .NET Framework 필수 조건도 업데이트해야 합니다.  그렇지 않으면 ClickOnce 배포 또는 InstallShield Limited Edition 프로젝트가 이전 버전의 .NET Framework를 검사하고 설치합니다.  
  
 최종 사용자 컴퓨터에 배포하기 위한 필수 조건 업데이트에 대한 자세한 내용은 [방법: 최종 사용자 컴퓨터에 Office 솔루션 실행을 위한 필수 구성 요소 설치](http://msdn.microsoft.com/ko-kr/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)를 참조하세요.  
  
## 최종 사용자 컴퓨터에 솔루션 다시 설치  
 ClickOnce를 사용하여 .NET Framework 3.5를 대상으로 하는 Office 솔루션을 배포한 다음 프로젝트 대상을 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상 버전으로 변경하는 경우 다시 게시한 후 최종 사용자가 솔루션을 제거하고 다시 설치해야 합니다.  대상이 변경된 솔루션을 다시 게시하고 최종 사용자 컴퓨터에서 솔루션이 업데이트되면 최종 사용자가 업데이트된 솔루션을 실행할 때 <xref:System.Runtime.InteropServices.COMException>이 수신됩니다.  
  
## 참고 항목  
 [.NET Framework 4 이상으로 Office 솔루션 마이그레이션](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  