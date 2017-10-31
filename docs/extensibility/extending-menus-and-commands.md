---
title: "확장 메뉴 및 명령 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "메뉴, 일반 작업"
  - "Vspackage를 메뉴 작업"
  - ".vsct 파일을 일반 메뉴 작업"
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 49
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 49
---
# 확장 메뉴 및 명령
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

주석은 Visual Studio에 작업 및 프로세스를 추가 하는 방법은 있습니다. 대부분의 경우에서 명령은 메뉴나 도구 모음에 표시 됩니다. VSPackage 프로젝트 템플릿은 매우 기본적인 명령을 구현 하는 방법을 보여 줍니다. 약간 긴 하지만 여전히 기본 구현에 대 한 참조 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)합니다.  
  
 Visual Studio 명령, 메뉴 및 도구 모음에 대 한 자세한 내용은 참조 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)합니다.  
  
 명령, 메뉴 및 도구 모음 VSPackage 프로젝트의 일부인.vsct 파일에 정의 됩니다. Visual Studio IDE 및.vsct 파일에 대 한 정보를 찾을 수 있습니다 [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)합니다.  
  
 다음 항목에는 여러 가지 명령, 메뉴 및 도구 모음을 추가 하는 방법을 설명 합니다.  
  
## 단원 내용  
 [Visual Studio 메뉴 모음에 메뉴를 추가합니다.](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Visual Studio 메뉴 모음 맨 위 메뉴를 추가 하는 방법에 설명 합니다.  
  
 [메뉴 항목에 바인딩 바로 가기 키](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 메뉴 항목에 바로 가기 키 \(예: CTRL \+ 3\)을 추가 하는 방법에 설명 합니다.  
  
 [하위 메뉴에 추가](../extensibility/adding-a-submenu-to-a-menu.md)  
 최상위 메뉴에는 하위 메뉴를 추가 하는 방법에 설명 합니다.  
  
 [하위 메뉴에는 목록에 사용 되는 가장 최근에 추가](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 가장 최근에 사용한 목록에 추가 하는 방법에 설명 합니다.  
  
 [단추의 다시 사용할 수 있는 그룹 만들기](../extensibility/creating-reusable-groups-of-buttons.md)  
 여러 메뉴에 포함 될 수 있도록 명령 항목을 그룹화 하는 방법에 설명 합니다.  
  
 [메뉴 명령에 아이콘 추가](../extensibility/adding-icons-to-menu-commands.md)  
 명령 메뉴와 도구 모음에서 아이콘을 추가 하는 방법을 설명 합니다.  
  
 [메뉴 명령 텍스트를 변경합니다.](../extensibility/changing-the-text-of-a-menu-command.md)  
 사용을 설명는 `TextChanges` 플래그 메뉴 항목을 동적으로 변경 될 수 있도록 합니다.  
  
 [명령의 모양 변경](../extensibility/changing-the-appearance-of-a-command.md)  
 동적으로 사용 하도록 설정 하거나 명령을 사용 하지 않도록 설정 하는 방법에 설명 합니다.  
  
 [사용자 인터페이스 업데이트](../extensibility/updating-the-user-interface.md)  
 최근 변경 내용을 반영 하는 사용자 인터페이스의 업데이트를 적용 하는 방법에 설명 합니다.  
  
 [메뉴 명령 지역화](../extensibility/localizing-menu-commands.md)  
 메뉴 명령을 지역화 하는 방법에 설명 합니다.  
  
## 관련 단원