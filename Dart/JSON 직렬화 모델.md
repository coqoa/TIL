### JSON 직렬화 모델
- JSON 데이터를 사용할 때 디버깅, 유효성 검사, 깔끔한 구조로 작성된 코드 등을 위해  
  직렬화하고 파싱하는 과정이 필요한데 보통 데이터를 매핑할 수 있는 클래스를 별도로 만들어서 사용한다 
- flutter doc에서도 중대형 프로젝트의 경우에는 위의 방법을 추천한다

```java
// model.dart
class Model {
  late int id;
  late String type;
  late String imagePath;
  late String title;
  late String content;
  late String createdAt;
  late String lastModifiedAt;
  late bool read;

  Model.fromJson(Map<String, dynamic> data){
    this.id = data["id"]; 
    this.type = data["type"];
    this.imagePath = data["imagePath"]??''; // ??'';로 null체크
    this.title = data["title"];
    this.content = data["content"];
    this.createdAt = data["createdAt"];
    this.lastModifiedAt = data["lastModifiedAt"];
    this.read = data["read"];
  }
}
```
- 사용 예제
```java
class Controller extends GetxController{

  final Repository _repo = Repository();
  
  RxList list = [].obs;
  
  // 리스트 가져오기
  Future<void> getList(String s) async {
    List<dynamic> response = await _repo.getList(); 
    list.clear();
    for(int i = 0; i<response.length; i++ ){
      // 들어온 인자값을 검사해서 통과하면 이 정보들을 list에 저장
      var responseResult = response[i];
      Model model = Model.fromJson(responseResult);

      if(s.toUpperCase() == 'ALL'){
        list.add(model);
      }else{
        // 통신결과의 type이 인자값과 동일한 데이터만 리스트에 추가
        if(responseResult["type"]==s.toUpperCase()){
          list.add(model);
        }
      }
    }
  }
}
// Repository의 getList 함수를 통해 데이터를 받아오고
// 데이터의 길이만큼 model을 통해 정리된 객체를 listdp 넣어준다
// 아래에서는 getList의 인자값에 따라 리스트에 모든 데이터를 넣을지, 
// 혹은 특정 데이터를 넣을 지 선택하는 조건문이 작성되어있다


```
