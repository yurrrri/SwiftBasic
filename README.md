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
- Character, String : 큰 따옴표("")로 감쌈

Q. Any, AnyObject, nil

- Any : Swift의 모든타입을 지칭하는 키워드
- AnyObject : 모든 클래스 타입을 지칭하는 프로토콜
- nil == null

Q. if 절 문법을 사용하여 라면끓이는 방법을 의사코드로 작성하라.

if "물이 끓는다" {

   "스프를 넣는다"
   
   "면을 넣는다"
   
   if "면이 익는다"{
   
     "계란을 넣는다"
     
     "호로록 맛있게 먹는다"
     
   }
   
}
   
Q. 1~10 사이의 자연수가 구성요소로 있는 배열이 있다. 여기서 5가 들어 있는 요소에 접근하는 방법은 무엇인가?

-  Array - 순서가 있는 리스트 컬렉션
    - **array 생성** 
      - var integers: Array<Int> = Array<Int> () == [Int] ()
      - var strings: [String] = [String] ()
      - var characters: [Character] = []
      - let arrays = [1, 2, 3] //let이기때문에 불변 array
    - **추가**
      - integers.append(100)
    - **포함여부**
      - integers.contains(100)
    - **삭제**
      - integers.remove(at:0)
      - integers.removeLast() //마지막 요소 제거
      - integers.removeAll() //모든 요소 제거
 
-  Dictionary - 키와 값의 쌍으로 이루어진 컬렉션
   - **Key가 String 타입이고 Value가 Any인 빈 Dictionary 생성**
     - var anyDictionary: Dictionary<String, Any> = [String: Any] ()
     - var anyDictionary: Dictionary <String, Any> = Dictionary<String, Any>()
     - var anyDictionary: Dictionary <String, Any> = [:]
     - var anyDictionary: [String: Any] = Dictionary<String, Any>()
     - var anyDictionary: [String: Any] = [String: Any]()
     - var anyDictionary: [String: Any] = [:]
     - var anyDictionary = [String: Any] ()
   - **키에 해당하는 값 할당**
     - anyDictionary["someKey"] = "value"
     - anyDictionary["anotherKey"] = 100
   - **딕셔너리 초기화**
     - let initalizedDictionary: [String: String] = ["name": "yagom", "gender": "male"]
 
-  Set 
   - 1) 순서가 없고, 멤버가 유일한 컬렉션 - 2)집합처럼 중복 불가능
   - **빈 Int Set 생성**
     - var integerSet: Set<Int> = Set<Int>()
     - integerSet.insert(1)
     - integerSet.insert(100)
     - integerSet.insert(99)
     - integerSet.insert(99)
     - integerSet.insert(99)
     - print(integerSet) //[100, 99, 1]
 
   - 삭제
     - integerSet.remove(100)
     - integerSet.removeFirst()
     - integerSet.count //1

Q. 독립변수와 종속변수의 관계를 표현한 표현식을 무엇이라고 하는가?

Q. 클래스와 구조체의 차이점은 무엇인가?

Q. 옵셔널은 무엇인가?
 - 값이 있을수도있고, 없을수도 있는 변수
 - nil의 가능성을 명시적으로 표현
 - 옵셔널이 아닌 변수는 nil 확인을 하지 않아도 되므로 효율적

Q. 부모클래스와 자식클래스의 예시를 UIKit에서 들어보시오.

Q. 익스텐션은 클래스와 차이점은 무엇인가?
