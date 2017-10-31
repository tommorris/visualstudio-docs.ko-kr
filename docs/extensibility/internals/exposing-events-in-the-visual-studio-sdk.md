---
title: "Visual Studio SDK의에서 이벤트를 노출합니다. | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "노출 되는 이벤트 [Visual Studio]"
  - "이벤트를 노출 하는 자동화 [Visual Studio SDK]"
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Visual Studio SDK의에서 이벤트를 노출합니다.
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있습니다 자동화를 사용 하 여 이벤트 소스입니다. 프로젝트 및 프로젝트 항목에 대 한 이벤트 소스는 것이 좋습니다.  
  
 이벤트에서 자동화 소비자가 검색 되는 <xref:EnvDTE.DTEClass.Events%2A> 개체 또는 <xref:EnvDTE.DTEClass.GetObject%2A> ("EventObjectName"). 환경 호출 `IDispatch::Invoke` 를 사용 하 여는 `DISPATCH_METHOD` 또는 `DISPATCH_PROPERTYGET` 이벤트를 반환 하는 플래그입니다.  
  
 다음 프로세스는 VSPackage 관련 이벤트가 반환 되는 방법을 설명 합니다.  
  
1.  환경을 시작합니다.  
  
2.  모든 Vspackage의 자동화, AutomationEvents 및 AutomationProperties 키 아래의 모든 값 이름이 레지스트리에서 읽고 테이블에 이러한 이름을 저장 합니다.  
  
3.  이 예제에서는 자동화 소비자 호출 `DTE.Events.AutomationProjectsEvents` 또는 `DTE.Events.AutomationProjectItemsEvents`합니다.  
  
4.  환경은 문자열 매개 변수를 찾아 테이블의 해당 VSPackage를 로드 합니다.  
  
5.  환경 호출의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 메서드 이름을 사용 하 여이 예제에서는 AutomationProjectsEvents 또는 AutomationProjectItemsEvents; 호출에 전달 합니다.  
  
6.  VSPackage와 같은 메서드가 있는 루트 개체를 만듭니다 `get_AutomationProjectsEvents` 및 `get_AutomationProjectItemEvents` 다음 개체를 IDispatch 포인터를 반환 합니다.  
  
7.  환경 자동화 호출에 전달 된 이름을 기반으로 적절 한 메서드를 호출 합니다.  
  
8.   `get_` 메서드 둘 다 구현 하는 다른 IDispatch 기반 이벤트 개체를 만듭니다는 `IConnectionPointContainer` 인터페이스 및 `IConnectionPoint` 인터페이스 및 개체에는 IDispatchpointer를 반환 합니다.  
  
 자동화를 사용 하 여 이벤트를 노출 하려면에 응답 해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 레지스트리에 추가 하는 문자열에 대 한 확인 합니다. 기본 프로젝트 샘플에는 문자열은 "BscProjectsEvents" 및 "BscProjectItemsEvents"입니다.  
  
## <a name="registry-entries-from-the-basic-project-sample"></a>기본 프로젝트 샘플에서 레지스트리 항목  
 이 섹션을 레지스트리에 자동화 이벤트 값을 추가 하는 위치를 보여 줍니다.  
  
 [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Packages\\< PkgGUID\>\AutomationEvents]  
  
 "AutomationProjectEvents 개체를 반환 AutomationProjectEvents"=""  
  
 "AutomationProjectItemsEvents 개체를 반환 AutomationProjectItemEvents"=""  
  
|이름|형식|범위|설명|  
|----------|----------|-----------|-----------------|  
|기본값 (@)|REG_SZ|사용 하지 않는|사용 되지 않습니다. 설명서에 대 한 데이터 필드를 사용할 수 있습니다.|  
|AutomationProjectsEvents|REG_SZ|이벤트 개체의 이름입니다.|키 이름에만 그렇습니다. 설명서에 대 한 데이터 필드를 사용할 수 있습니다.<br /><br /> 이 예제에서는 기본 프로젝트 샘플에서 제공 됩니다.|  
|AutomationProjectItemEvents|REG_SZ|이벤트 개체의 이름|키 이름에만 그렇습니다. 설명서에 대 한 데이터 필드를 사용할 수 있습니다.<br /><br /> 이 예제에서는 기본 프로젝트 샘플에서 제공 됩니다.|  
  
 이벤트 개체는 자동화 소비자에 의해 요청 된 경우 메서드를 지 원하는 VSPackage 모든 이벤트에 대 한 루트 개체를 만듭니다. 환경에서 적절 한 호출 `get_` 이 개체 메서드를 호출 합니다. 예를 들어 경우 `DTE.Events.AutomationProjectsEvents` 호출 되는 `get_AutomationProjectsEvents` 루트 개체에는 메서드가 호출 됩니다.  
  
 ![Visual Studio 프로젝트 이벤트](~/extensibility/internals/media/projectevents.gif "ProjectEvents")  
이벤트에 대 한 자동화 모델  
  
 클래스 `CProjectEventsContainer` BscProjectsEvents에 대 한 소스 개체를 나타내는 반면 `CProjectItemsEventsContainer` BscProjectItemsEvents에 대 한 원본 개체를 나타냅니다.  
  
 대부분의 경우 대부분의 이벤트 개체는 필터 개체를 사용 하기 때문에 모든 이벤트 요청에 대해 새 개체를 반환 해야 합니다. 이벤트를 발생 시키는 경우 이벤트 처리기가 호출 되 고 있는지 확인 하려면이 필터를 확인 합니다.  
  
 AutomationEvents.h 및 AutomationEvents.cpp 선언 및 구현이 다음 표에서의 클래스를 포함합니다.  
  
|클래스|설명|  
|-----------|-----------------|  
|`CAutomationEvents`|검색 하는 이벤트 루트 개체를 구현 하는 `DTE.Events` 개체입니다.|  
|`CProjectsEventsContainer` 및 `CProjectItemsEventsContainer`|해당 이벤트를 발생 시키는 이벤트 소스 개체를 구현 합니다.|  
  
 다음 코드 예제에는 이벤트 개체에 대 한 요청에 응답 하는 방법을 보여 줍니다.  
  
```cpp#  
STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
{  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)   
        //Is the requested name our Projects object?  
    {  
        return GetAutomationProjects(ppIDispatch);  
        // Gets our Projects object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        //Is the requested name our ProjectsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectEvents object.  
    }  
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?  
    {  
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
          // Gets our ProjectItemsEvents object.  
    }  
    return E_INVALIDARG;  
}  
```  
  
 위의 코드에서 `g_wszAutomationProjects` 프로젝트 컬렉션 ("FigProjects")의 이름인 `g_wszAutomationProjectsEvents` ("FigProjectsEvents") 및 `g_wszAutomationProjectItemsEvents` ("FigProjectItemEvents")은 프로젝트 이벤트의 이름 및 프로젝트 항목 VSPackage 구현에서 발생 한 이벤트를 합니다.  
  
 이벤트 개체는 같은 중앙 위치에서 검색 되는 `DTE.Events` 개체입니다. 이러한 방식으로 모든 이벤트 개체 그룹화 되어 최종 사용자는 특정 이벤트를 찾으려고 전체 개체 모델을 검색 하지 않아도 되도록 있습니다. 또한 그러면 시스템 수준 이벤트에 대 한 사용자 고유의 코드를 구현 하도록 요구 하는 대신 특정 VSPackage 개체를 제공 됩니다. 그러나 최종 사용자에 게 찾아야에 대 한 이벤트에 `ProjectItem` 인터페이스, 명확 하지 않습니다 즉시 해당 이벤트 개체가 검색 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>   
 [VSSDK 샘플](../../misc/vssdk-samples.md)