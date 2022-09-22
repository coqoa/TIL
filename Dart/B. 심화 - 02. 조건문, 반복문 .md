## 조건문
### if
조건이 맞으면 실행문 실행
```dart
ifExam(){
  int? i = 1;
  if(i==1){
    print('참');
  }
}
void main() {
  ifExam();
}
```
### if, else if, else 
조건에 따라 실행문을 분기하는 역할을 함
```dart
elseIfExam(){
  int? i = 1;
  if(i == 1){
    print('1');
  }else if(i == 2){
    print('2');
  }else{
    print('거짓');
  }
}
void main() {
  elseIfExam();
}
```

### switch
조건에 따라 실행문을 분기하는 역할을 함
```dart
switchExam(){
  int? i = 3;
  switch(i){
    case 1:
      print('1');
      break;
    case 2:
      print('2');
      break;
    dafault:
      print('default');
      break;
  }
}
void main() {
  switchExam();
}
```

### assert
조건식이 거짓이면 에러를 반환하는 함수, debug mode에서만 동작함
```dart
// assert(조건식);
assertExam(){
  assert((){
    if(true){
      print('참');
      return true;
    }else{
      print('거짓');
      return false;
    }
  }());
}
void main() {
  assertExam();
}
// 조건식 true ? 출력 = 참
// 조건식 false ? 출력 = 거짓, Uncaught Error: Assertion failed
```

## 반복문
### for
기본, 횟수를 지정할 수 있고 증감식을 통해 리스트 형식의 데이터에 유연하게 접근할 수 있다
```dart
// for(변수; 조건식; 증감식){실행문}
forExam(){
  for(int i=0; i<5; i++){
    print(i);
  }
}
void main() {
  forExam();
}
```
### while
조건문이 참이면 내부를 순환하고 조건식이 거짓일 때 까지 반복한다  
break를 만나면 반복문을 종료하고  
continue를 만나면 해당 조건문 블록을 탈출한뒤 다음 명령을 수행한다  
```dart
//while(조건식){실행문}
whileExam(){
  int i = 0;
  while(true){
    i++;
    if(i<5){
      print(i);
      continue;
    }else if(i>10){
      print('...10에 도달했음');
      break;
    } 
  }
}
void main() {
  whileExam();
}
```
### forEach
list의 요소 하나하나를 parameter로 지정해서 반복 실행한다
```dart
// 리스트.forEach((인자){실행문});
forEachExam(){
  List list1 = [];
  List list2 = [1,2,3,4,5];
  
  print('START');
  list2.forEach((element){
    list1.add(element);
    print(list1);
  });
  print('END');
}
void main() {
  forEachExam();
}
```
### for in
리스트 요소를 각각 반복실행한다
```dart
// for(타입 변수 in 리스트){실행문}
forInExam(){
  List list = [1,2,3,4,5];
  
  print('START');
  for(int forin in list){
    print(forin);
  }
  print('END');
}
void main() {
  forInExam();
}
```
