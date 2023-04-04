# Dart
## main()
- Dart 프로그램의 Entry point - 코드를 호출하는 함수
#### + Dart의 모든 메소드는 끝에 세미콜론(;)을 붙여줘야한다

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

## 2. DATA TYPES
- Basic Data Types
	- Dart의 모든것은 클래스다
	- 이러한 이유 때문에 변수명. 을 통해 내부 메소드를 사용할 수 있다
		```dart
		void main (){
			String name = '나병민'; // String 클래스 
			bool alive = true; // bool 클래스 
			int age = 32; // int 클래스 
			double height = 170.0; // double 클래스 
			num x = 12; // int와 double의 부모 클래스 
			x=1.1; 
		}
		```
- Lists
	- collection if 와 collection for를 지원함
		```dart
		void main(){
		// 선언 방법 1 
		var numbers = [1,2,3,4,]; 
		numbers.add(5) 

		// 선언 방법 2 
		List<int> numbers2 = [1,2,3,4,]; 
		numbers2.add(5); 

		// collection if : List 생성시 조건에 따라 element 추가 가능 
		var giveMeFive = true; 
		var numbers3 = [1,2,3,4,if(giveMeFive) 5,];
		// = if(giveMeFive){number.add(5)} 

		// Collection For 
		var oldFriends = ['병민','형준']; 
		var newFriends = ['Paul','Tom', for(var friend in oldFriends) "😃" $friend ]; 
		// [Paul, Tom, 😃 병민, 😃 형준] }
		```
- Set
	- List와 달리 모든 아이템들이 유니크함(같은 아이템을 추가할 수 없음)
		```dart
		void main() { 
			// 선언 방법 
			Set<int> numbers = {1,2,3,4}; 
			numbers.add(1); 
			numbers.add(1); 
			numbers.add(1); 
			numbers.add(1); 
			print(numbers); // {1,2,3,4} 
		}
		```
- Map
	- JS, TS의 object 역할
	- Map의 key와 value는 사용자에 의해 정해짐, 일반적으로는 <String, dynamic>의 형태로 사용함
		```dart
		void main(){ 
			var player = {'name': '나병민', 'xp': 19.99, 'superpower': false,}; 
			// player.Map메소드 사용 가능 
			print(player.length); // 3 
			print(player.isEmpty); // false 
			player.clear(); 
			print(player.length); // 0 
			print(player.isEmpty); //true 

			// List<Map>예시 
			List<Map<String, dynamic>> players = [
				{ 'name': '나병민', 'age' : 32, 'height' : 170.5, } 
			]; 
			print(players[0]); // {name: 나병민, age: 32, height: 170.5} 
			print(players[0]['name']); // 나병민 
			print(players[0]['age']); // 32 
			print(players[0]['height']); // 170.5 
		}
		```


## 3. 데이터 바인딩
- String Interpolation
	- text에 변수를 추가하는 방법
	- ‘’ `$변수`"형태로 작성, 띄어쓰기가 들어가거나 계산을 실행하려면 ‘`${변수}`’형태로 작성
		```dart
		void sayHello1(String name){
			print("Hello $name nice to meet you"); 
		}
		String sayHello2(String name){
			return "Hello $name nice to meet you"; 
		} 
		// 위와 같음 
		String sayHello3(String name) => "Hello $name nice to meet you"; 

		void main(){ 
			sayHello1('나병민1'); // 출력 : Hello 나병민1 nice to meet you 
			String greetings = sayHello2('나병민2'); // 할당 
			print(greetings); // 출력 : Hello 나병민2 nice to meet you 
		}
		```

## 4. FUNCTIONS
- Defining a Function
	- void : 아무것도 return하지 않음
	- String을 return 하려면 함수 내부에 return을 작성해야함
      ```dart
      void sayHello1(String name){
          print("Hello $name nice to meet you");
      }
      String sayHello2(String name){
          return "Hello $name nice to meet you";
      }
      // 위와 같음
      String sayHello3(String name) => "Hello $name nice to meet you";


      void main(){
          sayHello1('나병민1'); // 출력 : Hello 나병민1 nice to meet you
          String greetings = sayHello2('나병민2'); // 할당
          print(greetings); // 출력 : Hello 나병민2 nice to meet you
      }
      ```

- Positional Parameters & Named Parameters - 중괄호 {}
	```dart
	// Positional Parameters
	String sayHello(
		String name, 
		int age, 
		String country
	){
		return "Hello $name, you are $age, and you come from $country";
	}
	void main(){
		print(sayHello('나병민', 19, 'Seoul'));
	}

	// 사용자가 순서를 잊어버릴 수 있기 때문에 적절한 사용법이 아님
	// ⬇︎⬇︎ 그래서 네임드 파라미터를 사용함 

	// Named Parameters
	// 1. 파라미터를 중괄호로 감싸준다
	// 2. 파라미터에 default value를 정해주거나, required 를 붙여서 null safety를 적용한다
	String sayHello({
		required String name, 
		required int age, 
		required String country
	}){
		return "Hello $name, you are $age, and you come from $country";
	}
	void main(){
		print(sayHello(
			name : '나병민', 
			age : 19, 
			country : 'Seoul'
		));
	}

	```
- Optional Positional Parameters - [] 대괄호

	```dart
	String sayHello(
		required String name, 
		required int age, 
		[
			// Optional Parameters (기본값 지정1, 기본값 미지정1)
			String? hometown = 'ULSAN', 
			String? country
		]
	){
		return "Hello $name, you are $age, and you come from $hometown";
	}

	void main(){
		var result = sayHello(name : '나병민', age : 32, );
		print(result) // "Hello 나병민, you are 32, and you come from ULASN";
	}
	```
- Operator `??` , `?=`
  -  `??` : ??를 기준으로 좌항이 null이면 우항을 return한다
  -  `??=` : ??=를 기준으로 좌항이 null이라면 우측의 값을 할당한다
		```dart
		String capitalizeName(String name) => name.toUpperCase();

		void main(){
			print(capitalizeName('coqoa')); // COQOA

			// 사용자가 null도 입력할 수 있었으면 좋겠다

			String capitalizeName1(String? name) => 
				name != null ? name.toUpperCase() : 'coqoa';

			print(capitalizeName1(null)); // coqoa
			print(capitalizeName1('choibm0208')); // CHOIBM0208

			// 더 짧게 가능함 `??`
			String capitalizeName2(String? name) => 
				name?.toUpperCase()?? 'coqoa';

			print(capitalizeName2(null)); // coqoa
			print(capitalizeName2('choibm0208')); // CHOIBM0208
		}
		```
- Typedef 
  - 자료형이 헷갈릴 때 도움이 될 alias를 만드는 방법  
	```dart  
	typedef ListOfInts = List<int>;

	List<int> reverseListOfNumbers(ListOfInts list){
		var reverserd = list.reversed;
		return reversed.toList();
	}

	void main(){
		reverseListOfNumbers([1,2,3]);
	}
	```

--- 23.03.30

## 5. CLASSES
- Your First Dart Class
	```dart
	class Player{
		String name = 'coqoa';
		final String name1 = '나병민1'; // final 키워드가 붙으면 변경불가
		int xp = 1500;

		void sayHello(){
			print('Hi my name is $name');
		}
	}

	void main(){
		Player player = Player();
		player.name = '나병민'; // 재할당
		print(player.name); // 나병민
		print(player.xp.toString()); // 1500
		player.sayHello(); // Hi my name is 나병민
	}
	```

- Constructors
	```dart
	class Player{
		// Constructors
		Player(this.name, this.xp); 
		final String name; // final 필요, 나중에 값을 받으려면 late 붙여줌
		final int xp;
	}

	void main(){
		Player player1 = Player("나병민", 1500);
		Player player2 = Player("coqoa", 100);
		print(player1.name); // 나병민
		print(player1.xp.toString()); // 1500
		print(player2.name); // coqoa
		print('${player2.xp}'); // 100
	}
	```
- Named Constructor Parameters
	```dart
	class Player{
		Player({
			// Named Constructor Parameters
			required this.name,
			required this.xp, 
			required this.team,
		}); 
		final String name;
		final int xp;
		final String team;
	}

	void main(){
		Player player1 = Player(name:"나병민",xp: 1500, team:'blue');
		Player player2 = Player(team:'red', name:"coqoa", xp:100);
		print(player1.team); // blue
		print(player2.team); //red
	}
	```
- Named Constructors 
	```dart
	class Player{
	// default constructor
		Player({
		// Named Constructor Parameters
			required this.name,
			required this.xp, 
			required this.team,
			required this.age,
		}); 
	
	// named constructor
	Player.createBluePlayer({required String name,required int age}) : 
		this.name = name,
		this.age = age,
		this.team = 'blue',
		this.xp = 0;
	
	Player.createRedPlayer({required String name,required int age}) : 
		this.name = name,
		this.age = age,
		this.team = 'red',
		this.xp = 0;
	
		final String name;
		final int xp;
		final String team;
		final int age;
	}

	void main(){
		Player player1 = Player.createBluePlayer(name:"나병민", age:32);
		Player player2 = Player.createRedPlayer(name:"coqoa", age:40);
		print(player1.team); // blue
		print(player2.team); //red
	}
	```

## 6. JSON 직렬화
- api로부터 json data를 받아서 class로 바꾸는 작업
	```dart
	class Player{
		final String name;
		final int xp;
		final String team;
		final int height;
		final int weight;
	
		Player.fromJson(Map<String, dynamic> playerJson) :
			name = playerJson['name'],
			xp = playerJson['xp'],
			team = playerJson['team'],
			height = playerJson['hw']['height'],
			weight = playerJson['hw']['weight'];
		}

		void main(){
			// 더미데이터
			var apiData = [
			{
			"name":"coqoa",
			"xp":0,
			"team":"blue",
			"hw":{
				"height":170,
				"weight":70,
			}
			},
			{
			"name":"choibm0208",
			"xp":0,
			"team":"blue",
			"hw":{
				"height":180,
				"weight":80,
			}
			},
			{
			"name":"qudals28",
			"xp":0,
			"team":"blue",
			"hw":{
				"height":160,
				"weight":60,
			}
			},
			
		];
	
		apiData.forEach((playerJson){
			var pl = Player.fromJson(playerJson);
			print('${pl.name}, ${pl.height}, ${pl.weight}');
			//  coqoa, 170, 70
			//  choibm0208, 180, 80
			//  qudals28, 160, 60
		});
	}
	```

## 7. Cascade Notation
- 똑같은 코드를반복하는 대신 사용할 수 있음 
	```dart
	class Player{
		String name;
		int xp;
		String team;
	
		Player({
			required this.name, 
			required this.xp, 
			required this.team
		});
		
		void sayHello(){
			print('My name is $name');
		}
	}

	void main(){
		var coqoa = Player(name : 'coqoa', xp: 0, team:"red")
		..sayHello() // My name is coqoa
		..name = 'choibm0208'
		..xp = 15000
		..team = 'purple'
		..sayHello(); //My name is choibm0208
	}
	```
## 8. Enums
- 선택의 폭을 좁혀 실수를 방지함
	```dart
	enum Team {red,blue,green}
	// * Colors도 Enum이다 (ex. Colors.red, Colors.black ...)

	class Player{
		String name;
		int xp;
		Team team;
	
		Player({
			required this.name, 
			required this.xp, 
			required this.team
		});
	}

	void main(){
		var coqoa = Player(name : 'coqoa', xp: 0, team: Team.red)
		..name = 'choibm0208'
		..xp = 15000
		..team = Team.green;
	}
	```