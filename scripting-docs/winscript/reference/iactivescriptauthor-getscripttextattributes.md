---
title: "IActiveScriptAuthor::GetScriptTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetScriptTextAttributes"
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetScriptTextAttributes
스크립트 블록에 대 한 텍스트 특성을 반환합니다.  
  
## 구문  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### 매개 변수  
 `pszCode`  
 in, size\_is\(`cch`\)\] 스크립트 블록의 텍스트입니다.  이 문자열이 null 종료 없습니다.  
  
 `cch`  
 \[in\] 사용 되는 크기는 `pszCode` 및 `pattr` 매개 변수.  
  
 `pszDelimiter`  
 \[in\] 주소를 스크립트의 끝 구분 기호입니다.  때 `pszCode` 구문 분석 텍스트 스트림에서 호스트 일반적으로 구분 \(예: 두 개의 작은따옴표\)를에서 스크립트릿 끝 탐지를 사용 합니다.  경우 스크립트 블록의 끝을 나타내려면 구분 기호 없음이 매개 변수를 NULL로 설정 합니다.  
  
 `dwFlags`  
 \[in\] 스크립트 블록의 텍스트 특성에 연결 된 플래그입니다.  다음 값 조합이 될 수 있습니다.  
  
|상수|값|설명|  
|--------|-------|--------|  
|GETATTRTYPE\_DEPSCAN|0x0001|SOURCETEXT\_ATTR\_IDENTIFIER 특성이 식별자를 식별 하 고 SOURCETEXT\_ATTR\_MEMBERLOOKUP 특성을 사용 하는 도트 연산자를 확인 합니다.|  
|GETATTRFLAG\_THIS|0x0100|현재 SOURCETEXT\_ATTR\_THIS 특성이 있는 개체를 식별 합니다.|  
|GETATTRFLAG\_HUMANTEXT|0x8000|SOURCETEXT\_ATTR\_HUMANTEXT 특성을 가진 문자열 내용 및 설명 텍스트를 확인 합니다.|  
  
 `pattr`  
 in, out을 \(를\) \(`cch`\)\] 스크립트 블록 코드의 색상 정보입니다.  
  
## 반환 값  
 `HRESULT`입니다.  가능한 값 포함 되지만, 다음 테이블에 제한 되지는지 않습니다.  
  
|값|설명|  
|-------|--------|  
|`S_OK`|메서드가 성공했으며|  
  
## 설명  
  
## 참고 항목  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE\_TEXT\_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)