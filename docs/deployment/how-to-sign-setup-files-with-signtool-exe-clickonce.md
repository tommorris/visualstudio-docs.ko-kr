---
title: "방법: SignTool.exe를 사용하여 설치 파일에 서명(ClickOnce) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
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
  - "ClickOnce 응용 프로그램, setup.exe 다시 서명"
  - "ClickOnce 응용 프로그램, signtool.exe"
  - "ClickOnce 배포, setup.exe 다시 서명"
  - "ClickOnce 배포, signtool.exe"
  - "응용 프로그램 배포[ClickOnce], setup.exe 다시 서명"
ms.assetid: 545a4005-d283-4110-9821-c78a9833c250
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 방법: SignTool.exe를 사용하여 설치 파일에 서명(ClickOnce)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

SignTool.exe를 사용하여 설치 프로그램\(setup.exe\)에 서명을 할 수 있습니다.  이 프로세스를 수행하면 최종 사용자 컴퓨터에 훼손된 파일이 설치되지 않습니다.  
  
 ClickOnce는 기본적으로 서명된 매니페스트 및 서명된 설치 프로그램을 포함합니다.  그러나 설치 프로그램의 매개 변수를 나중에 변경하려는 경우 설치 프로그램에 나중에 서명해야 합니다.  설치 프로그램에 서명을 한 후에 매개 변수를 변경하면 서명이 손상됩니다.  
  
 다음 절차에서는 서명되지 않은 매니페스트 및 서명되지 않은 설치 프로그램을 생성합니다.  그런 다음 Visual Studio에서 ClickOnce 서명을 사용하도록 설정하여 서명된 매니페스트를 생성합니다.  고객이 자신의 인증서로 실행 파일에 서명을 할 수 있도록 설치 프로그램은 서명되지 않은 상태로 유지합니다.  
  
### 서명되지 않은 설치 프로그램을 생성하고 나중에 서명을 하려면  
  
1.  매니페스트에 서명하는 데 사용할 인증서를 개발 컴퓨터에 설치합니다.  
  
2.  **솔루션 탐색기**에서 프로젝트를 선택합니다.  
  
3.  **프로젝트** 메뉴에서 *ProjectName* **속성**을 클릭합니다.  
  
4.  **서명** 페이지에서 **ClickOnce 매니페스트 서명** 확인란 선택을 취소합니다.  
  
5.  **게시** 페이지에서 **필수 구성 요소**를 클릭합니다.  
  
6.  모든 필수 구성 요소가 선택되어 있는지 확인한 다음 **확인**을 클릭합니다.  
  
7.  **게시** 페이지에서 게시 설정을 확인하고 **지금 게시**를 클릭합니다.  
  
     서명되지 않은 응용 프로그램 매니페스트, 서명되지 않은 배포 매니페스트, 버전별 파일 및 서명되지 않은 설치 프로그램이 게시 폴더 위치에 게시됩니다.  
  
8.  **게시** 페이지에서 **필수 구성 요소**를 클릭합니다.  
  
9. **필수 구성 요소** 대화 상자에서 **필수 구성 요소를 설치하기 위한 설치 프로그램 만들기** 확인란 선택을 취소합니다.  
  
10. **게시** 페이지에서 게시 설정을 확인하고 **지금 게시**를 클릭합니다.  
  
     서명된 응용 프로그램 매니페스트, 서명된 배포 매니페스트 및 버전별 파일이 게시 폴더 위치에 게시됩니다.  게시 프로세스는 서명되지 않은 설치 프로그램을 덮어쓰지 않습니다.  
  
11. 고객 사이트에서 명령 프롬프트를 엽니다.  
  
12. .exe 파일이 포함된 디렉터리로 변경합니다.  
  
13. 다음 명령을 사용하여 .exe 파일에 서명을 합니다.  
  
    ```  
    signtool sign /sha1 CertificateHash Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
     예를 들어 설치 프로그램에 서명하려면 다음 명령 중 하나를 사용합니다.  
  
    ```  
    signtool sign /sha1 CCB... Setup.exe  
    signtool sign /f CertFileName Setup.exe  
    ```  
  
## 참고 항목  
 [방법: 응용 프로그램 및 배포 매니페스트에 다시 서명](../deployment/how-to-re-sign-application-and-deployment-manifests.md)