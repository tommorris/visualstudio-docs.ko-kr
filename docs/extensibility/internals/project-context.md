---
title: 프로젝트 상황에 맞는 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f52260d63088d7673322f3c42d43d00184a9af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134697"
---
# <a name="project-context"></a>프로젝트 컨텍스트
사용자를 추가 하거나 프로젝트 및 프로젝트 항목 사용 때 IDE에서는 프로젝트 컨텍스트의 개념 다양 한 연산을 수행 하는 결정 됩니다.  
  
 일반적으로 파일은 사용자가 명시적으로 선택 하 여 작성 하는 표준 프로젝트 개체는 **새 프로젝트** 명령이 나 사용 하면 선택 하 여 사용할 수는 **프로젝트 열기** 명령을  **파일** 메뉴. 이러한 경우에 파일 생성 되 고 프로젝트의 컨텍스트를 열 및 프로젝트 형식 문서를 편집 하기 위한 컨텍스트를 정의 합니다.  
  
 일부 프로젝트는 매우 다양 한 컨텍스트를 제공합니다. 예를 들어 프로젝트는 프로젝트 범위, 프로그래밍 방식으로 네임 스페이스 또는 데이터 바인딩에 대 한 프로젝트 범위 데이터베이스 연결을 관리합니다. 사용자 파일 또는 데이터베이스 연결 솔루션 탐색기에 표시 되는 프로젝트 항목 같은 특정 프로젝트 개체를 사용 하 여 직접 자주 열 수 있습니다.  
  
 다른 시간에 항목의 프로젝트 컨텍스트 하지 명시적으로 지정 됩니다. 예를 들어 항목의 상황에 맞는 때 사용할 수 없는 사용자가을 선택 하 여 파일을 열는 **기존 파일 열기** 명령을 **파일** 메뉴에서 디버거를 클릭할 때 또는 파일에서 작동 되는 **파일에서 찾기** 명령에 **찾기 및 바꾸기** 대화 상자. IDE 호출 하 여 이러한 상황을 처리 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> 최상의 프로젝트 문서를 찾는 과정을 관리할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 우선 순위](../../extensibility/internals/project-priority.md)   
 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)