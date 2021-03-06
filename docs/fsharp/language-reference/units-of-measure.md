---
title: 측정 단위(F#)
description: '어떻게 부동 소수점 알아봅니다 및 F #의 부호 있는 정수 값, 측정 단위 길이, 볼륨 및 대용량을 나타내기 위해 일반적으로 사용 되는 연결 수입니다.'
ms.date: 05/16/2016
ms.openlocfilehash: 6075742ec80d9510be51d4565e3397931c9f68c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517428"
---
# <a name="units-of-measure"></a>측정 단위

F #의 부동 소수점 및 부호 있는 정수 값 대용량, 길이, 볼륨을 나타내기 위해 일반적으로 사용 되는 측정값을 단위가 연결 될 수 있습니다. 한지 확인 하려면 산술 관계 올바른 단위를 방지할 수 있는 컴파일러를 사용 하면 수량 단위를 사용 하 여 오류를 프로그래밍 합니다.


## <a name="syntax"></a>구문

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a>설명
이전 구문 정의 *단위 이름* 으로 측정 단위입니다. 이전에 정의 된 단위를 기준으로 새 측정값을 정의 하는 선택적 부분 사용 됩니다. 다음 줄에서는 측정값을 정의 하는 예를 들어 `cm` (센티미터).

```fsharp
[<Measure>] type cm
```

다음 줄에서는 측정값 정의 `ml` (밀리 리터) 입방 형 3 센티미터도 (`cm^3`).

```fsharp
[<Measure>] type ml = cm^3
```

이전 구문에서 *측정값* 은 단위를 포함 하는 수식입니다. 단위를 포함 하는 수식에서 정수 거듭제곱 (긍정 및 부정) 지원 되는, 단위 사이 공백이 표시 단위 두 개를 곱한 `*` 단위의 제품을 나타내기도 및 `/` 단위 몫을 나타냅니다. 역 단위에 대 한 음의 정수 power를 사용 하거나 또는 `/` 분자와 분모 단위 수식의 사이의 구분을 나타내는입니다. 분모의 여러 단위는 괄호로 묶어야 합니다. 후 공백으로 구분 된 단위를 `/` 분모의 경우 다음 모든 단위의 일부인 것으로 해석 되는 `*` 분자의 일부로 해석 됩니다.

1 단위 식 수량을 나타내거나 단독으로 또는 분자와 같이 다른 단위를 함께 사용할 수 있습니다. 으로 요금에 대해 단위는 작성 하는 예를 들어 `1/s`여기서 `s` 시간 (초)을 나타냅니다. 괄호 단위 수식에서 사용 되지 않습니다. 단위 수식의; 숫자 변환 상수를 지정 하지 않으면 그러나 단위를 사용 하 여 변환 상수를 개별적으로 정의할 수 있으며 단위 검사 계산에서 사용할 수 있습니다.

해당 하는 다양 한 방법으로 동일한 의미로 사용 하는 단위 수식은 작성할 수 있습니다. 따라서 컴파일러는 단위 수식 변환 음수 거듭제곱 평균은 그룹 단위를 단일 분자와 분모의 분자와 분모의 단위를 사전순으로 정렬 하며 일관 된 형식으로 변환 합니다.

예를 들어, 단위 수식을 `kg m s^-2` 하 고 `m /s s * kg` 으로 변환 됩니다 `kg m/s^2`합니다.

측정 단위를 사용 하 여 부동 소수점 식에 있습니다. 측정값의 관련된 단위와 함께 부동 소수점 숫자를 사용 하 여 다른 수준의 형식 안전성 더하고 약한 형식의 부동 소수점 숫자를 사용 하는 경우 수식에서 발생할 수 있는 단위 불일치 오류를 방지할 수 있습니다. 부동을 작성 하는 경우 단위를 사용 하는 지점 식, 식 단위와 일치 해야 합니다.

다음 예제와 같이 리터럴 꺾쇠 괄호 안에 단위 수식 사용 하 여 주석을 달 수 있습니다.

```fsharp
1.0<cm>
55.0<miles/hour>
```

수 고 꺾쇠 괄호; 사이 공백을 넣지 않습니다. 와 같은 리터럴 접미사를 포함할 수는 있지만 `f`다음 예제와 같이 합니다.

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

해당 기본 형식에서 리터럴 형식을 변경 하는 이러한 주석의 (같은 `float`) 차원이 지정 된 형식에 같은 `float<cm>` 또는 경우 `float<miles/hour>`합니다. 에 대 한 단위 주석을 `<1>` 되었음을 해당 유형과 수량을 나타내거나 단위 매개 변수 없이 기본 형식과 동일 합니다.

측정 단위의 유형의 부동 소수점 또는 부호 있는 정수 계열 형식 대괄호로 표시, 추가 단위 주석의 함께 합니다. 따라서 작성 하는 경우 변환 유형의 `g` (그램)를 `kg` (킬로그램) 다음과 같이 형식을 설명 합니다.

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

측정 단위를 확인 하는 컴파일 시간 단위에 대 한 사용 되지만 런타임 환경에서 유지 되지 않습니다. 따라서 성능을 적용 되지 않습니다.

측정 단위 형식일 뿐 아니라 부동 소수점 형식;에 적용할 수 있습니다. 그러나만 부동 소수점 형식은 정수 계열 형식 및 소수 형식 지원 차원이 수량에 서명 합니다. 따라서 이러한 기본 형식을 포함 하는 집계 및 기본 형식에서 측정 단위를 사용 하는 것이 하면 됩니다.

다음 예제에서는 측정 단위를 사용을 하는 방법을 보여 줍니다.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
다음 코드 예제에는 값을 가지는 부동 소수점 숫자에서 차원이 지정 된 부동 소수점 값으로 변환 하는 방법을 보여 줍니다. 곱하기만 1.0에서 차원을 1.0을 적용 합니다. 와 같은 함수에이 추상화할 수 있습니다 `degreesFahrenheit`합니다.

또한 부동 소수점 숫자 값을 가지는 함수에 차원이 지정 된 값을 전달할 때의 단위를 취소 하거나 해야 캐스팅할 `float` 를 사용 하 여는 `float` 연산자입니다. 이 예에서 나누면 `1.0<degC>` 에 대 한 인수에 대 한 `printf` 때문에 `printf` 치수 수량을 예상 합니다.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

다음 예제에서는 세션에서 출력 및 입력이이 코드를 보여 줍니다.

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a>일반 단위를 사용 하 여
데이터에서 연결 된 단위에 대해 작동 하는 제네릭 함수를 작성할 수 있습니다. 이렇게 하면 형식 매개 변수와 함께 제네릭 단위 형식을 지정 하 여 다음 코드 예제에 표시 된 대로 합니다.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a>집합체 형식은 제네릭 단위를 사용 하 여 만들기
다음 코드에는 제네릭 단위가 있는 개별 부동 소수점 값으로 이루어진 집합체 형식을 만드는 방법을 보여 줍니다. 따라서 다양 한 단위를 사용 하 여 작동 하는 단일 형식을 만들 수 있습니다. 또한 제네릭 단위 단위 집합을 가진 제네릭 형식을 다른 형식 보다 다양 한 단위를 사용 하 여 동일한 제네릭 형식 인지 확인 하 여 형식 안전성을 유지 합니다. 이 기법으로 `Measure` 특성 형식 매개 변수에 적용할 수 있습니다.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a>런타임 시 단위
측정 단위는 정적 형식 확인에 사용 됩니다. 부동 소수점 값을 컴파일하면 단위 런타임 시 손실 되므로 측정 단위를 제거 됩니다. 따라서 런타임에 단위 확인에 의존 하는 기능을 구현 하려고 수는 없습니다. 예를 들어, 구현를 `ToString` 단위를 인쇄 하는 함수 불가능 합니다.


## <a name="conversions"></a>변환
단위에 있는 형식을 변환 하려면 (예를 들어 `float<'u>`) 단위 없는 형식으로 표준 변환 함수를 사용할 수 있습니다. 예를 들어 사용할 수 있습니다 `float` 변환할는 `float` 다음 코드 에서처럼 단위에 있지 않은 값입니다.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

단위 값 단위 값으로 변환 하려면 적절 한 단위를 사용 하 여 주석이 추가 되는 1 또는 1.0 값으로 곱하면 하는 것이 됩니다. 그러나 상호 운용성 레이어를 작성 하는 것에 대 한 가지도 단위 값 단위를 사용 하 여 값으로 변환 하는 데 사용할 수 있는 몇 가지 명시적 함수입니다. 이러한 합니다 [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) 모듈입니다. 예를 들어 단위를 변환할 `float` 에 `float<cm>`를 사용 하 여 [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9)다음 코드에 표시 된 것 처럼 합니다.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-core-library"></a>F # 핵심 라이브러리의 측정 단위
단위 라이브러리에서 사용할 수는 `FSharp.Data.UnitSystems.SI` 네임 스페이스입니다. 기호 형식으로 모두의 SI 단위를 포함 (같은 `m` 미터에 대 한)에 `UnitSymbols` 하위 네임 스페이스와 전체 이름 (같은 `meter` 미터에 대 한)에서 `UnitNames` 하위 네임 스페이스입니다.


## <a name="see-also"></a>참고 항목
[F# 언어 참조](index.md)
