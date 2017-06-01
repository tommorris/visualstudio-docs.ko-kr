---
title: "Visual Studio 배포에 대한 업데이트 제어 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: ko-kr
ms.lasthandoff: 05/09/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>네트워크 기반 Visual Studio 배포에 대한 업데이트 제어

엔터프라이즈 관리자는 때때로 레이아웃을 만들고 최종 사용자에게 배포하기 위해 네트워크 파일 공유에서 레이아웃을 호스트합니다.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Visual Studio가 업데이트를 검색하는 위치 제어
설치가 네트워크 공유에서 배포된 경우에도 기본적으로 Visual Studio에서는 온라인으로 업데이트를 계속 검색합니다. 사용 가능한 업데이트가 있을 경우 사용자는 업데이트를 설치할 수 있습니다. 오프라인 레이아웃에서 찾을 수 없는 모든 업데이트된 콘텐츠는 웹에서 다운로드됩니다.

Visual Studio가 업데이트를 검색하는 위치 및 사용자가 업데이트되는 버전을 직접 제어하려면 다음 단계에 따라 Visual Studio가 업데이트를 검색하는 위치를 수정합니다.

 1. 오프라인 레이아웃을 만듭니다.
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. 레이아웃을 호스트할 파일 공유로 복사합니다.
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. 레이아웃에서 response.json 파일을 수정하고 `channelUri` 값을 변경하여 관리자가 제어하는 channelManifest.json 복사본을 가리킵니다. <b>참고:</b> 다음과 같이 값에서 백슬래시를 이스케이프해야 합니다.
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. 이제 최종 사용자는 이 공유에서 설치 프로그램을 실행하여 Visual Studio를 설치할 수 있습니다.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. 엔터프라이즈 관리자가 사용자가 최신 버전의 Visual Studio로 업데이트할 시점을 결정할 경우 다음과 같은 명령으로 [레이아웃 위치를 업데이트](update-a-network-installation-of-visual-studio.md)하여 업데이트된 파일을 통합할 수 있습니다.
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. 업데이트된 레이아웃의 response.json 파일에 사용자 지정, 특히 channelUri 수정이 포함되어 있는지 확인합니다.
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. 이 레이아웃의 기존 Visual Studio 설치는 `\\server\share\VS2017\ChannelManifest.json`에서 업데이트를 검색하게 됩니다. 이 channelManifest.json이 사용자가 설치한 것보다 최신 버전인 경우 Visual Studio에서는 사용자에게 사용 가능한 업데이트가 있음을 알립니다.
 8. 새로운 설치를 통해 레이아웃에서 직접 Visual Studio의 업데이트된 버전이 자동으로 설치됩니다.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Visual Studio IDE에서 알림 제어
위의 설명 대로 Visual Studio에서는 설치가 시작된 위치(예: 네트워크 공유 또는 인터넷)를 확인하여 사용 가능한 업데이트가 있는지 확인합니다. 사용 가능한 업데이트가 있을 경우 기본적으로 Visual Studio에서는 창의 오른쪽 위에 알림 플래그를 표시하여 사용자에게 알립니다. ![업데이트 알림 플래그](media/notification-flag.png)

최종 사용자에게 업데이트에 대해 알리지 않으려는 경우(예: 중앙 소프트웨어 배포 메커니즘을 통해 업데이트를 제공하는 경우) 이러한 알림을 사용하지 않도록 설정할 수 있습니다.

Visual Studio 2017에서는 [레지스트리 항목을 전용 레지스트리에 저장](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)하므로 레지스트리를 일반적인 방법으로 직접 편집할 수 없습니다. 하지만 Visual Studio에는 Visual Studio 설정을 변경하는 데 사용할 수 있는 명령 `vsregedit.exe`가 포함됩니다. 다음 명령으로 알림을 끌 수 있습니다.

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

위의 명령에서 편집할 설치된 인스턴스와 일치하도록 디렉터리를 바꿉니다. 

> [!TIP]
> [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances)를 사용하여 클라이언트 워크스테이션에서 Visual Studio의 특정 인스턴스를 찾습니다. 

## <a name="see-also"></a>참고 항목
* [Visual Studio 설치](install-visual-studio.md)
* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 인스턴스 관리 도구](tools-for-managing-visual-studio-instances.md)
