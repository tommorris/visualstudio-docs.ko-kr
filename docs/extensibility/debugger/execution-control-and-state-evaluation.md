---
title: 실행 제어 및 상태 평가 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8961d2e06c7013b5667191c190053047f82de77d
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232405"
---
# <a name="execution-control-and-state-evaluation"></a>실행 제어 및 상태 평가
응용 프로그램을 디버깅할 함수를 한 단계씩 실행, 중단점에서 중지 및 계속 실행 같은 실행 제어 기능을 구현 해야 합니다. Visual Studio 기반 디버깅 디버거 구성 요소 사이 전송 하는 이벤트에 해당 실행 제어  
  
## <a name="in-this-section"></a>단원 내용  
 [프로그램 제어](../../extensibility/debugger/program-control.md)  
 프로그램 수준에서 발생 하는 다음 루틴은 나열: 다음 문 설정, 실행, 단계별 실행, 계속, 일시 중단 및 다시 시작 합니다.  
  
 [중단점 관련 메서드](../../extensibility/debugger/breakpoint-related-methods.md)  
 경계를 정의 및 지 원하는 Visual Studio 중단점 유형의 보류 중입니다.  
  
 [호출 스택 평가](../../extensibility/debugger/call-stack-evaluation.md)  
 중단 모드에 있는 동안 호출 스택의 스택 프레임의 보기를 허용 하는 메서드의 구현에 설명 합니다.  
  
 [식 계산](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 디버그 엔진 (DE), 식 평가 (EE) 및 세션 디버그 관리자가 구문 분석 하는 참여 및 IDE의 창 중 하나를 입력 한 식을 평가 하는 방법을 설명 합니다.  
  
 [컨트롤 이벤트](../../extensibility/debugger/control-events.md)  
 제어 된 프로그램을 실행 하는 동안 이벤트를 보내는 데 사용 하는 인터페이스를 설명 합니다.