---
title: "CLS 규격 경고 CLS04106 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CLS04106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS04106"
ms.assetid: a74e4cb7-c96a-4673-bf11-c2ff3c4b02f1
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 규격 경고 CLS04106
특성은 'System::Attribute' 형식 또는 여기에서 상속된 형식이어야 합니다.  
  
 CLS 규격을 준수하기 위해 사용자 지정 특성은 System::Attribute에서 상속해야 합니다.  System::Attribute에서 상속되지 않은 특성이 함수에 적용되었습니다.  
  
 다음 선언\(MSIL 어셈블리 언어 사용\)에서는 CLS04106을 발생시키는 원인을 보여 줍니다.  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Object  
```  
  
 그런 다음 특성을 사용하는 함수를 보여 줍니다.  
  
```  
.custom instance void MyAttribute::.ctor(int32) = ( 01 00 01 00 00 00 00 00 )  
```  
  
 특성이 System::Attribute에서 파생되도록 하면 경고가 해결됩니다.  
  
```  
.class public auto ansi MyAttribute extends [mscorlib]System.Attribute  
```