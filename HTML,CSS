순서 : css입히기전에 디자인을 빼고 콘텐트만으로 HTML문서 만들기



<h1>~<h6> : 크기조절



<li> : 리스트, <ul> 또는 <ol> 로 묶어서 사용

<ul> : 번호없는 리스트

<ol> : 번호 있는 리스트

<form> - <legend : 큰제목 : 레이아웃생기는> , fieldset : 범위, <label : 작은제목>, <input : 입력창>, <textarea : 2줄이상 입력할 수 있는 입력창>

<input>의 속성 - type = "text" : 텍스트 형태로 입력하는 창, type = "checkbox" : 체크박스, type = "radio" 라디오타입 선택지

                            type = "submit" 제출버튼, value ="해당 속성에 이름 부여"

<table> 로 묶은 <tr>, <td> : 표 생성 , tr = 가로, td = 세로

<div> : 정의할 수 없는 태그들을 그룹핑해주는 태그

<select>로 묶은 <option>, value값으로 이름 부여



시멘틱태그 (의미가 부여된 태그) : 사람들이 가장 많이 쓰는 이름으로 표준화

id 속성부여 ex) <div id = "header"> -> <header><h2></header> : 의미를 가진 <div>가 되었음

<section> : 여기서부터 다시 텀버링을 하겠다 -> header의 의미를 보존한 채로 넘버링이 가능한다

section태그를 의미에 맞게 변경

<nav> : 네비게이션 역할을 하는 태그 그룹핑

<aside> : head, main, footer가 아닌 역할 : 부가적인 정보를 표현



블럭태그와 인라인태그

블럭태그는 한줄을 모두 사용(자신만의 영역을 가짐, 너비의 100%) ex. <br>, <div>, <li>

인라인 태그는 옆으로 줄세워서 표현(너비와 높이를 지정할 수 없다, mark up으로만 의미가 있음) ex. <a> 





생코 : HTML - 언어는 약속이고 의미에 집중해서 mark up 한다, 디자인은 css의 영역으로 남겨둔다



<a></a> : 링크임을 알려주는 태그 

속성으로 href="링크주소"를 사용,

+ 새탭으로 열려면 target="_blank" 속성추가,

+ 툴팁은 title="툴팁내용" 속성 추가



<li></li> : 리스트

<ul>과 <ol>태그로 묶어서 사용한다, 

<ul></ul> : 순서 없는 리스트

<ol></ol> : 순서 있는 리스트



문서의 구조 

html - head : 본문 외의 정보, ex. title, meta 등등

           body : 본문



<p></p> : 단락 구분, 줄바꿈을 css를 통해서도 구현할 수 있다

<br> : (void element), 줄바꿈 태그, <br>을 줄바꿈 하기보단 <p>로 단락화 하는게 좋다

<img></img> 이미지 추가 태그

속성 : src ="이미지 주소", width = "너비", height = "높이", alt = "이미지 설명" (alternative, 시각장애인을 위해)

<table></table> :

각 항목을 <td></td>로 묶어줌, 각 행은 <tr></tr>그룹핑한 후 <table>로 묶어서 사용

속성 : border ="테두리크기"



<inpu></input> : 사용자의 입력 받는 태그

속성 :

type = "text",

type = "password",

type = "submit",

type = "name",

type = "value", 

type = "radio" 개별선택하려면 name=""속성을 추가하면 됨, 같은 name끼리는 하나만 선택가능

value=""속성으로 화면에 표시되는 값을 바꿀 수 있음

type ="checkbox" : 다중선택 가능한 체크박스, checked속성 넣으면 기본값으로 체크되어있음

type ="button" : 버튼생성

value=""속성으로 버튼명 설정

type ="reset" : 모든 form태그를 초기화



<form></form> : 사용자의 입력을 전송하는 태그 (input태그를 그룹핑하기위한 용도)

(<form action ="전송받을 주소" >)



<textarea></textarea> : 두 줄 이상 입력할 수 있는 텍스트 입력창 : 



<select></select> : option을 선택하는 dropdown list

name속성을 추가해서 해당 값을 서버에 전달함 <select name = "color"></select>

<option></option> : select태그로 묶어서 사용

value를 설정해서 해당 값 전달(option으로 묶은 값이 아니라 value에 부여된 값을 전달함) <option value = "black">

-> form태그로 submit태그와 함께 묶어서 제출하면 서버에 color=black 으로 전달됨



