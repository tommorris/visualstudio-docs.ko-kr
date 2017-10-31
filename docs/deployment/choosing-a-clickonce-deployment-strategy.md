---
title: "ClickOnce 배포 전략 선택 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 배포, 전략"
  - "응용 프로그램 배포, ClickOnce"
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# ClickOnce 배포 전략 선택
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 배포하는 전략에는 세 가지가 있으며, 주로 배포하는 응용 프로그램 종류에 따라 전략을 선택합니다.  세 가지 배포 전략은 다음과 같습니다.  
  
-   웹 또는 네트워크 공유에서 설치  
  
-   CD에서 설치  
  
-   웹 또는 네트워크 공유에서 응용 프로그램 시작  
  
    > [!NOTE]
    >  배포 전략을 선택하고 응용 프로그램 업데이트를 제공하는 전략을 선택할 수도 있습니다.  자세한 내용은 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)을 참조하십시오.  
  
## 웹 또는 네트워크 공유에서 설치  
 이 전략을 사용하면 응용 프로그램이 웹 서버나 네트워크 파일 공유에 배포됩니다.  최종 사용자가 응용 프로그램을 설치할 경우에는 웹 페이지에서 아이콘을 클릭하거나 파일 공유에서 아이콘을 두 번 클릭합니다.  그러면 최종 사용자 컴퓨터에 응용 프로그램이 다운로드되고 설치된 후 시작됩니다.  **시작** 메뉴 및 **제어판**의 **프로그램 추가\/제거**에 항목이 추가됩니다.  
  
 이 전략은 네트워크 연결에 의존하므로 LAN\(Local Area Network\)이나 고속 인터넷 연결에 액세스할 수 있는 사용자에게 배포할 응용 프로그램에 가장 적합합니다.  
  
 웹에서 응용 프로그램을 배포할 경우 응용 프로그램이 URL을 통해 활성화될 때 응용 프로그램으로 인수를 전달할 수 있습니다.  자세한 내용은 [방법: 온라인 ClickOnce 응용 프로그램에서 쿼리 문자열 정보 검색](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)을 참조하십시오.  이 문서에 설명된 다른 방법을 사용하여 활성화되는 응용 프로그램에는 인수를 전달할 수 없습니다.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 이 배포 전략을 사용하려면 게시 마법사의 **응용 프로그램 설치 방법** 페이지에서 **웹에서** 또는 **UNC 경로 또는 파일 공유에서**를 클릭합니다.  
  
 이는 기본 배포 전략입니다.  
  
## CD에서 설치  
 이 전략을 사용하면 응용 프로그램이 CD\-ROM 또는 DVD와 같은 이동식 미디어에 배포됩니다.  이전 옵션의 경우 사용자가 응용 프로그램을 설치하도록 선택하면 응용 프로그램이 설치되고 시작된 다음 **시작** 메뉴 및 **제어판**의 **프로그램 추가\/제거**에 항목이 추가됩니다.  
  
 이 전략은 네트워크에 지속적으로 연결되어 있지 않거나 저대역폭 연결을 사용하는 사용자에게 배포할 응용 프로그램에 가장 적합합니다.  응용 프로그램은 이동식 미디어에서 설치되므로 설치할 때는 네트워크 연결이 필요하지 않지만 응용 프로그램을 업데이트할 때 네트워크 연결이 필요합니다.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 이 배포 전략을 사용하려면 게시 마법사의 **응용 프로그램 설치 방법** 페이지에서 **CD\-ROM 또는 DVD\-ROM에서**를 클릭합니다.  
  
 이 배포 전략을 수동으로 사용하려면 배포 매니페스트에서 **deploymentProvider** 태그를 변경합니다. Visual Studio에서는 이 속성이 프로젝트 디자이너의 **게시** 페이지에 **설치 URL**로 노출됩니다.  Mage.exe에서는 **시작 위치**입니다.  
  
## 웹 또는 네트워크 공유에서 응용 프로그램 시작  
 이 전략은 응용 프로그램이 웹 응용 프로그램처럼 작동하는 점을 제외하면 첫 번째 전략과 비슷합니다.  사용자가 웹 페이지에서 링크를 클릭하거나 파일 공유에서 아이콘을 두 번 클릭하면 응용 프로그램이 시작됩니다.  사용자가 응용 프로그램을 닫으면 로컬 컴퓨터에서는 응용 프로그램을 사용할 수 없으며 **시작** 메뉴 및 **제어판**의 **프로그램 추가\/제거**에 아무 것도 추가되지 않습니다.  
  
> [!NOTE]
>  기술적으로 웹 응용 프로그램이 웹 캐시로 다운로드되는 것처럼 응용 프로그램은 로컬 컴퓨터의 응용 프로그램 캐시로 다운로드되어 설치됩니다.  웹 캐시의 경우 파일은 결국 응용 프로그램 캐시에서 청소됩니다.  그러나 사용자는 응용 프로그램이 웹이나 파일 공유에서 실행되고 있는 것으로 인식합니다.  
  
 이 전략은 대개 1년에 한 번만 실행되는 직원 복리후생 도구 같이 가끔 사용되는 응용 프로그램에 가장 적합합니다.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 이 배포 전략을 사용하려면 게시 마법사의 **웹에서 설치 또는 실행** 페이지에서 **응용 프로그램을 설치하지 않습니다.**를 클릭합니다.  
  
 이 배포 전략을 수동으로 사용하려면 배포 매니페스트에서 **install** 태그를 변경합니다. 이 값은 **true** 또는 **false**일 수 있습니다.  Mage.exe에서는 **응용 프로그램 종류** 목록의 **온라인 전용** 옵션을 사용합니다.  
  
## 웹 브라우저 지원  
 .NET Framework 3.5를 대상으로 하는 응용 프로그램을 브라우저로 설치할 수 있습니다.  
  
 .NET Framework 2.0을 대상으로 하는 응용 프로그램에는 Internet Explorer가 필요합니다.  
  
## 참고 항목  
 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)   
 [방법: 게시 마법사를 사용하여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)