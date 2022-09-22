[다음](https://brunch.co.kr/brunchbook/dartforflutter)을 참고해서 공부한 내용이다.

# Dart

- 모든 변수는 객체다  
모든 객체는 클래스의 인스턴스 이므로 숫자, 함수, null도 객체다  
모든 객체는 Object 클래스로부터 상속된다
- 타입을 명시적으로 지정할 수 있고 var나 dynamic을 사용해서 지정하지 않을 수 있다  
var는 한 번 타입이 결정되면 바꿀 수 없지만  
dynamic은 타입 변경이 가능하다
- 제네릭 타입을 지원한다  
제네릭 : 클래스 외부에서 타입을 지정하는 것으로  
잘못된 타입을 컴파일 단계에서 걸러낼 수 있고 데이터 파악이 쉬워진다는 장점이 있다
### Dart Keyword  

- 식별자 : 변수, 함수 등의 이름
  - 내장 식별자  
	- abstract [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2001.%20%ED%81%B4%EB%9E%98%EC%8A%A4,%20%EC%B6%94%EC%83%81%ED%81%B4%EB%9E%98%EC%8A%A4,%20%EC%83%9D%EC%84%B1%EC%9E%90,%20%EC%83%81%EC%86%8D.md)
	- as
	- convariant
	- deferred
	- dynamic
	- export
	- external
	- factory
	- get
	- implements [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2001.%20%ED%81%B4%EB%9E%98%EC%8A%A4,%20%EC%B6%94%EC%83%81%ED%81%B4%EB%9E%98%EC%8A%A4,%20%EC%83%9D%EC%84%B1%EC%9E%90,%20%EC%83%81%EC%86%8D.md)
	- import
	- interface
	- library
	- mixin
	- operator
	- part
	- set
	- static
	- typedef

- 문맥 키워드
  - sync 
  - async
  - hide
  - on
  - show
- 예약어 : 식별자로 사용할 수 없는 단어
  - assert [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2002.%20%EC%A1%B0%EA%B1%B4%EB%AC%B8%2C%20%EB%B0%98%EB%B3%B5%EB%AC%B8%20.md)
  - break [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2002.%20%EC%A1%B0%EA%B1%B4%EB%AC%B8%2C%20%EB%B0%98%EB%B3%B5%EB%AC%B8%20.md)
  - case [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2002.%20%EC%A1%B0%EA%B1%B4%EB%AC%B8%2C%20%EB%B0%98%EB%B3%B5%EB%AC%B8%20.md)
  - catch
  - default [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2002.%20%EC%A1%B0%EA%B1%B4%EB%AC%B8%2C%20%EB%B0%98%EB%B3%B5%EB%AC%B8%20.md)
  - do
  - else [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2002.%20%EC%A1%B0%EA%B1%B4%EB%AC%B8%2C%20%EB%B0%98%EB%B3%B5%EB%AC%B8%20.md)
  - enum
  - extends [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2001.%20%ED%81%B4%EB%9E%98%EC%8A%A4,%20%EC%B6%94%EC%83%81%ED%81%B4%EB%9E%98%EC%8A%A4,%20%EC%83%9D%EC%84%B1%EC%9E%90,%20%EC%83%81%EC%86%8D.md)
  - false
  - final
  - finally
  - for [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2002.%20%EC%A1%B0%EA%B1%B4%EB%AC%B8%2C%20%EB%B0%98%EB%B3%B5%EB%AC%B8%20.md)
  - if [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2002.%20%EC%A1%B0%EA%B1%B4%EB%AC%B8%2C%20%EB%B0%98%EB%B3%B5%EB%AC%B8%20.md)
  - in
  - is
  - new
  - null
  - rethrow
  - return
  - super
  - switch
  - this
  - throw
  - true
  - try
  - var
  - void
  - while [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2002.%20%EC%A1%B0%EA%B1%B4%EB%AC%B8%2C%20%EB%B0%98%EB%B3%B5%EB%AC%B8%20.md)
  - with
 
### 타입
- num : int와 double의 supertype
- int : 정수
- double : 실수
- String : 문자열
- bool : true / false
- var : 타입 미지정 및 타입 변경 불가
- dynamic : 타입 미지정 및 타입 변경 가능
- List : 배열
- Set : 순서가 없고 중복이 없는 collection
- Map : key-value 형태의 collection
- Class [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2001.%20%ED%81%B4%EB%9E%98%EC%8A%A4,%20%EC%B6%94%EC%83%81%ED%81%B4%EB%9E%98%EC%8A%A4,%20%EC%83%9D%EC%84%B1%EC%9E%90,%20%EC%83%81%EC%86%8D.md)
### 변수
기본 형태  
```dart
String name = '최병민'; 
// 타입 변수명 = 초기값;  
```  
Dart의 변수는 참조(reference)를 저장한다  
즉, 위의 name변수는 '최병민'이라는 값을 가진 String객체에 대한 참조를 가지는 것이다

- var를 통해 선언된 변수는 초기값을 참고하여 해당 변수의 타입을 추론한다.
```dart
var num = 1000;
num = '천'; // error
```
- dynamic 타입을 사용하면 위의 문제를해결할 수 있고, 최상위 클래스인 Object를 이용해도 가능하다
```dart
dynamic num1 = 1000;
num1 = '천';
Object num2 = 10000;
num2 = '만';
```
- 하지만 가급적이면 명시적으로 타입을 지정할 수 있도록 해야 한다

### 상수
- final : 런타임 시점에 값이 결정됨
- const : 컴파일 시점에 값이 결정됨



### 함수

- 다트는 완전한 객체지향언어이다  
-> 모든 것이 객체이기 때문에 함수도 객체다  
- 이로인해 발생하는 특징들  
	1. 변수가 함수를 참조할 수 있다  
	2. 함수의 인자로 함수를 전달할 수 있다
	3. 이름있는 선택 매개 변수
	4. 위치적 선택 매개 변수
	5. 익명함수와 람다

##### 1. 변수가 함수를 참조할 수 있다
```dart
// 타입 변수명 = 함수(){...}
var name = getName(){...}
```

##### 2. 함수의 인자로 함수를 전달할 수 있다

```dart
// 함수A(함수B(), 함수C()){...}
ind add(int a, int b){return a+b;}
ind sub(int a, int b){return a-b;}
ind multi(int a, int b){return a*b;}
main(){
	int a = 10;
    int b = 5; 
    print(multi(add(a,b), sub(a,b));
    // 15*5 = 75
}
```
##### 3. 이름있는 선택 매개 변수  => null safety문제인지 확인 필요 / 
함수 호출시 매개변수에 인자 값을 넘겨줄 때 매개변수명을 이용해서 인자값을 넘겨줄 수 있다  
이때 인자 값을 넘겨주는 매개변수는 {}로 감싸줘야한다


##### 4. 위치적 선택 매개변수
미리 초기값을 설정해놓고 함수 호출시 매개 변수를 생략하면 초기값을 사용한다
```dart
// 함수(매개변수,[매개변수1 = 초기값, 매개변수2 = 초기값]){...}
getAddress(city,[district = '강남', zipcode = '111122']){...}

// 값을 변경하기 위해 매개변수를 넘겨줄 대 위치를 잘 체크해줘야한다
getAddress('서울','012345');
// 위와같이 호출하면 zipcode가 아닌 district에 012345를 넘겨주게됨
```

##### 5. 익명함수와 람다
- 익명함수 기본 형태
```dart
// (매개변수명){표현식;}
(a,b){a+b;}
```
- 람다식 기본 형태
```dart
// (매개변수명)=>표현식;
(a,b) => a-b;a
```


### 연산자
- 산술 연산자
- 할당 연산자
- 관계 연산자
- 비트 & 시프트 연산자
- 타입검사 연산자
- 조건 표현식
- 캐스케이트 표현

##### 1. 산술연산자
`+` `-` `/` `~/` `&` `++` `--`

~/ : 나눈 후 몫을 구하는 연산자  
% : 나눈 후 나머지를 구하는 연산자

##### 2. 할당 연산자
`=` `+=` `-=` `/=` `~/=`

: 좌항 자신의 값에 우항의 값을 연산하는 것

##### 3. 관계 연산자
`==` `!=` `>` `>=` `<` `<=`

##### 4. 비트 & 시프트 연산자
- 비트 연산자 
`&` : 비트 AND 연산자 : 두 개의 피연산자으 비트 모두 1일때 1을 반환   
`|` : 비트 OR 연산자 : 두 개의 피연산자의 비트 중 하나라도 1이면 1을 반환  
`^` : 비트 XOR 연산자 : 두 개의 피연산자의 비트 중 하나만 1일때 1을 반환   
`~` : 비트 NOT 연산자 : 비트가 1이면 0으로 0이면 1로 반전  

- 비트 시프트 연산자  
`<<` `>>`  
= 비트 이동 연산자  
: 지정한 수만큼 비트를 좌/우로 이동시킨다
```dart
main(){
	int a = 3; // 0011
  int b = 12; // 1100
  print(a&b); // 0011 & 1100 => 0000 : 0출력
  print(a|b); // 0011 | 1100 => 1111 : 15출력
  print(a^b); // 0011 ^ 1100 => 1111 : 15출력
  print(a<<1); // 0011 => 0110 : 6출력
  print(a>>1); // 0011 => 0001 : 1출력
}
```
##### 5. 타입 검사 연산자

`as` : 형변환  
`is` : 객체가 특정 타입이면 true  
`is!` : 객체가 특정타입이면 false(특정 타입이 아니면 true)

##### 6. 조건 표현식
- 삼항 연산자  
: `조건 ? 표현식 1 : 표현식 2`   
조건이 true면 표현식 1 false면 표현식 2 실행  

- 조건적 멤버 접근 연산자  
: `좌항?.우항`  
좌항이 null이면 null을 리턴, 아니면 우항의 값을 리턴  

- ?? 연산자  
: `좌항 ?? 우항`  
좌항이 null이 아니면 좌항 값을 리턴, null이면 우항 값을 리턴

##### 7. 캐스케이트 표기법
: 한 객체로 해당 객체의 속성이나 멤버 함수를 연속적으로 호출할 때 유용하다
```dart
class Employee{
  String name = '';
  int? age;
  
  void setAge(int age){
    this.age = age;
  }
  void showInfo(){
    print('$name is $age old');
  }
}

main(){
	Employee employee = Employee()
  	// 캐스케이드 표현식 사용  
    ..name = '최병민'
    ..setAge(32)
    ..showInfo();
  
  // 캐스케이드 표현식 미사용
  //   employee.name = '최병민';
  //   employee.setAge(32);
  //   employee.showInfo();
  
 
  // 출력 : 최병민 is 32 old
}
```
## 조건문 & 반복문 [링크](https://github.com/coqoa/TIL/blob/main/Dart/B.%20%EC%8B%AC%ED%99%94%20-%2002.%20%EC%A1%B0%EA%B1%B4%EB%AC%B8%2C%20%EB%B0%98%EB%B3%B5%EB%AC%B8%20.md)


## 접근 지정자
접근 지정자를 이용해서 캡슐화 할 수 있고 이를 통해 데이터 은닉을 구현할 수 있다.
- public : 아무런 키워드가 없으면 public
- private : 변수나 메서드 앞에 언더바(_)가 잇으면 private
```dart
//person.dart
class Person{
  String name;
  int _age;
  eat(){
  	print('eat');
  }
  _sleep(){
  	print('zzZ);
  }
}
```
- person.dart의 private으로 선언된 멤버변수 _age와 메서드 _sleep은  
외부 파일인 main.dart에서 접근할 수 없다
- 이를 해결하기 위해 <b>getter</b>와 <b>setter</b>가 필요하다

### Getter & Setter
- Private 키워드를 통해 정보 은닉을 구현했다면 해당 데이터에 접근할 수 있는 권한을 가진 메서드를 public으로 선언해서 은닉된 데이터에 직접적으로 접근하는 것을 막을 수 있다
- Getter는 데이터의 값을 가져오는 역할을 하고,  
- Setter는 값을 수정하는 역할을 한다
- 이들을 Dart에서는 get / set 키워드를 통해 사용한다
```dart
class Person{
  String? _name;
  String? get getName => _name;
  set setName(String name) => _name = name;
}

main(){
  Person p = Person();
  p.setName = "CHOI";
  print(p.getName);
}
```
















