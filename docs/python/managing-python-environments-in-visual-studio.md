---
title: "Visual Studio에서 Python 환경 관리 | Microsoft Docs"
description: "Visual Studio에서 [Python 환경] 창을 사용하여 전역 및 가상 환경을 관리하며, Python 인터프리터 설치, 패키지 설치, 검색 경로 설정, Visual Studio 프로젝트의 환경 관리를 위한 사용자 지정 환경을 설정하는 방법입니다."
ms.custom: 
ms.date: 01/16/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 146e3f80de674e6219d1f7c89ea4186b66ee310f
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2018
---
# <a name="python-environments"></a>Python 환경

Python *환경*은 Python 코드를 실행하는 컨텍스트입니다. 환경은 인터프리터, 라이브러리(일반적으로 Python 표준 라이브러리) 및 설치된 패키지 집합으로 구성됩니다. 이러한 모든 구성 요소에 따라, 어떤 언어로 구성되고 구문이 유효한지, 어떤 운영 체제 기능에 액세스할 수 있으며 어떤 패키지를 사용할 수 있는지가 결정됩니다.

Visual Studio에서는 이 문서에 설명된 대로 [Python 환경 창](#managing-python-environments-in-visual-studio)을 사용하여 모든 환경을 관리합니다. 제공된 프로젝트의 경우 코드 실행, 디버깅, 구문 검사, 가져오기 및 멤버 완료 표시뿐 아니라 인터프리터 및 설치된 라이브러리에 관련된 다른 작업에 사용할 환경을 선택할 수 있습니다. 또한 Visual Studio는 코드를 입력할 때 자동 완성을 위해 제공되는 각 환경용 IntelliSense 데이터베이스를 유지 관리합니다.

또한 Visual Studio는 가상 환경, `requirements.txt` 파일 및 검색 경로에 대한 지원을 제공합니다.

**참고**: Visual Studio에서 Python을 처음 사용하는 경우 필요한 배경은 다음 문서를 참조하세요.

- [Visual Studio에서 Python 작업](overview-of-python-tools-for-visual-studio.md)
- [Visual Studio에서 Python 지원 설치](installing-python-support-in-visual-studio.md)

## <a name="global-and-virtual-environments"></a>전역 및 가상 환경

전역 및 가상의 두 가지 유형의 Python 환경이 있습니다.

**전역 환경**: 각 Python 설치(예: Python 2.7, Python 3.6 및 Anaconda 4.4.0)는 [Python 인터프리터 선택 및 설치](#selecting-and-installing-python-interpreters)를 참조하세요. 각 환경은 특정 Python 인터프리터, 표준 라이브러리 및 사전 설치된 패키지 집합으로 구성됩니다. 패키지를 전역 환경에 설치하면 해당 환경을 사용하는 모든 프로젝트에서 사용할 수 있습니다. 환경이 파일 시스템의 보호 영역(예: `c:\program files` 내)에 있는 경우 패키지를 설치하려면 관리자 권한이 필요합니다.

전역 환경은 컴퓨터의 모든 프로젝트에서 사용할 수 있습니다. Visual Studio에서는 특별히 프로젝트별로 다른 항목을 선택하지 않는 한 하나의 전역 환경을 모든 프로젝트에 사용되는 기본값으로 선택합니다. 자세한 내용은 [프로젝트의 환경 선택](#selecting-an-environment-for-a-project)을 참조하세요.

**가상 환경**: 전역 환경에 설치된 패키지는 해당 환경을 사용하는 모든 프로젝트에서 사용 가능하므로 두 프로젝트에 호환되지 않은 패키지 또는 동일한 패키지의 서로 다른 버전이 필요한 경우 충돌이 발생할 수 있습니다. 가상 환경은 전역 환경의 인터프리터 및 표준 라이브러리를 사용하지만 해당 패키지 저장소를 격리된 폴더에서 유지 관리하여 이러한 충돌을 방지합니다.

Visual Studio에서는 프로젝트의 하위 폴더에 저장된 특정 프로젝트에 대한 가상 환경을 만들 수 있습니다([가상 환경 만들기](#creating-virtual-environments) 참조). 프로젝트 파일은 가상 환경도 식별합니다. 또한 Visual Studio는 해당 가상 환경에 설치하는 모든 패키지를 프로젝트의 `requirements.txt` 파일에 기록합니다. 프로젝트를 공유하고 다른 개발자가 컴퓨터에서 이 프로젝트를 열 경우 Visual Studio에서는 가상 환경을 다시 만드는 옵션을 제공합니다.

### <a name="selecting-and-installing-python-interpreters"></a>Python 인터프리터 선택 및 설치

기본적으로 Visual Studio 2017에 Python 개발 워크로드를 설치하면 Python 3(64비트)도 설치됩니다. 필요한 경우 [설치](installing-python-support-in-visual-studio.md)에 설명된 대로 32비트 및 64비트 버전의 Python 2, Python 3, Anaconda 2 및 Anaconda 3을 설치하도록 선택할 수 있습니다. 다음 표에 나열된 인터프리터를 수동으로 설치할 수도 있습니다.

Visual Studio 2015 이하의 경우 인터프리터 중 하나를 수동으로 설치해야 합니다.

Visual Studio(모든 버전)는 레지스트리를 확인하여 각 설치된 Python 인터프리터의 환경을 자동으로 만듭니다([Windows 레지스트리의 PEP 514 - Python 등록](https://www.python.org/dev/peps/pep-0514/)에 따라). Visual Studio에서 설치된 환경을 감지하지 않는 경우 [기존 인터프리터에 대한 환경 만들기](#creating-an-environment-for-an-existing-interpreter)를 참조하세요.

| 인터프리터 | 설명 |
| --- | --- |
| [CPython](https://www.python.org/) | 가장 널리 사용되는 “기본” 인터프리터로, 32비트 및 64비트 버전으로 사용 가능합니다(32비트 권장). 최신 언어 기능, 최대 Python 패키지 호환성, 완전한 디버깅 지원 및 [IPython](http://ipython.org/)과 상호 interop을 포함합니다. [Python 2 또는 Python 3을 사용해야 하나요?](http://wiki.python.org/moin/Python2orPython3)도 참조하세요. Visual Studio 2015 및 이전 버전은 Python 3.6을 지원하지 않으며 “Python 버전 3.6 지원되지 않음” 오류가 표시될 수 있습니다. 대신 Python 3.5 또는 이전을 사용합니다. |
| [IronPython](https://github.com/IronLanguages/ironpython2) | Python의 .NET 구현으로, 32비트 및 64비트 버전으로 사용 가능하며 C#/F#/Visual Basic interop, .NET API에 대한 액세스, 표준 Python 디버깅(그러나 C++ 혼합 모드 디버깅은 제외) 및 혼합 IronPython/C# 디버깅을 제공합니다. 하지만 IronPython에서는 가상 환경을 지원하지 않습니다. |
| [Anaconda](https://www.continuum.io) | Python에서 제공하는 개방형 데이터 과학 플랫폼으로, 최신 버전의 CPython과 설치하기 어려운 대부분의 패키지를 포함합니다. 달리 결정할 수 없는 경우 권장됩니다. |
| [PyPy](http://www.pypy.org/) | Python의 고성능 추적 JIT 구현으로, 장기적으로 실행되는 프로그램과 성능 문제를 확인했으나 다른 해결 방법을 찾을 수 없는 상황에 적절합니다. Visual Studio에서 작동하지만 고급 디버깅 기능은 제한적으로 지원됩니다. |
| [Jython](http://www.jython.org/) | JVM(Java Virtual Machine)에서 Python 구현. IronPython과 마찬가지로, Jython에서 실행되는 코드는 Java 클래스 및 라이브러리와 상호 작용할 수 있지만 CPython용으로 작성된 많은 라이브러리는 사용할 수 없습니다. Visual Studio에서 작동하지만 고급 디버깅 기능은 제한적으로 지원됩니다. |

Python 환경에 대한 새로운 검색 양식을 제공하려는 개발자인 경우 [PTVS 환경 검색](https://github.com/Microsoft/PTVS/wiki/Extensibility-Environments)(github.com)을 참조하세요.

## <a name="managing-python-environments-in-visual-studio"></a>Visual Studio에서 Python 환경 관리

[Python 환경] 창을 열려면 **보기 > 다른 창 > Python 환경** 메뉴 명령을 선택하거나 솔루션 탐색기에서 프로젝트에 대한 **Python 환경** 노드를 마우스 오른쪽 단추로 클릭하고 **모든 Python 환경 보기**를 선택합니다.

    ![View All Environments command in Solution Explorer](media/environments-view-all.png)

두 경우 모두 Python 환경 창은 솔루션 탐색기의 형제 탭으로 나타납니다.

![Python 환경 창](media/environments-default-view.png)

위의 예제에서는 Python 3.4(32비트 CPython)가 IronPython 2.7 32비트 및 64비트 버전과 함께 설치되어 있습니다. 굵게 표시된 기본 환경은 Python 3.4이며 모든 새로운 프로젝트에 사용됩니다. 목록에 환경이 표시되지 않는 경우 Visual Studio 2015 또는 이전 버전에 Visual Studio용 Python 도구를 설치했으나 Python 인터프리터를 설치하지 않은 것입니다(위의 [Python 인터프리터 선택 및 설치](#selecting-and-installing-python-interpreters) 참조). **+ 사용자 지정...** 명령을 사용하면 [기존 인터프리터의 환경을 만들](#create-an-environment-for-an-existing-interpreter) 수 있습니다.

나열된 각 환경의 오른쪽에는 해당 환경에 대한 대화형 창을 여는 컨트롤이 있습니다. 해당 환경의 IntelliSense 데이터베이스를 새로 고치는 다른 컨트롤이 나타날 수 있습니다.

환경 목록 아래에는 이 섹션에 설명된 **개요**, **패키지** 및 **IntelliSense** 옵션에 대한 드롭다운 선택기가 있습니다. **Python 환경** 창을 충분히 넓게 확장하면 이러한 옵션이 탭으로 표시되어 작업하기가 더 편리할 수 있습니다.

![Python 환경 창 확장된 보기](media/environments-expanded-view.png)

> [!Note]
> Visual Studio에서는 system-site-packages 옵션을 적용하지만 Visual Studio 내에 이를 변경하는 방법은 제공하지 않습니다.

Visual Studio에서 환경 관리를 소개하는 비디오는 [Python 환경 관리](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=qrDmN4LWE_8305918567)(Microsoft Virtual Academy, 2m35s)를 참조하세요.

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Managing-Python-Environments-qrDmN4LWE_8305918567]

### <a name="creating-an-environment-for-an-existing-interpreter"></a>기존 인터프리터에 대한 환경 만들기

Visual Studio에서 인터프리터를 찾지 못하는 경우(예: 비표준 위치에 설치된 경우) 다음과 같이 환경을 만들 수 있습니다.

1. [Python 환경 창](#managing-python-environments-in-visual-studio)에서 **+ 사용자 지정...**을 선택하면 새 환경이 생성되고 아래 설명된 [**구성** 탭](#configure-tab)이 열립니다.

    ![새 사용자 지정 환경의 기본 보기](media/environments-custom-1.png)

1. **설명** 필드에 환경에 대한 이름을 입력합니다.
1. **접두사 경로** 필드에 인터프리터의 경로를 입력하거나 찾습니다.
1. **자동 검색**을 선택하여 Visual Studio에서 나머지 필드를 완성하도록 하거나 수동으로 작성합니다.
1. **적용**을 선택하여 환경을 저장합니다.
1. 환경을 제거해야 하는 경우 **구성** 탭에서 **제거** 명령을 선택합니다. 자동 감지 환경에서는 이 옵션을 제공하지 않습니다. 자세한 내용은 다음 섹션을 참조하세요.

### <a name="moving-an-existing-interpreter"></a>기존 인터프리터 이동

파일 시스템에서 새 위치로 기존 인터프리터를 이동하는 경우 Visual Studio는 변경 내용을 자동으로 검색하지 않으므로 환경을 수동으로 업데이트해야 합니다.

- 원래 해당 인터프리터에 환경을 만든 경우 새 위치를 가리키도록 해당 환경을 편집합니다.

- 원래 환경을 자동으로 검색한 경우 Visual Studio에서 검사하는 레지스트리 항목을 만든 고유한 설치 프로그램을 사용하여 컴퓨터에 설치합니다. 이 경우에 먼저 Python 인터프리터를 원래 위치로 복원합니다. 설치 관리자를 사용하여 제거합니다. 그러면 레지스트리 항목을 정리합니다. 그런 다음 원하는 위치에 인터프리터를 다시 설치합니다. Visual Studio를 다시 시작하면 자동으로 새 위치를 검색합니다. 이 프로세스는 설치 관리자의 다른 부작용이 적절히 적용되도록 됩니다.

### <a name="overview-tab"></a>개요 탭

환경에 대한 기본 정보와 명령을 제공합니다.

![Python 환경 개요 탭](media/environments-overview-tab.png)

| 명령 | 설명 |
| --- | --- |
| 이 환경을 새 프로젝트에 대한 기본값으로 설정 | 활성 환경을 설정합니다. 이 경우 IntelliSense 데이터베이스가 로드되는 동안 Visual Studio가 잠시 응답하지 않을 수 있습니다. 많은 패키지가 있는 환경에서는 더 오랫동안 응답하지 않을 수 있습니다. |
| 배포자 웹 사이트 방문 | Python 배포에서 제공된 URL로 브라우저를 엽니다. 예를 들어 Python 3.x는 python.org로 이동합니다. |
| 대화형 창 열기 | Visual Studio 내에서 이 환경에 대한 [대화형(REPL) 창](interactive-repl.md)을 열고 [시작 스크립트(아래 참조)](#startup-scripts)를 적용합니다. |
| 대화형 스크립트 탐색 | [시작 스크립트](#startup-scripts)를 참조하세요. |
| IPython 대화형 모드 사용 | 설정하면 기본적으로 IPython을 사용하여 대화형 창을 엽니다. 여기서 인라인 플롯과 확장된 IPython 구문을 사용할 수 있습니다. 예를 들어 도움말을 보려면 `name?`를 사용하고, 셸 명령을 실행하려면 `!command`를 사용합니다. 이 옵션은 추가 패키지를 요구하는 Anaconda 배포를 사용할 때 권장됩니다. 자세한 내용은 [대화형 창에서 IPython 사용](interactive-repl-ipython.md)을 참조하세요. |
| PowerShell에서 열기 | PowerShell 명령 창에서 인터프리터를 시작합니다. |
| (폴더 링크) | 환경 설치 폴더, python.exe 인터프리터, pythonw.exe 인터프리터에 대한 빠른 액세스를 제공합니다. 첫 번째 링크는 Windows 탐색기에서 열리고, 나머지 링크는 콘솔 창을 엽니다. |

#### <a name="startup-scripts"></a>시작 스크립트

일상적인 워크플로에 대화형 창을 사용하면서 정기적으로 사용하는 도우미 함수를 개발할 가능성이 큽니다. 예를 들어 Excel에서 데이터 프레임을 여는 함수를 만든 다음 대화형 창에서 항상 사용할 수 있도록 해당 코드를 시작 스크립트로 저장할 수 있습니다.

시작 스크립트에는 가져오기, 함수 정의 등을 포함하여 대화형 창에서 자동으로 로드하고 실행하는 코드가 포함됩니다. 이러한 스크립트는 다음 두 가지 방법으로 참조됩니다.

1. 환경을 설치할 때 Visual Studio는 `Documents\Visual Studio 2017\Python Scripts\<environment>` 폴더를 만듭니다. 여기서 &lt;environment&gt'는 환경 이름과 일치합니다. **대화형 스크립트 탐색** 명령을 사용하여 환경 관련 폴더를 쉽게 탐색할 수 있습니다. 해당 환경에 대한 대화형 창을 시작하면 여기서 발견된 `.py` 파일이 사전순으로 로드 및 실행됩니다.

1. **도구 > 옵션 > Python 도구 > 대화형 Windows** 탭([대화형 windows 옵션](options.md#interactive-windows-options) 참조)에 있는 **스크립트** 컨트롤은 모든 환경에서 로드 및 실행되는 시작 스크립트에 대한 추가 폴더를 지정하기 위한 것입니다. 그러나 이 기능은 현재 작동하지 않습니다.

### <a name="configure-tab"></a>구성 탭

표시된 경우, 아래 표에 설명된 세부 정보를 포함합니다. 이 탭이 없는 경우 Visual Studio에서 모든 세부 정보를 자동으로 관리하는 것입니다.

![Python 환경 구성 탭](media/environments-configure-tab.png)

| 필드 | 설명 |
| --- | --- |
| **설명** | 환경에 지정할 이름입니다. |
| **접두사 경로** | 인터프리터의 기본 폴더 위치입니다. 이 값을 입력하고 **자동 검색**을 클릭하면 Visual Studio에서 다른 필드를 채우려고 시도합니다. |
| **인터프리터 경로** | 인터프리터 실행 파일의 경로이며, 일반적으로 접두사 경로 다음에 `python.exe`가 나옵니다. |
| **창 인터프리터** | 비콘솔 실행 파일의 경로이며, 보통 접두사 경로 다음에 `pythonw.exe`가 나옵니다. |
| **라이브러리 경로** | 표준 라이브러리의 루트를 지정하지만 Visual Studio에서 인터프리터로부터 더 정확한 경로를 요청할 수 있는 경우 이 값은 무시될 수 있습니다. |
| **언어 버전** | 드롭다운 메뉴에서 선택합니다. |
| **아키텍처** | 일반적으로 검색되어 자동으로 채워지며 그렇지 않으면 32비트 또는 64비트가 지정됩니다. |
| **경로 환경 변수** | 인터프리터에서 검색 경로를 찾는 데 사용하는 환경 변수입니다. Visual Studio는 Python을 시작할 때 변수 값을 변경하여 프로젝트의 검색 경로를 포함하도록 합니다. 일반적으로 이 속성은 `PYTHONPATH`로 설정해야 하지만 일부 인터프리터에서는 다른 값을 사용합니다. |

### <a name="pip-tab"></a>pip 탭

환경에 설치된 패키지를 관리하여 종속성을 비롯한 새 패키지를 검색 및 설치할 수 있습니다. 검색을 수행하면 현재 설치된 패키지 및 [PyPI](https://pypi.python.org)가 필터링됩니다. 검색 상자에 `--user` 또는 `--no-deps` 등의 플래그를 포함하여 `pip install` 명령을 직접 입력할 수도 있습니다.

![Python 환경 pip 탭](media/environments-pip-tab.png)

패키지를 설치하면 파일 시스템에서 환경의 `Lib` 폴더 안에 하위 폴더가 생성됩니다. 예를 들어 `c:\Python36`에 Python 3.6이 설치되어 있는 경우 패키지는 `c:\Python36\Lib`에 설치됩니다. `c:\Program Files\Anaconda3`에 Anaconda3이 설치되어 있는 경우 패키지는 `c:\Program Files\Anaconda3\Lib`에 설치됩니다.

후자의 경우 환경이 파일 시스템의 보호된 영역인 `c:\Program Files`에 있기 때문에 Visual Studio에서 패키지 하위 폴더를 만들 수 있도록 권한이 상승된 `pip install`을 실행해야 합니다. 권한 상승이 요구되는 경우 Visual Studio에서 “이 환경용 패키지를 설치, 업데이트 또는 제거하려면 관리자 권한이 필요할 수 있습니다.” 프롬프트가 표시됩니다.

![패키지 설치를 위한 권한 상승 프롬프트](media/environments-pip-elevate.png)

**지금 권한 상승**은 단일 작업에 대한 관리 권한을 pip에 부여하며, 사용 권한에 대한 운영 체제 프롬프트에도 적용됩니다. **관리자 권한 없이 계속**을 선택하면 패키지 설치가 시도되지만, pip에서 폴더를 만들려고 할 때 실패하고 “오류: ‘C:\Program Files\Anaconda3\Lib\site-packages\png.py’를 만들 수 없습니다. 사용 권한이 거부되었습니다.” 등의 출력이 표시됩니다.

**패키지를 설치하거나 제거할 때 항상 권한 상승**을 선택하면 해당 환경에 대해 대화 상자가 표시되지 않습니다. 대화 상자를 다시 표시하려면 **도구 > 옵션 > Python 도구 > 일반**으로 이동한 다음 **영구적으로 숨겨진 모든 대화 상자 다시 설정** 단추를 선택합니다.

동일한 옵션 탭에서 **항상 관리자로 pip 실행**을 선택하여 모든 환경에 대해 대화 상자를 표시하지 않을 수도 있습니다. [옵션 - 일반 탭](options.md#general-options)을 참조하세요.

### <a name="intellisense-tab"></a>IntelliSense 탭

IntelliSense 완성 데이터베이스의 현재 상태를 보여 줍니다.

![Python 환경 IntelliSense 탭](media/environments-intellisense-tab.png)

데이터베이스에는 모든 환경의 라이브러리에 대한 메타데이터가 포함되며 IntelliSense 속도가 향상되고 메모리 사용량이 줄어듭니다. Visual Studio에서 새 환경을 검색하거나 사용자가 환경을 추가하면 라이브러리 소스 파일을 분석하여 데이터베이스 컴파일을 자동으로 시작합니다. 이 프로세스는 설치된 항목에 따라 1분에서 1시간 또는 그 이상이 소요될 수 있습니다. (예를 들어 Anaconda에는 많은 라이브러리가 함께 제공되며 데이터베이스를 컴파일하는 데 다소 시간이 소요됩니다.) 완료되면 자세한 IntelliSense를 얻게 되며 더 많은 라이브러리를 설치할 때까지 데이터베이스를 다시 새로 고치지 않아도 됩니다(**DB 새로 고침** 단추 사용).

컴파일되지 않은 데이터에 대한 라이브러리는 **!**로 표시되며 환경의 데이터베이스가 완료되지 않은 경우 주 환경 목록에서 데이터베이스 옆에도 **!** 가 표시됩니다.

## <a name="selecting-an-environment-for-a-project"></a>프로젝트에 대한 환경 선택

프로젝트별 환경은 기본 글로벌 환경은 무시하고 프로젝트가 항상 특정 환경에서 실행되도록 합니다. 예를 들어 글로벌 기본 환경이 CPython이지만 프로젝트에 IronPython과 글로벌 환경에 설치되지 않은 특정 라이브러리가 필요한 경우 프로젝트별 환경이 필요합니다.

프로젝트 환경은 솔루션 탐색기에서 Python 환경 노드 아래 나열됩니다. 굵게 표시된 항목은 현재 활성 상태이며, Visual Studio에서 디버깅, 가져오기 및 멤버 완성, 구문 검사 및 환경이 필요한 기타 모든 작업에 사용됩니다.

![프로젝트 환경이 솔루션 탐색기에 표시됨](media/environments-project.png)

프로젝트에 대해 서로 다른 환경을 활성화하려면 해당 환경을 마우스 오른쪽 단추로 클릭하고 **Activate Environment**(환경 활성화)를 선택합니다.

**Python 환경**을 마우스 오른쪽 단추로 클릭하고 **Add/Remove Python Environments...**(Python 환경 추가/제거...)를 선택하여 모든 글로벌 환경을 프로젝트 환경으로 추가할 수 있습니다. 표시된 목록에서 사용자 프로젝트에 사용 가능한 환경을 선택하거나 선택 취소할 수 있습니다.

![Python 환경 추가/제거 대화 상자](media/environments-add-remove.png)

솔루션 탐색기에서 환경을 확장하여 설치된 패키지를 표시할 수도 있습니다(환경이 활성 상태일 때 가져와 코드에서 사용할 수 있음).

![솔루션 탐색기에서 환경에 대한 Python 패키지](media/environments-installed-packages.png)

새 패키지를 설치하려면 환경을 마우스 오른쪽 단추로 클릭하고 **Python 패키지 설치...**를 선택하고 원하는 패키지 이름을 입력합니다. 패키지(및 종속성)은 [Python 패키지 인덱스(PyPI)](https://pypi.python.org/pypi)에서 다운로드하며 여기에서 사용 가능한 패키지의 검색도 가능합니다. Visual Studio의 상태 표시줄 및 출력 창에 설치에 대한 정보가 표시됩니다. 패키지를 제거하려면 마우스 오른쪽 단추로 클릭하고 **제거**를 선택합니다.

> [!Note]
> Python의 패키지 관리 지원은 코어 Python 개발 팀에서 현재 개발 중입니다. 표시된 항목은 정확하지 않을 수 있으며 설치 및 설치 제거가 안정적이지 않거나 사용 가능하지 않을 수 있습니다. Visual Studio는 pip 패키지 관리자(가능한 경우)를 사용하며 필요할 경우 다운로드하여 설치합니다. 또한 Visual Studio는 easy_install 패키지 관리자도 사용할 수 있습니다. 명령줄에서 pip 또는 easy_install을 사용하여 설치된 패키지도 표시됩니다.

> [!Tip]
> pip에서 패키지 설치에 실패하는 일반적인 상황은 패키지가 `*.pyd` 파일에 기본 구성 요소에 대한 소스 코드를 포함하는 경우입니다. 필요한 Visual Studio 버전이 설치되어 있지 않으면 pip에서 해당 구성 요소를 컴파일할 수 없습니다. 이 경우 표시되는 오류 메시지는 `error: Unable to find vcvarsall.bat`입니다. 대체로 `easy_install`은 미리 컴파일된 이진 파일을 다운로드할 수 있으며, [http://aka.ms/VCPython27](http://aka.ms/VCPython27)에서 이전 버전의 Python에 적합한 컴파일러를 다운로드할 수 있습니다. 자세한 내용은 Python 도구 팀 블로그에서 ["vcvarsallbat을 찾을 수 없는" 어려움을 해결하는 방법](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/)(영문)을 참조하세요.

## <a name="creating-virtual-environments"></a>가상 환경 만들기

1. 솔루션 탐색기에서 **Python 환경**을 마우스 오른쪽 단추로 클릭하고 **Add Virtual Environment...**(가상 환경 추가...)를 선택하면 다음이 표시됩니다.

    ![가상 환경 만들기](media/environments-add-virtual-1.png)

1. 프로젝트 경로에 가상 환경을 만들 이름을 지정하고 다른 위치에 만들려면 전체 경로를 지정합니다. (다른 도구와 최대 호환성을 보장하려면 이름에 문자와 숫자만 사용하세요.)

1. 기본 인터프리터로 글로벌 환경을 선택하고 **만들기**를 클릭합니다. `pip` 및 `virtualenv` 또는 `venv` 패키지를 사용할 수 없는 경우 다운로드하여 설치합니다.

    제공된 경로가 기존 가상 환경인 경우 기본 인터프리터가 검색되고 만들기 단추가 **추가**로 변경됩니다.

    ![기존 환경 추가](media/environments-add-virtual-2.png)

솔루션 탐색기에서 **Python 환경**을 마우스 오른쪽 단추로 클릭하거나 **기존 가상 환경 추가...**를 선택하여 기존 가상 환경을 추가할 수도 있습니다. Visual Studio는 환경의 `lib` 디렉터리에서 `orig-prefix.txt` 파일을 사용하여 기본 인터프리터를 검색합니다.

가상 환경이 프로젝트에 추가되면 **Python 환경** 창에 나타나며 다른 환경처럼 프로젝트를 활성화하고 해당 패키지를 관리할 수 있습니다. 마우스 오른쪽 단추로 클릭하고 **제거**를 클릭하면 해당 환경에 대한 참조가 제거되거나 해당 환경 및 디스크의 모든 파일이 삭제됩니다(기본 인터프리터 제외).

가상 환경에 대한 한 가지 단점은 하드 코드된 파일 경로를 포함하므로 다른 개발 컴퓨터와 쉽게 공유하거나 전송할 수 없다는 점입니다. 다행히, 다음 섹션에 설명된 대로 `requirements.txt` 파일을 사용하면 프로젝트의 수신자가 환경을 쉽게 복원할 수 있습니다.

## <a name="managing-required-packages-requirementstxt"></a>필수 패키지(requirements.txt) 관리

빌드 시스템을 사용하여 다른 사람과 프로젝트를 공유하거나 [Microsoft Azure에 게시](template-azure-cloud-service.md)할 계획인 경우 프로젝트에 필요한 외부 패키지를 지정해야 합니다. 권장되는 방법은 필요한 종속 패키지 버전을 설치하는 pip 명령 목록이 들어 있는 [requirements.txt 파일](http://pip.readthedocs.org/en/latest/user_guide.html#requirements-files)(readthedocs.org)을 사용하는 것입니다.

기술적으로, 파일 이름을 사용하여 요구 사항을 추적할 수 있으나(패키지 설치 시 `-r <full path to file>` 사용) Visual Studio에서 `requirements.txt`에 대한 구체적인 지원을 제공합니다.

- `requirements.txt`가 포함된 프로젝트를 로드하여 이 파일에 나열된 모든 패키지를 설치하려면 **솔루션 탐색기**에서 **Python 환경** 노드를 확장한 다음 환경 노드를 마우스 오른쪽 단추로 클릭하고 **requirements.txt에서 설치**를 선택합니다.

    ![requirements.txt에서 설치](media/environments-requirements-txt-install.png)

- 프로젝트에 필요한 모든 패키지가 설치되었으면 솔루션 탐색기에서 환경을 마우스 오른쪽 단추로 클릭하고 **requirements.txt 생성**을 선택하여 필요한 파일을 만듭니다. 파일이 이미 있는 경우 업데이트 방법을 묻는 메시지가 표시됩니다.

    ![requirements.txt 옵션 업데이트](media/environments-requirements-txt-replace.png)

  - **전체 파일 바꾸기**는 존재하는 모든 항목, 주석 및 옵션이 제거됩니다.
  - **기존 항목 새로 고침**은 패키지 요구 사항을 검색하고 버전 지정자를 현재 설치된 버전에 맞게 업데이트합니다.
  - **항목 업데이트 및 추가**는 확인된 요구 사항을 새로 고치고 모든 다른 패키지를 파일 끝에 추가합니다.

`requirements.txt` 파일은 프로젝트의 요구 사항을 동결하기 위해 작성된 것이므로 모든 설치된 패키지가 정확한 버전으로 작성됩니다. 정확한 버전을 사용하면 다른 컴퓨터에서 사용자 환경을 쉽게 재현할 수 있습니다. 패키지는 다른 패키지의 종속성으로 버전 범위로 되거나 pip 이외의 설치 관리자로 설치된 경우에도 포함됩니다.

새 가상 환경을 추가할 때 `requirements.txt` 파일이 존재하면 **가상 환경 추가** 대화 상자에 패키지를 자동으로 설치하는 옵션이 표시되어 다른 컴퓨터에서 환경을 쉽게 다시 만들 수 있습니다.

![requirements.txt로 가상 환경 만들기](media/environments-requirements-txt.png)

pip로 패키지를 설치할 수 없고 `requirements.txt` 파일에 나타나는 경우 전체 설치에 실패합니다. 이 경우 이 패키지를 제외하도록 수동으로 파일을 편집하거나 패키지의 설치 가능한 버전을 참조하도록 [pip의 옵션](http://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format)을 사용합니다. 예를 들어 [`pip wheel`](http://pip.readthedocs.org/en/latest/reference/pip_wheel.html)을 사용하여 종속성을 컴파일하고 `--find-links <path>` 옵션을 사용자의 `requirements.txt`에 추가하는 것이 좋습니다.

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="search-paths"></a>검색 경로

일반적인 Python 사용에서 `PYTHONPATH` 환경 변수(또는 `IRONPYTHONPATH` 등)는 모듈 파일에 대한 기본 검색 경로를 제공합니다. 즉, `from <name> import...` 또는 `import <name>` 문을 사용하는 경우 Python은 다음 위치에서 일치하는 이름을 순서대로 검색합니다.

1. Python의 기본 제공 모듈입니다.
1. 실행 중인 Python 코드를 포함하는 폴더입니다.
1. 적용 가능한 환경 변수에 정의된 “모듈 검색 경로” 입니다. (코어 Python 설명서의 [모듈 검색 경로](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) 및 [환경 변수](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) 참조)

그러나 Visual Studio에서는 변수가 전체 시스템에 대해 설정된 경우에도 검색 경로 환경 변수를 무시합니다. 이렇게 무시되는 이유는 실제로 엄밀히 말해 전체 시스템에 대해 설정되었기 *때문이며* 따라서 자동으로 해결할 수 없는 다음과 같은 특정 질문이 제기됩니다. 참조된 모듈이 Python 2.7 또는 Python 3.3용인가? 이 모듈이 표준 라이브러리 모듈을 재정의하게 되는가? 개발자가 이 동작을 알고 있는가 아니면 악의적인 하이재킹 시도인가?

따라서 Visual Studio에서는 환경 및 프로젝트 모두에서 검색 경로를 직접 지정하는 방법을 제공합니다. Visual Studio에서 실행하거나 디버그하는 코드는 `PYTHONPATH` 값으로 검색 경로(및 기타 동등한 변수)를 받습니다. Visual Studio는 검색 경로를 추가하여 해당 위치의 라이브러리를 검사하고 라이브러리에 대한 IntelliSense 데이터베이스를 빌드합니다(라이브러리 수에 따라 데이터베이스를 구성하는 데 다소 시간이 걸릴 수 있음).

검색 경로를 추가하려면 솔루션 탐색기에서 **검색 경로** 항목을 마우스 오른쪽 단추로 클릭하고 **검색 경로에 폴더 추가...**를 선택하고 포함할 폴더를 선택합니다. 이 경로는 프로젝트와 연결된 환경에 사용됩니다. (환경이 Python 3을 기반으로 하고 Python 2.7 모듈에 검색 경로를 추가하려는 경우 오류가 표시될 수 있습니다.)

`.zip` 또는 `.egg` 확장명이 있는 파일도 **검색 경로에 Zip 보관 파일 추가...**를 선택하여 검색 경로로 추가할 수 있습니다. 폴더와 마찬가지로 이러한 폴더의 내용을 검색하고 IntelliSense에 제공합니다.

정기적으로 동일한 검색 경로를 사용하고 그 내용이 자주 변경되지 않는 경우 site-packages 폴더에 설치하는 것이 더 효율적일 수 있습니다. 검색 경로가 분석되어 IntelliSense 데이터베이스에 저장되며 항상 의도한 환경과 연결되고 각 프로젝트에 대해 검색 경로를 추가할 필요가 없습니다.