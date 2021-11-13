# MongoDB세팅하기

### MongoDB Atlas 가입/초기셋팅 방법
1. mongodb atlas 검색, 가입  
2. 프리티어 선택  
3. 서버위치 선택 : 무료면서 한국과 가까운 도쿄  
4. Create Cluster  
5. 왼쪽의 Database Access 가서 DB접속용 ID/password 생성  
6. 왼쪽의 Network Access 에서 IP추가 (데이터베이스에 접속할 수 있는 IP를 미리 정의해놓는 보안장치)  
7. Databases메뉴로 들어가서 Browse Collection 클릭  
8. Collections탭에서 Add My Own Data 클릭
9. Database name / Collection Name 설정

### 서버에서 DB에 접속하기위한 url
1. 왼쪽 Databases 메뉴에 들어가서 데이터베이스의 Connect버튼을 클릭  
2. Connect your application클릭  
3. url 복사  
`ex.) mongod+srv://DB계정아이디:DB계정패스워드@cluster0.l9rep.mongodb.net/데이터베이스이름?retryWrites=true&w=majority`

### 서버에서 DB 접속하기
1. 터미널에서 npm install mongodb 입력해서 라이브러리 설치  
2. server.js 상단에 코드추가  
```const MongoClient = require('mongodb').MongoClient;```

3. 하단에 코드추가   
``` js
MongoClient.connect('위에서 복사한 URL', function(err, client){
  if (err) return console.log(에러);
  // 서버를 띄우기 위한 코드를 내부에 배치하기
  app.listen('8080', function(){
    console.log('8080포트 접속성공')
  });
})
* 접속url에서 DB계정아이디, DB패스워드, 데이터베이스이름을 잘 맞춰서 넣어야 작동함
에러시 확인할 부분
1. 접속url의 따옴표확인
2. url의 아이디/패스워드에 Atlas계정이 아닌 Datavase Access메뉴에서 만든 DB계정을 넣은건지 확인
3. URL내에 패스워드 입력시 특수문자를 넣었는지 확인
4. Network Access메뉴에서 허용한 IP로 접속한건지 확인
5. app.listen 코드의 위치 확인
``` 


