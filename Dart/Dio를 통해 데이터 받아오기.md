### Dio를 통해 데이터 받아오기

- 설치
```java
// pubspec.yaml
dependencies:
  dio: ^4.0.6

// 터미널에 flutter pub get 입력해서 마무리
```

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

// repository.dart
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

// * response의 구조

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
