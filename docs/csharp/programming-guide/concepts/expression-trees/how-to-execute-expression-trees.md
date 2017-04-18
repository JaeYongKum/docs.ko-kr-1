---
title: "방법: 식 트리 실행(C#) | Microsoft 문서"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: get-started-article
dev_langs:
- CSharp
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
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
ms.openlocfilehash: 0e7d061644aa6c0f36b7a193ded5485000ad0309
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-execute-expression-trees-c"></a>방법: 식 트리 실행(C#)
이 항목에서는 식 트리를 실행하는 방법을 보여 줍니다. 식 트리를 실행할 때 값이 반환될 수 있거나, 메서드 호출 등의 작업만 수행할 수도 있습니다.  
  
 람다 식을 나타내는 식 트리만 실행할 수 있습니다. 람다 식을 나타내는 식 트리는 <xref:System.Linq.Expressions.LambdaExpression> 또는 <xref:System.Linq.Expressions.Expression%601> 형식입니다. 이러한 식 트리를 실행하려면 <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> 메서드를 호출하여 실행 가능한 대리자를 만든 후 대리자를 호출합니다.  
  
> [!NOTE]
>  대리자 형식을 알 수 없는 경우, 즉 람다 식이 <xref:System.Linq.Expressions.LambdaExpression> 형식이고 <xref:System.Linq.Expressions.Expression%601>이 아닌 경우 직접 호출하는 대신 대리자에서 <xref:System.Delegate.DynamicInvoke%2A> 메서드를 호출해야 합니다.  
  
 식 트리가 람다 식을 나타내지 않는 경우 <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> 메서드를 호출하여 원래 식 트리를 해당 본문으로 사용하는 새 람다 식을 만들 수 있습니다. 그런 다음 이 섹션의 앞부분에서 설명한 대로 람다 식을 실행할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 코드 예제에서는 람다 식을 만들고 실행하여 숫자의 거듭제곱을 나타내는 식 트리를 실행하는 방법을 보여 줍니다. 숫자의 거듭제곱을 나타내는 결과가 표시됩니다.  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a>코드 컴파일  
  
-   아직 참조되지 않는 경우 System.Core.dll에 대한 프로젝트 참조를 추가합니다.  
  
-   System.Linq.Expressions 네임스페이스를 포함합니다.  
  
## <a name="see-also"></a>참고 항목  
 [식 트리(C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)   
 [방법: 식 트리 수정(C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)