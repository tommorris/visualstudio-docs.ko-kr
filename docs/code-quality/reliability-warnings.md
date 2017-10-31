---
title: "안정성 경고 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.reliabilityrules"
helpviewer_keywords: 
  - "경고, 안정성"
  - "안정성 경고"
  - "관리 코드 분석 경고, 안정성 경고"
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# 안정성 경고
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

안정성 경고는 올바른 메모리 및 스레드 사용과 같은 라이브러리 및 응용 프로그램 안정성을 지원합니다.  
  
## 단원 내용  
  
|규칙|설명|  
|--------|--------|  
|[CA2000: 범위를 벗어나기 전에 개체를 삭제하십시오.](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|개체의 종료자가 실행되지 못하도록 하는 예외 이벤트가 발생할 수 있기 때문에 개체에 대한 모든 참조가 범위를 벗어나기 전에 개체를 명시적으로 삭제해야 합니다.|  
|[CA2001: 문제가 있는 메서드는 호출하지 마십시오.](../Topic/CA2001:%20Avoid%20calling%20problematic%20methods.md)|멤버에서 잠재적 위험이나 문제가 있는 메서드를 호출합니다.|  
|[CA2002: 약한 ID를 가진 개체를 잠그지 마십시오.](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|응용 프로그램 도메인 경계를 가로질러 직접 액세스할 수 있는 개체를 약한 ID를 가진 개체라고 합니다.  약한 ID를 가진 개체에 대해 잠금을 가져오려고 시도하는 스레드는 같은 개체에 대해 잠금을 가진 다른 응용 프로그램 도메인의 스레드에 의해 차단될 수 있습니다.|  
|[CA2003: 파이버를 스레드로 취급하지 마십시오.](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|관리되는 스레드가 Win32 스레드처럼 취급됩니다.|  
|[CA2004: GC.KeepAlive에 대한 호출을 제거하십시오.](../Topic/CA2004:%20Remove%20calls%20to%20GC.KeepAlive.md)|SafeHandle을 사용하는 방식으로 변환하는 경우 GC.KeepAlive\(개체\)에 대한 모든 호출을 제거해야 합니다.  이 경우 클래스에 종료자가 없지만 SafeHandle을 사용하여 OS 핸들을 종료하는 것으로 간주하므로 클래스에서 GC.KeepAlive를 호출할 필요가 없습니다.|  
|[CA2006: SafeHandle을 사용하여 네이티브 리소스를 캡슐화하십시오.](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|관리 코드에 IntPtr을 사용하는 것은 잠재적인 보안 및 안정성 문제를 나타냅니다.  IntPtr을 사용할 때마다 SafeHandle 또는 유사한 기술을 대신 사용해야 하는지 여부를 결정하도록 검토해야 합니다.|