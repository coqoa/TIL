## Collection : List Set Map
- collection : 다수의 데이터를 처리할 수 있는 자료구조
### List 
- 데이터 순서가 있고 중복을 허용한다.
- 인덱스로 데이터에 접근할 수 있다
```dart
// List<타입> 변수명 = [데이터1, 데이터2,...,데이터n];
List<String> alphabet = ['a','b','c','d'];  
List<int> number = [1,2,3,4];  

print(alphabet[0]); // a
print(alphabet[1]); // b
print(alphabet[2]); // c
print(alphabet[3]); // d
print(number[0]); // 1
print(number[1]); // 2
print(number[2]); // 3
print(number[3]); // 4
```
- Method
	- .add(데이터)
	- .addAll([데이터1, 데이터2, ...])
	- .remove(요소)
	- .removeAt(인덱스)
	- .contains(요소)
	- .clear()
	- .sort()
	- .first
	- .last
	- .reversed
	- .isNotEmpty
	- .isEmpty
	- .single
	- .indexOf 
	- .length  
	등등
### Set
- 중복을 허용하지 않는다,   
중복을 허용하지 않기 때문에 같은 값을 여러번 넣어도 단 하나만 존재한다.
- 데이터 순서가 없다,  
순서가 없기 때문에 index로 접근하지 못하고 for ..in문을 통해 접근이 가능하다
- for..in문은 in 뒤에 선언된 객체에서 하나의 요소를 가져와 in 앞에 선언된 변수에 할당한다
- List에서 사용하는 메서드중 index를 사용하는 메서드는 Set에서 사용하지 못한다
	- .indexOf()
	- .removeAt()
	- .sort()
	- .reversed()   
	등등
```dart
Set<타입> 변수명 = {데이터1, 데이터2,... 데이터n}
```

### Map
- key-value 형태로 구성된 컬렉션으로 키는 중복되지 않고 값은 중복이 가능하다
- key와 value가 매칭되어 빠른 탐색이 가능하다
- 순서를 가리지 않지만 key값을 정수로 할당하면 순서를 가진것처럼 활용도 가능하다
- 키는 중복이 불가능하고 값은 중복이 가능하다
```dart
Map<String, dynamic> mapExam = {
  'key1': 'pomotodo.kr',
  'key2': 'Blue',
  'key3': 'Green',
  'key4': 'Orange'
};

void main(){
  print(mapExam['key1']); /* 탐색 */ 
  
  print(mapExam['key5']); // null
  mapExam['key5'] = "Navy"; /* 추가 */
  print(mapExam['key5']); // Navy
  
  print(mapExam['key4']); // Orange
  mapExam['key4'] = 'White'; /* 수정 */
  print(mapExam['key4']); // White
  mapExam.update('key4', (value)=>'RED'); /* 수정 */
  print(mapExam['key4']); // RED
}
```
