---
title: 프로젝트 항목에는 특성을 추가 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65df74335bd6a79941f588f00d2b1c129e4e022c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081382"
---
# <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성을 추가 합니다.
메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 가져오기 및 프로젝트 항목의 특성 값을 설정 합니다. SetItemAttribute 만듭니다 특성 아직 존재 하지 않는 경우 프로젝트 항목 메타 데이터를 추가 합니다.  
  
## <a name="add-an-attribute-to-a-project-item"></a>프로젝트 항목에 특성을 추가 합니다.  
  
-   다음 코드에서는 합니다 <xref:EnvDTE.DTE> 자동화 개체 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> 프로젝트 항목에 특성을 추가 하는 방법입니다. 프로젝트 항목 이름 "program.cs"에서 프로젝트 항목 ID는 가져옵니다. 특성 "MyAttribute"이 프로젝트 항목에 추가 되 고 "MyValue" 값을 지정 합니다.  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>참고자료  
 [MSBuild 프로젝트 파일의 데이터를 유지 합니다.](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)