# Dart

#### Dart의 모든 메소드는 끝에 세미콜론(;)을 붙여줘야한다

## 0. main()
- Dart 프로그램의 Entry point - 코드를 호출하는 함수  



## 1. Keyword
### 1-1. variables
- 암시적타입 - 여러가지 타입을 가질 수 있는 변수(var, dynamic)
	- var
		- 재할당을 통한 타입 변경이 불가능
		- 관습적으로 함수의 내부 지역변수를 선언할 때 사용
	- dynamic
		- 재할당을 통한 타입 변경 가능
		- 할당값의 타입을 알기 어렵거나 변경이 잦은 경우처럼 엄격한 규칙을 회피하기 위해 사용
		- 조건문을 통해 하나의 변수에 분기할 수 있고 각 타입의 메소드를 사용할 수 있다
			```dart
			var v = 'var'; 
			dynamic d = 'dynamic'; 
			void main() {
				 v = 'var2'; // 재할당 가능 
				 // v = 1; // 타입 변경 불가능 
				 
				 d = 'dynamic2'; // 재할당 가능 
				 d = 2; // 타입 변경 가능 
				 
				 print(d.toString()); // 데이터 타입의 메소드 사용 가능
			 }

			```

- 명시적 타입 (String, int, double, num, bool, List, Set, Map)
	- 관습적으로 Class의 변수나 property를 선언할 때는 타입을 지정해준다

### 1-2. final / const
- 지정된 값을 바꿀 수 없는 상수
	- final
		- 컴파일 시점에 값이 결정됨
	- const
		- 선언시 값을 할당하지 않을 수 있고 이후에 한번 할당할 수 있다
		- => 실행 중에 값이 결정되는 특징이 있음 

### 1-3. late
- final이나 var 앞에 붙여줄 수 있는 수식어, 초기 데이터 없이 변수를 선언할 수 있게 해줌
- API 요청값을 받아서 변수에 할당하는 data fetching에 유용하다
- 값 할당 전에 접근하지 못하도록 해서 실수를 막아줌 (null safety와 동일한 역할)
	```dart
	late final String name;
	```

### 1-4. Nullable DataType
- null ?
	> 많은 프로그램에서 발생하는 런타임 에러(앱을 사용하던 중에 뜨는 에러)중 가장 큰 비중을 차지하는 원인이 null이다.
	> null이 할당된 변수는 데이터타입의 메소드를 찾지 못하기 때문에 'NoSuchMethodError'를 발생시킨다.
	> 이는 사용자의 디바이스에서 발생한 에러이기 때문에 컴파일러가 잡아내지 못한다.
	> null도 유용하게 사용되는 개념이므로 null을 삭제하는건 적절치않고 null을 컴파일 단계 전에 잡아내는게 이상적이다
	
-  Dart에서는?
	> 기본적으로 Dart의 모든 자료형은 'non-nullable' 하다
	> ‘null이 될 수 있음을 정확히 표시’하도록 해서 개발자가 null값을 참조하는 상황을 막아주는 방법으로 'null safety'를 구현했다
	> null이 될 수있음을 표시하는 방법하려면 데이터 타입에 ?를 붙여준다
	>  이를 통해 컴파일러가 에러를 잡을 수 있도록 해줌 (null이 아닐 경우라는 조건을 넣어서 회피할 수 있음)
```dart
String? name = '나병민';
name = null; 
// 조건 처리 방법 1 
if(name != null){
	name.isNotEmpty; 
}else{ 
	print("I'M NULL!!"); 
} 
// 혹은 조건 처리 방법 2 
name?.isNotEmpty;
```
