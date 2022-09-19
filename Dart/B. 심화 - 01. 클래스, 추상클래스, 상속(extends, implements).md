### Class
```dart
// 선언
class Person {
    String name;   
}
// 객체 생성 후 Person.name 으로 접근 가능

// 생성자를 이용해서 클래스 생성시에 값을 넣어줄 수 있음
class Person{
    String name;
    Person(this.name);
}

main(){
    Person person = Person('최병민');
    print(person.name); // 출력 : 최병민
}
```
### 생성자
추가하기  ------------------------------------------


### 상속 : extends & implements
- extends
	- 단 하나만 상속이 가능
	- 별다른 선언없이 부모 클래스의 멤버 변수, 메서드를 사용할 수 있음
	- 변수나 함수의 기능을 변경하려면 @override 어노테이션을 통해 재정의 해야함
- implements
	- 여러개를 상속할 수 있음
	- 추상 메서드는 물론 일반 메서드도 부모클래스의 멤버 변수와 메서드는 반드시 재정의 해야함
```dart

// 예제코드변경하기 ------------------------------------------

// extends 상속
class Vehicle{
  Vehicle(this.color);
  final String color;
  final String definition = 'Vehicle';
}
class Car extends Vehicle {
  Car(String color) : super(color);
}
class Hatch extends Car {
  Hatch(String color);
}
main(){
  final hatch = Hatch('red');
  print('Result: ${hatch is Vehicle}');
}

// implements 상속 
class Vehicle{
  Vehicle(this.color); // 생성자
  final String color;
  final String definition = 'Vehicle';
}
class Car implements Vehicle {
  Car(this.carColor); // 생성자
  final String carColor;
  @override
  String get color => carColor;
  @override
  String get definition => '$carColor car';
}
main(){
  final car = Car('red'); 
  print('Result: ${car is Vehicle}');
}

// with를 통한 여러개의 클래스 상속
class Animal {}
class Flyer {
  void fly() => print('I can fly!');
}
abstract class Swimmer {
  void swim() => print('I can swim!');
}
class Bird extends Animal with Flyer {}
class Duck extends Animal with Swimmer, Flyer {}
main(){
  final bird = Bird();
  print(bird is Flyer);
}
```

### abstract : 추상클래스
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

##### 심화 : 추상클래스를 통해 Repository만들기
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

