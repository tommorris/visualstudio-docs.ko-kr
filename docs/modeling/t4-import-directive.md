---
title: T4 Import 지시문
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6b0479bf427930d19b12fa0de5728f26e7cdb10d
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510180"
---
# <a name="t4-import-directive"></a>T4 Import 지시문

코드 블록에는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] T4 텍스트 템플릿은 `import` 지시문을 사용 하면 정규화 된 이름을 지정 하지 않고 다른 네임 스페이스의 요소를 참조할 수 있습니다. 이 지시문은 C#의 `using` 또는 `imports`의 [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)]에 해당합니다.

T4 텍스트 템플릿 작성의 일반적인 개요를 참조 하세요 [T4 텍스트 템플릿 쓰기](../modeling/writing-a-t4-text-template.md)합니다.

## <a name="using-the-import-directive"></a>Import 지시문 사용

```
<#@ import namespace="namespace" #>
```

 이 예제에서는 다음과 같이 템플릿 코드에서 System.IO의 멤버에 대한 명시적 네임스페이스를 생략할 수 있습니다.

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>표준 가져오기
 다음 네임스페이스를 자동으로 가져오므로 해당 네임스페이스에 대한 import 지시문을 작성할 필요가 없습니다.

-   `System`

 또한 사용자 지정 지시문을 사용하는 경우 지시문 프로세서에서 일부 네임스페이스를 자동으로 가져올 수 있습니다.

 예를 들어 DSL(Domain-Specific Language)을 위한 템플릿을 작성하는 경우 다음 네임스페이스에 대한 import 지시문을 작성할 필요가 없습니다.

-   `Microsoft.VisualStudio.Modeling`

-   DSL의 네임 스페이스

## <a name="see-also"></a>참고 항목

- [T4 Assembly 지시문](../modeling/t4-assembly-directive.md)