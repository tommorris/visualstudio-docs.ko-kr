---
title: "도구 모음에 메뉴 컨트롤러 추가 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "도구 모음 [Visual Studio] 메뉴의 컨트롤러 추가"
  - "메뉴, 도구 모음 메뉴 컨트롤러를 추가 합니다."
  - "컨트롤러 메뉴, 도구 모음에 추가"
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# 도구 모음에 메뉴 컨트롤러 추가
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

이 연습은 [도구 창에는 도구 모음 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md) 연습 하 고 도구 창 도구 모음에 메뉴 컨트롤러를 추가 하는 방법을 보여 줍니다. 여기에 나와 있는 단계도 적용할 수에서 만든 도구 모음에는 [도구 모음 추가](../extensibility/adding-a-toolbar.md) 연습 합니다.  
  
 메뉴 컨트롤러 분할 컨트롤입니다. 메뉴 컨트롤러의 왼쪽에는 최근에 사용 된 명령 표시 하 고 클릭 하 여 실행할 수 있습니다. 메뉴 컨트롤러의 오른쪽 화살표입니다를 클릭 하면 추가 명령 목록이 열립니다. 명령이 실행 목록에서 명령을 클릭 하면 메뉴 컨트롤러의 왼쪽에 있는 명령을 대체 시점과 합니다. 이러한 방식으로 메뉴 컨트롤러 목록에서 최근에 사용 된 명령에는 항상 표시 하는 명령 단추 처럼 작동 합니다.  
  
 메뉴 컨트롤러 메뉴에 나타날 수 있지만 도구 모음에 가장 자주 사용 하는.  
  
## 사전 요구 사항  
 Visual Studio 2015를 시작 하면 설치 하지 마십시오 Visual Studio SDK 다운로드 센터에서. Visual Studio 설치 프로그램의 선택적 기능으로 포함 됩니다. 또한 VS SDK를 나중에 설치할 수 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)을 참조하십시오.  
  
## 메뉴 컨트롤러 만들기  
  
#### 메뉴 컨트롤러를 만들려면  
  
1.  에 설명 된 절차에 따라 [도구 창에는 도구 모음 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md) 도구 모음에 있는 도구 창을 만들 수 있습니다.  
  
2.  TWTestCommandPackage.vsct에서 기호 섹션으로 이동 합니다. 이라는 GuidSymbol 요소에 **guidTWTestCommandPackageCmdSet**, 메뉴 컨트롤러, 메뉴 컨트롤러 그룹 및 세 개의 메뉴 항목을 선언 합니다.  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  메뉴 섹션에서 마지막 메뉴 항목 후 메뉴로 메뉴 컨트롤러를 정의 합니다.  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     `TextChanges` 및 `TextIsAnchorCommand` 플래그 마지막 선택한 명령에 맞게 메뉴 컨트롤러를 사용 하도록 설정 하려면 포함 되어야 합니다.  
  
4.  그룹의 마지막 그룹 항목을 다음 섹션 메뉴 컨트롤러 그룹을 추가 합니다.  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     부모 메뉴 컨트롤러를 설정 하 여이 그룹에 배치 하는 모든 명령 메뉴 컨트롤러에 표시 됩니다.`priority` 특성은 생략 하면 기본값인 0으로 설정 하는 메뉴 컨트롤러에서 유일한 그룹 수 있으므로 합니다.  
  
5.  단추 섹션에서 마지막 단추 항목 후에 각 메뉴 항목에 대 한 Button 요소를 추가 합니다.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  이 시점에서 메뉴 컨트롤러 볼 수 있습니다. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 표시 됩니다.  
  
    1.  에 **보기 \/ 다른 창** 메뉴, 열기 **테스트 도구 창**합니다.  
  
    2.  메뉴 컨트롤러 도구 창에서 도구 모음에 표시 됩니다.  
  
    3.  세 가지 가능한 명령을 보려면 메뉴 컨트롤러의 오른쪽에 있는 화살표를 클릭 합니다.  
  
     명령을 클릭 하면 메뉴 컨트롤러의 제목을 해당 명령을 표시 하려면 변경 되는지 확인 합니다. 다음 섹션에서 이러한 명령을 활성화 하는 코드를 추가 합니다.  
  
## 컨트롤러 메뉴 명령 구현  
  
1.  TWTestCommandPackageGuids.cs에서 세 메뉴 항목에 대 한 명령 Id를 기존 명령 Id 뒤에 추가 합니다.  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  TWTestCommand.cs에서 TWTestCommand 클래스의 위쪽에 다음 코드를 추가 합니다.  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  TWTestCommand 생성자에 대 한 마지막 호출 후에 `AddCommand` 메서드를 동일한 처리기를 통해 각 명령에 대 한 이벤트를 라우팅하는 코드를 추가 합니다.  
  
    ```c#  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  확인 된으로 선택한 명령을 표시 하려면 TWTestCommand 클래스에 이벤트 처리기를 추가 합니다.  
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  사용자가 메뉴 컨트롤러에서 명령을 선택 하는 경우 MessageBox를 표시 하는 이벤트 처리기를 추가 합니다.  
  
    ```c#  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## 메뉴 컨트롤러를 테스트합니다.  
  
1.  프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 표시 됩니다.  
  
2.  열기는 **테스트 도구 창** 에 **보기 \/ 다른 창** 메뉴.  
  
     메뉴 컨트롤러 도구 창에서 도구 모음에 나타나고 표시 **MC 항목 1**합니다.  
  
3.  메뉴 컨트롤러 단추 왼쪽의 화살표를 클릭 합니다.  
  
     세 항목의 선택 되 고 해당 아이콘 주위에 강조 표시 상자가 표시 됩니다. 클릭 **MC 항목 3**합니다.  
  
     메시지와 함께 대화 상자가 나타납니다 **메뉴 컨트롤러 항목 3 선택한**합니다. 메시지 메뉴 컨트롤러 단추 텍스트에 해당 하는지 확인 합니다. 메뉴 컨트롤러 단추를 사용 하는 이제 표시 **MC 항목 3**합니다.  
  
## 참고 항목  
 [도구 창에는 도구 모음 추가](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [도구 모음 추가](../extensibility/adding-a-toolbar.md)