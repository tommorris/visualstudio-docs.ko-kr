---
title: 예상 &#39;)&#39; 정규식 (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d1075a41d2b97d10166b1372e8df3a93dd9d8e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279130"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>예상 &#39;)&#39; 정규식 (JavaScript)
정규식 캡처, 어설션 또는 그룹을 만들려고 시도 했음 해도 닫는 괄호를 포함 하지 않았습니다. 괄호는 정규식의 몇 가지 목적이 있습니다. 주로 사용 되는 하위 식에서 어설션을 지정 하거나 항목으로 하나의 단위로 처리할 수 있도록 패턴을 그룹화 하려면 캡처 *, +,? 등입니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
-   오른쪽에 있는 닫는 괄호를 추가 합니다.  
  
    > [!NOTE]
    >  단일 괄호 일치 하도록 하려는 경우-백슬래시로 이스케이프 \\(에서 특수 문자로 해석 되지 않습니다 있도록- [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Regular Expression 개체](../../javascript/reference/regular-expression-object-javascript.md)   
 [정규식 구문 (JavaScript)](https://msdn.microsoft.com/library/1400241x)