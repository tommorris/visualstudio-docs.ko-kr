---
title: Office 솔루션 빌드
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 081a3dfd809cc936f11d436e593d2be258452f85
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675148"
---
# <a name="build-office-solutions"></a>Office 솔루션 빌드
  일반적으로 Office 프로젝트를 빌드하고 디버깅하는 것은 Windows Forms와 같이 Visual Studio에서 다른 형식의 프로젝트를 빌드하고 디버깅하는 것과 같습니다. 이 섹션의 항목에서는 차이점에 대해 설명합니다. 응용 프로그램을 빌드하는 방법에 대 한 일반 정보를 참조 하세요. [Visual Studio에서 컴파일 및 빌드](/visualstudio/ide/compiling-and-building-in-visual-studio)합니다.  
  
> [!NOTE]  
>  Office 환경을 확장 하는 솔루션을 개발 하는 데 관심이 [여러 플랫폼](https://dev.office.com/add-in-availability)? 새 확인해 [Office 추가 기능 모델](https://dev.office.com/docs/add-ins/overview/office-add-ins)합니다. Office 추가 기능의 VSTO 추가 기능 및 솔루션에 비해 작은 사용 공간이 있고 거의 모든 웹 프로그래밍 기술을, HTML5, JavaScript, CSS3, XML 등을 사용 하 여 빌드할 수 있습니다.  
  
## <a name="project-output-for-office-projects"></a>Office 프로젝트용 프로젝트 출력  
 Office 프로젝트의 출력 위치는 *projectname*\bin\release 또는 *projectname*\bin\debug입니다. 배포 디렉터리에 빌드할 수 없습니다.  
  
### <a name="document-level-projects"></a>문서 수준 프로젝트  
 문서 수준 프로젝트를 빌드하면 프로젝트 출력에 다음과 같은 항목이 포함됩니다.  
  
-   프로젝트 문서의 복사본  
  
-   프로젝트 어셈블리 및 **true** 로 설정된 해당 **로컬 복사**속성을 가진 참조되는 모든 어셈블리  
  
-   파일 이름 확장명에는 응용 프로그램 매니페스트의 *.manifest*합니다. 자세한 내용은 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.  
  
-   배포 매니페스트 파일 이름 확장명이 *.vsto*합니다. 자세한 내용은 [Deployment manifests for Office 솔루션](../vsto/deployment-manifests-for-office-solutions.md)합니다.  
  
-   프로그램 데이터베이스 (*PDB*) 파일입니다.  
  
> [!NOTE]  
>  로컬 컴퓨터 대신 원격 위치에 문서 수준의 솔루션을 빌드하는 경우 응용 프로그램의 보안 센터에서 신뢰할 수 있는 위치 목록에 정규화된 경로를 추가합니다. 자세한 내용은의 문서에 신뢰 부여 라는 섹션을 참조 하세요 [Secure Office 솔루션](../vsto/securing-office-solutions.md)합니다.  
  
### <a name="application-level-projects"></a>응용 프로그램 수준 프로젝트  
 VSTO 추가 기능 프로젝트를 빌드하면 프로젝트 출력에 다음 항목이 포함 됩니다.  
  
-   프로젝트 어셈블리 및 **true** 로 설정된 해당 **로컬 복사**속성을 가진 참조되는 모든 어셈블리  
  
-   파일 이름 확장명에는 응용 프로그램 매니페스트의 *.manifest*합니다. 자세한 내용은 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.  
  
-   배포 매니페스트 파일 이름 확장명이 *.vsto*합니다. 자세한 내용은 [Deployment manifests for Office 솔루션](../vsto/deployment-manifests-for-office-solutions.md)합니다.  
  
-   프로그램 데이터베이스 (*PDB*) 프로젝트 어셈블리 파일입니다.  
  
 또한 VSTO 추가 기능 프로젝트의 빌드 프로세스는 VSTO 추가 기능을 로드하는 데 필요한 개발 컴퓨터에서 레지스트리 항목 집합을 만듭니다. 자세한 내용은 [VSTO 추가 기능에 대 한 레지스트리 항목](../vsto/registry-entries-for-vsto-add-ins.md)합니다.  
  
 양식 영역을 포함하는 Outlook VSTO 추가 기능 프로젝트를 빌드하는 경우 빌드 프로세스는 다음과 같은 추가 정보를 레지스트리에 추가합니다.  
  
-   하나 이상의 양식 영역과 연결된 각 메시지 클래스에 대한 키  
  
-   각 양식 영역에 대한 항목 및 Outlook VSTO 추가 기능의 이름을 나타내는 관련된 값  
  
 Outlook은 이 정보를 양식 영역으로 로드해야 합니다.  
  
## <a name="referenced-assemblies"></a>참조된 어셈블리  
 Office 솔루션 빌드 프로젝트에서 어셈블리(클래스 라이브러리 프로젝트 포함)를 참조할 수 있습니다. 모든 참조된 어셈블리에는 **로컬 복사**라는 속성이 있습니다. **로컬 복사** 는 어셈블리를 출력 디렉터리에 복사할지 여부를 나타냅니다. 기본적으로 이 속성은 **true**로 설정됩니다. **로컬 복사** 를 **true** 로 설정한 모든 참조된 어셈블리는 출력 디렉터리에 복사됩니다.  
  
## <a name="security-during-the-build-process"></a>빌드 프로세스 중 보안  
 Visual Studio는 개발 컴퓨터에서 보안 설정을 자동으로 구성하여 빌드 프로세스 동안 솔루션에 신뢰를 부여합니다. 그렇게 하면 솔루션을 디버깅하면서 실행할 수 있습니다.  
  
 Office 프로젝트는 인증서를 사용하여 게시자를 확인합니다. Visual Studio는 자동으로 임시 인증서를 만들어 Office 솔루션을 식별하고 임시 인증서를 신뢰하도록 개발 컴퓨터를 구성합니다.  
  
 자세한 내용은 [Secure Office 솔루션](../vsto/securing-office-solutions.md)합니다.  
  
### <a name="network-projects"></a>네트워크 프로젝트  
 어셈블리 또는 문서 위치가 네트워크 공유에 있는 경우 로컬(사용자 수준) 보안 정책 업데이트로는 솔루션을 충분히 실행할 수 없습니다. 관리자는 솔루션을 실행하기 전에 네트워크 공유에 있는 어셈블리와 문서에 컴퓨터 수준에서 완전 신뢰를 부여해야 합니다. 보안 정책을 설정 하는 방법에 대 한 자세한 내용은 참조 하세요. [Secure Office 솔루션](../vsto/securing-office-solutions.md)합니다.  
  
 또한 문서 수준 프로젝트의 경우 Office 신뢰할 수 있는 폴더 목록에 문서의 정규화된 위치를 추가해야 합니다. 자세한 내용은 [문서에 신뢰 부여](../vsto/granting-trust-to-documents.md)합니다.  
  
## <a name="change-the-platform-target"></a>대상 플랫폼 변경  
 기본적으로 Office 프로젝트의 플랫폼 대상은 **임의 CPU**입니다. 일반적으로 이 설정을 변경해서는 안 됩니다. **임의 CPU** 플랫폼 대상 설정으로 빌드된 Office 솔루션은 32비트 및 64비트 버전의 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 또는 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]에서 실행됩니다.  
  
 64비트 버전의 Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 또는 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]에서만 실행되는 솔루션을 만드는 경우에만 플랫폼 대상을 x64로 설정해야 하며, 솔루션은 네이티브 64비트 API를 호출합니다. 플랫폼 대상 설정을 변경 하는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 플랫폼을 대상으로 한 프로젝트 구성](../ide/how-to-configure-projects-to-target-platforms.md)합니다.  
  
 플랫폼 대상을 x64로 설정하는 경우 솔루션이 32비트 버전의 Windows 또는 Office에서는 실행되지 않습니다. x64 플랫폼 대상은 64비트 프로세스에서 실행되는 솔루션이 필요합니다.  
  
## <a name="use-the-clean-command"></a>정리 명령을 사용 하 여  
 개발 컴퓨터에서 빌드된 프로젝트 파일을 제거하려면 **의** 빌드 **메뉴에서** 정리 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]명령을 사용하면 됩니다. **정리** 명령은 빌드 출력 위치에 있는 모든 파일을 삭제합니다. 또한 응용 프로그램 수준 프로젝트에서 **정리** 명령은 빌드 프로세스에서 만들어지는 레지스트리 항목을 제거합니다.  
  
## <a name="related-topics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[Office 프로젝트 디버깅](../vsto/debugging-office-projects.md)|Office 프로젝트 디버깅과 관련된 문제를 나타냅니다.|  
|[연습: Excel 용 첫 문서 수준 사용자 지정 만들기](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Excel용 기본 문서 수준 사용자 지정을 만드는 방법을 보여 줍니다.|  
|[방법: VSTO 추가 기능을 비활성화 된 다시 사용 하도록 설정](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|VSTO 추가 기능을 하드 또는 소프트 비활성화 된 다시 사용 하도록 설정 하는 방법에 설명 합니다.|  
|[Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)|Office 솔루션을 만드는 방법 및 솔루션에서 어셈블리의 역할 정보에 대한 링크를 제공합니다.|  
  
  