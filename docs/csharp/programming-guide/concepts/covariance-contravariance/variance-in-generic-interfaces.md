---
title: "제네릭 인터페이스의 가변성(C#) | Microsoft 문서"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4c4f3ab00b4de2a6f38858dd5f332db3d47eb85b
ms.lasthandoff: 03/13/2017

---
# <a name="variance-in-generic-interfaces-c"></a>제네릭 인터페이스의 가변성(C#)
.NET Framework 4에서는 기존의 몇몇 제네릭 인터페이스에 대한 가변성 지원이 추가되었습니다. 가변성 지원은 이러한 인터페이스를 구현하는 클래스의 암시적 변환을 가능하게 합니다. 다음 인터페이스는 현재 variant입니다.  
  
-   <xref:System.Collections.Generic.IEnumerable%601>(T는 공변(covariant))  
  
-   <xref:System.Collections.Generic.IEnumerator%601>(T는 공변(covariant))  
  
-   <xref:System.Linq.IQueryable%601>(T는 공변(covariant))  
  
-   <xref:System.Linq.IGrouping%602>(`TKey` 및 `TElement`는 공변(covariant))  
  
-   <xref:System.Collections.Generic.IComparer%601>(T는 반공변(contravariant))  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601>(T는 반공변(contravariant))  
  
-   <xref:System.IComparable%601>(T는 반공변(contravariant))  
  
 공변성(covariance)은 메서드가 인터페이스의 제네릭 형식 매개 변수에 정의된 것보다 더 많은 수의 파생된 반환 형식을 갖도록 허용합니다. 공변성(covariance) 기능을 설명하려면 `IEnumerable<Object>` 및 `IEnumerable<String>`이라는 제네릭 인터페이스를 고려하세요. `IEnumerable<String>` 인터페이스는 `IEnumerable<Object>` 인터페이스를 상속하지 않습니다. 그러나 `String` 형식은 `Object` 형식을 상속하며, 경우에 따라 이러한 인터페이스의 개체를 서로 할당할 수 있습니다. 다음 코드 예제에서 이를 확인할 수 있습니다.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 .NET Framework의 이전 버전에서는 이 코드가 `Option Strict On` 상태의 C#에서 컴파일 오류를 일으킵니다. 그러나 <xref:System.Collections.Generic.IEnumerable%601> 인터페이스는 공변(covariant) 이므로 이제 다음 예제와 같이 `objects` 대신 `strings`를 사용할 수 있습니다.  
  
 반공변성(Contravariance)은 메서드가 인터페이스의 제네릭 매개 변수에 지정된 것보다 더 적은 수의 파생된 형식의 인수 형식을 갖도록 허용합니다. 반공변성(contravariance)을 설명하기 위해, 사용자가 `BaseComparer` 클래스를 만들어 `BaseClass` 클래스의 인스턴스를 비교한다고 가정합니다. `BaseComparer` 클래스는 `IEqualityComparer<BaseClass>` 인터페이스를 구현합니다. <xref:System.Collections.Generic.IEqualityComparer%601> 인터페이스는 이제 반공변(contravariant)이므로 `BaseClass` 클래스를 상속하는 클래스의 인스턴스를 비교하는 데 `BaseComparer`를 사용할 수 있습니다. 다음 코드 예제에서 이를 확인할 수 있습니다.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 추가 예제는 [제네릭 컬렉션용 인터페이스의 가변성 사용(C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)을 참조하세요.  
  
 제네릭 인터페이스의 가변성은 참조 형식에 대해서만 지원됩니다. 값 형식은 가변성을 지원하지 않습니다. 정수는 값 형식으로 표시되므로 예를 들어 `IEnumerable<int>`를 `IEnumerable<object>`로 암시적으로 변환할 수 없습니다.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Variant 인터페이스를 구현하는 클래스는 여전히 비 variant라는 점에 유의해야 합니다. 예를 들어 <xref:System.Collections.Generic.List%601>은 공변(covariant) 인터페이스 <xref:System.Collections.Generic.IEnumerable%601>을 구현하지만 명시적으로 `List<Object>`를 `List<String>`으로 변환할 수 없습니다. 다음 코드 예제에서 이 내용을 보여 줍니다.  
  
```cs  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a>참고 항목  
 [제네릭 컬렉션용 인터페이스의 가변성 사용(C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)   
 [Variant 제네릭 인터페이스 만들기(C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)   
 [제네릭 인터페이스](http://msdn.microsoft.com/library/88bf5b04-d371-4edb-ba38-01ec7cabaacf)   
 [대리자의 가변성(C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)