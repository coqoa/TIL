### Dio
- api통신을 하기 위해 사용하는 패키지  

```java
// 설치 : pubspec.yaml에 작성
dependencies:
  dio: ^4.0.6

```

##### Request & Response
```java

// get예제 1 
final response = await Dio().get('/test?id=1&name=coqoa');
// get예제 2
final response = await.Dio().get(
	'/test', 
	queryParameters:{'id':1, 'name':'coqoa'}
)
// get예제 3
final response = await.Dio().request(
	'/test',
    data:{'id':1, 'name':'coqoa'},
    options: Options(method:'GET'),
);
// post예제 1
final response = await.Dio().post('/test', data:{'id':1, 'name':'coqoa'}

```
##### Options
```dart

Dio().options.baseUrl = 'https://www.xx.com/api';
Dio().options.connectTimeout = 5000; //5s
Dio().options.receiveTimeout = 3000;

var options = BaseOptions(
  baseUrl: 'https://www.xx.com/api',
  connectTimeout: 5000,
  receiveTimeout: 3000,
);

Dio dio = Dio(options);


// BaseOptions 객체
BaseOptions({
    String? method,
    int? connectTimeout,
    int? receiveTimeout,
    int? sendTimeout,
    String baseUrl = '',
    Map<String, dynamic>? queryParameters,
    Map<String, dynamic>? extra,
    Map<String, dynamic>? headers,
    ResponseType? responseType = ResponseType.json,
    String? contentType,
    ValidateStatus? validateStatus,
    bool? receiveDataWhenStatusError,
    bool? followRedirects,
    int? maxRedirects,
    RequestEncoder? requestEncoder,
    ResponseDecoder? responseDecoder,
    ListFormat? listFormat,
    this.setRequestContentTypeWhenNoPayload = false,
  })
```
dio 객체를 생성하면서 공통적으로 사용하고 싶은 것들을 BaseOptions를 통해 지정할 수 있다. 

- 주로 사용하는 옵션  
  - baseUrl: 요청할 기본 주소 설정   
  - connectTimeout: 서버로부터 응답받는 시간 설정  
  - receiveTimeout: 파일 다운로드 등과 같은 연결 지속 시간 설정  
  - headers: 요청 header의 데이터 설정


##### interceptor





##### 실제 사용 예시

```java

// counter_repository.dart
import 'package:dio/dio.dart'; // dio import
import 'package:first_test_click/repositories/count_controller_ab.dart'; // 추상클래스 import

class CountRepository implements CountControllerRepositoryAb{
  @override
  Future<Map<String, dynamic>> getVersion(String platForm) async {
    // Dio().get(url)을 통해 get요청
    var response = await Dio().get('요청 주소');
    // 대게 Map타입을 많이 사용하므로 return하는 result을 Map타입으로 지정해주고 response.data를 넣어준다
		Map<String, dynamic> result = response.data;
    return result;
  }
}

```
