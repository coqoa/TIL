## Class
- 멤버 변수와 메서드를 가진다
- 클래스를 사용하기 위해선 객체를 생성해야 한다  
객체를 생성하는 것은 클래스가 메모리에 올라간다는 의미이고 이를 인스턴스화라고 한다  
이렇게 메모리에 클래스가 할당되어 인스턴스가 된 것을 객체라고 한다  

```dart
class Person{
  String? name;
  Person(this.name);
  // 생성자를 이용해서 클래스 생성시에 값을 넣어줄 수 있음

}

main(){
    Person person = Person('최병민');
    
    print(person.name); // 객체 생성 후 person.name 으로 접근 가능
    // 최병민
}

```

## 생성자
- 객체가 생성될 때 호출된다
##### 1. 기본 생성자
- 클래스 구현시 생성자 선언을 생략하면 기본 생성자가 자동 제공된다
- 기본 생성자는 <u>클래스와 동일한 이름을 가지고</u>, <u>인자가 없고</u>, <u>부모 클래스의 기본 생성자를 '호출'</u>한다
- 기본 생성자는 하나만 가질 수 있다

	```dart
	/* 기본 생성자 */
	class Parent {
	  Parent(){
	    print('부모 클래스 기본 생성자');
	  }
	}
	class Child extends Parent{
	  Child(){
	    print('자식 클래스 기본 생성자');
	  }
	  //   Child(String a){
	  //     print(a);
	  //   }
	  //   기본 생성자 중복 : ERROR
	}
	void main(){
	  Child c = Child();

	  c; 
	  // 부모 클래스 기본 생성자
	  // 자식 클래스 기본 생성자
	}
	```

##### 2. named 생성자
- 한 클래스에 많은 생성자를 생성하거나
- 생성자를 명확히 하기 위해 사용한다
- named 생성자를 선언하면 기본 생성자는 생략할 수 없다
- 기본 생성자가 자동으로 생성되어 에러는 없지만 객체생성을 위해선 기본 생성자를 명시적으로 선언해야한다
	```dart
	/* named 생성자 */
	class Named {
	  Named.n1(String a){
	      print('$a');
	  }
	  Named.n2(){
	      print('n2');
	  }
	}
	void main(){
	  // Person1 p1 = Person1(); // 객체 생성 ERROR : 객체로 생성하기 위해선 기본 생성자가 필요함
	  var n1 = Named.n1('Named1');
	  var n2 = Named.n2();

	  n1; // Named1
	  n2; // n2
	}
	```
##### 3. 초기화 리스트
- 생성자의 구현부가 실행되기 전에 인스턴스 변수를 초기화 할 수 있다
	```dart
	/* 초기화 리스트 */
	class Initialize {
	  String? name;

	  Initialize() : name = 'INITIALIZE'{
	    print(name);
	  }
	}
	void main(){
	  Initialize i = Initialize();
	  i;
	  // INITIALIZE 
	}
	```
##### 4. 리다이렉팅 생성자
- 본체가 비어있고 메인 생성자에게 위임하는 역할을 함
	```dart
	/* 리다이렉팅 생성자 */
	class Redirecting {
	  String? name;
	  int? num;

	  Redirecting(this.name, this.num){
	    print('$name & $num');
	  }

	  Redirecting.init(String s, int i) : this(s, i);
	  // 여기서 this는 현재 인스턴스를 가리킴, 
	  // 그러므로 this(s,i)는 현재 인스턴스의 생성자인 Redirecting(String s, int i)이 됨
	}
	void main(){
	  Redirecting r = Redirecting.init('REDI', 1);

	  r; // REDI & 1
	}
	```
##### 5. 상수 생성자
- 생성자를 상수처럼 만들어준다 = 해당 클래스가 변하지 않는 객체를 생성한다
- 멤버 변수가 모두 final이어야 하고 생성자는 const 키워드가 붙어야 한다
	```dart
	class Constant {
	  final String? name;
	  final num? age;

	  const Constant(this.name, this.age);
	}
	void main(){
	  Constant c1 = const Constant('CHOI', 32);
	  Constant c2 = const Constant('CHOI', 32);
	  Constant c3 = new Constant('CHOI', 32);
	  Constant c4 = new Constant('CHOI', 32);
	  // 인스턴스를 비교하는 identical method
	  print(identical(c1, c2)); // true
	  print(identical(c1, c3)); // false
	  print(identical(c1, c4)); // false
	  print(identical(c2, c3)); // false
	  print(identical(c2, c4)); // false
	  print(identical(c3, c4)); // false
	  // 결론 : const 키워드를 통해 만들어진 상수 생성자는 같은 인스턴스다
	}
	```


## 상속 : extends & implements
- extends
	- 단 하나만 상속이 가능
	- 별다른 선언없이 부모 클래스의 멤버 변수, 메서드를 사용할 수 있음
	- 변수나 함수의 기능을 변경하려면 @override 어노테이션을 통해 재정의 해야함
- implements
	- 여러개를 상속할 수 있음
	- 추상 메서드는 물론 일반 메서드도 부모클래스의 멤버 변수와 메서드는 반드시 재정의 해야함
```dart
// 1. extends 상속
class Person {
  String name = 'CHOI';
  int age = 32;
  sleep(){
    print('Person sleep');
  }
  
}
class Male extends Person{
  @override
  sleep(){
    print('Male sleep');
  }
}
void main(){
  Person p = Person();
  Male m = Male();
  print(p.name);
  print(m.name); // 부모 클래스 멤버 변수 사용
  p.sleep();
  m.sleep(); // 자식 클래스에서 재정의 한 메서드 사용
}

// 2. implements 상속 
class Person {
  String? name;
  
  sleep(){
    print('Person sleep');
  }
}
class Adult{
  int? age;
}

class Coqoa implements Person, Adult{
  @override
  String? name = 'coqoa';
  sleep(){print('coqoa sleep zzZ..');}
  
  int? age = 32;
}
void main(){
  Coqoa coqoa = Coqoa();
  print(coqoa.name);
  print(coqoa.age);
  coqoa.sleep();
}

// 3. with를 통한 여러개의 클래스 상속
class Animal {
  String animal = 'animal';
}
class Flyer {
  void fly() => print('I can fly!');
}
abstract class Swimmer {
  void swim() => print('I can swim!');
}
class Bird extends Animal with Flyer {
  String species = 'bird';
}
class Duck extends Animal with Swimmer, Flyer {
  String species = 'duck';
}
main(){
  final bird = Bird();
  print('${bird.animal} ${bird.species}');
  bird.fly();
  
  final duck = Duck();
  print('${duck.animal} ${duck.species}');
  duck.fly();
  duck.swim();
}
// animal bird
// I can fly!
// animal duck
// I can fly!
// I can swim!
```

## abstract : 추상클래스
: 선언은 되었지만 바디가 정의되지 않은 형태의 미완성 클래스로 extends상속, implements상속이 가능하다  
abstract class 키워드를 붙여서 선언한다


#### 주의점
- 추상 클래스는 객체를 생성할 수 없음
- 참조형 변수의 타입으로 사용 가능함
- 추상 메서드는 추상 클래스만 가질 수 있음 (일반 클래스는 불가능)
- 추상 메서드는 extends 상속이든 implements 상속이든 반드시 @override해야함
- @override 어노테이션을 생략할 수 있음
- 자식 클래스는 부모 클래스의 멤버 변수, 메서드를 별다른 정의없이 사용할 수 있음

```dart
abstract class PersonAB{
  eat();
  eat2(){
    print('AB-eat2');
  }
  eat3(){
    print('AB-eat3');
  }
}

class Person extends PersonAB{
  @override
  eat(){} // 추상메서드는 사용하지 않더라도 정의해야됨
  eat3(){
    print('override-eat3');
  }
}

void main(){
  PersonAB person = Person();
  person.eat(); // 멤버 함수 사용
  person.eat2(); // AB-eat2 : 멤버 함수 사용
  person.eat3(); // override-eat3 : 재정의한 함수 사용
  
  Person person1 = Person(); //OK
  PersonAB person2 = Person(); //OK
//   Person person3 = PersonAB(); // ERROR : 추상클래스는 객체 생성 불가능
//   PersonAB Person4 = PersonAB(); // ERROR : 추상클래스는 객체 생성 불가능
  
}
```

## 심화 : 추상클래스를 통해 Repository만들기
```dart
// repository_ab.dart
abstract class RepositoryAB {
  Future<Map<String,dynamic>?> getJson();
}
```

```dart
// repository.dart
import 'package:dio/dio.dart';
import 'package:first_test_click/repositories/repository_ab.dart';

class Repository implements RepositoryAb{
  @override
  Future<Map<String, dynamic>> getJson() async {
    var response = await Dio().get('url');
    Map<String, dynamic> result = response.data;
    return result;
  }
}
```

```dart
// controller.dart
import 'package:get/get.dart';
import 'package:kees/screen/alarm/repository/repository.dart';

class Controller extends GetxController{
  final Repository _repo = Repository();
    Future<void> getList() async {
       Map<String,dynamic>? response = await _repo.getJson(); 
       // response를 이용해서 데이터 가공 및 출력
    }
}
```

