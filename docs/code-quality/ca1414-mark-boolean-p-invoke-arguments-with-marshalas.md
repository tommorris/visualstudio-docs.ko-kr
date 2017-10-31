---
title: 'CA1414: Mark boolean P-Invoke arguments with MarshalAs | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: f5b44ea17ce00bf3a3f04e17fc1a86e33367ea8e
ms.contentlocale: ko-kr
ms.lasthandoff: 08/30/2017

---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Mark boolean P/Invoke arguments with MarshalAs
|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A platform invoke method declaration includes a <xref:System.Boolean?displayProperty=fullName> parameter or return value but the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> attribute is not applied to the parameter or return value.  
  
## <a name="rule-description"></a>Rule Description  
 A platform invoke method accesses unmanaged code and is defined by using the `Declare` keyword in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] or the <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> specifies the marshaling behavior that is used to convert data types between managed and unmanaged code. Many simple data types, such as <xref:System.Byte?displayProperty=fullName> and <xref:System.Int32?displayProperty=fullName>, have a single representation in unmanaged code and do not require specification of their marshaling behavior; the common language runtime automatically supplies the correct behavior.  
  
 The <xref:System.Boolean> data type has multiple representations in unmanaged code. When the <xref:System.Runtime.InteropServices.MarshalAsAttribute> is not specified, the default marshaling behavior for the <xref:System.Boolean> data type is <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. This is a 32-bit integer, which is not appropriate in all circumstances. The Boolean representation that is required by the unmanaged method should be determined and matched to the appropriate <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool is the Win32 BOOL type, which is always 4 bytes. UnmanagedType.U1 should be used for C++ `bool` or other 1-byte types. For more information, see [Default Marshaling for Boolean Types](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, apply <xref:System.Runtime.InteropServices.MarshalAsAttribute> to the <xref:System.Boolean> parameter or return value. Set the value of the attribute to the appropriate <xref:System.Runtime.InteropServices.UnmanagedType>.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule. Even if the default marshaling behavior is appropriate, the code is more easily maintained when the behavior is explicitly specified.  
  
## <a name="example"></a>Example  
 The following example shows two platform invoke methods that are marked with the appropriate <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributes.  
  
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)] [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)] [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## <a name="related-rules"></a>Related Rules  
 [CA1901: P/Invoke declarations should be portable](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101: Specify marshaling for P/Invoke string arguments](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## <a name="see-also"></a>See Also  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index)