---
title: SetEnv 작업 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2d9cec2c76b2159e14b1e7abe19b93ab91f6688
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153776"
---
# <a name="setenv-task"></a>SetEnv 작업
지정된 환경 변수의 값을 설정하거나 삭제합니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 **SetEnv** 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|**이름**|필수 **String** 매개 변수입니다.<br /><br /> 환경 변수의 이름입니다.|  
|**OutputEnvironmentVariable**|선택적 **String** 출력 매개 변수입니다.<br /><br /> **이름** 매개 변수에서 지정한 환경 변수에 할당된 값이 포함됩니다.|  
|**접두사**|`Boolean` 필수 매개 변수입니다.<br /><br /> `true`인 경우 **이름** 매개 변수에서 지정한 환경 변수 값 앞에 **값** 매개 변수의 값을 연결한 다음 환경 변수에 대한 결과를 할당합니다. `false`인 경우 환경 변수에 대한 **값** 매개 변수의 값만 할당합니다.|  
|**Target**|선택적 **문자열** 매개 변수입니다.<br /><br /> 환경 변수가 저장되는 위치를 지정합니다. “사용자” 또는 “컴퓨터”를 지정합니다.<br /><br /> 자세한 내용은 MSDN 웹 사이트에서 [EnvironmentVariableTarget 열거형](https://msdn.microsoft.com/library/system.environmentvariabletarget(v=vs.110).aspx)을 참조하세요.|  
|**값**|선택적 **문자열** 매개 변수입니다.<br /><br /> **이름** 매개 변수에서 지정한 환경 변수에 할당된 값입니다. **값**이 비어 있고 해당 변수가 존재하면 변수가 삭제됩니다. 변수가 존재하지 않으면 작업을 수행할 수 없더라도 오류가 발생하지 않습니다.<br /><br /> 자세한 내용은 MSDN 웹 사이트에서 [Environment::SetEnvironmentVariable 메서드](https://msdn.microsoft.com/library/96xafkes(v=vs.110).aspx)를 참조하세요.|  
  
## <a name="see-also"></a>참고 항목  
 [작업 참조](../msbuild/msbuild-task-reference.md)