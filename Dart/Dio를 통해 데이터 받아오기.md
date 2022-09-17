### Dio
Flutter에서 api통신을 하기 위해 사용하는 라이브러리.  
pubspec.yaml 파일의 dependencies에 다음을 추가해준다   

##### 설치
```java
// pubspec.yaml
dependencies:
  dio: ^4.0.6

// 터미널에 flutter pub get 입력해서 마무리
```

##### response의 구조
```dart
{
  "code": "200",
  "message": "success",
  "result": [
    {
    "id": 1,
    "sender": {
      "id": 1,
      "name": "이름",
      "phoneNumber": 폰번호
    },
  "type": "Member",
  "imagePath": "경로",
  "title": "타이틀",
  "content": "내용",
  "createdAt": "생성일시",
  "lastModifiedAt": "수정일시",
  "read": true
},
...
```

##### 사용
- import
```java
import 'package:dio/dio.dart';
```

- 사용법
```java
// repository_ab.dart - 추상클래스

abstract class RepositoryAB {
  Future<List<dynamic>> getList();
}

// repository.dart - 클래스
import 'package:dio/dio.dart';

class Repository implements RepositoryAB{
	Response? response;
	
	@override
	Future<List<dynamic>> getList() async {
	  Dio dio = Dio();
	  response = await dio.get(url);
      // rsponse.data는 Map타입으로 받아야 하고
      // response.data["result"]는 List 타입으로 받아야 한다
	  List<dynamic> result = response?.data["result"];
	  return result;
	}
}
        
```
