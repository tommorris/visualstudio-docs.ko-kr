---
title: "Visual Studio에서 PyLint 사용 | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: 4b22d434b99bdd2648408b9191c5f050589883ae
ms.contentlocale: ko-kr
ms.lasthandoff: 08/14/2017

---

# <a name="using-pylint-to-check-python-code"></a>PyLint를 사용하여 Python 코드 검사

Python 코드의 오류를 검사하고 적절한 Python 코딩 패턴을 권장하며 널리 사용되는 도구인 [PyLint](https://www.pylint.org/)는 Python 프로젝트용 Visual Studio에 통합되어 있습니다.

[솔루션 탐색기]에서 Python 프로젝트를 마우스 오른쪽 단추로 클릭하고 **Python > PyLint 실행...**을 차례로 선택합니다.

![Python 프로젝트의 상황에 맞는 메뉴에 있는 PyLint 명령](media/code-pylint-command.png)

이 명령을 사용하면 활성 환경에 PyLint를 설치하라는 메시지가 표시됩니다(없는 경우).

[오류 목록] 창에 PyLint 경고 및 오류가 표시됩니다.

![PyLint 오류 목록](media/code-pylint-error-list.png)

오류를 두 번 클릭하면 문제가 발생한 소스 코드로 직접 이동합니다.

> [!Tip]
> 모든 PyLint 출력 메시지에 대한 자세한 목록은 [PyLint 기능 참조](https://pylint.readthedocs.io/en/latest/technical_reference/features.html)(영문)를 참조하세요.

## <a name="setting-pylint-command-line-options"></a>PyLint 명령줄 옵션 설정

PyLint 설명서의 [명령줄 옵션](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) 섹션에서는 `.pylintrc` 구성 파일을 통해 PyLint의 동작을 제어하는 방법에 대해 설명합니다. 이러한 파일은 Visual Studio 또는 해당 설정을 적용하려는 범위에 따라 다른 곳에 있는 Python 프로젝트의 루트에 배치할 수 있습니다.

예를 들어 프로젝트에서 `.pylintrc` 파일을 사용하여 이전 이미지에 표시된 “docstring이 없습니다”라는 경고를 표시하지 않으려면 다음 단계를 수행합니다.

1. 명령줄에서 프로젝트 루트(`.pyproj` 파일이 포함된 위치)로 이동하고 다음 명령을 실행하여 주석으로 처리된 구성 파일을 생성합니다.

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. Visual Studio 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭하여 **추가 > 항목 종료 중...**을 선택하고, 새 `.pylintrc` 파일로 이동하여 선택하고 **추가**를 선택합니다.

1. 편집을 위해 작업할 수 있는 다양한 설정이 포함된 파일을 엽니다. 경고를 사용하지 않도록 설정하려면 `[MESSAGES CONTROL]` 섹션을 찾은 다음 해당 섹션에서 `disable` 설정을 찾습니다. 특정 메시지의 긴 문자열이 표시되며, 원하는 경고를 추가할 수 있습니다. 이 예제에서는 `,missing-docstring`을 추가합니다(쉼표로 구분된 기호 포함).

1. `.pylintrc` 파일을 저장하고 PyLint를 다시 실행하여 해당 경고가 표시되지 않는지 확인합니다.
