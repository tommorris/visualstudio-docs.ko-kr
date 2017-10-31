---
title: 'CA2112: Secured types should not expose fields | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
manager: wpickett
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
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: b57c27397fc28536aade5bb5907a0b8d6ad28aab
ms.contentlocale: ko-kr
ms.lasthandoff: 08/30/2017

---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: Secured types should not expose fields
|||  
|-|-|  
|TypeName|SecuredTypesShouldNotExposeFields|  
|CheckId|CA2112|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A public or protected type contains public fields and is secured by a [Link Demands](/dotnet/framework/misc/link-demands).  
  
## <a name="rule-description"></a>Rule Description  
 If code has access to an instance of a type that is secured by a link demand, the code does not have to satisfy the link demand to access the type's fields.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, make the fields nonpublic and add public properties or methods that return the field data. LinkDemand security checks on types protect access to the type's properties and methods. However, code access security does not apply to fields.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Both for security issues and for good design, you should fix violations by making the public fields nonpublic. You can suppress a warning from this rule if the field does not hold information that should remain secured, and you do not rely on the contents of the field.  
  
## <a name="example"></a>Example  
 The following example is composed of a library type (`SecuredTypeWithFields`) with unsecured fields, a type (`Distributor`) that can create instances of the library type and mistaken passes instances to types do not have permission to create them, and application code that can read an instance's fields even though it does not have the permission that secures the type.  
  
 The following library code violates the rule.  
  
 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]  
  
## <a name="example"></a>Example  
 The application cannot create an instance because of the link demand that protects the secured type. The following class enables the application to obtain an instance of the secured type.  
  
 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]  
  
## <a name="example"></a>Example  
 The following application illustrates how, without permission to access a secured type's methods, code can access its fields.  
  
 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]  
  
 This example produces the following output.  
  
 **Creating an instance of SecuredTypeWithFields.**  
**Secured type fields: 22, 33**  
**Changing secured type's field...**  
**Cached Object fields: 99, 33**   
## <a name="related-rules"></a>Related Rules  
 [CA1051: Do not declare visible instance fields](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## <a name="see-also"></a>See Also  
 [Link Demands](/dotnet/framework/misc/link-demands)   
 [Data and Modeling](/dotnet/framework/data/index)