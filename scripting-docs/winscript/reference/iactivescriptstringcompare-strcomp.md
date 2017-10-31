---
title: "IActiveScriptStringCompare::StrComp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStringCompare.StrComp
apilocation: scrobj.dll
helpviewer_keywords: 
  - "StrComp 메서드, IActiveScriptStringCompare 인터페이스"
ms.assetid: 124d1281-8037-4766-a2a1-61244ac1f114
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStringCompare::StrComp
스크립팅 엔진에 대 한 문자열 비교 메서드를 정의합니다.  
  
## 구문  
  
```  
HRESULT StrComp(  
// The first string:  
    [in] BSTR bszStr1,    
// The second string:   
    [in] BSTR bszStr2,    
// The result of the comparison:  
    [out, retval] LONG* iRet   
);  
```  
  
#### 매개 변수  
 `bszStr1`  
 첫 번째 문자열입니다.  
  
 `bszStr2`  
 두 번째 문자열입니다.  
  
 `iRet`  
 비교의 결과입니다.  0 `bszStr1` 및 `bszStr2`동일 합니다. \-1 if `bszStr1` \<  `bszStr2`; 1 if `bszStr1` \>  `bszStr2`.  
  
## 반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|----------|--------|  
|`S_OK`|성공|  
|`E_INVALIDARG`|인수가 잘못된 경우.|  
|`E_UNEXPECTED`|호출이 필요 없습니다 \(예를 들어, 스크립팅 엔진이 아직 로드 초기화 되었거나\).|  
  
## 설명  
 이 메서드는 문자열 비교 실행 될 때마다 호출 됩니다.  
  
## 예제  
 다음 예제에서는 문자열 비교 함수를 오버 로드 하는 방법을 보여 줍니다.  사용 하는 경우 오버 로드에 사용할 수 [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) SCRIPTPROP\_STRINGCOMPAREINSTANCE를 설정 합니다.  
  
```cpp#  
cpp_quote("// {58562769-ED52-42f7-8403-4963514E1F11}")  
cpp_quote("DEFINE_GUID(IID_IActiveScriptStringCompare, 0x58562769,   
    0xED52, 0x42f7, 0x84, 0x03, 0x49, 0x63, 0x51, 0x4E, 0x1F, 0x11);")  
cpp_quote("")  
  
cpp_quote("#define SCRIPTPROP_INTEGERMODE              0x00003000")  
cpp_quote("#define SCRIPTPROP_STRINGCOMPAREINSTANCE    0x00003001")  
cpp_quote("")  
interface IActiveScriptStringCompare;  
[  
         object,  
         uuid(58562769-ED52-42f7-8403-4963514E1F11),  
         pointer_default(unique)  
]  
interface IActiveScriptStringCompare : IUnknown  
{  
        // StrComp  
        //     bszStr1: first string  
        //     bszStr2: second string  
        //     iRet: 0 if identical, -1 if bszStr1 < bszStr2, 1 if   
        //         bszStr1 > bszStr2  
        //            
        //     Return values:  
        //         S_OK: Success  
        //         E_NOTIMPL: Not implemented  
        //  
        HRESULT StrComp(  
                [in] BSTR bszStr1,  
                [in] BSTR bszStr2,  
                [out, retval] LONG* iRet  
        );  
}  
```  
  
## 참고 항목  
 [IActiveScriptStringCompare 인터페이스](../../winscript/reference/iactivescriptstringcompare-interface.md)