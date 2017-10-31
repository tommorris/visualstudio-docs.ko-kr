---
title: "방법: .NET Framework 런타임 지정 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 45baa5754e5ffb44edf948dc39fa80d2249e03f1

---
# <a name="how-to-specify-the-net-framework-runtime"></a>방법: .NET Framework 런타임 지정
[!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] 릴리스에서는 다양한 버전의 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 런타임을 사용하여 빌드된 모듈로 응용 프로그램을 구성할 수 있습니다. 기본적으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구는 응용 프로그램이 로드한 첫 번째 런타임을 프로파일링합니다. 프로파일러를 사용하여 응용 프로그램을 시작할 때, 그리고 프로파일러를 이미 실행 중인 응용 프로그램에 연결할 때 프로파일링할 런타임을 지정할 수 있습니다.  
  
 **Requirements**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>프로파일러를 사용하여 응용 프로그램을 시작할 때 프로파일링할 .NET Framework 런타임을 지정하려면  
  
1.  **성능 탐색기**에서 성능 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**, **고급**을 차례로 클릭합니다.  
  
     **대상 CLR 버전** 목록 상자에는 **자동** 및 컴퓨터에 설치된 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 런타임 버전이 표시됩니다.  
  
2.  다음 단계 중 하나를 수행합니다.  
  
    -   프로파일링할 CLR 버전을 클릭합니다.  
  
    -   **자동**을 클릭하여 응용 프로그램이 로드한 첫 번째 버전을 프로파일링합니다.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>프로파일러를 응용 프로그램에 연결할 때 프로파일링할 .NET Framework 런타임을 지정하려면  
  
1.  [분석] 메뉴에서 [프로파일러]를 가리키고 [연결/분리]를 클릭합니다.  
  
2.  [프로세스에 프로파일러 연결] 대화 상자에서 프로파일링할 프로세스를 클릭합니다.  
  
     **대상 CLR 버전** 목록 상자에는 **자동** 및 컴퓨터에 설치된 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 런타임 버전이 표시됩니다.  
  
3.  다음 단계 중 하나를 수행합니다.  
  
    -   프로파일링할 CLR 버전을 클릭합니다.  
  
    -   **자동**을 클릭하여 프로파일러가 응용 프로그램에 연결될 때 로드된 버전을 프로파일링합니다.


<!--HONumber=Feb17_HO4-->

