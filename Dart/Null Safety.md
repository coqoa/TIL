NullPointException 같은 상황은 매번 Null 값을 체크해주는 간단한 방법으로 막을 수 있지만  
개발자가 의도치않게 Null체크를 하지 않는 실수를 범할 수 있다.  
그래서 등장한 개념이 Null Safety다.

##### Null Safety ?
: null 값을 통해 발생할 수 있는 예측 불가능한 상황을 미리 막는 것으로 

변수는 null값을 가질 수 없음을 뜻하고 변수 생성 시 null safety를 기본값으로 적용하자는 취지

- int age ; or int age = null ; (x)

- 컴파일 단계에서 null값이 할당될 수 없도록 해서 실행이 불가능하도록 함

 



할당 없이 선언만 하고 싶을 수도 있고,  
선언과 동시에 할당되는 게 아니라 잠시 후에 할당되어야 할 때도 있는 등   
Null Safety를 통해 발생하는 문제도 있음

##### 해결법
```dart

// 1번 예제 
// 타입 뒤에 ?를 붙여준다
class Person{
  String? name;
  
  String nameChange(String? name){
    this.name = name;
    //null check
    if(name == null){
      return('need a name');
    }else{
      return name.toUpperCase();
    }
  }
}
void main() {
  Person p = Person();
  if(p.name == null){
    print('need a name'); //출력
  }else{
    print(p.nameChange(p.name));
  }
}

// 2번 예제
// 선언과 동시에 변수값이 할당되지 않고 나중에 할당되야하는 경우는 'late' 키워드를 통해 선언한다
class Person{
  late int age;
  
  int sum(int age, int num){
    this.age = age;
    int total = age + num;
      return total + age;
  }
}

void main() {
  Person p = Person();
  print(p.sum(100,50)); // 250
}

// 3번 예제
// !를 붙인다
void main() {
  int x = 50;
  int? y;
  if (x>0){
    y = x;
  }
  // nullable int 타입의 y변수는 int 타입의 value에 할당될수 없으므로 컴파일 에러
  // 즉, nullable 변수는 non-nullable변수에 할당될 수 없다
  // nullable변수 y를 항상 non-nullable값을 가질거라고 알려주어야 하는데
  // !를 추가해서 해결한다 (Exclamation or Bang)
  int value = y!;
  print(value);
}

// 4번예제
// required 키워드를 사용한다
void main() {
  print(add());
}
int add({int a, int b}){
  int sum = a + b;
  return sum;
}

// null safety 기능때문에 named argument를 전달하지 않으면 컴파일 에러
// 타입 앞에 required라는 키워드를 추가해서 해결한다
// 하지만 두 인자값중에 하나만 전달되거나 null값이 전달되면 컴파일 에러가 발생한다
// 인자의 타입에 ?를 붙여서 null 값일 수 있음을 알리면
// null 값으로 덧셈연산을 할 수 없으므로 변수 a에 대한 null check를 해줘야한다

void main() {
  print(add(a: null , b:5));
}
int add({required int? a, required int b}){
  if( a == null){
    return b;
  }
  int sum = a + b;
  return sum;
}

```

