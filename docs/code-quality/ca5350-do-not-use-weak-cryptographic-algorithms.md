---
title: "CA5350: 취약한 암호화 알고리즘 사용 안 함 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA5350: 취약한 암호화 알고리즘 사용 안 함
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|범주|Microsoft.Cryptography|  
|변경 수준|주요 변경 아님|  
  
> [!NOTE]
>  이 경고는 2015년 11월에 마지막으로 업데이트되었습니다.  
  
## 원인  
 <xref:System.Security.Cryptography.TripleDES> 등의 암호화 알고리즘과 <xref:System.Security.Cryptography.SHA1> 및 <xref:System.Security.Cryptography.RIPEMD160> 등의 해시 알고리즘은 취약한 것으로 간주됩니다.  
  
 이러한 암호화 알고리즘은 최신 알고리즘만큼 강력하게 보안을 보장하지 않습니다. 암호화 해시 알고리즘 <xref:System.Security.Cryptography.SHA1> 및 <xref:System.Security.Cryptography.RIPEMD160>은 최신 해시 알고리즘보다 충돌 방지 기능이 약합니다. 암호화 알고리즘 <xref:System.Security.Cryptography.TripleDES>는 최신 암호화 알고리즘보다 더 적은 보안 비트를 제공합니다.  
  
## 규칙 설명  
 오늘날 여러 가지 이유로 약한 암호화 알고리즘 및 해시 함수가 사용되지만 데이터의 기밀성을 보장하기 위해서는 이 방법을 사용하지 않아야 합니다.  
  
 이 규칙은 코드에 3DES, SHA1 또는 RIPEMD160 알고리즘이 있을 때 트리거되며 사용자에게 경고를 throw합니다.  
  
## 위반 문제를 해결하는 방법  
 보다 강력한 암호화 옵션을 사용합니다.  
  
-   TripleDES 암호화의 경우 <xref:System.Security.Cryptography.Aes> 암호화를 사용합니다.  
  
-   SHA1 또는 RIPEMD160 해시 함수의 경우 [SHA\-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx) 제품군의 암호화\(예: <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>\)를 사용합니다.  
  
## 경고를 표시하지 않는 경우  
 데이터에 필요한 보호 수준이 보안 보장을 요구하지 않는 경우 이 규칙에서 실행되는 경고를 표시하지 않도록 설정합니다.  
  
## 의사 코드 예제  
 다음 의사 코드 샘플에서는 이 문서를 작성할 당시 이 규칙에 의해 검색되는 패턴을 보여 줍니다.  
  
### SHA\-1 해시 위반  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA1.Create();  
  
```  
  
### 솔루션  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### RIPEMD160 해시 위반  
  
```  
using System.Security.Cryptography; ... var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### 솔루션  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### TripleDES 암호화 위반  
  
```  
using System.Security.Cryptography; ... using (TripleDES encAlg = TripleDES.Create()) { ... }  
```  
  
### 솔루션  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```