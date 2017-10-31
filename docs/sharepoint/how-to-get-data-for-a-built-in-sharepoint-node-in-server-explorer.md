---
title: 'How to: Get Data for a Built-In SharePoint Node in Server Explorer | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: 7
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 962250192868c710cfbe40e69b44eeb348a696f9
ms.contentlocale: ko-kr
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>How to: Get Data for a Built-In SharePoint Node in Server Explorer
  For each built-in SharePoint node in **Server Explorer**, you can get data for the underlying SharePoint component that the node represents. For more information, see [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Example  
 The following code example demonstrates how to get data for the underlying SharePoint list that a list node represents in **Server Explorer**. By default, list nodes have a **View in Browser** context menu item that you can click to open the lists in a Web browser. This example extends list nodes by adding a **View in Visual Studio** context menu item that opens the lists directly in Visual Studio. The code accesses the list data for the node to get the URL of the list to open in Visual Studio.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)] [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 This example uses the SharePoint project service to obtain the <xref:EnvDTE.DTE> object that is used to open lists in Visual Studio. For more information about the SharePoint project service, see [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 For more information about the basic tasks to create an extension for a SharePoint node, see [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compiling-the-code"></a>Compiling the Code  
 This example requires references to the following assemblies:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Deploying the Extension  
 To deploy the **Server Explorer** extension, create a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) package for the assembly and any other files that you want to distribute with the extension. For more information, see [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>See Also  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  