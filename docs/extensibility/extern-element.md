---
title: "Extern 요소 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 15
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
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: d4559aa03af16faf955594c3850281e6cf7b4903
ms.contentlocale: ko-kr
ms.lasthandoff: 09/06/2017

---
# <a name="extern-element"></a>Extern 요소
Extern 요소는 컴파일 타임에.vsct 파일에 병합 하려면 외부 헤더 (.h) 파일을 참조 합니다. 병합할 파일은 VSCT 컴파일러에 지정 되거나에 의해 참조 포함 경로에 있어야 합니다.는 [포함 요소](../extensibility/include-element.md)합니다. 다른.vsct 파일 또는 c + + 헤더 파일의 파일 수 있습니다.  
  
 헤더 파일의 정의 양식의 여야 합니다. "#define [Value] [기호]" 값 이전에 정의 되어 있는 경우 다른 기호를 수 있습니다. 정의 명령 항목의 조건문에 사용할 수 있습니다. 실제로 사용 되지 모든 기호는 무시 됩니다.  
  
 CommandTable 요소  
Extern 요소  
  
## <a name="syntax"></a>구문  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|href|필수 요소. 헤더 파일의 경로:<br /><br /> href="stdidcmd.h"|  
|조건|선택 사항입니다. 참조 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)합니다.|  
|language|선택 사항입니다. 모든 기본 언어 [ \<문자열 >](../extensibility/strings-element.md) 명령 테이블의 요소:<br /><br /> 언어 = "en-주세요."|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|없음|없음|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[CommandTable 요소](../extensibility/commandtable-element.md)|모든 명령을 나타내는 요소 정의-메뉴 항목, 메뉴, 도구 모음 및 콤보 상자 즉,-IDE에 VSPackage를 제공 하 합니다.|  
  
## <a name="example"></a>예제  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-  
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>  
    ...  
  <Commands package="guidMyPackage">  
</CommandTable>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블 (합니다. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Vspackage에서 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)