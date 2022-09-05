### GetX
- 가볍고 간단하고 사용하기 편하다 
	- State Management
		- Simple State Manager with GetBuilder
		- Reactive State Manager 	
	- 페이지 이동 `Get.to(SecondPage());`   
	- 기타 등등
##### Simple State Manager with GetBuilder
- 설치 
  ```dart
  //pubspec.yaml
  dependencies
    get:

  ```
##### 사용
- Controller.dart생성 및 Controller class 생성
  ```dart
  class Controller extends GetxController{
    int _X = 0;
    int get x = _x;

    void increment(){
      _x++;
      update();
    }
  }

  ```  
      
	- private변수를 get 키워드를 붙인 변수에 대입하면 외부에 controller.`private변수`로 접근이 가능하다
	- state update를 위해 Controller.dart의 함수 내부에update()를 사용해야함

- main.dart의 Build메서드 내부에 작성
   ```dart
   Controller controller = Get.put(Controller());
   ```
   
- GetBuilder 위젯 사용  
  ```dart
  GetBuilder<Controller>(
  	build: (_)=>Text(controller.x)
  ) 
  ElevatedButton(
  	onPressed:(){
    	controller.increment();
    }
    ...
  )
  ```
  
##### 정리  
1. GetX패키지 설치
2. Controller 클래스 생성
3. GetxController 상속
4. update() 호출
5. Dependency Injection(Get.put)
6. GetBuilder 호출
7. controller.x 또는 Get.find<controller> 사용

---
        
