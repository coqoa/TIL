### Class
```dart
// 선언
class Person {
    String name;
		// Person.name 으로 접근 가능
}

// 생성자를 이용해서 클래스 생성시에 값을 넣어줄 수 있음
class Person{
    String name;
    Person(this.name);
}
main(){
    Person person = Person('sneakstarberry');
    print(person.name); // sneakstarberry
}

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
  Vehicle(this.color);
  final String color;
  final String definition = 'Vehicle';
}
class Car implements Vehicle {
  Car(this.carColor); 
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
### Abstract Class
(= 미완성 메서드)
: 기존 클래스 앞에 abstract 키워드를 붙여서 선언한다
```dart 
// count_controller_ab.dart
abstract class CountControllerRepositoryAb {
  Future<Map<String, dynamic>> getVersion(String platForm);
}
```
: implements 키워드를 통해 참조형 변수의 타입으로 사용이 가능하고 **반드시** 추상 메서드를 override해야한다

(사용하지 않는 추상메서드도 반드시 override 해야한다)
```dart
import 'package:dio/dio.dart';
import 'package:first_test_click/repositories/count_controller_ab.dart';

class CountRepository implements CountControllerRepositoryAb{
  @override
  Future<Map<String, dynamic>> getVersion(String platForm) async {
    var response = await Dio().get('http://ec2-3-36-48-209.ap-northeast-2.compute.amazonaws.com:8080/api/version/1.0.7/$platForm');
    Map<String, dynamic> result = response.data;
    return result;
  }
}
```
: 추상 메서드가 아닌 일반 메서드를 추가하려면 implements하는 클래스에 재정의되어야한다.

: 클래스는 implements를 통해 여러개의 추상클래스를 상속받을 수 있다
