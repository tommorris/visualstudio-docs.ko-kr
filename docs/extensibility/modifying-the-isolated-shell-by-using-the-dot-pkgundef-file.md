---
title: "격리 된 셸 사용 하 여 수정 된 합니다. Pkgundef 파일 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: b49f3c5a39e82e0385aab12ef7042a6845b12664
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>격리 된 셸 사용 하 여 수정 된 합니다. Pkgundef 파일
격리 된 셸 응용 프로그램에서 지정 된 레지스트리 항목을 제외 하려면.pkgundef 파일을 수정할 수 있습니다. 일반적으로 처음으로 컴퓨터에서 응용 프로그램을 시작 하는 Visual Studio shell 복사 기존 Visual Studio 레지스트리 항목 응용 프로그램에 대 한 루트 레지스트리 키에 있습니다. 현재 설치 된 VSPackages에 대 한 참조가 포함 됩니다.  
  
 격리 된 셸 응용 프로그램에서 특정 레지스트리 항목을 제외 하려면 패키지 키 뒤에 항목으로 응용 프로그램.pkgundef 파일에 추가 합니다. 키 및 항목에서.pkgdef 파일에서와 같이 표시 됩니다. 즉, [$RootKey $] 또는 [$RootKey$\\*하위 키*] 및 "*항목*" =*값*여기서 *하위 키* 영향을 하위 키가 *항목* 항목은 항목을 제거 하려면 및 *값* 은 `""` 또는 `dword:00000000`.  
  
 레지스트리 키에서 여러 항목을 제외 하려면 방금 나열 키 한 번 제외 하려면 각 항목에 대 한 줄 뒤 합니다.  
  
 격리 된 셸 응용 프로그램에서 전체 레지스트리 키를 제외 하려면 응용 프로그램.pkgundef 파일에 키를 추가 하지만 그 키에 대 한 레지스트리 항목을 지정 하지 마십시오.  
  
 .Pkgundef 파일에 주석을 추가할 수 있습니다. 한 줄 주석 처음 두 문자로 슬래시 두 개 있어야 합니다.  
  
 예를 들어, 제거 하는 **연결할 데이터베이스** 및 **Serve r에 연결** 에 있는 명령을 **도구** 메뉴 줄의 주석 처리 제거:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 줄을 추가 합니다.  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 응용 프로그램의.pkgundef 파일입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio의 기능 패키지 Guid](../extensibility/package-guids-of-visual-studio-features.md)   
 [격리 된 셸 사용자 지정](../extensibility/customizing-the-isolated-shell.md)