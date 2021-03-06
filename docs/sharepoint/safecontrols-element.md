---
title: SafeControls 요소 | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fe8b3c026b7386d89ef04d0a966eccad425f1629
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119898"
---
# <a name="safecontrols-element"></a>SafeControls 요소
  ASPX 컨트롤 및 SharePoint 사이트의 모든 ASPX 페이지에 액세스 하려면 모든 사용자에 대 한 보안 지정 된 웹 파트의 컬렉션입니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소
  
|요소|설명|  
|-------------|-----------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|선택적 요소입니다.<br /><br /> ASPX 컨트롤 또는 SharePoint 사이트의 모든 ASPX 페이지에 액세스 하려면 모든 사용자에 대 한 보안 지정 된 웹 파트를 나타냅니다.|  
  
### <a name="parent-elements"></a>부모 요소
  
|요소|설명|  
|-------------|-----------------|  
|[프로젝트 항목](../sharepoint/projectitem-element.md)|SharePoint 프로젝트 항목을 나타냅니다. 이 요소는 필수 루트 요소에는 *.spdata* 파일.|  
  
## <a name="remarks"></a>설명  
 안전 컨트롤에 대 한 자세한 내용은 참조 하세요. [프로젝트 항목에 패키징 및 배포 정보를 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)합니다.  
  
## <a name="element-information"></a>요소 정보
  
|||  
|-|-|  
|**네임스페이스**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|  
|**유효성 검사 파일**|ProjectItemModelSchema.xsd|  
|**비어 있을 수 있습니다.**|아니요|  
  
## <a name="see-also"></a>참고자료
 [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [프로젝트 항목에 패키징 및 배포 정보를 제공 합니다.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
