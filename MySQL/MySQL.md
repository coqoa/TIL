# MySQL

[생활코딩 MySQL 수업을 듣고 정리한 내용입니다](https://opentutorials.org/course/3161)

---

1. 데이터를 기록하는 최종적인 곳 : __표(table)__  
   관계형 데이터베이스는 엑셀처럼 스프레드시트와 비슷한 구조
2. 표가 많아지면 ?  
   정리정돈을 해야함 (파일이 많아지면 폴더에 정리하듯)  
   -> 파일의 폴더같은 개념이 데이터베이스(database) = __스키마(schema)__ = 연관된 데이터들을 그룹핑한 것  

3. 스키마가 많아지면 저장하는곳 : __데이터베이스 서버(database server)__ 

<br>

### 데이터베이스의 효용

1. 보안 (자체적인 보안체계 보유)
2. 권한기능 (권한에 따라 읽기/쓰기/수정/삭제 제한)

---

### 스키마(schema) = database

- 생성 :  __CREATE DATABASE__ 스키마이름;  
  `ex) CREATE DATABASE POMOTODO;`

- 제거 : __DROP DATABASE__ 스키마이름;  
  `ex) DROP DATABASE POMOTODO;`

- 스키마 보기 : __SHOW DATABASES__;

- 사용 : __USE__ 스키마이름;  
  `ex) USE POMOTODO;`
  
---

__SQL (Structured Query Language)__ : 구조화된 요청/질의하는 언어  
  -> 공통의 약속에 따라 데이터서버에 요청하도록하는 언어

__2가지특징__  
1. 쉽다
2. 중요하다 (관계형데이터베이스 카테고리의 제품들이 공통적으로 데이터베이스 서버를 제어할 때 사용하는 언어이므로)

__용어정리__  
- table : 표
- row, record : 행 ( = 데이터 하나하나)
- column : 열 ( = 데이터의 구조)


---

- 표 보기 : __SHOW TABLES__;

- 표만들기 

1. 컬럼만들기 :  
__CREATE TABLE__ 테이블명(  
    컬럼이름 __자료형__(length)      -> 엑셀과 SQL의 차이점(자료형), 자료형이 맞지않으면 에러   
 )  
 
    `ex) id INT(11) NOT NULL AUTO_INCREMENT, = 칼럼이름이 id이고 자료형은 int형이다`

2. __NOT NULL__ 으로 값이 없는것을 허용하지않는다

3. 각 id값을 다르게 하기 위해서 자동으로 증가해서 추가되도록 하는 __AUTO_INCREMENT__(자동증가 1)를 사용한다.  
   식별자가 중복되지않도록  
  * ID는 값이 무조건 필요하므로  NOT NULL을 뒤에 추가해준다.  

<br>

__* MySQL data type__  
    INT(m) : 정수  
    BIGINT(m) : 큰 정수  
        m은 숫자를 얼마까지 노출시킬지 결정하는 것 보통은 11을 지정함  

<br>

 __MySQL의 CRUD__
 ( create, read, update, delete)

<br>

SQL의 INSERT 구문 (row추가하기)

   * DESC 테이블명 하면 테이블의 구조가 나옴

__1.SQL INSERT 구문__

INSERT INTO 테이블명 (필드선택) VALUES('값');  
여러개를 하려면 콤마를 통해 구문

`ex) INSERT INTO 테이블명 (필드1,필드2,필드3,시간1) VALUES('필드1의값','필드2의값','필드3의값',NOW());`

  * 현재시간을 넣으려면 VALUES에 NOW()를 넣으면 됨


? 추가한 데이터를 보려면 ?   
__2. SQL SELECT구문 : 데이터 읽기__

__SELECT__ (projection) __FROM__ 테이블명;

* (projection) = 컬럼의 목록 / 모든 행을 다 보려면  ==  *

`ex) SELECT id,title,created,author FROM topic;  ==  topic테이블의 id, title, created, author만 본다`

__2-1 author가 coqoa인 컬럼만 보고싶으면?__

   SELECT * FROM 테이블명 __WHERE author='coqoa'__;

__2-2 정렬? (ASC는 오름차순 정렬, DESC는 내림차순 정렬)__ 

   SELECT * FROM 테이블명 WHERE author='coqoa' __ORDER BY id DESC__; `id기준 내림차순 정렬`

__2-3 보여지는 데이터의 수를 제한하려면 ?__

   SELECT * FROM 테이블명 WHERE author='coqoa' ORDER BY id DESC __LIMIT 2__; `보여지는 데이터 수 2로 제한`

__3. SQL UPDATE구문__  

   __UPDATE__ 테이블명 __SET__ 컬럼이름='변경사항', 또다른컬럼이름='변경사항' __WHERE id=2__; `id 가 2인행의 컬럼을 변경한다`

   __* WHERE를 항상 잘 사용하기__


__4. SQL DELETE구문__

   __DELETE__ (projection) __FROM__ 테이블이름 __WHERE id=5__; `id가 5인 projection을 삭제`

__-테이블 이름 수정하기__ 

__RENAME TABLE__ 테이블명 __TO__ 바꿀테이블명;

<br>
---

__관계형 데이터베이스__

필요한 이유?
장점 : 변수와 비슷한 역할 
1. 중복을 제거할 수 있다
2. 유지보수가 편해진다(수정, 제거, 첨가 등등..)
3. 같은속성이라도 다른 값이란 것을 확신할 수 있다

단점 : 복잡해진다
-> 단점을 해결하기 위해 저장은 분산하고 볼때는 합친다.

<br>

__- 관계형 데이터베이스의 꽃 JOIN__

__SELECT__ * __FROM__ 테이블명 __LEFT JOIN__ 결합할테이블명 __ON__ 테이블.컬럼명 = 결합할테이블.컬럼명;

`(ex. SELECT * FROM topic LEFT JOIN author ON topic.author_id = author.id;`

<br>

 __* 결합하는 부분을 제외__하고 깔끔하게 보고싶으면?__

SELECT __(projection)__ FROM 테이블명 LEFT JOIN 결합할테이블명 ON 테이블.컬럼명 = 결합할테이블.컬럼명;  
-> amigous 에러가 뜨면 컬럼이 __겹쳐서__ 애매하다는 뜻이므로 __테이블명.컬럼__ 으로 명확하게 지정해준다 

`(ex. SELECT topic.id,title,description.created,name,profile FROM topic LEFT JOIN author ON topic.author_id = author.id;)`


- MySQL 클라이언트

MySQL monitor : 어디에서나 사용할 수 있는 명령어 기반의 프로그램 / 어렵다

__MySQL workbench__ : gui기반의 프로그램, 쉽다 / 서버컴퓨터들이 gui를 지원하지 않는다면 사용이 불가능하다, 다소 느리다,

* 명령어기반 / GUI기반을 적절하게 잘 혼용하는게 데이터베이스를 잘 다루는 방법
