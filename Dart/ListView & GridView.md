### ListView & GridView
- 스크롤 위젯으로 리스트 스크롤과 그리드 스크롤을 위해 사용한다

### LitstView
- ListView를 명시적으로 호출하는 방법
- ListView.builder를 사용하는 방법
- ListView.separated를 통해 구분선을 추가하는 방법
#### ListView 요소
```dart
{
  Key? key,
  Axis scrollDirection = Axis.vertical, //스크롤 방향
  bool reverse = false, // 역방향
  ScrollController? controller, // 스크롤 컨트롤러
  bool? primary,
  ScrollPhysics? physics, // 스크롤 동작여부
  bool shrinkWrap = false, // 리스트 범위 지정
  EdgeInsetsGeometry? padding,
  double? itemExtent,
  Widget? prototypeItem,
  required Widget Function(BuildContext, int) itemBuilder,
  int? Function(Key)? findChildIndexCallback,
  int? itemCount, // 표시할 리스트 개수
  bool addAutomaticKeepAlives = true,
  bool addRepaintBoundaries = true,
  bool addSemanticIndexes = true,
  double? cacheExtent,
  int? semanticChildCount,
  DragStartBehavior dragStartBehavior = DragStartBehavior.start,
  ScrollViewKeyboardDismissBehavior keyboardDismissBehavior = ScrollViewKeyboardDismissBehavior.manual,
  String? restorationId,
  Clip clipBehavior = Clip.hardEdge,
})
```
- 요소들을 각각 호출하는 ListView
```dart
ListView(
  padding: const EdgeInsets.all(8),
  children: <Widget>[
  Container(
    height: 50,
    color: Colors.amber[600],
    child: const Center(child: Text('Entry A')),
  ),
  Container(
    height: 50,
    color: Colors.amber[500],
    child: const Center(child: Text('Entry B')),
  ),
    Container(
      height: 50,
      color: Colors.amber[100],
      child: const Center(child: Text('Entry C')),
    ),
    //...
  ],
)
```
- ListView.builder
```dart
ListView.builder(
  padding: const EdgeInsets.all(8),
  itemCount: entries.length,
  itemBuilder: (BuildContext context, int index) {
    return Container(
      height: 50,
      color: Colors.amber[colorCodes[index]],
      child: Center(child: Text('Entry ${entries[index]}')),
    );
  }
),
```
- ListView.seperated
```dart
ListView.separated(
  padding: const EdgeInsets.all(8),
  itemCount: entries.length,
  itemBuilder: (BuildContext context, int index) {
    return Container(
      height: 50,
      color: Colors.amber[colorCodes[index]],
      child: Center(child: Text('Entry ${entries[index]}')),
    );
  },
  separatorBuilder: (BuildContext context, int index) => const Divider(),
)
```
### GridView
- 리스트뷰와 비슷하지만 `gridDelegate`가 필요하다
- `gridDelegate`는 그리드뷰의 모양을 결정해주는 속성
	- SliverGridDelegateWithFixedCrossAxisCount  
	: 그리드 컬럼 개수를 미리 선정하고 그리드의 사이즈를 화면 크기에 맞추는 방식
   - SliverGridDelegateWithMaxCrossAxisExtent  
     : 그리드의 가로 길이를 정하고 그에 맞게 컬럼들이 들어가는 방식 

- 두개의 컬럼이 있는 예제
```dart
GridView.count(
  primary: false,
  padding: const EdgeInsets.all(20),
  crossAxisSpacing: 10,
  mainAxisSpacing: 10,
  crossAxisCount: 2,
  children: <Widget>[
    Container(
      padding: const EdgeInsets.all(8),
      color: Colors.teal[100],
      child: const Text("He'd have you all unravel at the"),
    ),
    Container(
      padding: const EdgeInsets.all(8),
      color: Colors.teal[200],
      child: const Text('Heed not the rabble'),
    ),
    Container(
      padding: const EdgeInsets.all(8),
      color: Colors.teal[300],
      child: const Text('Sound of screams but the'),
    ),
    Container(
      padding: const EdgeInsets.all(8),
      color: Colors.teal[400],
      child: const Text('Who scream'),
    ),
    Container(
      padding: const EdgeInsets.all(8),
      color: Colors.teal[500],
      child: const Text('Revolution is coming...'),
    ),
    Container(
      padding: const EdgeInsets.all(8),
      color: Colors.teal[600],
      child: const Text('Revolution, they...'),
    ),
  ],
)
```
GridView.builder 방식도 ListView.builder 방식과 유사하다

- 대표적인 에러
    - `Vertical viewport was given unbounded height`  
    : 발생하는 이유? ListView는 부모 위젯의 높이에 따라 높이를 맞추는데   
    ListView는 자식요소가 적더라도 사용할 수 있는 최대한의 공간을 사용하게 된다,  
    Column위젯 / Row위젯의 높이/ 널이는 무한하므로 자식요소로 넣으면  
    ListView가 자식위젯으로 들어가면 ListView의 높이 / 넓이도 무한이 되서 에러가 발생한다  
    - 해결법  
    : ListView안에 **shrinkWrap: true**를 작성하거나 ListView위젯을   Expanded 위젯으로 감싸서 해결 
