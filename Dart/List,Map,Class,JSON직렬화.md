### List 
- index를 가지는 리스트 데이터 컬렉션  
  ```dart
  List<String> alphabet = ['a','b','c','d'];  
  List<int> number = [1,2,3,4];  
  ```

- index로 접근 가능  
  ```dart
  print(alphabet[0]); // a
  print(alphabet[1]); // b
  print(alphabet[2]); // c
  print(alphabet[3]); // d
  print(number[0]); // 1
  print(number[1]); // 2
  print(number[2]); // 3
  print(number[3]); // 4
  ```

  - .length : 길이를 반환
  - .add(value) : 데이터 추가
  - .addAll() : 다수의 데이터 추가
  - .removeAt([]) : 단일 데이터 삭제
  - .clear() : 데이터 전체 삭제
  - .refresh() : 새로고침
  - .indexOf(value) : 데이터 위치 찾기

---

#### Map
- key-value형식의 데이터 컬렉션
  ```dart
  Map<String, dynamic> age = {
    // Key:    Value
    'choi': 32,
    'kim': 27,
    'park': 54
  };
  print(age);
  ```

- key값으로 value값에 접근 가능
  ```dart
  데이터 출력하기
  print(age["choi"]);
  데이터 추가하기
  age['lee'] = 42;
  print(age);
  ```

- 연습예제
  ```dart
  Map<String, dynamic> james = {
      'name': 'James',
      'Height': 186.5,
      'Weight': 78.1,
      'age': 43,
      'favorite color': ['red','orange', 'green'],
      'family': { 'wife': 'Lily',
                  'son': 'Harry',
                  'daugther': 'Marry'},
  };​
  // orange 를 출력하려면?
  print(james['favorite color'][1]);
  // Harry 를 가져오려면?
  print(james['family']['son']);
  ```

---

### Class
- 변수나 메소드를 정의해놓은 코드 모음이다  
- 클래스를 통해 객체를 만들 수 있다  
- constructor와 this키워드를 통해 인자가 적용된 객체를 생성할 수 있다  

- 클래스 선언
  ```dart
  class Human {
      String name;
      int age;
      int height;

      Human(this.name, this.hp, this.mp)

      void eat() {
          print('Yummy!!');
      }
      void sleep() {
          print('zzZ..');
      }
  }
  ```
  - 객체 생성
  ```dart
  Human me = Human('COQOA', 32, 170)
  ```

- 객체 내부 데이터는 .을 통해 접근할 수 있다
  ```dart
  print(me.name); //'COQOA'
  print(me.age); // 32
  print(me.height); // 170
  print(me.eat()); // yummy!!
  print(me.sleep()); // zzZ..
  ```

#### 추상클래스
- 추상 메소드를 가질 수 있는 클래스 (= 미완성 클래스)  
- 객체를 생성할 수 없지만 참조형 변수의 타입으로 사용가능하다  
- 추상클래스는 Implements 키워드를 통해 상속할 수 있고 하나의 클래스에 여러개를 상속할 수 있으며 내부에 선언된 변수나 메소드를 override해서 사용해야한다.  
  ```dart
  abstract class Person{
      eat()
  }
  class Male implements Person{
      @override
      eat();
  }
  main(){
      Person person1 = Person();
      Person person2 = Male();
  } // 정상작동
  ```

---  

### 심화 - JSON 데이터 출력하기 

- 가상의 url은 다음과 같은 형태로 되어있다고 가정한다
  ```dart
  {
      "code": "200",
      "message": "success",
      "result": [
          {
              "name": 'COQOA',
              "age" : 32
              "height" : 170
          },
          {
              "name": 'Tom',
              "age" : 44
              "height" : 187
          },
          {
              "name": 'Leo',
              "age" : 37
              "height" : 175
          },
       ]
  }
  ```

1. 추상클래스 RepositoryAB 생성  
    ```dart
    // repository_ab.dart
    abstract class RepositoryAB {
      Future<Map<String, dynamic>> getPerson();
    }
    ```

2. repositoryAB를 상속받는 Repository 클래스 생성
    ```dart
    // repository.dart
    import 'package:dio/dio.dart';

    class Repository implements RepositoryAB{
        @override
        Future<Map<String, dynamic>> getPerson() async {
            Response response = await Dio().get(url);
            Map<String, dynamic> result = response.data;
            return result;
      }
    }
    ```

3. 객체 Model 생성
    ```dart
    // object_model.dart
    class Model {
      String? name;
      int? age;
      int? height;

      // JSON 직렬화
      Model.fromJson(Map<String, dynamic> data){
        this.name = data["id"];
        this.name = data["age"];
        this.name = data["height"];
      }
    }
    ```

4. 컨트롤러 생성
    ```dart
    // controller.dart
    import 'package:get/get.dart';

    class Controller extends GetxController {
        final Repository _repo = Repository();

        RxList list = [].obs;

        Future<void> getList() async {
        Map<String, dynamic> response = await _repo.getPerson();
        List result = response["result"];

        // forEach
        result?.forEach((element) {
          Model model = Model.fromJson(element);
          list.add(model);
        }
      }
    }
    ```

5. main.dart에서 getList() 호출
    ```dart
    final Controller controller = Controller();
    controller.getList();
    ```
#### 결과
getList()를 통해서 JSON의 데이터를 가공해서 사용할 수 있는 list를 받을 수 있다
