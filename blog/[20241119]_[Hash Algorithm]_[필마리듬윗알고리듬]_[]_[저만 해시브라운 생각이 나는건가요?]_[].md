맨날 곱하기 문제 약수 문제 이런거 풀다가 이번주부터 스토리형..? 알고리즘을 문제를 풀게 되었다.
튜터님께 '해시'를 통해 알고리즘을 푸는 것을 힌트로 받았다.
하지만 해시 알고리즘에 대해 알지 못해 유튜브를 검색했다.

[해시 알고리즘 5분만에 이해하기 - 개발자로 취직하기](https://www.youtube.com/watch?v=zFL29ydL9D8)

### Hash?
Key:Value의 구조를 갖는 자료구조
- Key : 무언가를 찾기 위한 검색어
- Value : 검색어로 나온 결과 값

우리는 친구의 번호를 검색할때, 친구의 이름을 검색하면 친구의 번호를 가져올 수 있다. 이때, 이름은 Key, 전화번호는 Value가 된다. 

만약, 전화번호가 Hash가 아닌 배열이었다면 어땠을까?
배열은 고유 인덱스인 정수로만 접근이 가능하다. 이름을 안다고 해서 이 String 값으로 번호를 가져올 수 없다. 따라서 해시가 없다면 반복문을 통해 내가 찾는 이름과 매칭이 되는지 확인해야 할 것이다.

Hash는 배열과 달리 String 타입이나 다른 어떤 데이터형을 기반으로 자료구조에 접근 및 관리가 가능하다. 데이터가 많아질 수록 단순한 반복문으로만 답을 도출하는데에 한계가 있다. Hash를 사용하여 간단하게 문제를 해결해보자.

#### 1️⃣ HashMap 생성  
#### 2️⃣ 값 넣기 `hashMap.put("A", true)`  
== `hashMap["A"] = true`  
이는 hashMap이라는 배열의 "A"번째 값이 true인 것과 같은 역할을 하게 된다. 
#### 3️⃣ 값 읽기 `var fin = hashMap.get("key")`  
`getOrDafault` 함수를 통해 key 값이 없을 때의 예외처리 가능하다.  
`getOrDafault("A", false)`와 같이 쓴다면 A가 있다면 값을 가져오고, 없다면 기본값인 false를 반환하게 된다.

언제 Hash를 써야 할까?  
-> String을 기반으로 정보를 기록하고 관리해야 할 때 유용

---

위 내용을 바탕으로 프로그래머스 [의상](https://school.programmers.co.kr/learn/courses/30/lessons/42578) 문제를 풀어보았다.

문제를 다시 보니 내가 착각하고 있던 것이 있었다. 결국 답은 조합의 개수를 물어보는 것이므로 각각의 옷을 어떻게 조합하는지는 몰라도 된다. 즉, 해시테이블을 만들때 Key는 의상 종류가 될 것이고, Value는 해당 종류의 옷 이름이 아닌 **가짓수를 Int형**으로 저장하면 된다.

그럼 가보자고.

#### 1. Dictionary를 이용해서 String 키값과 Int Value 값을 갖도록 만든다.


```swift
func solution(_ clothes:[[String]]) -> Int{
    
    var clothesTable = [String: Int]()
    
    for item in clothes {
        let category = item[1]
        clothesTable[category] == nil 
        ? (clothesTable[category] = 1)
        : (clothesTable[category]! += 1) 
    }

    return 0
}
```

반복문으로 받아온 clothes의 이중배열을 딕셔너리로 정리한다.
clothes의 각 행은 [의상의 이름, 의상의 종류]로 이루어져 있으므로, `let category = item[1]` 와 같이 상수로 할당해주었다.
만약 의상의 종류가 없다면, 딕셔너리에 해당 키값으로는 최초 등록하는 것이므로 값으로 1 값을 준다. 이미 해당 키가 있다면, 기존 값에 + 1 해준다.
이렇게 되면 각 종류별로 의상이 몇 개 있는지 파악할 수 있다.

#### 2. 각 카테고리 의상 수를 통해 경우의 수를 계산한다.

```swift
    func getNumberOfCases(table: Dictionary<String, Int>) -> Int {
    
    var numberOfCase = 1
    
    for number in table {
        numberOfCase = numberOfCase * (number.value + 1)
    }
    
    return numberOfCase - 1
}
```

딕셔너리를 파라미터로 받아서 경우의 수를 계산에 반환해주는 함수를 만들었다. 고민했던 부분은, 해당 옷 종류를 안입을 수도 있다는 것. 그렇다면 안 입는 경우를 + 1 해준다. (종류 개수 n + 안입는 경우 1) 반복문 내에서 각각의 수를 곱해서 모든 경우의 수를 구할 수 있다. 하지만, 이 경우 모두 안 입는 경우가 생긴다. 이를 고려하여 마지막 반환 값에 - 1 해준다.

`return getNumberOfCases(table: clothesTable)`
solution 함수 반환 값에 이 함수를 호출하고 정리한 딕셔너리를 넘겨주면 조건에 맞는 경우의 수를 알아낼 수 있다.