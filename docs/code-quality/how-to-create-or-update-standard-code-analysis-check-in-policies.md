---
title: "방법: 표준 코드 분석 체크 인 정책 만들기 또는 업데이트 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.policyeditor
helpviewer_keywords: code analysis, migrating check-in policy
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6396b698a5f4d2602c9969d6cab0422832b3e6dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>방법: 표준 코드 분석 체크 인 정책 만들기 또는 업데이트
코드 분석 체크 인 정책을 사용 하 여 코드 분석 팀 프로젝트의 모든 코드 프로젝트에서 실행할 수 있는지를 요구할 수 있습니다. 코드 분석에 필요한 코드 베이스에 체크 인 된 코드의 품질을 향상 시킬 수 있습니다.  
  
> [!NOTE]
>  이 기능은 Team Foundation Server를 사용 하는 경우에 사용할 수 있습니다.  
  
 코드 분석 체크 인 정책 팀 프로젝트 설정에서 설정 하 고 팀 프로젝트의 각 코드 프로젝트에 적용 합니다. 코드 분석 실행 코드 프로젝트에 대 한 프로젝트 (.xxproj) 파일에 코드 프로젝트에 대해 구성 됩니다. 코드 분석 실행은 로컬 컴퓨터에서 수행 됩니다. 팀 프로젝트 설정의 규칙은 컴퓨터에서 수행 해야 코드 분석 체크 인 정책을 사용 하도록 설정 하 고 체크 인 되는 코드 프로젝트의에서 파일은 마지막 편집 후 컴파일해야 합니다. 여기에 최소한의 코드 분석 실행 하는 포함 하는 경우에 c hanges 지정 되었습니다.  
  
-   관리 되는 코드를 지정 하 여 체크 인 정책 설정는 *규칙 집합* 코드 분석 규칙의 하위 집합을 포함 하는 합니다.  
  
-   C/c + + 코드에 대 한 모든 코드 분석 규칙이 실행 됩니다. 체크 인 정책 필요 합니다. 팀 프로젝트의 개별 코드 프로젝트에 대 한 특정 규칙을 사용 하지 않도록 설정 하는 전처리기 지시문을 추가할 수 있습니다.  
  
 관리 코드에 대 한 체크 인 정책을 지정 하면 팀 멤버가 코드 프로젝트에 팀 프로젝트 정책 설정에 대 한 코드 분석 설정을 동기화 할 수 있습니다.  
  
### <a name="to-open-the-check-in-policy-editor"></a>체크 인 정책 편집기를 열려면  
  
1.  팀 탐색기에서 팀 프로젝트 이름을 마우스 오른쪽 단추로 클릭, 가리킨 **팀 프로젝트 설정**, 클릭 하 고 **소스 제어**합니다.  
  
2.  에 **소스 제어** 대화 상자는 **체크 인 정책** 탭 합니다.  
  
3.  다음 작업 중 하나를 수행합니다.  
  
    -   클릭 **추가** 새 체크 인 정책을 만들 수 있습니다.  
  
    -   기존 두 번 클릭 **코드 분석** 항목에 **정책 형식을** 정책을 변경 하려면 목록입니다.  
  
### <a name="to-set-policy-options"></a>정책 옵션을 설정 하려면  
  
-   선택 하거나 다음 옵션을 선택 취소 합니다.  
  
    |옵션|설명|  
    |------------|-----------------|  
    |**체크 인 적용 현재 솔루션의 일부인 파일만 포함 하도록 합니다.**|코드 분석 솔루션 및 프로젝트 구성 파일에 지정 된 파일에 대해서만 실행할 수 있습니다. 이 정책을 솔루션의 일부인 모든 코드를 분석 하는 것을 보장 합니다.|  
    |**C/c + + 코드 분석 적용 (/analyze)**|모든 C 또는 c + + 프로젝트를 빌드할 수 필요는 /analyze 컴파일러 옵션 검사 하기 전에 코드 분석 실행을 합니다.|  
    |**관리 코드에 대 한 코드 분석을 적용**|에서는 모든 관리 되는 프로젝트 코드 분석을 실행 하 고 빌드 전에 체크 인할 수 있습니다.|  
  
-  
  
### <a name="to-specify-a-managed-rule-set"></a>관리 되는 규칙 집합을 지정 하려면  
  
-   **이 규칙 집합 실행** 목록에서 다음 방법 중 하나를 사용 합니다.  
  
    -   Microsoft 표준 규칙 집합을 선택 합니다.  
  
    -   사용자 지정 규칙 집합을 선택 하려면 클릭  **\<...에 소스 제어에서 규칙 집합 선택 >**, 소스 제어 브라우저에서 규칙 집합의 버전 제어 경로 입력 합니다. 버전 제어 경로 구문은 다음과 같습니다.  
  
    -   **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    -   집합을 만들고 사용자 지정 체크 인 정책 규칙을 구현 하는 방법에 대 한 자세한 내용은 참조 하십시오. [관리 코드에 대 한 사용자 지정 구현에서 체크 인 정책을](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [코드 분석 체크 인 정책 만들기 및 사용](../code-quality/creating-and-using-code-analysis-check-in-policies.md)