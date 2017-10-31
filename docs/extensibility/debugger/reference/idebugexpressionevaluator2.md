---
title: "IDebugExpressionEvaluator2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2 인터페이스"
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluator2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015의 식 계산기를 구현 합니다. 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하십시오 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 및 [관리 되는 식 계산기 예제](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.  
  
 식 계산기 \(EE\)의 향상 된 버전을 나타냅니다.  
  
## 구문  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## 구현자를 위한 정보  
 이 인터페이스는 식 계산기에 의해 구현 됩니다.  
  
## 메서드  
 메서드 외에 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) 인터페이스,이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|---------|--------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|고유 식별자를 지정 하는 서비스 개체를 검색 합니다.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|지정한 기호 공급자로 지정 된 모듈을 미리 로드 합니다.|  
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|식 계산기를 \(EE\) 메트릭 설정을 읽지 디버거 엔진 \(DE\)는 데 사용 하는 콜백 인터페이스를 지정할 수 있습니다.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|디버거에서 로드 된 공용 언어 런타임 \(CLR\)에 경로 설정 합니다.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|디버그 엔진을을 초기화 하는 동안 콜백을 식 계산기에 전달할 수 있습니다.|  
|[종료](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|중지 하 고 식 계산기를 정리 합니다.|  
  
## 요구 사항  
 헤더: Ee.h  
  
 네임 스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll