---
title: "테스트 영역 4: 체크 인 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "소스 제어 [Visual Studio SDK] 항목을 체크 인"
  - "소스 제어 플러그 인, 항목을 체크 인"
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 테스트 영역 4: 체크 인
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

이 소스 제어 플러그 인 테스트 기능은 업데이트 된 항목을 버전 저장소를 통해 보낸는 **체크 인** 명령입니다.  
  
## 명령 메뉴 액세스  
 다음 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합된 개발 환경 메뉴 경로 테스트 사례에서 사용 됩니다.  
  
##### 체크 인 합니다.  
 **파일**, **소스 제어**, **체크 인**합니다.  
  
 **파일**, **체크 인**합니다.  
  
 바로 가기 메뉴를 **체크 인**합니다.  
  
## 예상 되는 일반적인 동작  
  
-   프로젝트 및 솔루션 또는 프로젝트 소스 제어에 추가 된 파일에 표시 된 **체크 인** 대화 상자 및 **보류 중인 체크 인** 창입니다.  
  
-   체크 인 후 소스 제어에 추가 된 항목이 나타납니다.  
  
-   체크 인 한 후 업데이트 된 항목은 저장소에 제대로 버전입니다.  
  
## 테스트 사례  
 체크 인 테스트 영역에 대 한 특정 테스트 사례는 다음과 같습니다.  
  
### 4a case: 항목 수정  
 작업에서 검사를 사용 하 여 수정 된 소스 제어에서 파일을 업데이트에 대해 설명 합니다.  
  
|작업|테스트 단계|예상된 결과 확인 하려면|  
|--------|------------|-------------------|  
|체크 아웃 된 텍스트 파일을 수정만 파일을 체크 인 \(**체크 인** 대화 상자\)|1.  텍스트와 함께 새 프로젝트를 만듭니다.<br />2.  소스 제어에 솔루션을 추가 합니다.<br />3.  체크 아웃 하 고 텍스트 파일을 수정 합니다.<br />4.  체크 인 대화 상자를 통해 체크 인 \(**파일**, **소스 제어**, **체크 인**\).|예상 되는 일반적인 동작입니다.|  
|체크 아웃 된 텍스트 파일을 수정만 파일을 체크 인 \(**보류 중인 체크 인** 창\)|1.  텍스트와 함께 새 프로젝트를 만듭니다.<br />2.  소스 제어에 솔루션을 추가 합니다.<br />3.  체크 아웃 하 고 텍스트 파일을 수정 합니다.<br />4.  통해 체크 인 된 **보류 중인 체크 인** 창입니다.|예상 되는 일반적인 동작입니다.|  
  
### 4b case: 파일 추가  
 프로젝트 또는 솔루션에는 항목에 파일을 추가할 때 프로젝트 또는 솔루션도 변경 해야 합니다. 따라서 부모 파일도 체크 아웃 하 고 추가 완료 하려면 체크 인 합니다.  
  
|작업|테스트 단계|예상된 결과 확인 하려면|  
|--------|------------|-------------------|  
|텍스트 파일을 추가 하 고 모두 체크 인 \(**체크 인** 대화 상자\)|1.  새 프로젝트를 만듭니다.<br />2.  소스 제어에 솔루션을 추가 합니다.<br />3.  텍스트 파일을 프로젝트에 추가 합니다.<br />4.  메시지가 표시 되는 프로젝트의 체크 아웃을 허용 합니다.<br />5.  솔루션을 선택 **솔루션 탐색기**합니다.<br />6.  체크 인 된 **체크 인** 대화 상자입니다.|예상 되는 일반적인 동작입니다.|  
|텍스트 파일을 추가 하 고 모두 체크 인 \(**보류 중인 체크 인** 창\)|1.  새 프로젝트를 만듭니다.<br />2.  소스 제어에 솔루션을 추가 합니다.<br />3.  텍스트 파일을 프로젝트에 추가 합니다.<br />4.  메시지가 표시 되는 프로젝트의 체크 아웃을 허용 합니다.<br />5.  솔루션에서 체크 인 **보류 중인 체크 인** 창입니다.|예상 되는 일반적인 동작|  
  
### 사례 4 c: 프로젝트 추가  
 프로젝트를 솔루션에 추가할 때 솔루션도 변경 해야 합니다. 따라서 솔루션 파일도 체크 아웃 하 고 추가 완료 하려면 체크 인 합니다.  
  
|작업|테스트 단계|예상된 결과 확인 하려면|  
|--------|------------|-------------------|  
|소스 제어에서 빈 솔루션에 프로젝트를 추가 \(**체크 인** 대화 상자\)|1.  빈 솔루션을 만듭니다.<br />2.  소스 제어에 솔루션을 추가 합니다.<br />3.  새 프로젝트를 추가 합니다.<br />4.  메시지가 표시 되 면 솔루션의 체크 아웃을 적용 합니다.<br />5.  체크 인 된 **체크 인** 대화 상자입니다.|예상 되는 일반적인 동작입니다.|  
|소스 제어에서 빈 솔루션에 프로젝트를 추가 \(**보류 중인 체크 인** 창\)|1.  빈 솔루션을 만듭니다.<br />2.  소스 제어에 솔루션을 추가 합니다.<br />3.  새 프로젝트를 추가 합니다.<br />4.  메시지가 표시 되 면 솔루션의 체크 아웃을 적용 합니다.<br />5.  솔루션에서 체크 인 **보류 중인 체크 인** 창입니다.|예상 되는 일반적인 동작입니다.|  
  
## 참고 항목  
 [소스 제어 플러그 인에 대 한 테스트 가이드](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)