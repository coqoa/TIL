### Type
- dart 내장 타입
    - num : int와 double의 supertype
    - int : 정수
    - double : 실수
    - String : 문자열
    - bool : true/false
    - var : 타입 미지정 및 타입 변경 불가
    - dynamic : 타입 미지정 및 타입 변경 가능
    - List : array
    - Set : 순서가 없고 중복이 없는 collection
    - Map : key-value 형태를 가지는 collection
    - final : 상수 선언 타입, 런타임 시에 선언됨
    - const : 상수 선언 타입, 컴파일 시점에 선언됨
	
### Future

비동기로 처리되어야 할 값 (미래에 요청한 데이터 혹은 에러가 담길 곳)
```dart
class CountRepository implements CountControllerRepositoryAb{
  @override
  Future<Map<String, dynamic>> getVersion(String platForm) async {
    var response = await Dio().get('http://ec2-3-36-48-209.ap-northeast-2.compute.amazonaws.com:8080/api/version/1.0.7/$platForm');
    Map<String, dynamic> result = response.data;
    return result;
  }
}
// Map<String, dynamic>타입의 result를 받는 Future 함수,
// 사용하는 곳에서 클래스를 선언하고 ~~.getVersion(argument)를 사용하면 
// Dio를 통해 argument를 넣은 URL을 기반으로 api통신하고
// api통신 결과인 response의 data를 Map<String, dynamic>타입의 result에 넣어서 반환한다
```
