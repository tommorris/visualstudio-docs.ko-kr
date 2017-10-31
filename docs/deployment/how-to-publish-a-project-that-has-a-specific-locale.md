---
title: "방법: 특정 로캘이 지정된 프로젝트 게시 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "응용 프로그램 배포[ClickOnce], 지역화된 프로젝트"
  - "로캘, 배포"
  - "로캘, 게시"
  - "매크로, 배포"
  - "매크로, 게시"
  - "지역화된 프로젝트 게시"
  - "게시, 지역화된 프로젝트"
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# 방법: 특정 로캘이 지정된 프로젝트 게시
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

응용 프로그램에 포함된 구성 요소가 서로 다른 로캘을 사용하는 경우를 흔히 볼 수 있습니다.  이러한 시나리오에서는 여러 프로젝트가 포함된 솔루션을 만든 다음 각 로캘에 대해 프로젝트를 별도로 게시합니다.  아래 절차에서는 매크로를 통해 'en' 로캘을 사용하는 솔루션의 첫 번째 프로젝트를 게시하는 방법을 보여줍니다.  'en' 이외의 로캘에 대해 이 절차를 수행하려면 매크로의 `localeString`을 'de' 또는 'de\-DE'와 같이 사용 중인 로캘과 일치하도록 설정합니다.  
  
> [!NOTE]
>  이 매크로를 사용할 때 게시 위치는 올바른 URL 또는 UNC\(범용 명명 규칙\) 공유여야 합니다.  또한 IIS\(인터넷 정보 서비스\)가 컴퓨터에 설치되어 있어야 합니다.  IIS를 설치하려면 **시작** 메뉴에서 **제어판**을 클릭합니다.  **프로그램 추가\/제거**를 두 번 클릭합니다.  **프로그램 추가\/제거**에서 **Windows 구성 요소 추가\/제거**를 클릭합니다.  **Windows 구성 요소 마법사**에서 **구성 요소** 목록의 **IIS\(인터넷 정보 서비스\)** 확인란을 선택합니다.  그런 다음 **마침**을 클릭하여 마법사를 닫습니다.  
  
### 게시 매크로를 만들려면  
  
1.  매크로 탐색기를 열려면 **도구** 메뉴에서 **매크로**를 가리킨 다음 **매크로 탐색기**를 클릭합니다.  
  
2.  새 매크로 모듈을 만듭니다.  매크로 탐색기에서 **MyMacros**를 선택합니다.  **도구** 메뉴에서 **매크로**를 가리킨 다음 **새 매크로 모듈**을 클릭합니다.  모듈 이름을 PublishSpecificCulture로 지정합니다.  
  
3.  매크로 탐색기에서 **MyMacros** 노드를 확장하고 **PublishAllProjects** 모듈을 두 번 클릭하여 열거나 **도구** 메뉴에서 **매크로**를 가리키고 **매크로 IDE**를 클릭합니다.  
  
4.  매크로 IDE에서 모듈의 `Import` 문 뒤에 다음 코드를 추가합니다.  
  
    ```vb#  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certficate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  매크로 IDE를 닫습니다.  포커스가 다시 Visual Studio로 돌아옵니다.  
  
### 특정 로캘에 대한 프로젝트를 게시하려면  
  
1.  Visual Basic Windows 응용 프로그램 프로젝트를 만들려면 **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.  
  
2.  **새 프로젝트** 대화 상자의 **Visual Basic** 노드에서 **Windows 응용 프로그램**을 선택합니다.  프로젝트 이름을 PublishLocales로 지정합니다.  
  
3.  Form1을 클릭합니다.  **속성** 창의 **디자인**에서 **언어** 속성을 **\(기본값\)**에서 **영어**로 변경합니다.  폼의 **텍스트** 속성을 MyForm으로 변경합니다.  
  
     지역화된 리소스 DLL은 필요할 때까지 만들어지지 않습니다.  예를 들어 새 로캘을 지정한 후 폼의 텍스트 또는 해당 컨트롤 중 하나를 변경하면 이러한 DLL이 만들어집니다.  
  
4.  Visual Studio IDE를 사용하여 PublishLocales를 게시합니다.  
  
     **솔루션 탐색기**에서 PublishLocales를 선택합니다.  **프로젝트** 메뉴에서 **속성**을 선택합니다.  프로젝트 디자이너의 **게시** 페이지에서 게시 위치를 http:\/\/localhost\/PublishLocales로 지정하고 **지금 게시**를 클릭합니다.  
  
     게시 웹 페이지가 표시되면 닫습니다.  이 단계에서는 프로젝트를 게시만 하면 되며 설치할 필요는 없습니다.  
  
5.  Visual Studio 명령 프롬프트 창에서 매크로를 호출하여 PublishLocales를 다시 게시합니다.  명령 프롬프트 창을 표시하려면 **보기** 메뉴에서 **다른 창**을 가리킨 다음 **명령 창**을 클릭하거나 Ctrl\+Alt\+A를 누릅니다.  명령 프롬프트 창에 `macros`를 입력하면 자동 완성 기능을 통해 사용 가능한 매크로의 목록이 표시됩니다.  다음 매크로를 선택하고 Enter 키를 누릅니다.  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  게시 프로세스가 정상적으로 완료되면 "PublishLocales\\PublishLocales.vbproj를 게시했습니다.  게시 언어는 'en'입니다."라는 메시지가 표시됩니다. 메시지 상자에서 **확인**을 클릭합니다.  게시 웹 페이지가 표시되면 **설치**를 클릭합니다.  
  
7.  C:\\Inetpub\\wwwroot\\PublishLocales\\en을 확인합니다.  지역화된 리소스 DLL 외에 매니페스트, setup.exe, 게시 웹 페이지 파일 등의 설치된 파일이 표시되어야 합니다.  ClickOnce는 기본적으로 EXE 및 DLL에 대해 .deploy 확장명을 추가합니다. 배포 후에 이 확장명을 제거할 수 있습니다.  
  
## 참고 항목  
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [Macros Development Environment](http://msdn.microsoft.com/ko-kr/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Macro Explorer Window](http://msdn.microsoft.com/ko-kr/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [How to: Edit and Programmatically Create Macros](http://msdn.microsoft.com/ko-kr/6716f820-1feb-48ad-a718-27eb6b473c5a)