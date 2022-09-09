#### Container()

- Containers with no children try to be as big as possible

	"컨테이너는 child가 없을 경우 최대한의 공간을 차지하려한다"

 

- Containers with Children size themselves to their children

	"컨테이너는 children를 가지게 되면 children의 크기로 줄어든다

 

- 컨테이너는 오직 하나만의 child를 가진다

```dart

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Containers',
      home: MyPage(),
    );
  }
}
class MyPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      // backgroundColor를 blue로 지정했음에도 Container() 때문에 스크린 전체가 red로 출력된다
      backgroundColor: Colors.blue,
      body: Container(
        color: Colors.red,
      ),
    );
  }
}

```

```dart

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Containers',
      home: MyPage(),
    );
  }
}
class MyPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.blue,
      // SafeArea()를 통해 컨텐츠가 스크린 밖으로 빠져나가지 않도록 경계를 쳐준다
      body: SafeArea(
        child: Container(
          color: Colors.red,
          //Container()에 child가 있으면 Container()는 Child의 부분 만큼만 차지한다
          child: Text('hello'),
          width: 100,
          height: 100,
          // margin: EdgeInsets.all(20)
          // 세로축과 가로축을 가진 속성
          margin:EdgeInsets.symmetric(
            vertical: 80,
            horizontal: 20
          ),
          padding: EdgeInsets.all(40),
        ),
      ),
    );
  }
}


```

### Column & Row

#### Column()

- 세로축 정렬을 위한 위젯으로 가로축은 크기제한이 있고 세로축은 제한이 없다

- `Center()`와 `Column()의 mainAxisAlignment.center` 속성을 통해  화면 가운데 정렬을 할 수 있다

```dart

// Center() 정렬
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Containers',
      home: MyPage(),
    );
  }
}
class MyPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.green[200],
      // SafeArea()를 통해 컨텐츠가 스크린 밖으로 빠져나가지 않도록 경계를 쳐준다
      body: SafeArea(
        // Center() 정렬
        child: Center(
          child: Column(
            // mainAxisAlignment를 사용하면 위젯의 좌우 통제권은 Center()가, 상하 통제권은 Column()이 가진다
            // mainAxisAlignment: MainAxisAlignment.center,

            // mainAxisSize.min을 사용하면 Center() 위젯의 상하 통제권을 가지게 됨
            mainAxisSize: MainAxisSize.min,
            
            children: [
              Container(
                width: 100,
                height: 100,
                color: Colors.white,
                child: Text('Container 1'),
              ),
              Container(
                width: 100,
                height: 100,
                color: Colors.blue,
                child: Text('Container 2'),
              ),
              Container(
                width: 100,
                height: 100,
                color: Colors.red,
                child: Text('Container 3'),
              )
            ],
          ),
        )
      ),
    );
  }
}

```

```dart

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Containers',
      home: MyPage(),
    );
  }
}
class MyPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.green[200],
      // SafeArea()를 통해 컨텐츠가 스크린 밖으로 빠져나가지 않도록 경계를 쳐준다
      body: SafeArea(
        child: Column(
          // 아래에서 위로 순서대로 배치
          // verticalDirection: VerticalDirection.up,

          // 위에서 아래로 순서대로 배치
          // verticalDirection: VerticalDirection.down,

          // child가 child만큼 간격을 두고 배치
          // mainAxisAlignment: MainAxisAlignment.spaceEvenly,

          // 세로축의 위, 중간, 아래 위치에 각각 배치
          // mainAxisAlignment: MainAxisAlignment.spaceBetween,

          // 가로축 end 위치로 정렬
          // crossAxisAlignment: CrossAxisAlignment.end,
          
          // 각 컨테이너의 width를 없애면 화면 길이만큼 늘림
          crossAxisAlignment: CrossAxisAlignment.stretch,

          children: [
            Container(
              width: 100,
              height: 100,
              color: Colors.white,
              child: Text('Container 1'),
            ),
            // SizedBox를 통해 컨테이너간 간격을 설정할 수 있음
            // SizedBox(
            //   height: 30.0,
            // ),
            Container(
              width: 100,
              height: 100,
              color: Colors.blue,
              child: Text('Container 2'),
            ),
            Container(
              width: 100,
              height: 100,
              color: Colors.red,
              child: Text('Container 3'),
            ),
            // // crossAxisAlignment: CrossAxisAlignment.end,와 
            // // invisible Container를 사용해서 모든 컨테이너를 우측 배치
            // Container(
            //   // 가로축 끝까지 확장
            //   width: double.infinity,
            //   height: 20,
            // )
          ],
        ),
      ),
    );
  }
}

```

#### Row( )

- 가로축 정렬을 위한 위젯으로 세로축은 크기제한이 있고 가로축은 제한이 없다

+ `Center()`와 `Row()의 mainAxisAlignment.center` 속성을 통해 화면 가운데 정렬을 할 수 있다

```dart

import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Containers',
      home: MyPage(),
    );
  }
}
class MyPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.green[200],
      // SafeArea()를 통해 컨텐츠가 스크린 밖으로 빠져나가지 않도록 경계를 쳐준다
      body: SafeArea(
        child: Row(
          children: [
            Container(
              width: 100,
              height: 100,
              color: Colors.white,
              child: Text('Container 1'),
            ),
            // SizedBox를 통해 컨테이너간 간격을 설정할 수 있음
            // SizedBox(
            //   width: 30.0,
            // ),
            Container(
              width: 100,
              height: 100,
              color: Colors.blue,
              child: Text('Container 2'),
            ),
            Container(
              width: 100,
              height: 100,
              color: Colors.red,
              child: Text('Container 3'),
            ),
          ],
        ),
      ),
    );
  }
}

```


#### 정리하기
- SafeArea()  
: 컨텐츠가 스크린 밖으로 빠져나가지 않도록 경계를 만들어줌

 
- Column()
	- 세로축 : 길이 제한 x
	- 가로축 : children width값에 따른 길이 제한

- Row()
	- 세로축 : children height값에 따른 길이 제한
	- 가로축 : 길이 제한 x

- mainAxisAlignment  
	: 위젯의 진행 방향으로 배치하는 속성
	- .start : 시작 부분 정렬
	- .center : 가운데 정렬
	- .end : 끝 부분 정렬
	- .spaceAround : children을 각각 둘러싸는 공백 생성
	- .spaceBetween : children 간에만 공백을 주고 양 끝은 공백없이 배치
	- . spaceEvenly : 동일한 공백을 생성

- mainAxisSize  
: 상위 위젯인 Center()에 상/하 통제권을 넘겨줌
 
- crossAxisAlignment  
: 위젯의 진행 방향을 가로지르는 방향으로 배치하는 속성
	- .start : 시작 부분 정렬
	- .center : 가운데 정렬
	- .end : 끝 부분 정렬  
   	(end 속성과 invisible container를 같이 사용해서 모든 컨테이너를 우측에 배치할 수 있음)
	- .stretch : 끝까지 늘리기
	- .baseline
	- .value

---
Column. 
![col](https://user-images.githubusercontent.com/81023768/189307198-7e6b459b-8202-4f7f-88b3-27c64c589915.png)  
---
Row  
![row](https://user-images.githubusercontent.com/81023768/189307246-d598a6b9-8587-42c1-8723-56abc5ecb805.png)   
---
Center  
![center](https://user-images.githubusercontent.com/81023768/189307242-4c7660ba-f7a2-4ca6-afb8-9712246d32be.png)
---
