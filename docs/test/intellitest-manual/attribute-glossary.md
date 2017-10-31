---
title: "특성 용어집 | Microsoft IntelliTest 개발자 테스트 도구 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Attribute glossary
ms.assetid: 557C7869-48BE-4B82-9563-1FF356ABACDB
caps.latest.revision: 56
ms.author: douge
manager: douge
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 45d36934cf1c46902cac566203cddf4a118b7fe4
ms.openlocfilehash: ad5a3dab018ccafba6462d92fea8401939d1b278
ms.contentlocale: ko-kr
ms.lasthandoff: 06/02/2017

---
# <a name="attribute-glossary"></a>특성 용어집

## <a name="attributes-by-namespace"></a>네임스페이스별 특성

* **Microsoft.Pex.Framework**
  * [PexAssumeNotNull](#pexassumenotnull)
  * [PexClass](#pexclass)
  * [PexGenericArguments](#pexgenericarguments)
  * [PexMethod](#pexmethod)
     - [PexExplorationAttributeBase](#pexexplorationattributebase)<p />

* **Microsoft.Pex.Framework.Settings**
  * [PexAssemblySettings](#pexassemblysettings)<p />

* **Microsoft.Pex.Framework.Instrumentation**
  * [PexAssemblyUnderTest](#pexassemblyundertest)
  * [PexInstrumentAssembly](#pexinstrumentassemblyattribute)<p />

* **Microsoft.Pex.Framework.Using**
  * [PexUseType](#pexusetype)<p />

* **Microsoft.Pex.Framework.Validation**
  * [PexAllowedException](#pexallowedexception)
  * [PexAllowedExceptionFromAssembly](#pexallowedexceptionfromassembly)
  * [PexAllowedExceptionFromType](#pexallowedexceptionfromtype)
  * [PexAllowedExceptionFromTypeUnderTest](#pexallowedexceptionfromtypeundertest)

<a name="pexassumenotnull"></a>
## <a name="pexassumenotnull"></a>PexAssumeNotNull

이 특성은 제어되는 값이 **null**일 수 없음을 어설션합니다. 다음에 연결될 수 있습니다.

* 매개 변수가 있는 테스트 메서드의 **매개 변수**

  ```
  // assume foo is not null
  [PexMethod]
  public void SomeTest([PexAssumeNotNull]IFoo foo, ...) {}
  ```

* **필드**

  ```
  public class Foo {
     // this field should not be null
     [PexAssumeNotNull]
     public object Bar;
  }
  ```

* **형식**

  ```
  // never consider null for Foo types
  [PexAssumeNotNull]
  public class Foo {}
  ```

또한 테스트 어셈블리, 테스트 설비 또는 테스트 메서드에 연결될 수 있습니다. 이 경우 첫 번째 인수는 가정이 적용되는 필드 또는 형식을 나타내야 합니다. 특성이 형식에 적용되면 이 정식 형식의 모든 필드에 특성이 적용됩니다.

<a name="pexclass"></a>
## <a name="pexclass"></a>PexClass

이 특성은 *explorations*가 포함된 클래스를 표시합니다. MSTest **TestClassAttribute**(또는 NUnit **TestFixtureAttribute**)에 해당합니다. 이 특성은 선택적 요소입니다.

[PexClass](#pexclass)로 표시된 클래스는 *기본 생성 가능한* 클래스여야 합니다.

* 공개적으로 내보낸 형식
* 기본 생성자
* 추상이 아님

클래스가 해당 요구 사항을 충족하지 않을 경우 오류가 보고되고 탐색에 실패합니다.

IntelliTest가 클래스의 일부인 새 테스트를 별도의 파일로 생성할 수 있도록 해당 클래스를 **partial**로 만드는 것이 좋습니다. 이 방법은 [표시 여부](input-generation.md#visibility)로 인한 많은 문제를 해결하며 C#의 일반적인 기술입니다.

**추가 도구 모음 및 범주**:

```
[TestClass] // MSTest test fixture attribute
[PexClass(Suite = "checkin")] // fixture attribute
public partial class MyTests { ... }
```

**테스트 중인 형식 지정**:

```
[PexClass(typeof(Foo))] // this is a test for Foo
public partial class FooTest { ... }
```

클래스에 [PexMethod](#pexmethod)로 주석이 달린 메서드가 포함될 수 있습니다. IntelliTest는 [설정 및 해체 메서드](test-generation.md#setup-teardown)도 인식합니다.

<a name="pexgenericarguments"></a>
## <a name="pexgenericarguments"></a>PexGenericArguments

이 특성은 [제네릭 매개 변수가 있는 단위 테스트](test-generation.md#generic-parameterized)를 인스턴스화하기 위한 형식 튜플을 제공합니다.

<a name="pexmethod"></a>
## <a name="pexmethod"></a>PexMethod

이 특성은 메서드를 [매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)로 표시합니다.
메서드는 [PexClass](#pexclass) 특성으로 표시된 클래스 내에 있어야 합니다.

IntelliTest는 다양한 매개 변수를 사용하여 [매개 변수가 있는 단위 테스트](test-generation.md#parameterized-unit-testing)를 호출하는 기존의 매개 변수가 없는 테스트를 생성합니다.

매개 변수가 있는 단위 테스트:

* 인스턴스 메서드여야 합니다.
* [폭포수형 설정](settings-waterfall.md)에 따라 생성된 테스트가 배치되는 테스트 클래스에 [표시](input-generation.md#visibility)되어야 합니다.
* 제한 없이 매개 변수를 사용할 수 있습니다.
* 제네릭일 수 있습니다.

**예제**

```
[PexClass]
public partial class MyTests {
     [PexMethod]
     public void MyTest(int i)
     { ... }
}
```

<a name="pexexplorationattributebase"></a>
## <a name="pexexplorationattributebase"></a>PexExplorationAttributeBase

[추가 정보](https://msdn.microsoft.com/library/microsoft.pex.framework.pexexplorationattributebase.aspx)

<a name="pexassemblysettings"></a>
## <a name="pexassemblysettings"></a>PexAssemblySettings

이 특성은 어셈블리 수준에서 모든 탐색에 대한 기본 설정 값을 재정의하도록 설정될 수 있습니다.

```
using Microsoft.Pex.Framework;
// overriding the test framework selection
[assembly: PexAssemblySettings(TestFramework = "Naked")]
```

<a name="pexassemblyundertest"></a>
## <a name="pexassemblyundertest"></a>PexAssemblyUnderTest

이 특성은 현재 테스트 프로젝트에서 테스트 중인 어셈블리를 지정합니다. 

```
[assembly: PexAssemblyUnderTest("MyAssembly")]
```

<a name="pexinstrumentassemblyattribute"></a>
## <a name="pexinstrumentassemblyattribute"></a>PexInstrumentAssemblyAttribute

이 특성은 계측되는 어셈블리를 지정하는 데 사용됩니다.

**예제**

```
using Microsoft.Pex.Framework;

// the assembly containing ATypeFromTheAssemblyToInstrument should be instrumented
[assembly: PexInstrumentAssembly(typeof(ATypeFromTheAssemblyToInstrument))]

// the assembly name can be used as well
[assembly: PexInstrumentAssembly("MyAssemblyName")]
```

<a name="pexusetype"></a>
## <a name="pexusetype"></a>PexUseType

이 특성은 특정 형식을 사용하여 기본 형식 또는 인터페이스를 인스턴스화(추상화)할 수 있음을 IntelliTest에 알립니다.

**예제**

```
[PexMethod]
[PexUseType(typeof(A))]
[PexUseType(typeof(B))]
public void MyTest(object testParameter)
{
     ... // IntelliTest will consider types A and B to instantiate 'testParameter'
}
```

<a name="pexallowedexception"></a>
## <a name="pexallowedexception"></a>PexAllowedException

이 특성은 [PexMethod](#pexmethod)(또는 [PexClass](#pexclass))에 연결되면 테스트에 실패한 경우를 나타내는 기본 IntelliTest 논리를 변경합니다. 테스트는 지정된 예외를 throw하더라도 실패로 간주하지 않습니다.

**예제**

다음 테스트는 **Stack**의 생성자가 **ArgumentOutOfRangeException**을 throw할 수 있도록 지정합니다.

```
class Stack {
  int[] _elements;
  int _count;
  public Stack(int capacity) {
    if (capacity<0) throw new ArgumentOutOfRangeException();
    _elements = new int[capacity];
    _count = 0;
  }
  ...
}
```

필터는 다음과 같이 설비에 연결됩니다(어셈블리 또는 테스트 수준에서 정의될 수도 있음).

```
[PexMethod]
[PexAllowedException(typeof(ArgumentOutOfRangeException))]
class CtorTest(int capacity) {
  Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException
}
```

<a name="pexallowedexceptionfromassembly"></a>
## <a name="pexallowedexceptionfromassembly"></a>PexAllowedExceptionFromAssembly

[추가 정보](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromassemblyattribute.aspx)

<a name="pexallowedexceptionfromtype"></a>
## <a name="pexallowedexceptionfromtype"></a>PexAllowedExceptionFromType

[추가 정보](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeattribute.aspx)

<a name="pexallowedexceptionfromtypeundertest"></a>
## <a name="pexallowedexceptionfromtypeundertest"></a>PexAllowedExceptionFromTypeUnderTest

[추가 정보](https://msdn.microsoft.com/library/microsoft.pex.framework.validation.pexallowedexceptionfromtypeundertestattribute.aspx)

## <a name="got-feedback"></a>피드백이 있으신가요?

아이디어와 기능 요청을 **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**에 게시하세요.
