---
title: "Visual Studio에서 Python 설치 | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce3d3656-7ba2-490d-92df-0bb3e3badf92
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 613af31a2e44cc447980b68de4b0b5642dde1262
ms.contentlocale: ko-kr
ms.lasthandoff: 07/18/2017

---

# <a name="installing-python-support-in-visual-studio-on-windows"></a>Windows의 Visual Studio에서 Python 지원 설치

Visual Studio용 Python 지원을 설치하려면 Visual Studio 버전과 일치하는 섹션의 지침을 따릅니다.

- [Visual Studio 2017](#visual-studio-2017)
- [Visual Studio 2015](#visual-studio-2015)
- [Visual Studio 2013 및 이전 버전](#visual-studio-2013-and-earlier)

Visual Studio 2015 및 이전 버전의 경우 원하는 Python 인터프리터도 별도로 설치해야 합니다. 자세한 내용은 [Python 환경](python-environments.md)을 참조하세요.

설치 단계를 따른 후 Python 지원을 신속하게 테스트하려면 Alt+I를 누르고 `2+2`를 입력하여 Python 대화형 창을 엽니다. `4`의 출력이 표시되지 않으면 수행한 단계를 다시 확인합니다.

> [!Tip]
> Python 작업에는 템플릿을 검색하고, 템플릿 옵션을 입력하고, 프로젝트와 파일을 만들 수 있는 그래픽 사용자 인터페이스를 제공하는 유용한 Cookiecutter 확장 프로그램이 포함되어 있습니다. 자세한 내용은 [Cookiecutter 사용](cookiecutter.md)을 참조하세요.

> [!Note]
> Python 지원은 현재 Mac용 Visual Studio에서 사용할 수 없으며 Visual Studio Code를 통해 Mac 및 Linux에서 사용할 수 있습니다. [질문과 대답](python-in-visual-studio.md#questions-and-answers)을 참조하세요.

## <a name="visual-studio-2017"></a>Visual Studio 2017

1. [https://www.visualstudio.com/vs/](https://www.visualstudio.com/vs/)에서 Visual Studio 2017을 설치합니다.

1. Visual Studio 설치 관리자에서 **웹 및 클라우드 > Python 개발** 워크로드를 선택합니다.

    ![Visual Studio 설치 관리자의 Python 개발 작업](media/installation-python-workload.png)

    > [!Note]
    > Python은 **데이터 과학 및 분석 응용 프로그램** 워크로드에도 포함됩니다.

1. 설치 관리자의 오른쪽에서 포함하고자 하는 Python 인터프리터 및 기타 관련 도구를 선택합니다. 예를 들어 Python용 C++ 확장을 개발하려는 경우 **Python 네이티브 개발 도구** 옵션을 포함합니다.

    ![Visual Studio 설치 관리자의 Python 개발 옵션](media/installation-python-options.png)

1. 컴퓨터에 인터프리터가 이미 설치되어 있는 경우 [기존 인터프리터에 대한 환경 만들기](python-environments.md#creating-an-environment-for-an-existing-interpreter)를 참조하세요.

## <a name="visual-studio-2015"></a>Visual Studio 2015

1. **제어판 > 프로그램 및 기능**에서 **Microsoft Visual Studio 2015**, **변경**을 차례로 선택하여 Visual Studio 설치 관리자를 실행합니다.

1. 설치 관리자에서 **수정**을 선택합니다.

1. **프로그래밍 언어 > Visual Studio용 Python 도구**를 선택한 후 **다음**을 선택합니다.

    ![Visual Studio 2015 설치 관리자의 PTVS 옵션](media/installation-vs2015.png)    

1. Visual Studio 설치가 완료되면 [원하는 Python 인터프리터를 설치](python-environments.md#selecting-and-installing-python-interpreters)합니다. 인터프리터가 이미 설치되어 있는 경우 [기존 인터프리터에 대한 환경 만들기](python-environments.md#creating-an-environment-for-an-existing-interpreter)를 참조하세요.

## <a name="visual-studio-2013-and-earlier"></a>Visual Studio 2013 및 이전 버전

1. 사용 중인 Visual Studio 버전에 맞는 적절한 버전의 Visual Studio용 Python 도구를 설치합니다.

    - Visual Studio 2013: [Visual Studio 2013용 PTVS 2.2](https://github.com/Microsoft/PTVS/releases/v2.2). Visual Studio 2013에서 **파일 > 새 프로젝트** 대화 상자는 이 프로세스에 대한 바로 가기를 제공합니다.
    - Visual Studio 2012: [Visual Studio 2012용 PTVS 2.1](https://pytools.codeplex.com/downloads/get/920478)
    - Visual Studio 2010: [Visual Studio 2010용 PTVS 2.1](https://pytools.codeplex.com/downloads/get/920479)

1. [원하는 Python 인터프리터를 설치합니다](python-environments.md#selecting-and-installing-python-interpreters). 인터프리터가 이미 설치되어 있는 경우 [기존 인터프리터에 대한 환경 만들기](python-environments.md#creating-an-environment-for-an-existing-interpreter)를 참조하세요.

## <a name="install-locations"></a>설치 위치

기본적으로 Python 지원은 컴퓨터의 모든 사용자를 위해 설치됩니다.

Visual Studio 2017의 경우 Python 작업이 `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\<VS_edition>Common7\IDE\Extensions\Microsoft\Python`에 설치됩니다. 여기서 &lt;VS_edition&gt;은 Community, Professional 또는 Enterprise입니다.

Visual Studio 2015 및 이전 버전에서 설치 경로는 다음과 같습니다.

- 32비트:
  - 경로: `%Program Files(x86)%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - 경로의 레지스트리 위치: `HKEY_LOCAL_MACHINE\Software\Microsoft\PythonTools\<VS_ver>\InstallDir`
- 64비트:
  - 경로: `%Program Files%\Microsoft Visual Studio <VS_ver>\Common7\IDE\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`
  - 경로의 레지스트리 위치: `HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\PythonTools\<VS_ver>\InstallDir`

여기서

- &lt;VS_ver&gt;는 다음과 같습니다.    
    - Visual Studio 2015의 경우 14.0
    - Visual Studio 2013의 경우 12.0
    - Visual Studio 2012의 경우 11.0
    - Visual Studio 2010의 경우 10.0
- &lt;PTVS_ver&gt;는 2.2, 2.1, 2.0, 1.5, 1.1 또는 1.0과 같은 버전 번호입니다.

### <a name="user-specific-installations-15-and-earlier"></a>사용자 고유의 설치(1.5 및 이전 버전)

Visual Studio용 Python 도구 1.5 이하에서는 현재 사용자에 대한 설치만 허용했습니다. 이 경우 설치 경로는 `%LocalAppData%\Microsoft\VisualStudio\<VS_ver>\Extensions\Microsoft\Python Tools for Visual Studio\<PTVS_ver>`이고, 여기서 &lt;VS_ver&gt; 및 &lt;PTVS_ver&gt;는 위에 설명된 것과 같습니다.
