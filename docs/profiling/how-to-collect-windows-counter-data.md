---
title: "방법: Windows 카운터 데이터 수집 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.syscounter"
  - "vs.performance.property.wincounter"
helpviewer_keywords: 
  - "Windows 카운터"
  - "성능 도구, Windows 카운터 사용"
  - "프로파일링 도구, Windows 카운터 사용"
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 방법: Windows 카운터 데이터 수집
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows 카운터는 프로파일링을 수행하는 동안 설정된 간격에 따라 수집할 수 있는 시스템 성능 카운터입니다.  프로파일링 도구 보고서의 표시 뷰에는 각 수집 간격에 대해 **AutoMark**라는 행이 있습니다.  이 행에는 각 간격의 성능 카운터 값을 설명하는 열이 있습니다.  두 개의 특정 표시 사이의 시간대로 분석을 제한하려면 표시를 선택하고 마우스 오른쪽 단추를 클릭한 다음 단축 메뉴에서 **필터링** \-\>  **표시** 을 선택합니다.  
  
 **요구 사항**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Windows 8 및 Windows Server 2012의 강화된 보안 기능으로 Visual Studio 프로파일러가 해당 플랫폼에서 데이터를 수집하는 방식에 중요한 변경 사항이 발생합니다.  Windows 스토어 응용 프로그램에는 또한 새 컬렉션 기술이 필요합니다.  [Windows 8 및 Windows Server 2012 응용 프로그램 프로파일링](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하십시오.  
  
### Windows 카운터 데이터를 수집하려면  
  
1.  성능 탐색기에서 Windows 카운터를 구성할 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.  
  
2.  **속성 페이지**에서 **Windows 카운터**를 클릭합니다.  
  
3.  **Windows 카운터 수집** 확인란을 선택합니다.  
  
4.  **수집 간격\(밀리초\)** 텍스트 상자에 시간 간격을 입력합니다.  
  
5.  **카운터 범주** 드롭다운 목록에서 범주를 선택합니다.  
  
6.  **인스턴스** 드롭다운 목록에서 인스턴스를 선택합니다.  
  
7.  응용 프로그램을 프로파일링할 때 사용할 카운터를 선택합니다.  
  
8.  **적용**을 클릭합니다.  
  
## 참고 항목  
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)   
 [성능 세션 속성](../profiling/performance-session-properties.md)   
 [CPU 및 Windows 카운터](../profiling/cpu-and-windows-counters.md)