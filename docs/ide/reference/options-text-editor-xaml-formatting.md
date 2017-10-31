---
title: "옵션, 텍스트 편집기, XAML, 서식 | Microsoft 문서"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.XAML.Miscellaneous
- VS.ToolsOptionsPages.Text_Editor.XAML.Formatting.Spacing
helpviewer_keywords:
- element spacing, XAML view settings
- attribute spacing, XAML view settings
- XAML view settings, auto-formatting events
- auto-formatting events, XAML view settings
- XAML view settings, tag wrapping
- XAML view settings, auto insert
- quotation mark style, XAML view settings
- XAML formatting, WPF Designer
- XAML view settings, Toolbox
- XAML view settings, element spacing
- default view, XAML view settings
- auto insert, XAML view settings
- XAML view settings, default view
- XAML view settings, quotation mark style
- tag wrapping, XAML view settings
- WPF Designer, XAML formatting
- XAML view settings, attribute spacing
ms.assetid: ad3820b1-0d94-4807-a74c-c3467ed973a2
caps.latest.revision: 15
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 0d087d735f3db1f1d8fa7f37f049b6208e5242c0
ms.contentlocale: ko-kr
ms.lasthandoff: 05/30/2017

---
# 옵션, 텍스트 편집기, XAML, 서식
<a id="options-text-editor-xaml-formatting" class="xliff"></a>
**서식** 속성 페이지를 사용하여 XAML 문서에서 요소와 특성의 형식 지정 방법을 지정할 수 있습니다. **옵션** 대화 상자를 열려면 **도구** 메뉴를 클릭한 후 **옵션**을 클릭합니다. **서식** 속성 페이지에 액세스하려면 **텍스트 편집기**, **XAML**, **서식** 노드를 확장합니다.  

> [!NOTE]
>  표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.  

## 자동 서식 지정 이벤트
<a id="auto-formatting-events" class="xliff"></a>  
 다음 이벤트가 검색되면 자동 서식 지정이 실행될 수 있습니다.  

-   끝 태그 또는 단순 태그의 완료.  

-   시작 태그의 완료.  

-   클립보드에서 붙여넣기.  

-   서식 키보드 명령.  

 자동 서식 지정을 일으키는 이벤트를 지정할 수 있습니다.  

|||  
|-|-|  
|**끝 태그 또는 간단한 태그 완료 시**|끝 태그 또는 단순 태그 입력을 완료할 때 자동 서식 지정이 실행됩니다. 단순 태그에는 특성이 없습니다(예: `<Button />`).|  
|**시작 태그 완료 시**|시작 태그 입력을 완료할 때 자동 서식 지정이 실행됩니다.|  
|**클립보드에서 붙여 넣을 때**|클립보드에서 XAML 보기로 XAML을 붙여넣을 때 자동 서식 지정이 실행됩니다.|  

## 따옴표 스타일
<a id="quotation-mark-style" class="xliff"></a>  
 이 설정은 특성 값을 작은따옴표 또는 큰따옴표로 묶을지 여부를 나타냅니다. 자동 포맷터 및 IntelliSense의 자동 완성에 이 설정이 사용됩니다.  

 이 옵션을 설정하면 디자이너를 사용하거나 XAML 뷰에서 수동으로 이후에 추가된 특성만 영향을 받습니다.  

|||  
|-|-|  
|**큰따옴표(")**|특성 값을 큰따옴표로 묶습니다.<br /><br /> `<Button Name="button1">Hello</Button>`|  
|**작은따옴표(')**|특성 값을 작은따옴표로 묶습니다.<br /><br /> `<Button Name='button1'>Hello</Button>`|  

## 태그 줄 바꿈
<a id="tag-wrapping" class="xliff"></a>  
 태그 줄 바꿈을 위해 줄 길이를 지정할 수 있습니다. 태그 줄 바꿈을 사용하도록 설정하면 디자이너를 사용하여 이후에 추가된 XAML이 이에 따라 래핑됩니다.  

|||  
|-|-|  
|**지정한 길이를 초과할 때 태그 줄 바꿈**|**길이**에 의해 지정된 줄 길이에서 줄 바꿈할지 지정합니다.|  
|**길이**|줄에 포함할 수 있는 문자 수입니다. 필요한 경우 일부 XAML 줄이 지정된 줄 길이를 초과할 수 있습니다.|  

## 특성 간격
<a id="attribute-spacing" class="xliff"></a>  
 이 설정을 사용하여 XAML 문서에서 특성 정렬 방식을 제어합니다.  

|||  
|-|-|  
|**특성 간에 줄 바꿈과 공간 유지**|자동 서식 지정은 특성 간의 새 줄 및 공백에 영향을 미치지 않습니다.<br /><br /> `<Button Height="23"   Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**특성 간에 단일 공백 삽입**|특성에 한 줄이 사용되고 인접 특성은 하나의 공백으로 구분됩니다. 태그 줄 바꿈 설정이 적용됩니다.<br /><br /> `<Button Height="23" Name="button1" Width="75">Hello</Button>`|  
|**한 줄에 하나의 특성 배치**|각 특성에는 각각의 줄이 사용됩니다. 이 설정은 많은 특성이 있을 경우 유용합니다.<br /><br /> `<Button`<br /><br /> `Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  
|**첫 번째 특성을 시작 태그와 같은 줄에 배치**|이 설정을 선택하면 첫 번째 특성이 요소의 시작 태그와 같은 줄에 표시됩니다.<br /><br /> `<Button Height="23"`<br /><br /> `Name="button1"`<br /><br /> `Width="75">Hello</Button>`|  

## 요소 간격
<a id="element-spacing" class="xliff"></a>  
 이 설정을 사용하여 XAML 문서에서 요소 정렬 방식을 제어합니다.  

|||  
|-|-|  
|**콘텐츠의 줄 바꿈 유지**|요소 콘텐츠의 빈 줄이 제거되지 않습니다.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**콘텐츠의 여러 빈 줄을 한 줄로 축소**|요소 콘텐츠의 빈 줄이 한 줄로 축소됩니다.<br /><br /> `<Grid>`<br /><br /> ``<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> ``<br /><br /> `</Grid>`|  
|**콘텐츠에서 빈 줄 제거**|요소 콘텐츠의 모든 빈 줄이 제거됩니다.<br /><br /> `<Grid>`<br /><br /> `<Button Name="button1">Hello</Button>`<br /><br /> `</Grid>`|  

## 기타 섹션, 자동 삽입
<a id="miscellaneous-section-auto-insert" class="xliff"></a>  
 이 설정을 사용하여 태그 및 따옴표가 자동으로 생성되는 경우를 제어합니다.  

|||  
|-|-|  
|**닫는 태그**|보다 큼 문자(>)로 여는 태그를 닫을 때 요소의 닫는 태그를 자동으로 생성할지 지정합니다.|  
|**특성 따옴표**|문 완성 드롭다운 목록에서 특성 값을 선택할 때 묶는 따옴표를 생성할지 지정합니다.|  
|**MarkupExtensions의 닫는 중괄호**|여는 중괄호 문자({)를 입력할 때 태그 확장의 닫는 중괄호(})를 자동으로 생성할지 지정합니다.|  
|**MarkupExtension 매개 변수를 구분하는 쉼표**|태그 확장에 둘 이상의 매개 변수를 입력할 때 쉼표를 생성할지 지정합니다.|  

## 참고 항목
<a id="see-also" class="xliff"></a>  
 [WPF의 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)   
 [방법: XAML 뷰 설정 변경](http://msdn.microsoft.com/en-us/aee87c79-ca01-4f84-8fb7-a9e47048ee47)   
 [XAML 및 코드 연습](http://msdn.microsoft.com/en-us/b3ff41a0-a2a3-4f61-b698-ac88ec8f799c)
