---
title: "액세스 위반을 어떻게 디버깅할 수 있습니까? | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.access"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "액세스 위반 디버깅"
  - "디버깅[Visual Studio], 액세스 위반"
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 액세스 위반을 어떻게 디버깅할 수 있습니까?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## 문제 설명  
 프로그램에 액세스 위반이 발생합니다. 어떻게 디버깅할 수 있습니까?  
  
## 솔루션  
 여러 포인터를 역참조하는 코드 줄에서 액세스 위반이 발생하는 경우 액세스 위반을 유발한 포인터를 찾기 어려울 수 있습니다. Visual Studio 2015 업데이트 1부터 이제 예외 대화 상자가 액세스 위반을 유발한 포인터의 이름을 명시적으로 지정합니다.  
  
 예를 들어 다음과 같은 코드에서는 액세스 위반이 발생합니다.  
  
```cpp  
#include <iostream> using namespace std; class ClassB { public: ClassC* C; ClassB() { C = new ClassC(); } void printHello() { cout << "hello world"; } }; class ClassA { public: ClassB* B; ClassA() { B = nullptr; } }; int main() { ClassA* A = new ClassA(); A->B->printHello(); }  
```  
  
 Visual Studio 2015 업데이트 1에서 이 코드를 실행하는 경우 다음 예외 대화 상자가 표시됩니다.  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 포인터가 액세스 위반을 유발한 이유를 확인할 수 없는 경우 전체 코드를 추적하여 문제를 유발한 포인터가 올바르게 할당되었는지 확인합니다.  포인터가 매개 변수로 전달된 경우 제대로 전달되었는지, 실수로 [단순 복사](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)를 만들지 않았는지 확인합니다. 그런 다음 프로그램의 다른 곳에서 수정되지 않도록 문제가 되는 포인터에 대한 데이터 중단점을 만들어 프로그램의 어딘가에서 값이 실수로 변경되지 않는지 확인합니다. 데이터 중단점에 대한 자세한 내용은 [중단점 사용](../debugger/using-breakpoints.md)에서 데이터 중단점 섹션을 참조하세요.  
  
## 참고 항목  
 [네이티브 코드 디버깅 FAQ](../debugger/debugging-native-code-faqs.md)