---
title: "도구 상자, HTML 탭 | Microsoft 문서"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 13
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
ms.sourcegitcommit: d2f4eba36e9069a35cf279ccf1c78f72a51d77a1
ms.openlocfilehash: bc243e4d5ec1141244314109aa76fef86287d1c1
ms.contentlocale: ko-kr
ms.lasthandoff: 06/23/2017

---
# <a name="toolbox-html-tab"></a>도구 상자, HTML 탭
도구 상자의 **HTML** 탭에서는 웹 페이지와 Web Forms에서 유용한 구성 요소를 제공합니다. 이 탭을 보려면 먼저 HTML 디자이너에서 편집할 문서를 엽니다. **보기** 메뉴에서 **도구 상자**를 클릭하고 도구 상자의 **HTML** 탭을 클릭합니다.  

 **HTML** 탭에서 도구 인스턴스를 만들려면 도구를 두 번 클릭하여 현재 삽입 지점에 있는 문서에 추가하거나 도구를 선택하고 편집 화면의 원하는 위치로 끌어다 놓습니다.  

## <a name="tasks"></a>작업  

-   [도구 상자 사용](../../ide/using-the-toolbox.md)  

## <a name="ui-elements"></a>UI 요소  
 다음 도구는 [HTML] 탭에서 기본적으로 사용할 수 있습니다.  

 **포인터**  
 ![ASP.NET 모바일 디자이너 HTMLpage 포인터](~/ide/reference/media/vxpointer.gif "vxPointer")  

 [도구 상자] 탭이 열리면 이 도구가 기본적으로 선택됩니다. 이 도구는 삭제할 수 없습니다. 포인터를 사용하여 개체를 디자인 보기 화면에 끌어다 놓고, 크기를 조정하고, 페이지 또는 양식에서 위치를 변경합니다. 자세한 내용은 [도구 상자 사용](../../ide/using-the-toolbox.md)을 참조하세요.  

 **Input (Button)**  
 ![HTML 웹 페이지 단추](~/ide/reference/media/vxbutton.gif "vxButton")  

 `type="button"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Button1"`은 첫 번째 단추로 삽입되고, `id="Button2"`는 두 번째 단추로 삽입되는 식으로 항목이 삽입됩니다.  

 **Input (Button)**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  

 **Input (Reset)**  
 ![HTMLpageResetButton 스크린샷](~/ide/reference/media/vxreset.gif "vxReset")  

 `type="reset"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Reset1"`은 첫 번째 다시 설정 단추로 삽입되고, `id="Reset2"`는 두 번째 다시 설정 단추로 삽입되는 식으로 항목이 삽입됩니다.  

 **Input (Reset)**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  

 **Input (Submit)**  
 ![HTMLpageToolbarSubmitButton 스크린샷](~/ide/reference/media/vxsubmit.gif "vxSubmit")  

 `type="submit"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Submit1"`은 첫 번째 제출 단추로 삽입되고, `id="Submit2"`는 두 번째 제출 단추로 삽입되는 식으로 항목이 삽입됩니다.  

 **Input (Submit)**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  

 **Input (Text)**  
 ![HTMLpageToolbarTextField 스크린샷](~/ide/reference/media/vxtextfield.gif "vxTextfield")  

 `type="text"`의 `input` 요소를 문서에 삽입합니다. 표시되는 기본 텍스트를 변경하려면 `value` 특성을 편집합니다. 기본적으로 `id="Text1"`은 첫 번째 텍스트 필드로 삽입되고, `id="Text2"`는 두 번째 텍스트 필드로 삽입되는 식으로 항목이 삽입됩니다.  

 **Input (Text)**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  

> [!IMPORTANT]
>  모든 사용자 입력의 유효성을 검사하는 것이 좋습니다. 자세한 내용은 [Validating User Input in ASP.NET Web Pages (Razor) Sites](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)(ASP.NET 웹 페이지(Razor) 사이트에서 사용자 입력 유효성 검사)를 참조하세요.  

 **Input (File)**  
 ![HTML 페이지 파일 필드](~/ide/reference/media/vxfilefield.gif "vxFilefield")  

 `type="file"`의 `input` 요소를 문서에 삽입합니다. 기본적으로 `id="File1"`은 첫 번째 파일 필드로 삽입되고, `id="File2"`는 두 번째 파일 필드로 삽입되는 식으로 항목이 삽입됩니다.  

 **Input (File)**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<input id="File1" type="file" name="File1">  
```  

> [!IMPORTANT]
>  모든 사용자 입력의 유효성을 검사하는 것이 좋습니다. 자세한 내용은 [Validating User Input in ASP.NET Web Pages (Razor) Sites](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)(ASP.NET 웹 페이지(Razor) 사이트에서 사용자 입력 유효성 검사)를 참조하세요.  

 **Input (Password)**  
 ![Visual Studio 암호 필드](~/ide/reference/media/vxpassword.gif "vxPassword")  

 `type="password"`의 `input` 요소를 삽입합니다. 기본적으로 `id="Password1"`은 첫 번째 암호 필드로 삽입되고, `id="Password2"`는 두 번째 암호 필드로 삽입되는 식으로 항목이 삽입됩니다.  

 **Input (Password)**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<input id="Password1" type="password" name="Password1">  
```  

> [!IMPORTANT]
>  응용 프로그램에서 사용자 이름과 암호를 전송할 경우 SSL(Secure Sockets Layer)을 사용하여 전송을 암호화하도록 웹 사이트를 구성해야 합니다. 자세한 내용은 [IIS Operations Guide](http://go.microsoft.com/fwlink/?linkid=47856)(IIS 작업 가이드)에서 "Securing Connections with SSL(SSL을 사용하여 연결 보호)"을 참조하세요. 또한 모든 사용자 입력의 유효성을 검사하는 것이 좋습니다. 자세한 내용은 [Validating User Input in ASP.NET Web Pages (Razor) Sites](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)(ASP.NET 웹 페이지(Razor) 사이트에서 사용자 입력 유효성 검사)를 참조하세요.  

 **Input (Check box)**  
 ![HTML 웹 페이지 도구 상자 확인란 옵션](~/ide/reference/media/vxcheckbox.gif "vxCheckbox")  

 `type="checkbox"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Checkbox1"`은 첫 번째 확인란으로 삽입되고, `id="Checkbox2"`는 두 번째 확인란으로 삽입되는 식으로 항목이 삽입됩니다.  

 **Input (Check box)**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  

 **Input (Radio)**  
 ![VisualStudioHTMLpageRadioButton 스크린샷](~/ide/reference/media/vxradio.gif "vxRadio")  

 `type="radio"`의 `input` 요소를 삽입합니다. 표시되는 텍스트를 변경하려면 `name` 속성을 편집합니다. 기본적으로 `id="Radio1"`은 첫 번째 라디오 단추로 삽입되고, `id="Radio2"`는 두 번째 라디오 단추로 삽입되는 식으로 항목이 삽입됩니다.  

 **Input (Radio)**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<input id="Radio1" type="radio" name="Radio1">  
```  

 **Input (Hidden)**  
 ![HTML 페이지 숨겨진 항목](~/ide/reference/media/vxhidden.gif "vxhidden")  

 `type="hidden"`의 `input` 요소를 삽입합니다. 기본적으로 `id="Hidden1"`은 첫 번째 숨겨진 필드로 삽입되고, `id="Hidden2"`는 두 번째 숨겨진 필드로 삽입되는 식으로 항목이 삽입됩니다.  

 **Input (Hidden)**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  

 **Textarea**  
 ![HTMLpage 도구 모음 텍스트 영역](~/ide/reference/media/vxtextarea.gif "vxTextarea")  

 `textarea` 요소를 삽입합니다. 텍스트 영역의 크기를 조정하거나, 스크롤 막대를 사용하여 표시 영역을 벗어나는 텍스트를 볼 수 있습니다. 표시되는 기본 텍스트를 변경하려면 `value` 특성을 편집합니다. 기본적으로 `id="textarea1"`은 첫 번째 텍스트 영역으로 삽입되고, `id=" textarea 2"`는 두 번째 텍스트 영역으로 삽입되는 식으로 항목이 삽입됩니다.  

 **Textarea**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  

> [!IMPORTANT]
>  모든 사용자 입력의 유효성을 검사하는 것이 좋습니다. 자세한 내용은 [Validating User Input in ASP.NET Web Pages (Razor) Sites](https://docs.microsoft.com/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)(ASP.NET 웹 페이지(Razor) 사이트에서 사용자 입력 유효성 검사)를 참조하세요.  

 **Table**  
 ![HTMLpageToolbarTable 스크린샷](~/ide/reference/media/vxtable.gif "vxTable")  

 `table` 요소를 삽입합니다.  

 **Table**을 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  

**Image**  
 ![HTML 페이지 이미지 항목](~/ide/reference/media/vximage.gif "vxImage")  

 `img` 요소를 삽입합니다. 이 요소를 편집하여 해당 `src` 및 `alt` 텍스트를 지정합니다.  

 **Image**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<img alt="" src="">  
```  

 **선택**  
 ![HTML 페이지 도구 상자 드롭다운](~/ide/reference/media/vxdropdown.gif "vxDropdown")  

 `select` 요소를 삽입합니다(`size` 특성 없음). 기본적으로 `id="select1"`은 첫 번째 목록 상자로 삽입되고, `id="select2"`는 두 번째 목록 상자로 삽입되는 식으로 항목이 삽입됩니다.  

 **Select**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<select id="select1" name="select1"><option selected></option></select>  
```  

 size 속성 값을 늘려 여러 줄 `select` 요소를 만들 수 있습니다.  

 **Horizontal Rule**  
 ![HTML 페이지 가로줄 항목](~/ide/reference/media/vxhorizontal.gif "vxHorizontal")  

 `hr` 요소를 삽입합니다. 줄 두께를 늘리려면 `size` 특성을 편집합니다.  

 **Horizontal Rule**을 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<hr width="100%" size=1>   
```  

 **Div**  
 ![HTML 페이지 레이블](~/ide/reference/media/vxlabel.gif "vxLabel")  

 `ms_positioning="FlowLayout"` 특성을 포함하는 `div` 요소를 삽입합니다. 너비 및 높이를 제외하고 이 항목은 선형 레이아웃 패널과 동일합니다. `div` 요소 내에 포함된 텍스트의 서식을 지정하려면 `class="stylename"` 특성을 여는 태그에 추가합니다.  

 **Div**를 디자인 보기 화면으로 끌어다 놓으면 다음과 같은 HTML 태그가 문서에 삽입됩니다.  

```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  

## <a name="see-also"></a>참고 항목  
 [도구 상자](../../ide/reference/toolbox.md)   
 [도구 상자 사용](../../ide/using-the-toolbox.md)   
