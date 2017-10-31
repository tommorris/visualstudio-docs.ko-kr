---
title: 'How to: Programmatically Search for an E-Mail Address in Contacts | Microsoft Docs'
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
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
ms.assetid: e973a407-8b94-45c7-acdf-fe330115fb33
caps.latest.revision: 25
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: d4dfba7f395b3ad113ccc2ea205f49d9bbdaed61
ms.contentlocale: ko-kr
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>How to: Programmatically Search for an E-Mail Address in Contacts
  This example searches a contact folder for contacts that have the domain name **example.com** in their e-mail addresses.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Example  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compiling the Code  
 This example requires:  
  
-   Contacts that have the domain name **example.com** in their e-mail addresses (for example, `somebody@example.com`), and that have first names and last names.  
  
## <a name="see-also"></a>See Also  
 [Working with Contact Items](../vsto/working-with-contact-items.md)   
 [How to: Programmatically Send E-Mail](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [How to: Programmatically Access Outlook Contacts](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [How to: Programmatically Add an Entry to Outlook Contacts](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  