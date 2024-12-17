공부하다보니 코틀린에서는 분명 늦은초기화의 종류가 `latest var` 과 `let ... by lazy` 가 있었는데 스위프트는 `lazy var` 만 가능했다.

Kotlin과 Swift의 늦은 초기화(Late Initialization) 패턴에 대해 알아보자.

## 1. Kotlin의 늦은 초기화:  

***1️⃣ lateinit var***
- var로만 선언 가능 (val 불가)
- null을 허용하지 않는 타입에만 사용
- primitive type(Int, Boolean 등)에는 사용할 수 없음
- 초기화 전에 접근하면 UninitializedPropertyAccessException 발생

```swift
lateinit var name: String
```

***2️⃣ by lazy***
- val에만 사용 가능 (읽기 전용)
- 처음 접근할 때 한 번만 초기화됨
- 람다 식으로 초기화 로직 정의

```swift
val name: String by lazy {
    // 초기화 로직
    "Minji"
}
```

## 2. Swift의 늦은 초기화

***1️⃣ lazy var***
- var로 선언 (let 불가)
- 처음 접근할 때 한 번만 초기화됨
- 클래스와 구조체에서만 사용 가능

```swift
lazy var name: String = {
    // 초기화 로직
    return "Minji"
}()
```

***2️⃣ Optional 이용***
- let/var 모두 가능
- 값이 있을 수도 있고 없을 수도 있음을 나타냄
- nil 가능

```swift
var name: String?  // 옵셔널 var
let age: Int?      // 옵셔널 let
```



## Kotlin의 by lazy와 Swift의 lazy var

Kotlin의 by lazy와 Swift의 lazy var는 비슷한 역할을 하는것 같은데, 왜 코틀린은 let만 가능하고 Swift는 var만 가능할까?

Kotlin의 `by lazy` 가 val(let)만 가능한 이유는 "한 번 초기화된 후 변경되지 않는다"는 lazy initialization의 원칙을 더 엄격하게 지키기 위함이다.
lazy 초기화는 첫 접근 시점에 한 번만 실행되어야 하는데, var로 허용하면 값이 변경될 수 있어 이 원칙이 깨질 수 있다.  
Kotlin은 함수형 프로그래밍의 영향을 받아 **불변성(immutability)** 이 강조된다.

반면, Swift의 `lazy var` 이 var만 가능한 이유는 let(상수)의 경우 선언과 동시에 초기화되어야 한다는 Swift의 기본 원칙 때문이다. lazy는 초기화를 지연시키는 것인데, let은 즉시 초기화를 요구하므로 이가 서로 모순된다고 보는 것.  
Swift에서 let은 **컴파일 시점에 값이 확정되어야 한다**는 더 엄격한 규칙을 가지고 있다.

즉, 두 언어 모두 type safety와 명확성을 추구하지만, 그것을 실현하는 방식이 다르다. **Kotlin은 값의 불변성에 초점을 맞추고, Swift는 초기화 시점의 명확성에 더 중점을 두는 것이다.**
