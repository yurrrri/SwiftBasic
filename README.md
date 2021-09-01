# SwiftBasic
 스위프트 문법 공부

Q. 변수와 상수가 있는데, 언제 변수를 사용하고 언제 상수를 사용하는가?

- 변수 : 값이 변할 수 있는 값 → 값이 변경이 가능할때 사용
    - swift에서 var
    - ex) var yuri:Int = 3 (자료형이 명확할 경우, 생략가능)
- 상수 : 항상 값이 같음 → 값이 변할일이 없을때?
    - swift에서 let
    - ex) let yuri:Int = 3

Q. 기본 자료형 4 가지는 무엇인가?

- Bool, Int/UInt, Float/Double, Character/String
- Int : 정수타입 /  UInt: 양의 정수 타입
- Character, String : **큰 따옴표("")로 감쌈**

Q. Any, AnyObject, nil

- Any : Swift의 모든타입을 지칭하는 키워드
- AnyObject : 모든 클래스 타입을 지칭하는 프로토콜
- nil == null

Q. if 절 문법을 사용하여 라면끓이는 방법을 의사코드로 작성하라.
```swift
if "물이 끓는다" {

   "스프를 넣는다"
   
   "면을 넣는다"
   
   if "면이 익는다"{
   
     "계란을 넣는다"
     
     "호로록 맛있게 먹는다"
     
   }  
}
```
   
Q. 1~10 사이의 자연수가 구성요소로 있는 배열이 있다. 여기서 5가 들어 있는 요소에 접근하는 방법은 무엇인가?

-  Array - 순서가 있는 리스트 컬렉션
```swift
//array 생성

var integers: Array<Int> = Array<Int>() == [Int]()
var strings: [String] = [String] ()
var characters: [Character] = []
let arrays = [1, 2, 3] //let이기때문에 불변 array

//추가
integers.append(100)

//포함여부
integers.contains(100)

//삭제
integers.remove(at:0)
integers.removeLast() //마지막 요소 제거
integers.removeAll() //모든 요소 제거
 
-  Dictionary - 키와 값의 쌍으로 이루어진 컬렉션
```swift
//Key가 String 타입이고 Value가 Any인 빈 Dictionary 생성

var anyDictionary: Dictionary<String, Any> = [String: Any]()
var anyDictionary: Dictionary <String, Any> = Dictionary<String, Any>()
var anyDictionary: Dictionary <String, Any> = [:]
var anyDictionary: [String: Any] = Dictionary<String, Any>()
var anyDictionary: [String: Any] = [String: Any]()
var anyDictionary: [String: Any] = [:]
var anyDictionary = [String: Any]()

//키에 해당하는 값 할당
anyDictionary["someKey"] = "value"
anyDictionary["anotherKey"] = 100

//딕셔너리 초기화**
let initalizedDictionary: [String: String] = ["name": "yagom", "gender": "male"]
```
 
-  Set
   - 1) 순서가 없고, 멤버가 유일한 컬렉션 - 2)집합처럼 중복 불가능

```swift
//빈 Int Set 생성
var integerSet: Set<Int> = Set<Int>()
integerSet.insert(1)
integerSet.insert(100)
integerSet.insert(99)
integerSet.insert(99)
integerSet.insert(99)
print(integerSet) //[100, 99, 1]
 
//삭제
integerSet.remove(100)
integerSet.removeFirst()
integerSet.count //1
```

Q. 독립변수와 종속변수의 관계를 표현한 표현식을 무엇이라고 하는가? => 클로저
{ () -> 반환타입 in
  실행코드
}

```swift
// 함수를 사용한다면
func sumFunction(a: Int, b: Int) -> Int {
    return a + b
}

var sumResult: Int = sumFunction(a: 1, b: 2)

print(sumResult) // 3

// 클로저의 사용
var sum: (Int, Int) -> Int = { (a: Int, b: Int) -> Int in
    return a + b
}

sumResult = sum(1, 2)
print(sumResult) // 3

// 함수는 클로저의 일종이므로
// sum 변수에는 당연히 함수도 할당할 수 있습니다
sum = sumFunction(a:b:)

sumResult = sum(1, 2)
print(sumResult) // 3


//MARK: - 함수의 전달인자로서의 클로저

let add: (Int, Int) -> Int
add = { (a: Int, b: Int) -> Int in
    return a + b
}

let substract: (Int, Int) -> Int
substract = { (a: Int, b: Int) -> Int in
    return a - b
}

let divide: (Int, Int) -> Int
divide = { (a: Int, b: Int) -> Int in
    return a / b
}

func calculate(a: Int, b: Int, method: (Int, Int) -> Int) -> Int {
    return method(a, b)
}

var calculated: Int

calculated = calculate(a: 50, b: 10, method: add)

print(calculated) // 60

calculated = calculate(a: 50, b: 10, method: substract)

print(calculated) // 40

calculated = calculate(a: 50, b: 10, method: divide)

print(calculated) // 5

calculated = calculate(a: 50, b: 10, method: { (left: Int, right: Int) -> Int in
    return left * right
})

print(calculated) // 500


/* 클로저 고급 */

var result: Int

//MARK: - 후행 클로저
// 클로저가 함수의 마지막 전달인자라면
// 마지막 매개변수 이름을 생략한 후
// 함수 소괄호 외부에 클로저를 구현할 수 있습니다

result = calculate(a: 10, b: 10) { (left: Int, right: Int) -> Int in
    return left + right
}

print(result) // 20


//MARK: - 반환타입 생략
// calculate 함수의 method 매개변수는
// Int 타입을 반환할 것이라는 사실을 컴파일러도 알기 때문에
// 굳이 클로저에서 반환타입을 명시해 주지 않아도 됩니다
// 대신 in 키워드는 생략할 수 없습니다

result = calculate(a: 10, b: 10, method: { (left: Int, right: Int) in
    return left + right
})

print(result) // 20

// 후행클로저와 함께 사용할 수도 있습니다
result = calculate(a: 10, b: 10) { (left: Int, right: Int) in
    return left + right
}

//MARK: - 단축 인자이름
// 클로저의 매개변수 이름이 굳이 불필요하다면 단축 인자이름을 활용할 수 있습니다
// 단축 인자이름은 클로저의 매개변수의 순서대로 $0, $1... 처럼 표현합니다

result = calculate(a: 10, b: 10, method: {
    return $0 + $1
})

print(result) // 20

// 당연히 후행 클로저와 함께 사용할 수 있습니다
result = calculate(a: 10, b: 10) {
    return $0 + $1
}

print(result) // 20


//MARK: - 암시적 반환 표현
// 클로저가 반환하는 값이 있다면
// 클로저의 마지막 줄의 결과값은 암시적으로 반환값으로 취급합니다

result = calculate(a: 10, b: 10) {
    $0 + $1
}

print(result) // 20

// 간결하게 한 줄로 표현해 줄 수도 있습니다
result = calculate(a: 10, b: 10) { $0 + $1 }

print(result) // 20

// 축약하지 않은 클로저 문법과 축약 후의 문법 비교

result = calculate(a: 10, b: 10, method: { (left: Int, right: Int) -> Int in
    return left + right
})

result = calculate(a: 10, b: 10) { $0 + $1 }

print(result) // 20
```

Q. 클래스와 구조체의 차이점은 무엇인가?

구조체는 값 타입, 클래스는 참조 타입이라는 점에서 큰 차이점
클래스는 다중상속 x

 - 구조체
 ```swift
 struct Sample {
    // 가변 프로퍼티
    var mutableProperty: Int = 100
    
    // 불변 프로퍼티
    let immutableProperty: Int = 100
    
    // 타입 프로퍼티
    static var typeProperty: Int = 100
    
    // 인스턴스 메서드
    func instanceMethod() {
        print("instance method")
    }
    
    // 타입 메서드
    static func typeMethod() {
        print("type method")
    }
}

//MARK: 구조체 사용

// 가변 인스턴스
var mutable: Sample = Sample()

// 불변 인스턴스
let immutable: Sample = Sample()

// 불변 인스턴스는 아무리 가변 프로퍼티라도
// 인스턴스 생성 후에 수정할 수 없습니다
// 컴파일 오류 발생
//immutable.immutableProperty = 200

// 타입 프로퍼티 및 메서드
Sample.typeProperty = 300
Sample.typeMethod() // type method

// 인스턴스에서는 타입 프로퍼티나 타입 메서드를
// 사용할 수 없습니다
// 컴파일 오류 발생
//mutable.typeProperty = 400
//mutable.typeMethod()


//MARK: - 학생 구조체

struct Student {
    // 가변 프로퍼티
    var name: String = "unknown"
    
    // 키워드도 `로 묶어주면 이름으로 사용할 수 있습니다
    var `class`: String = "Swift"
    
    // 타입 메서드
    static func selfIntroduce() {
        print("학생타입입니다")
    }
    
    // 인스턴스 메서드
    // self는 인스턴스 자신을 지칭하며, 몇몇 경우를 제외하고 사용은 선택사항입니다
    func selfIntroduce() {
        print("저는 \(self.class)반 \(name)입니다")
    }
}

// 타입 메서드 사용
Student.selfIntroduce() // 학생타입입니다

// 가변 인스턴스 생성
var yagom: Student = Student()
yagom.name = "yagom"
yagom.class = "스위프트"
yagom.selfIntroduce()   // 저는 스위프트반 yagom입니다

// 불변 인스턴스 생성
let jina: Student = Student()

// 불변 인스턴스이므로 프로퍼티 값 변경 불가
// 컴파일 오류 발생
//jina.name = "jina"
jina.selfIntroduce() // 저는 Swift반 unknown입니다

```

 - 클래스

```swift
class Sample {
    // 가변 프로퍼티
    var mutableProperty: Int = 100
    
    // 불변 프로퍼티
    let immutableProperty: Int = 100
    
    // 타입 프로퍼티
    static var typeProperty: Int = 100
    
    // 인스턴스 메서드
    func instanceMethod() {
        print("instance method")
    }
    
    // 타입 메서드
    // 재정의 불가 타입 메서드 - static
    static func typeMethod() {
        print("type method - static")
    }
    
    // 재정의 가능 타입 메서드 - class
    class func classMethod() {
        print("type method - class")
    }
}

// 인스턴스 생성 - 참조정보 수정 가능
var mutableReference: Sample = Sample()

mutableReference.mutableProperty = 200

// 불변 프로퍼티는 인스턴스 생성 후 수정할 수 없습니다
// 컴파일 오류 발생
//mutableReference.immutableProperty = 200

// 인스턴스 생성 - 참조정보 수정 불가
let immutableReference: Sample = Sample()

// 클래스의 인스턴스는 참조 타입이므로 let으로 선언되었더라도
// 인스턴스 프로퍼티의 값 변경이 가능합니다
immutableReference.mutableProperty = 200

// 다만 참조정보를 변경할 수는 없습니다
// 컴파일 오류 발생
//immutableReference = mutableReference

// 참조 타입이라도 불변 인스턴스는
// 인스턴스 생성 후에 수정할 수 없습니다
// 컴파일 오류 발생
//immutableReference.immutableProperty = 200


// 타입 프로퍼티 및 메서드
Sample.typeProperty = 300
Sample.typeMethod() // type method

// 인스턴스에서는 타입 프로퍼티나 타입 메서드를
// 사용할 수 없습니다
// 컴파일 오류 발생
//mutableReference.typeProperty = 400
//mutableReference.typeMethod()


//MARK: - 학생 클래스

class Student {
    // 가변 프로퍼티
    var name: String = "unknown"
    
    // 키워드도 `로 묶어주면 이름으로 사용할 수 있습니다
    var `class`: String = "Swift"
    
    // 타입 메서드

    class func selfIntroduce() {
        print("학생타입입니다")
    }
    
    // 인스턴스 메서드
    // self는 인스턴스 자신을 지칭하며, 몇몇 경우를 제외하고 사용은 선택사항입니다
    func selfIntroduce() {
        print("저는 \(self.class)반 \(name)입니다")
    }
}

// 타입 메서드 사용
Student.selfIntroduce() // 학생타입입니다

// 인스턴스 생성
var yagom: Student = Student()
yagom.name = "yagom"
yagom.class = "스위프트"
yagom.selfIntroduce()   // 저는 스위프트반 yagom입니다

// 인스턴스 생성
let jina: Student = Student()
jina.name = "jina"
jina.selfIntroduce() // 저는 Swift반 jina입니다

```

Q. 옵셔널은 무엇인가?
 - 값이 있을수도있고, 없을수도 있는 변수
 - nil의 가능성을 명시적으로 표현
 - 옵셔널이 아닌 변수는 nil 확인을 하지 않아도 되므로 효율적
 - 스위프트의 특징 중 하나인 안정성을 문법으로 담보하는 기능
 - var optionalValue: Int? = 100
 
 - 암시적 추출 옵셔널 : 변수 뒤에 느낌표를 붙임 (!)
   - 얘 뭔지 모르겠음... 넌 누구냐
 
 - 옵셔널 바인딩
  - nil 체크 + 안전한 값 추출 => 값이 있으면 꺼내오고, 아니면 아니고
 
 ```swift
// ,를 사용해 한 번에 여러 옵셔널을 바인딩 할 수 있습니다
// 모든 옵셔널에 값이 있을 때만 동작합니다
myName = "yagom"
yourName = nil

if let name = myName, let friend = yourName {
    print("\(name) and \(friend)")
}
// yourName이 nil이기 때문에 실행되지 않습니다

yourName = "hana"

if let name = myName, let friend = yourName {
    print("\(name) and \(friend)")
}
// yagom and hana
 ```
 
 - 옵셔널 강제추출
   - 값이 있는지 없는지 확인하지 않고 바로 값을 꺼내옴

- 옵셔널 기본값
  - ?? ex) delegate?.passData(sender.text ?? "기본값") 

```swift
printName(myName!) // 강제추출 : yagom

myName = nil

//print(myName!)
// 강제추출시 값이 없으므로 런타임 오류 발생

yourName = nil

//printName(yourName)
// nil 값이 전달되기 때문에 런타임 오류발생
```

Q. 부모클래스와 자식클래스의 예시를 UIKit에서 들어보시오.

Q. 익스텐션은 클래스와 차이점은 무엇인가?
 - 클래스의 상속은 클래스 타입에서만 가능하지만 익스텐션은 구조체, 클래스, 프로토콜 등에 적용이 가능합니다. 
 - 상속을 받으면 기존 기능을 재정의할 수 있지만, 익스텐션은 재정의할 수 없음
