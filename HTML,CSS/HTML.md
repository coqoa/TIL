# HTML

### HTML - 언어는 약속이고 의미에 집중해서 mark up 한다, 디자인은 css의 영역으로 남겨둔다


#### ```<h1>```~```<h6>``` : 크기조절

#### ```<a> </a>``` : 링크임을 알려주는 태그 
```
	속성으로 href="링크주소"를 사용,
	
	+ 새탭으로 열려면 target="_blank" 속성추가,
	
	+ 툴팁은 title="툴팁내용" 속성 추가
```


#### ```<li> </li>``` : 리스트
```
	<ul>과 <ol>태그로 묶어서 사용한다, 

	<ul></ul> : 순서 없는 리스트

	<ol></ol> : 순서 있는 리스트
```


#### 문서의 구조 
```
	html - head : 본문 외의 정보, (ex. title, meta 등등)   
		   - body : 본문
```


#### ```<p> </p>``` : 단락 구분, 줄바꿈을 css를 통해서도 구현할 수 있다



#### ```<br>``` : (void element), 줄바꿈 태그
```
	<br>을 줄바꿈 하기보단 <p>로 단락화 하는게 좋다
```                              

#### ```<img> </img>``` 이미지 추가 태그
```
	속성 : src ="이미지 주소", width = "너비", height = "높이", 
    	  alt = "이미지 설명" (alternative, 시각장애인을 위해)
```

#### ```<table> </table>``` : 표  
```
	각 항목을 <td> </td>로 묶어줌, 각 행은 <tr> </tr>그룹핑한 후 <table>로 묶어서 사용
	
	속성 : border ="테두리크기"
```





#### ```<form> </form>``` : 사용자의 입력을 전송하는 태그 (input태그를 그룹핑하기위한 용도)
```
<form action ="전송받을 주소" >
```

#### 정보를 감춰서 보내야 할 경우 : method="post"속성 추가 (form태그는 대부분 post방식)

(사용자 정보가 url로 노출되지 않도록)

\* url로 데이터를 보내는 방식 : get방식  


#### ```<legend> </legend>``` : 레이아웃이 생기는 큰 제목
```
	<legend></legend> 큰 제목을 생성하는 태그 (레이아웃의 이름을 정의하는데 사용, field태그로 감싸서 사용한다)
```
#### ```<field> </field>``` : 범위를 표시하는 레이아웃을 생성


#### ```<label> </label>``` : 이름표 (field태그로 감싸면 레이아웃 생성)
```
	for속성을 통해 어느 이름표인지 표시하고 input태그의 type대신 id="for속성에서 정의한 이름"으로 연결

	label클릭시 해당 영역에 커서가 자동으로 간다 (더 넓은영역을 사용 할 수 있다)

	아니면 <label> </label>로 감싸주면 됨
```

#### ```<textarea> </textarea>``` : 두 줄 이상 입력할 수 있는 텍스트 입력창 : 



#### ```<input> </input>``` : 사용자의 입력 받는 태그
```
속성 :

	type = "text" : 텍스트 형태로 입력하는 창

	type = "password" : 비밀번호 입력 창

	type = "submit" : 제출버튼 생성(form의 action에 정의된 주소로 값 전달)

	type = "name" : 그룹핑, 전달시 url에 값 표시

	type = "value" : 해당 속성에 이름 부여, url에 값 표시

	type = "radio" : 라디오 타입 선택지

		 개별선택하려면 name=""속성을 추가하면 같은 name끼리는 하나만 선택가능

	type ="checkbox" : 다중선택 가능한 체크박스, checked속성 넣으면 기본값으로 체크되어있음

	type ="button" : 빈 값의 버튼생성

 		value=""속성으로 버튼명 설정

	type ="reset" : 모든 form태그를 초기화
```


#### ```<select> </select>``` : option을 선택하는 dropdown list
```
 	name속성을 추가해서 해당 값을 서버에 전달함

		<select name = "color"></select>
```
#### ```<option> </option>``` : select태그로 묶어서 사용
```
   value를 설정해서 이름 부여,option으로 묶은 값이 아니라 value에 부여된 값을 전달함)
   		
        <option value = "black">
```
```
  -> form태그로 submit태그와 함께 묶어서 제출하면 서버에 color=black 으로 전달됨
```






#### file전송 

type = "file" name="파일받는 곳" 하고 form태그로 감싸준다
```
	<form action="주소" method="post" enctype="multiple/form-data"></form>
```


#### ```<meta>``` : 설명하는 태그
```
	<meta charset = "utf-8>

	<meta name = "description" contents="소개내용">

	<meta name="keyword" contents = "키워드1,키워드2,키워드3">

	<meta name = "author" contents = "저작권자 정보">
```


#### 시맨틱태그 : 기능은 없고 의미를 부여하는 태그
```
	큰제목 : <header></header>

	하단정보 : <footer></footer>

	네비게이션 : <nav></nav>

	본문 : <article></article>

	head, main, footer가 아닌 역할 / 부가적인 정보 표현 : <aside></aside>

	여러개의 article은 <section></section>으로 묶어준다
```
```
	article : 내용이 각기 동립적이고 홀로 설 수 있는 내용 (블로그 글, 포럼 글, 뉴스 기사 등)
	
		* 여러개의 article을 section으로 묶어서 사용 가능
	
    
	section : 서로 관계 있는 문서를 분리하는 역할 (문서를 다른주제로 구분짓기 위해 사용)

		여기서부터 다시 넘버링을 하겠다는 의미로 header의 의미를 보존한 채로 넘버링 할 수 있다

			(<h1>~<h6>사용)

	div : 의미적으로 관계가 없다며 오직 묶는 역할을 위해 사용

		밑으로 갈 수록 추상적인 의미
```



#### 블럭태그와 인라인태그
```
	블럭태그는 한줄을 모두 사용(자신만의 영역을 가짐, 너비의 100%) ex. <br>, <div>, <li>

	인라인 태그는 옆으로 줄세워서 표현(너비와 높이를 지정할 수 없다, mark up으로만 의미가 있음) ex. <a> 
```
