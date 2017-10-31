---
title: "색 및 스타일 지정에 대 한 Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e384ea1-4d9e-4307-8884-6e183900732c
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9524ecc3cadef58821fba857de8e82e59eea9b43
ms.openlocfilehash: 93bfad7dc919364770a7d225c09db8b432cf1be0
ms.contentlocale: ko-kr
ms.lasthandoff: 05/04/2017

---
# <a name="colors-and-styling-for-visual-studio"></a>색 및 Visual Studio에 대 한 스타일 지정
## <a name="using-color-in-visual-studio"></a>Visual Studio에서 색을 사용 하 여  
Visual Studio에서 색 뿐 아니라 장식으로의 통신 도구도 주로 사용 됩니다. 색을 최소한으로 사용 하 고을 상황에 대 한 예약 합니다.  
  
-   통신 의미 또는 정보 (예: 플랫폼 또는 언어 한정자)  
  
-   (예: 상태 변경을 나타내는) 관심을 갖게  
  
-   가독성을 개선 하 고 UI를 탐색 하기 위한 이정표 제공  
  
-   원활 하 게 사용할 증가  
  
Visual Studio에서 UI 요소에 색을 할당 하기 위한 몇 가지 옵션이 있습니다. 경우에 따라 그림 하기 어려울 수 있습니다 옵션을 사용 해야 하는 또는 올바르게 사용 하는 방법입니다. 이 항목에는 데 도움이 됩니다.  
  
1.  다른 서비스 및 Visual Studio에서 색을 정의 하는 데 사용 하는 시스템을 이해 합니다.  
  
2.  지정된 된 요소에 대 한 올바른 옵션을 선택 합니다.  
  
3.  선택한 옵션을 올바르게 사용 합니다.  
  
> **참고:** 하드 코드 16 진수, RGB 또는 시스템 색 UI 요소에 없습니다. 서비스를 사용 하 여 색상을 나타내는 튜닝의 유연성을 위해 수 있습니다. 또한 서비스가 없으면 됩니다의 테마 전환 기능을 이용할 수 [VSColor 서비스](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)합니다.
  
### <a name="methods-for-assigning-color-to-visual-studio-interface-elements"></a>Visual Studio 인터페이스 요소에 색을 할당 하기 위한 메서드  
UI 요소에 가장 적합 한 방법을 선택 합니다.  
  
| UI | 메서드 | 무엇 인가요? |  
| --- | --- | --- |  
| 포함 되었는지 또는 독립 실행형 대화 상자. | **시스템 색** | 색 및 UI 요소의 모양을 정의 하는 운영 체제를 허용 하는 시스템 이름 같은 공용 대화 상자 컨트롤입니다. |
| 사용자 지정 하는 UI를 전체 VS 환경과 일치 하도록 해야 하며 공유 토큰의 특별 한 의미가 부여 및 범주와 일치 하는 UI 요소를 해야 합니다. | **일반적인 공유 색** | 특정 UI 요소에 대 한 기존 미리 정의 된 색 토큰 이름 |
| 개별 기능 또는 기능 그룹 이며 유사한 요소에 대 한 공유 색이 없습니다. | **사용자 지정 색** | 영역 관련 되어 있으며이 아니며를 다른 UI와 공유할 수는 색 토큰 이름 |
| 최종 사용자 (예: 텍스트 편집기 또는 디자이너 창 특수화 된) UI 또는 콘텐츠를 사용자 지정할 수 있도록 하려고 합니다. | **최종 사용자 사용자 지정**<br /><br />**(도구 &gt; 옵션 대화 상자)** | "글꼴 및 색" 페이지에 정의 된 설정을 **도구 &gt; 옵션** 대화 또는 UI 기능 중 하나에 특수 페이지입니다. |
| UI HTML에서 제작 해야 합니다. | **Daytona** | 색 및 글꼴 서비스에 액세스 하는 HTML에서 작성 하는 UI를 허용 합니다. |
  
### <a name="visual-studio-themes"></a>Visual Studio 테마  
Visual Studio에는 세 가지 서로 다른 색 테마 기능: 밝게, 어둡게, 및 파란색입니다. 또한 접근성을 위해 설계 된 시스템 수준 색 테마 고대비 모드를 검색 합니다.  
  
사용자의 Visual Studio 처음 사용 하는 동안에 테마를 선택 하 라는 메시지가 나타나면 및으로 이동 하 여 나중에 테마를 전환할 수 있는 **도구 &gt; 옵션 &gt; 환경 &gt; 일반** "색 테마" 드롭 다운 메뉴에서 새 테마를 선택 합니다.  
  
사용자가 여러 고대비 테마 중 하나에 전체 시스템을 전환 하려면 제어판 사용할 수도 있습니다. 사용자가 고대비 테마를 선택 하는 경우 다음 Visual Studio 색 테마 선택기 더 이상 영향을 줍니다 Visual Studio의 색을 있지만 사용자가 고대비 모드를 종료 하는 경우에 대 한 테마 변경 내용이 저장 됩니다. 고대비 모드에 대 한 자세한 내용은 참조 [선택 고대비 색상](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ChoosingHighContrastColors)합니다.
  
### <a name="the-vscolor-service"></a>VSColor 서비스  
Visual Studio UI 요소의 색상 값에 대 한 각 Visual Studio 테마 색 값을 포함 하는 명명 된 항목에 바인딩할 수 있는 VSColor 서비스 라고 하는 환경 색 서비스를 제공 합니다. 이렇게 하면 현재 사용자가 선택한 테마 또는 시스템 고대비 모드를 반영 하기 위해 색을 자동으로 변경 됩니다. 서비스를 이용 모든 색 테마와 관련 된 변경의 구현 한 곳에서 처리 되 고 서비스에서 일반적인 공유 색을 사용 하는 UI를 자동으로 반영 됩니다 이후 버전의 Visual Studio에서 새 테마를 의미 합니다.  
  
### <a name="implementation"></a>구현  
Visual Studio 소스 코드에 토큰 이름 및 각 테마에 대 한 각 색상 값의 목록이 포함 된 여러 가지 패키지 정의 파일에 포함 됩니다. 색 서비스에는 이러한 패키지 정의 파일에 정의 된 VSColors 읽습니다. 이러한 색상 코드 또는 XAML 태그에서 참조 되 고 다음 중 하나를 통해 로드 되는 `IVsUIShell5.GetThemedColor` 메서드 또는 DynamicResource 매핑.  
  
### <a name="system-colors"></a>시스템 색  
공용 컨트롤 기본적으로 시스템 색을 참조합니다. UI가 포함 된 또는 독립 실행형 대화 상자를 만들 때와 같은 시스템 색상을 사용 하도록 하려는 경우에 아무 작업도 수행할 필요가 없습니다.  
  
### <a name="common-shared-colors-in-the-vscolor-service"></a>VSColor 서비스에서 일반적인 공유 색  
인터페이스 요소에는 전체 Visual Studio 환경을 반영 되어야 합니다. 디자인 하 고 UI 구성 요소에 해당 되는 일반적인 공유 색을 다시 사용 하 여 인터페이스에 다른 Visual Studio 인터페이스와 일치 하 고 테마 추가 되거나 업데이트 되 면 색은 자동으로 업데이트를 확인 합니다.  
  
일반적인 공유 색을 사용 하기 전에 확인 올바르게 사용 하는 방법을 이해 해야 합니다. 일반적인 공유 색 잘못 사용 하면 사용자가 일치 하지 않는 하면 당황 스 러, 또는 혼란 스러운 환경이 발생할 수 있습니다.  
  
### <a name="user-customizable-colors"></a>사용자 지정 가능한 색  
참고: [최종 사용자에 대 한 색을 노출 합니다.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)  
  
경우에 따라 코드 편집기 또는 디자인 화면을 만들 때와 같은 UI를 사용자 지정 하려면 최종 사용자 수 있게 합니다. 사용자 지정 가능한 UI 구성 요소에서 발견 되는 **글꼴 및 색** 의 섹션은 **도구 &gt; 옵션** 전경색, 배경색, 또는 둘 다를 변경 하려면 사용자가 선택할 수 있는 대화 상자.  
  
![도구 &gt; 옵션 대화 상자](../../extensibility/ux-guidelines/media/0301-a_toolsoptionsdialog.png "0301-a_ToolsOptionsDialog")<br />도구 &gt; 옵션 대화 상자
  
### <a name="web-ui-colors"></a>웹 UI 색  
Visual Studio online 및 Visual Studio 내에서 사용할 수 있도록 HTML을 사용 하 여 만든 UI 구성 요소에 공통 되 고이 있습니다. 여전히 HTML로 작성 된 UI는 Visual Studio 환경 내에서 실행할 경우 VSColor 서비스를 사용 해야 합니다. Daytona 및 사용 하는 방법에 대 한 정보를 참조 하십시오. [Daytona 웹 UI 및](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_DaytonaAndWebUI)합니다.  
  
##  <a name="BKMK_TheVSColorService"></a>VSColor 서비스  
Visual Studio VSColor 서비스 또는 셸 색 서비스 라고도 하는 환경 색 서비스를 제공 합니다. 이 서비스를 사용 하면 각 테마에 대 한 색을 포함 하는 집합이 이름 / 값 색 UI 요소의 색상 값을 바인딩할 수 있습니다. 색이 자동으로 현재 사용자가 선택한 테마에 맞게 변경 되 고 UI 환경 색 서비스에 바인딩된 있도록 통합 되 새로운 테마 이후 버전의 Visual Studio VSColor 서비스가 모든 UI 요소에 대해 사용 될 해야 합니다.  
  
### <a name="how-the-service-works"></a>서비스의 작동 방식  
환경 색 서비스 UI 구성 요소에 대 한.pkgdef에 정의 된 VSColors 읽습니다. 이러한 VSColors XAML 태그 또는 코드에서 참조 하 고 하나를 통해 로드 되는 `IVsUIShell5.GetThemedColor` 또는 `DynamicResource` 매핑.  
  
![환경 색 서비스 아키텍처](../../extensibility/ux-guidelines/media/0302-a_environmentcolorservicearchitecture.png "0302-a_EnvironmentColorServiceArchitecture")<br />환경 색 서비스 아키텍처
  
### <a name="accessing-the-service"></a>서비스에 액세스
하면 어떤 종류의 색 토큰에 따라 VSColor 서비스를 사용 하는 액세스 및 컴퓨터에 설치 된 코드의 종류에는 여러 가지가 있습니다.  

#### <a name="predefined-environment-colors"></a>미리 정의 된 환경 색  
  
##### <a name="from-native-code"></a>네이티브 코드에서  
셸은 제공에 대 한 액세스를 제공 하는 서비스는 `COLORREF` 색상입니다. 다음은 서비스/인터페이스입니다.  
  
```  
IVsUIShell2::GetVSSysColorEx(VSSYSCOLOR dwSysColIndex, DWORD *pdwRGBval)  
```  
  
파일 VSShell80.idl, 열거형에에서 `__VSSYSCOLOREX` 셸 색 상수 했습니다. 를 사용 하려면에서 값으로 전달 인덱스의 값 중 하나는 `enum __VSSYSCOLOREX` 에 문서화 된 MSDN 또는 일반 인덱스 번호를 Windows 시스템, API `GetSysColor`를 허용 합니다. 이 두 번째 매개 변수에서 사용 해야 하는 색의 RGB 값을 다시 가져옵니다.  
  
해야 펜 또는 새로운 색을 사용 하 여 브러시를 저장 하면 `AdviseBroadcastMessages` (Visual Studio 셸)에서 수신 대기 하 고 `WM_SYSCOLORCHANGE` 및 `WM_THEMECHANGED` 메시지입니다.  
  
  
네이티브 코드에서 색 서비스에 액세스 하려면이 유사한를 호출을 하 합니다. 

```
pUIShell2->GetVSSysColorEx(VSCOLOR_COLOR_NAME, &rgbLOCAL_COLOR);    
```  

> **참고:** 는 `COLORREF` 에서 반환 된 값 `GetVSSysColorEx()` 포함 방금 R, G, 테마 색의 B 구성 요소입니다. 테마 항목에서 투명도 사용 하는 경우 알파 채널 값을 반환 하기 전에 삭제 됩니다. 따라서 원하는 환경 색 투명도 채널은 중요 한 곳에 사용 하는 경우 사용 해야 `IVsUIShell5.GetThemedColor` 대신 `IVsUIShell2::GetVSSysColorEx`이 항목의 뒷부분에 설명 된 대로 합니다.  
  
##### <a name="from-managed-code"></a>관리 코드에서  
네이티브 코드를 통해 VSColor 서비스에 액세스 하는 것은 매우 간단 합니다. 그러나 관리 되는 코드를 통해 작업 하는 경우 서비스를 사용 하는 방법을 결정 까다로울 수 있습니다. 이 점을 염두에서에서이 프로세스는 C# 코드 조각은 다음과 같습니다.  
  
```  
private void VSColorPaint(object sender, System.Windows.Forms.PaintEventArgs e)  
{  
    //getIVSUIShell2  
    IVsUIShell2 uiShell2 = Package.GetService(typeof(SVsUIShell)) as IVsUIShell2;  
    Debug.Assert (uiShell2 != null, "failed to get IVsUIShell2");  
  
    if (uiShell2 != null)  
    {  
        //get the COLORREF structure  
        uint win32Color;  
        uiShell.GetVSSysColorEx(VSSYSCOLOREX.VSCOLOR_SMARTTAG_HOVER_FILL, out win32Color);  
  
        //translate it to a managed Color structure  
        Color myColor = ColorTranslator.FromWin32((int)win32Color);  
        //use it  
        e.Graphics.FillRectangle(new SolidBrush(myColor), 0, 0, 100, 100);  
    }  
}  
```  
  
Visual Basic에서 작업 하는 경우 사용 합니다.  
  
```  
Dim myColor As Color = ColorTranslator.FromWin32((Integer)win32Color)  
```  
  
##### <a name="from-wpf-ui"></a>WPF UI에서  
응용 프로그램의 내보낸 값을 통해 Visual Studio 색에 바인딩할 수 `ResourceDictionary`합니다. 다음은 XAML의 환경 글꼴 데이터를 바인딩할 수 있을 뿐만 아니라 리소스 색상표를 사용 하는 예제입니다.  
  
```  
<Style TargetType="{x:Type Button}">  
    <Setter Property="TextBlock.FontFamily"  
            Value="{DynamicResource VsFont.EnvironmentFontFamily}" />  
    <Setter Property="TextBlock.FontSize"  
            Value="{DynamicResource VsFont.EnvironmentFontSize}" />  
    <Setter Property="Background"  
            Value="{DynamicResource VsBrush.EnvironmentBackgroundGradient}" />  
</Style>  
```  
  
#### <a name="helper-classes-and-methods-for-managed-code"></a>도우미 클래스 및 관리 코드에 대 한 메서드  
관리 코드에서 셸 관리 패키지 프레임 워크 라이브러리에 대 한 (`Microsoft.VisualStudio.Shell.12.0.dll`)에 두 가지 쉽게 테마 색을 사용할 수 있도록 하는 도우미 클래스입니다.  
  
도우미 메서드는 `Microsoft.VisualStudio.Shell.VsColors` MPF 클래스 포함 `GetThemedGDIColor()` 및 `GetThemedWPFColor()`합니다. 이러한 도우미 메서드도 테마 항목의 색 값을 반환 `System.Drawing.Color` 또는 `System.Windows.Media.Color`, WinForms 또는 WPF UI에서 사용할 수 있습니다.  
  
```  
IVsUIShell5 shell5;  
Button button = new Button();  
button.BackColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemBrushKey);  
button.ForeColor = GetThemedGDIColor(shell5, SolutionExplorerColors.SelectedItemTextBrushKey);  
  
/// <summary>  
/// Gets a System.Drawing.Color value from the current theme for the given color key.  
/// </summary>  
/// <param name="vsUIShell">The IVsUIShell5 service, used to get the color's value.</param>  
/// <param name="themeResourceKey">The key to find the color for.</param>  
/// <returns>The current theme's value of the named color.</returns>  
public static System.Drawing.Color GetThemedGDIColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorRgba(vsUIShell, themeResourceKey);  
  
   // Note: The Win32 color we get back from IVsUIShell5.GetThemedColor is ABGR  
   return System.Drawing.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}  
  
private static byte[] GetThemedColorRgba(IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Guid category = themeResourceKey.Category;  
   __THEMEDCOLORTYPE colorType = __THEMEDCOLORTYPE.TCT_Foreground  
   if (themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundColor || themeResourceKey.KeyType == ThemeResourceKeyType.BackgroundBrush)  
   {  
      colorType = __THEMEDCOLORTYPE.TCT_Background;  
   }  
  
   // This call will throw an exception if the color is not found  
   uint rgbaColor = vsUIShell.GetThemedColor(ref category, themeResourceKey.Name, (uint)colorType);  
   return BitConverter.GetBytes(rgbaColor);  
}  
public static System.Windows.Media.Color GetThemedWPFColor(this IVsUIShell5 vsUIShell, ThemeResourceKey themeResourceKey)  
{  
   Validate.IsNotNull(vsUIShell, "vsUIShell");  
   Validate.IsNotNull(themeResourceKey, "themeResourceKey");  
  
   byte[] colorComponents = GetThemedColorComponents(vsUIShell, themeResourceKey);  
  
    return System.Windows.Media.Color.FromArgb(colorComponents[3], colorComponents[0], colorComponents[1], colorComponents[2]);  
}    
```  
  
클래스 수 또한 가져오는 데 사용할 특정된 WPF 색 리소스 키에 대 한 VSCOLOR 식별자 또는 그 반대로 합니다.  
  
```  
public static string GetColorBaseKey(int vsSysColor);  
public static bool TryGetColorIDFromBaseKey(string baseKey, out int vsSysColor);  
```  
  
메서드 `VsColors` 클래스 호출 될 때마다 색 값을 반환 하도록 VSColor 서비스를 쿼리 합니다. 으로 색 값을 얻기 위해 `System.Drawing.Color`, 대신의 메서드를 사용 하는 보다 나은 성능는 `Microsoft.VisualStudio.PlatformUI.VSThemeColor` VSColor 서비스에서 가져온 색상 값을 캐시 하는 클래스입니다. 클래스는 내부적으로 셸에서 브로드캐스트 메시지 이벤트를 구독 하 고 테마 변경 이벤트가 발생할 때 캐시 된 값을 무시 합니다. 또한 제공 하는 클래스는 있습니다. 테마 변경 구독할 NET 친화적인 이벤트입니다. 사용 하 여는 `ThemeChanged` 새 처리기를 추가 하 고 사용 하 여 이벤트를는 `GetThemedColor()` 메서드 색에 대 한 값은 `ThemeResourceKeys` 관심 있는 합니다. 샘플 코드는 다음과 같습니다.  
  
```  
public MyWindowPanel()  
{  
    InitializeComponent();  
  
    // Subscribe to theme changes events so we can refresh the colors  
    VSColorTheme.ThemeChanged += VSColorTheme_ThemeChanged;  
  
    RefreshColors();  
}  
  
private void VSColorTheme_ThemeChanged(ThemeChangedEventArgs e)  
{  
    RefreshColors();  
  
    // Also post a message to all the children so they can apply the current theme appropriately  
    foreach (System.Windows.Forms.Control child in this.Controls)  
    {  
        NativeMethods.SendMessage(child.Handle, e.Message, IntPtr.Zero, IntPtr.Zero);  
    }  
}  
  
private void RefreshColors()  
{  
    this.BackColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowBackgroundColorKey);  
    this.ForeColor = VSColorTheme.GetThemedColor(EnvironmentColors.ToolWindowTextColorKey);  
}  
  
protected override void Dispose(bool disposing)  
{  
    if (disposing)  
    {  
        VSColorTheme.ThemeChanged -= this.VSColorTheme_ThemeChanged;  
        base.Dispose(disposing);}  
}  
```  
  
##  <a name="BKMK_ChoosingHighContrastColors"></a>고대비 색 선택  
  
### <a name="overview"></a>개요  
Windows 더 분명 화면에 표시 되는 요소에 텍스트, 배경 및 이미지의 색상 대비 증가 하는 여러 고대비 시스템 수준 테마를 사용 합니다. 이 액세스 가능성을 위해 사용자가 고대비 테마를 전환할 때 Visual Studio 인터페이스 요소 올바르게 응답 중요 합니다.  
  
시스템 색 중 소수의 쿼리만 고대비 테마의 사용할 수 있습니다. 시스템 색 이름을 선택할 때는 다음 팁을 고려 하세요.  
  
1.  **의미 체계 의미가 동일한 시스템 색 선택** 색 지정 되는 요소와 합니다. 예를 들어, 창 내에서 텍스트에 대 한 고대비 색을 선택할 경우 WindowText 및 하지 ControlText를 사용 합니다.  
  
2.  **전경/배경 쌍을 선택** 함께 또는 모든 고대비 테마의 색 선택을 작동 하는지 확신할 수 없습니다.  
  
3.  **가장 중요 한 UI의 부분을 확인 하 고 콘텐츠 영역 강조 합니다 있는지 확인 합니다.** 에 다양 한 콘텐츠 영역에 대 한 색상 변형이 없는 때문에 강력한 테두리 색을 사용 콘텐츠 영역 정의에 공통적으로 적용 되므로 다양 한 색 색상에 약간의 차이점을 구분 하기 일반적으로 세부 손실 됩니다.  
  
### <a name="system-color-set"></a>시스템 색 집합입니다.  
테이블에 [WPF 팀 블로그: SystemColors 참조](http://blogs.msdn.com/b/wpf/archive/2010/11/30/systemcolors-reference.aspx) 시스템 색 이름 및 각 테마에 표시 된 해당 색상의 전체 집합을 나타냅니다.  
  
UI, 색 집합을 제한이 적용 될 때 *"일반" 테마에 있던 것 미묘한 세부 정보를 잃게 됩니다 것으로 예상*합니다. 도구 창 내에서 영역을 구분 하기 위해 사용 되는 미묘한 회색 색으로 UI의 예를 들면 다음과 같습니다. 고대비 모드에 표시 된 같은 창 쌍을 이루는, 모든 배경이 색조를 영역의 테두리 테두리 단독으로 표시 됩니다를 확인할 수 있습니다.  
  
![어떻게 미묘한 세부 정보의 예제 고대비에서 손실 됩니다.](../../extensibility/ux-guidelines/media/030303-a_propertieswindow.png "030303-a_PropertiesWindow")<br />어떻게 미묘한 세부 정보의 예제 고대비에서 손실 됩니다.
  
#### <a name="choosing-text-colors-in-an-editor"></a>편집기에서 텍스트 색을 선택합니다.  
컬러로 텍스트는 유사 항목 그룹을 쉽게 식별 하기 위해 있도록 하는 등의 의미를 나타내는 데 편집기 또는 디자인 화면에 사용 됩니다. 그러나 고대비 테마의 않아도 텍스트 색이 세 개 이상의 구분할 수 있는 기능이 있습니다. WindowText, GrayText 및 HotTrackText WindowBackground 표면에 사용할 수 있는 유일한 색을입니다. 4 가지 이상의 색을 사용할 수 없으므로 신중 하 게 고대비 모드에 있을 때 표시할 가장 중요 한 차이점을 선택 합니다.  
  
각 고대비 테마에 표시 된 대로 편집기 화면에서 허용 되는 토큰 이름을의 각 색상을 바꿉니다.  
  
![고대비 편집기 비교](../../extensibility/ux-guidelines/media/030303-b_hceditorcomparison.png "030303-b_HCEditorComparison")<br />고대비 편집기 비교
  
파란색 테마의 편집기 화면의 예:  
  
![파란색 테마의 편집기](~/extensibility/ux-guidelines/media/030303-c_editorblue.png "030303-c_EditorBlue")<br />파란색 테마의 편집기
  
![고대비 #1 테마의 편집기](../../extensibility/ux-guidelines/media/030303-d_editorhc1.png "030303-d_EditorHC1")<br />고대비 #1 테마의 편집기
  
### <a name="usage-patterns"></a>사용 패턴
많은 일반적인 UI 요소에 이미 정의 된 고대비 색. 참조할 수 있습니다 이러한 사용 패턴 색 이름이 시스템을 직접 선택할 때 UI 요소는 비슷한 구성 요소와 일치 합니다.  
  
| 시스템 색 | 사용량 |
| --- | --- |
| ActiveCaption | -활성 IDE와 rafted 창 가리키기 및 키를 눌러에 있는 문자 모양의 단추<br />-IDE 및 rafted windows 제목 표시줄 배경<br />기본 상태 표시줄 배경 |
| ActiveCaptionText | -활성 IDE 및 rafted 창의 제목 표시줄 전경 (텍스트 및 문자 모양)<br />-배경색 및 테두리의 단추 가리키기와 해당 키를 눌러 활성 창 |
| Control | -기본값을 제어 하 고 배경, 드롭다운 단추를 포함 하 여 사용 하지 않도록 설정 콤보 상자, 드롭 다운 목록 및 검색<br />--대상 단추 배경을 도킹 하는 중<br />명령 모음 배경<br />도구 창 배경 |
| ControlDark | -IDE 배경<br />메뉴 및 명령 모음 구분 기호<br />명령 모음 테두리<br />메뉴 그림자<br />-도구 창 탭 기본값 및 가리킨 항목 테두리 및 구분 기호<br />-문서 오버플로 단추 배경 잘<br />-도킹 대상 문자 모양의 테두리 |
| ControlDarkDark |-포커스가 없는 선택한 문서 탭 창 |
| ControlLight |-자동 숨기기 탭 테두리<br />-콤보 상자 및 드롭다운 목록 테두리<br />-대상 배경색 및 테두리를 도킹 |
| ControlLightLight | -선택한 포커스가 있는 임시 테두리 |
| ControlText | -콤보 상자 및 드롭다운 목록 문자 모양<br />-도구 창 선택 되지 않은 탭 텍스트 |
| GrayText |-테두리, 드롭 다운 문자 모양, 텍스트 및 메뉴 항목의 텍스트 콤보 상자 및 드롭다운 목록에서 비활성화<br />-비활성화 된 메뉴 텍스트<br />-컨트롤 '검색 옵션' 머리글 텍스트 검색<br />검색 컨트롤 섹션 구분 기호 |
| 하이라이트 | -모든 가리키기 및 누름된 배경, 테두리, 콤보 상자 드롭다운 단추 배경 및 문서 잘 오버플로 단추 테두리를 제외 하 고<br />-선택한 항목 배경 |
| HighlightText | -모든 가리키기 및 (텍스트 및 문자 모양)는 눌린된 foregrounds<br />-포커스가 있는 도구 창 및 문서 탭 창 컨트롤 전경<br />-포커스가 있는 도구 창 제목 표시줄 테두리<br />--임시 탭 포커스가 있는, 선택한 전경<br />가리키기 및 키를 눌러에 문서 잘 오버플로 단추 테두리<br />-선택한 아이콘 테두리|
| HotTrack | -스크롤 막대의 엄지 단추 배경색 및 테두리에 키를 눌러<br />-스크롤 막대 화살표 문자 모양에 키를 눌러 |
| InactiveCaption | -비활성 IDE 및 rafted 창 단추 문자 모양 가리키기<br />-IDE 및 rafted windows 제목 표시줄 배경<br />-사용할 수 없는 검색 컨트롤 배경 |
| InactiveCaptionText | -비활성 IDE 및 rafted windows 제목 표시줄 전경 (텍스트 및 문자 모양)<br />-비활성 창 단추 배경색 및 테두리 가리키기<br />-포커스가 없는 도구 창 단추 배경색 및 테두리<br />-사용할 수 없는 검색 컨트롤 전경 |
| 메뉴 | -드롭 다운 메뉴 배경<br />-Checked 및 사용 안 함 확인 표시 배경 |
| MenuText | -드롭 다운 메뉴 테두리<br />-확인 표시<br />메뉴 문자 모양<br />-드롭 다운 메뉴 텍스트<br />-선택한 아이콘 테두리 |  
| 스크롤 막대 | -스크롤 막대와 스크롤 막대 화살표 배경, 모든 상태 |
| 창 | -자동 숨기기 탭 배경<br />메뉴 모음 및 명령 선반 배경<br />-포커스가 없는 또는 선택 되지 않은 문서 창의 탭 배경 및 열기 및-임시 탭에 대 한 문서 테두리<br />-포커스가 없는 도구 창 제목 표시줄 배경<br />선택한 선택 되지 않은 도구 창 탭 배경 |
| WindowFrame | -IDE 테두리 |
| WindowText | -자동 숨기기 탭 전경<br />-선택한 도구 창 탭 전경<br />-포커스가 없는 문서 창의 탭 및 포커스 없음 또는 선택 하지 않은-임시 탭 전경<br />-트리 보기 기본 전경 및 가리키기 선택 하지 않은 문자 위로<br />도구 창 선택 된 탭 테두리<br />-스크롤 막대의 엄지 단추 배경, 테두리 및 문자 모양 |
  
##  <a name="BKMK_ExposingColorsForEndUsers"></a>최종 사용자에 대 한 색을 노출합니다.  
  
### <a name="overview"></a>개요  
경우에 따라 코드 편집기 또는 디자인 화면을 만들 때와 같은 UI를 사용자 지정 하려면 최종 사용자 수 있게 합니다. 사용 하 여이 작업을 수행 하는 가장 일반적인 방법은는 **도구 &gt; 옵션** 대화 상자. 사용자 지정을 표시 하는 가장 쉬운 방법은 방식은 특수 컨트롤을 필요로 하는 UI의 특수화 된 고도로 있는 경우가 아니면는 **글꼴 및 색** 내에서 페이지는 **환경** 대화 상자의 섹션. 사용자 지정에 대 한 노출 하는 각 요소에 대 한 사용자는 전경색, 배경색, 또는 둘 다 변경 하도록 선택할 수 있습니다.

### <a name="building-a-vspackage-for-your-customizable-colors"></a>에 대 한 색을 사용자 지정할 수 있는 VSPackage를 작성합니다.  
VSPackage는 글꼴 및 색 사용자 지정 범주를 통해 제어 하 고 글꼴 및 색 속성 페이지에서 항목을 표시할 수입니다. 이 메커니즘을 사용할 경우 Vspackage를 구현 해야 합니다는 [IVsFontAndColorDefaultsProvider](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.aspx) 인터페이스와 연결 된 해당 인터페이스입니다.  
  
기본적으로이 메커니즘 모든 기존 항목 및 포함 된 범주를 수정 하려면 사용할 수 있습니다. 그러나 텍스트 편집기 범주 또는 해당 표시 항목을 수정 하려면 사용 하지 해야 합니다. 텍스트 편집기 범주에 대 한 자세한 내용은 참조 하십시오. [글꼴 및 색 개요](https://msdn.microsoft.com/en-us/library/bb165065.aspx)합니다.  
  
를 사용자 지정 범주를 구현 하거나 항목을 표시 하려면 VSPackage 수행 해야 합니다.  
  
-   **만들거나 레지스트리에 범주를 식별 합니다.** 구현에서 IDE의는 **글꼴 및 색** 속성 페이지에서이 정보를 사용 하 여 올바르게 지정된 된 범주를 지 원하는 서비스에 대 한 쿼리 합니다.  
  
-   **만들거나 레지스트리 (선택 사항)의 그룹을 식별 합니다.** 두 개 이상의 범주의 합집합을 나타내는 그룹 정의에 유용할 수 있습니다. 그룹을 정의 하는 경우 IDE 자동으로 병합 하는 하위 범주 고이 배포 그룹 내에서 항목을 표시 합니다.  
  
-   **IDE 지원을 구현 합니다.**  
  
-   **글꼴 및 색 변경 내용을 처리 합니다.**  
  
#### <a name="to-create-or-identify-categories"></a>만들거나 범주를 확인 하려면  
아래에 레지스트리 항목 범주에는 특수 한 유형의 생성 `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<Category\>]` 여기서 `<Category>` 범주의 지역화 되지 않은 이름입니다.
  
두 값을 사용 하 여 레지스트리를 채웁니다.  

| 이름 | 형식 | 데이터 | 설명 |
| --- | --- | --- | --- |
| 범주 | REG_SZ | GUID | 범주를 식별 하기 위해 만든 GUID |
| 패키지 | REG_SZ | GUID | 범주를 지 원하는 VSPackage 서비스의 GUID |
  
 레지스트리에 지정 된 서비스의 구현을 제공 해야 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 해당 범주에 대 한 합니다.  
  
#### <a name="to-create-or-identify-groups"></a>만들거나 그룹 식별  
아래에 레지스트리 항목 범주에는 특수 한 유형의 생성 `[HKLM\SOFTWARE\Microsoft \Visual Studio\\<Visual Studio version\>\FontAndColors\\<group\>]` 여기서 `<group>` 그룹의 지역화 되지 않은 이름입니다.  
  
두 값을 사용 하 여 레지스트리를 채웁니다.

| 이름 | 형식 | 데이터 | 설명 |
|--- | --- | --- | --- |
| 범주 | REG_SZ | GUID | 범주를 식별 하기 위해 만든 GUID |
| 패키지 | REG_SZ | GUID | 범주를 지 원하는 VSPackage 서비스의 GUID |
  
레지스트리에 지정 된 서비스의 구현을 제공 해야 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` 해당 그룹에 대 한 합니다.

![IVsFontAndColorGroup의 구현](../../extensibility/ux-guidelines/media/0304-a_fontandcolorgroup.png "0304-a_FontAndColorGroup")<br />구현`IVsFontAndColorGroup`
  
### <a name="to-implement-ide-support"></a>IDE 지원 기능을 구현 하려면  
구현 [GetObject](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaultsprovider.getobject.aspx)를 반환 하는 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 인터페이스 또는 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` 각 범주에 대 한 IDE에 인터페이스 또는 제공 된 GUID를 그룹화 합니다.  
  
VSPackage 지 원하는 모든 범주에 대해 별도의 인스턴스를 구현 하는 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 인터페이스입니다.  
  
메서드를 통해 구현 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 있는 IDE를 제공 해야 합니다.  
  
-   범주에서 표시 항목 목록  
  
-   표시 항목에 대 한 지역화 가능한 이름  
  
-   범주에 속하는 각 멤버에 대 한 정보를 표시 합니다.  
  
 > **참고:** 모든 범주에는 표시 항목을 하나 이상 포함 해야 합니다.
  
사용 하 여 IDE는 `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` 여러 종류의 합집합을 정의 하는 인터페이스입니다.

구현을 사용 하 여 IDE를 제공합니다.

-   지정된 된 그룹을 구성 하는 범주 목록  
  
-   인스턴스에 대 한 액세스 [IVsFontAndColorDefaults](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolordefaults.aspx) 그룹 내에서 각 범주를 지원 합니다.  
  
-   지역화할 수 있는 그룹 이름  
  
#### <a name="updating-the-ide"></a>IDE를 업데이트합니다.  
IDE 글꼴 및 색 설정에 대 한 정보를 캐시 합니다. 따라서 IDE 글꼴 및 색상 구성의 모든 수정 후 캐시가 최신 상태 인지 확인 한 가장 좋습니다.  
  
통해 수행 되는 캐시를 업데이트 하는 [IvsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 인터페이스를 전역으로 또는만 선택한 항목 수행된 될 수 있습니다.  
  
### <a name="handling-font-and-color-changes"></a>글꼴 및 색 변경 내용 처리  
VSPackage를 표시 하는 텍스트의 색 지정을 올바르게 지원 하려면 VSPackage를 지 원하는 색 지정 서비스 글꼴 및 색 속성 페이지를 통해 사용자가 시작한 변경에 응답 해야 합니다.  
  
이 작업을 수행 하려면 VSPackage 해야 합니다.  
  
-   **IDE에서 생성 된 이벤트를 처리할** 구현 하 여는 [IVsFontAndColorEvents](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.aspx) 인터페이스입니다. IDE 글꼴 및 색 페이지의 사용자 수정 사항에 따라 적절 한 메서드를 호출 합니다. 예를 들어 호출는 [OnFontChanged](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorevents.onfontchanged.aspx) 메서드 새 글꼴을 선택 합니다.  
  
 **OR**  
  
-   **변경 내용에 대 한 IDE를 폴링할**합니다. 시스템 구현를 통해 이렇게 [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) 인터페이스입니다. 지 속성 지원을 위해 주로 있지만 [GetItem](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.getitem.aspx) 메서드 표시 항목에 대 한 글꼴 및 색 정보를 얻을 수 있습니다. 글꼴 및 색 설정에 대 한 자세한 내용은 MSDN 문서를 참조 하십시오. [에 액세스 하는 저장 된 글꼴 및 색 설정](https://msdn.microsoft.com/en-us/library/bb166382.aspx)합니다.  
  
> **참고:** 폴링 결과가 올바른지 하려면 사용 하 여는 [IVsFontAndColorCacheManager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorcachemanager.aspx) 의 검색 메서드를 호출 하기 전에 캐시 플러시 및 업데이트는 필요한 경우를 확인 하는 인터페이스는 [IVsFontAndColorStorage](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivsfontandcolorstorage.aspx) 인터페이스입니다.
  
#### <a name="registering-custom-font-and-color-category-without-implementing-interfaces"></a>인터페이스를 구현 하지 않고 사용자 지정 글꼴 및 색 범주를 등록  
다음 코드 예제에서는 인터페이스를 구현 하지 않고도 색 범주 및 사용자 지정 글꼴을 등록 하는 방법을 보여 줍니다.  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\FontAndColors\CSharp Tool Window]  
"Package"="{F5E7E71D-1401-11D1-883B-0000F87579D2}"  
"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"  
"ToolWindowPackage"="{7259e420-6241-4e0d-b535-5b820671d183}"  
  
    "NameID"=dword:00000064  
```  

이 코드 예제:   
-   `"NameID"` 패키지에 지역화 된 범주 이름의 리소스 ID =
-   `"ToolWindowPackage"` = 패키지 GUID
-   `"Category"="{9FF46859-A47E-47bf-8AC5-EC3DBE69D1FE}"`예로 든 것 이며 실제 값은 구현자에서 제공 하는 새 GUID를 수 있습니다.  
  
### <a name="set-the-font-and-color-property-category-guid"></a>GUID의 글꼴 및 색 속성 범주를 설정 합니다.  
아래의 코드 예제에서는 범주 Guid를 설정 하는 방법을 보여 줍니다.  
  
```  
// m_pView is your IVsTextView  
IVsTextEditorPropertyCategoryContainer spPropCatContainer =  
(IVsTextEditorPropertyCategoryContainer)m_pView;  
if (spPropCatContainer != null)  
{  
IVsTextEditorPropertyContainer spPropContainer;  
Guid GUID_EditPropCategory_View_MasterSettings =  
new Guid("{D1756E7C-B7FD-49a8-B48E-87B14A55655A}");  
hr = spPropCatContainer.GetPropertyCategory(  
ref GUID_EditPropCategory_View_MasterSettings,  
out spPropContainer);  
if(hr == 0)  
{  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_FontCategory,  
catGUID);  
hr =  
spPropContainer.SetProperty(  
VSEDITPROPID.VSEDITPROPID_ViewGeneral_ColorCategory,  
catGUID);  
}  
}  
```  
  
##  <a name="BKMK_DaytonaAndWebUI"></a>Daytona 및 웹 UI  
  
### <a name="overview"></a>개요  
"Daytona"는 Api, 도구 및 사용자가 HTML, CSS 및 JavaScript 다양 한 Visual Studio 또는 f12 키와 같은 호스트에서에서 사용할 수 있는 플러그 인을 만들 수 있도록 하는 서비스의 집합. HTML, CSS 및 JavaScript로 작성 이식 가능한 구성 요소 및 선택적 호스트 관련 구성 요소는 플러그 인으로 구성 됩니다. 각 Daytona 호스트 UI 규칙, 암시적 또는 명시적 플러그 인 해당 환경에 고유한 표시 되기 위해 준수 해야 하는 고유한 집합이 있을 수 있습니다. Visual Studio와 같은 일부 호스트 하는 스타일 시트를 작성 하는 경우 호스트의 시각적 측면 정적으로 대상이 될 수 없습니다 "기본"테마를 변경 하려면 최종 사용자가 허용 합니다. 이 사용 하는 경우 휴대용 플러그 인을 작성 하는 개발자에 게 유용 합니다. 이 웹 Daytona 호스트를 사용 하 여 제대로 테마 및 고대비 모두를 지원 하는 방식으로 Visual Studio에서 UI를 작성 하는 방법을 설명 합니다.  
  
### <a name="daytona-theming-mechanism"></a>Daytona 테마 설정 메커니즘  
Daytona 런타임 UI 규칙을 추출 하는 서비스 집합 및 호스트의 테마 설정 기능을 제공 합니다. 이러한 서비스 플러그 인 자동으로 준수 확인에 호스팅된 환경에 따라 사용자의 시각적 예상 합니다. 이 동작은 세 가지 기본 기능에서 제공 됩니다.  
  
1.  플러그 인의 UI에 CSS 규칙의 집합 적용 및 (예를 들어 HTMLInputElement 및 HTMLButtonElement HTML 컨트롤의 기본 집합이 스타일을 투명 하 게 하는 런타임 삽입 스타일 시트 (plugin.css)  
  
2.  대신 하드 코드 된 테마에 기반 하는 값을 사용 하 여 스타일 UI 요소에 사용할 수 있는 호스트에서 제공한 토큰의 집합은  
  
    -  CSS로 이러한 토큰에 액세스 하기 위한 선언적 구문  
  
    -  JavaScript에서 테마 토큰을 프로그래밍 방식으로 액세스 하기 위한 API  
  
3.  테마 변경 알림  
  
#### <a name="runtime-injected-style-sheet"></a>런타임 삽입 스타일 시트  
스타일을 삽입 하는 호스트와 Daytona 런타임 좌표 시트 테마 플러그 인의 표준 UI 요소를 자동으로입니다. 다음과 같은 개념에 대 한 스타일 지정은 다음과 같습니다.  
  
-   환경 글꼴  
  
-   배경색  
  
-   하이퍼링크  
  
-   양식 컨트롤 (예: `<select>`, `<input>`,`<button>`  
  
-   Tables  
  
-   제목  
  
-   스크롤 막대  
  
이 UI 표준 HTML UI 컨트롤의 전적으로 구성 하는 경우 다음 추가 작업이 필요 하지 않습니다 테마 변경에 제대로 대응 하 고 고대비를 지원 하도록 것을 의미 합니다.  
  
#### <a name="custom-ui"></a>사용자 지정 UI  
거의 모든 중요 한 경우에는 표준 HTML UI 컨트롤 플러그 인에 대 한 전체 환경을 제공 하는 데 충분 한 없게 되 고 사용자 지정 UI를 도입 해야 합니다. 적절 한 글꼴 선택 및 색 사용을 지원 하기 위해 **테마 토큰** 아래에서 설명 하는 JavaScript API를 통해 CSS에서 선언적으로 또는 명령적으로 사용 해야 합니다. Daytona 런타임 테마 변경 및 플러그 인 로드에서 이러한 토큰을 사용 하는 스타일 시트를 업데이트 해 줄 것입니다.  
  
##### <a name="theme-tokens"></a>테마 토큰  
사용할 수 있는 표준 및 호스트 별로 테마 토큰이 모두 합니다. 표준 토큰은 호스트 삽입 및 항상 사용 가능 합니다. 가능한 경우 표준 토큰을 사용 하는 것이 좋습니다. 표준 토큰은 항상 모든 Daytona 호스트에서 제공 하 고 사용 하 여 플러그 인 이식성은 기본적으로. 표준 토큰 집합이 변경 될 수만 새 토큰을 추가 해야 하 고 제거할 수 없음입니다. Visual Studio 2013 버전은 아래에서 설명 합니다.  
  
| 토큰 이름 | 설명 |
| --- | --- |
| `plugin-background-color` | 플러그 인에 대 한 기본 배경색 |
| `plugin-color` | 플러그 인에 대 한 기본 전경색 |
| `plugin-contextmenu-active-color` | 활성화 않은 상황에 맞는 메뉴에 대 한 기본 전경색 선택 (포커스 보유) |
| `plugin-contextmenu-background-color` | 상황에 맞는 메뉴에 대 한 기본 배경색 |
| `plugin-contextmenu-border-color` | 상황에 맞는 메뉴에 대 한 기본 테두리 색 |
| `plugin-contextmenu-color` | 상황에 맞는 메뉴에 대 한 기본 전경색 |
| `plugin-contextmenu-hover-color` | 상황에 맞는 메뉴에 대 한 기본 가리키기 배경색 |
| `plugin-contextmenu-hover-text-color` | 상황에 맞는 메뉴에 대 한 기본 가리키기 전경색 |
| `plugin-contextmenu-icon-checkbox` | 상황에 맞는 메뉴에 대 한 기본 확인란 아이콘 색 |
| `plugin-contextmenu-inactive-text-color` | 활성화 하지 않은 상황에 맞는 메뉴에 대 한 기본 전경색 선택 |
| `plugin-contextmenu-separator-color` | 상황에 맞는 메뉴에 대 한 기본 구분 기호 색 |
| `plugin-font-family` | 플러그 인에 사용할 기본 글꼴 패밀리 |
  
Visual studio에서는 다음 `plugin-font` 환경 글꼴 설정에 따라 토큰:  
  
-   `plugin-font-size`  
  
-   `plugin-font-weight`  
  
-   `plugin-highlight-background-color`  
  
-   `plugin-highlight-color`  
  
-   `plugin-inactive-color` 
  
다음 `plugin-link` 토큰 스타일에 익숙한 `HTMLElements` (하이퍼링크):
  
-   `plugin-link-color`  
  
-   `plugin-link-active-color`  
  
-   `plugin-link-hover-color`  
  
Plugin.css 스타일 스크롤 막대 지원 향상 시키기 위해 다음과 같은 토큰을 사용 하 여 기본적으로 (특히, Visual Studio)의 다양 한 호스트에서 테마:
  
-   `plugin-scrollbar-arrow-color`  
  
-   `plugin-scrollbar-background-color`  
  
-   `plugin-scrollbar-face-color`  
  
다음 `plugin-select` 토큰 스타일 하는 데 사용 되는 `HTMLSelectElement` (콤보 상자 드롭다운):  
  
-   `plugin-select-option-background-color` 
  
-   `plugin-select-option-color`  
  
-   `plugin-select-option-checked-background-color`  
  
-   `plugin-select-option-checked-border-color`  
  
-   `plugin-select-option-checked-foreground-color`  
  
-   `plugin-select-option-hover-background-color`  
  
-   `plugin-select-option-hover-border-color`  
  
-   `plugin-select-option-hover-foreground-color`  
  
-   `plugin-select-border-color`  
  
-   `plugin-select-background-color`  
  
-   `plugin-select-foreground-color`  
  
-   `plugin-select-hover-background-color`  
  
-   `plugin-select-hover-border-color`  
  
-   `plugin-select-hover-foreground-color`  
  
-   `plugin-table-border-color`  
  
-   `plugin-table-header-background-color`  
  
-   `plugin-table-header-color`  
  
-   `plugin-textbox-border-color`  
  
-   `plugin-textbox-background-color`  
  
-   `plugin-textbox-color`  
  
-   `plugin-textbox-disabled-background-color`  
  
-   `plugin-textbox-disabled-border-color`  
  
-   `plugin-textbox-disabled-color`  
  
이러한 토큰에 사용할 *모든* 올바른 기본 테마 및 고대비 지원 하기 위해 다양 한 호스트 설정 했기 때문에 트리 뷰 및 테이블의 경우:  
  
-   `plugin-treeview-content-background-color`  
  
-   `plugin-treeview-content-color` 
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-mouseover-background-color`  
  
-   `plugin-treeview-content-mouseover-color`  
  
-   `plugin-treeview-content-inactive-selected-color`  
  
-   `plugin-treeview-content-selected-background-color`  
  
-   `plugin-treeview-content-selected-border-color`  
  
-   `plugin-treeview-content-selected-color`  
  
##### <a name="host-specific-tokens"></a>호스트 별로 토큰  
토큰의 표준 집합을 지원할 뿐 아니라 호스트는 비표준 토큰을 제공할 수도 있습니다. Visual Studio 호스트 매니페스트의 Visual Studio 관련 섹션에서 테마 토큰 별칭을 지정 하 여 플러그 인을 허용 하 여이 작업을 수행 합니다. 예를 들면 다음과 같습니다.
  
```  
"vs": {  
    "theme_token_aliases": {   
        "diagnostics-host-border": {   
            "category": "f8a8b2a5-dd35-43f6-a382-fd6a61325c22",   
            "key_type": "BackgroundColor",   
            "name": "Border"   
        },   
        ...   
    }   
}    
```  
  
 이 예제에서는 테마 토큰 이라는 `diagnostics-host-border`, 위에서 언급 한 표준 토큰에 동일 하 게 참조할 수 있는 합니다. `category`, `key_type`, 및 `name` 색을 통해 해결 하는 데 사용 되는 `IVsFontAndColorStorage` 인터페이스입니다. 대부분의 경우에서 적절 한 색을 찾을 수는 (함께 `category`, `key_type`, 및 `name` 정보)에 있는 XML 파일에서 `VSCommonContent\themes`합니다. 패키지 구성 가능한 새 색을 소개 하는 경우 동일한이 메커니즘을 사용: 일치는 `category`, `key_type`, 및 `name` 을 사용 하려는 색입니다. 플러그 인 작성자는 가능 하면 표준 토큰을 사용 하도록 시도 하 고만 반드시 필요한 경우 호스트 관련 토큰을 사용 해야 합니다.  
  
##### <a name="using-theme-tokens-in-css"></a>CSS에서 테마 토큰 사용  
 테마 토큰 구체적으로 형식이 지정 된 주석 구문을 통해 참조 됩니다. 토큰 구문 분석 중에 대 한 규칙:  
  
1.  주석 식은 대괄호로 묶어야 합니다 (`[ ]`).  
  
2.  메모, 내에 있지만 식 외부의 모든 공백은 무시 됩니다.  
  
3.  주석 식 대체 속성을 직접 따라야 합니다.  
  
4.  식 내의 모든 선행 또는 후행 공백은 잘립니다.  
  
5.  식 내의 각 토큰 이름 중괄호로 묶어야 합니다 (예를 들어 `{font-family}` 및 `{button-hover-color}`). 그렇지 않으면 리터럴 값으로 처리 됩니다.  
  
 어떻게 토큰 파서 값을 바꿉니다. CSS를 가정 하 고의 예는 `plugin-background-color` 토큰의 값은 `#000` 및 `plugin-font-family` 토큰의 값은 `Verdana`합니다.
  
| 작성 된 CSS | CSS 구문 분석된 | 노트 |  
| --- | --- | --- |
| `background-color: #fff; /*[{plugin-background-color}]*/` | `background-color: #000;` | 기본값은 동적 호스트 관련 값으로 대체 됩니다. |  
| `background-color: #fff; /*   [{plugin-background-color}]   */` | `background-color: #000;` | 식 범위 공백은 무시 됩니다. |  
| `background-color: #fff; /*[   {plugin-background-color}   ]*/` | `background-color: #000;` | 식 내에 선행 및 후행 공백이 잘립니다. |
| `background-color: #fff; /*{plugin-background-color}*/` | `background-color: #fff;` | 식은 대괄호로 묶인 되지 않습니다 및 메모 있으므로 무시 됩니다. |
| `background-color: #fff; /*[plugin-background-color]*/` | `background-color: plugin-background-color;` | 토큰을 중괄호로 묶인 없는 이며 따라서 리터럴 값으로 처리 됩니다. |
| `/*[{plugin-background-color}]*/ background-color: #fff;` | `background-color: #fff;` | 속성 값을 따르지 않는 주석과 있으므로 무시 됩니다. |
| `background-color: #fff;  /*[{plugin-background-color}]*/` | `background-color: #fff;`| *위와 동일* |
| `/*[{plugin-background-color}]*/  background-color: #fff;` | `background-color: #fff;` | *위와 동일* |
| `font-family: Arial, sans-serif; /*[{plugin-font-family}, sans-serif]*/` | `font-family: Verdana, sans-serif;` | 토큰이 바뀌고 리터럴 콘텐츠는 유지 관리 합니다. |
| `background-image: linear-gradient(0% #000, 100% #ccc); /*[linear-gradient(0% #000, 100% {plugin-background-color})]*/` | `background-image: linear-gradient(0% #000, 100% #000);` | *위와 동일* |
  
CSS 파일에 테마 토큰에 포함 된 경우으로 표시 되어야 합니다는 `data-plugin-theme` 특성에 `link` HTML 파일의 요소입니다. 예를 들면 다음과 같습니다.  
  
```  
<link href="default.css" rel="stylesheet" data-plugin-theme="true" />  
```

##### <a name="using-theme-tokens-from-javascript"></a>JavaScript에서 테마 토큰 사용  
사용자 지정 UI 테마가 적용 된 CSS에서 가능한 경우 해야 하는 동안 시나리오가 테마 값 토큰 프로그래밍 방식으로 액세스할 수 있어야 하는 경우. 예를 들어, 사용자 지정 UI에 그릴는 `CanvasElement` 을 css 스타일을 상속 하지 않습니다는 또는를 스타일 시트를 참조 하는으로 동적으로 생성 되 고 해도 상관 없다면 경우는 UI 요소입니다. 시나리오는 Daytona API를 사용 하 여 설정 된 `Plugin.Theme.getValue`합니다. 이 함수는 토큰 이름이 지정 될 때 호스트에서 제공한 테마 값을 반환 합니다.  
  
| 하지 테마 | 테마 |
| --- | --- |
| `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = "#ccc";  surface.fillRect(0, 0, 200, 200);` | `var surface = document.getElementById("surface").getContext("2d");  surface.fillStyle = ("plugin-background-color");  surface.fillRect(0, 0, 200, 200);` |
| `var el = document.createElement("div");  el.style.backgroundColor = "#ccc";` | `var el = document.createElement("div");  el.style.backgroundColor = Plugin.Theme.getValue("plugin-background-color");` |  
  
JavaScript에서 토큰 사용 되는 경우 **업데이트에 응답 하는 테마 변경 이벤트를 처리 해야**합니다. 이 필요 하지 않습니다 CSS에서 선언적으로 사용 되는 테마 토큰에 대 한 Daytona 런타임 플러그 인을 담당 합니다. 테마 이벤트는 다음과 같은 방식으로 처리할 수 있습니다.

**멤버 (단일 처리기)**
```
Plugin.Theme.onchange = function () 
{
    // re-draw dynamic UI here
}
```

**DOM 이벤트 (여러 처리기)**
```
Plugin.Theme.addEventListener("change", function () 
{
    // re-draw dynamic UI here
});
```
  
이 경우에서는 일반적으로 다시 호출할 수는 `Plugin.Theme.getValue` 테마가 변경 될 때 변경 가능성이 테마 토큰의 값으로 이러한 처리기에 있습니다.  
  
##### <a name="standard-token-mapping"></a>표준 토큰 매핑  
토큰은 표준 환경 및 셸 색에 매핑됩니다. 아래 목록 이러한 매핑에 이란의 버전을 제공 합니다.  
  
| 토큰 이름 | VS 매핑 (`EnvironmentColors`) |  
| --- | --- |  
| `plugin-color` | `ToolWindowTextColorKey` |
| `plugin-background-color` | `ToolWindowBackgroundColorKey` |
| `plugin-link-color` | `ControlLinkTextColorKey` |
| `plugin-link-hover-color` | `ControlLinkTextHoverColorKey` |
| `plugin-link-active-color` | `ControlLinkTextPressedColorKey` |
| `plugin-highlight-color` | `HighlightTextColorKey` |
| `plugin-highlight-background-color` | `HighlightColorKey` |
| `plugin-table-header-background-color` | `GridHeadingBackgroundColorKey` |
| `plugin-table-header-color` | `GridHeadingTextColorKey` |
| `plugin-table-border-color` | `GridLineColorKey` |
| `plugin-button-background-color` | `ButtonFaceColorKey` |
| `plugin-button-hover-background-color` | `ButtonHighlightColorKey` | 
| `plugin-button-color` | `ButtonTextColorKey` |
| `plugin-button-border-color` | `ButtonBorderColorKey` |
  
##### <a name="theme-changes"></a>테마 변경  
Visual Studio 호스트 트리거 플러그 인 테마 변경 내용을 때 최종 사용자가 다음 설정을 변경 내용:  
  
**색 테마:**  
  
![색 테마 변경](~/extensibility/ux-guidelines/media/0305-a_colortheme.png "0305-a_ColorTheme")<br />색 테마 변경  
  
**환경 테마:**  
  
![환경 테마 변경](~/extensibility/ux-guidelines/media/0305-b_environmenttheme.png "0305-b_EnvironmentTheme")<br />환경 테마 변경  
  
**운영 체제 테마** (경우에 변경 하 고 고대비에서):  
  
![운영 체제 테마 변경](../../extensibility/ux-guidelines/media/0305-c_ostheme.png "0305-c_OSTheme")<br />운영 체제 테마 변경