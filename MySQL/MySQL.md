1. 데이터를 기록하는 최종적인 곳 : 표(table)

관계형 데이터베이스는 엑셀처럼 스프레드시트와 비슷한 구조



2. 표가 많아지면 ? 정리정돈을 해야함 (파일이 많아지면 폴더에 정리하듯)

-> 파일의 폴더같은 개념이 데이터베이스(database) = 스키마(schema) = 연관된 데이터들을 그룹핑한 것



3. 스키마가 많아지면 저장하는곳 : 데이터베이스 서버(database server)



데이터베이스의 효용

1. 보안 (자체적인 보안체계 보유)

2. 권한기능 (권한에 따라 읽기/쓰기/수정/삭제 제한)



스키마(schema) = database

- 생성 :  CREATE DATABASE 스키마이름;
  ex) CREATE DATABASE POMOTODO;

- 제거 : DROP DATABASE 스키마이름;

  ex) DROP DATABASE 스키마이름;

- 스키마 보기 : SHOW DATABASES;

- 사용 : USW 스키마이름;



SQL (Structured Query Language) - 구조화된 요청/질의하는 언어

-> 공통의 약속에 따라 데이터서버에 요청하도록하는 언어

2가지특징

1. 쉽다

2. 중요하다 (관계형데이터베이스 카테고리의 제품들이 공통적으로 데이터베이스 서버를 제어할 때 사용하는 언어이므로)



용어정리

table : 표

row, record : 행 ( = 데이터 하나하나)

column : 열 ( = 데이터의 구조)



표만들기 (표 보기 : SHOW TABLES;)

1. 컬럼만들기 :

CREATE TABLE 테이블명(

    컬럼이름 자료형(length)      -> 엑셀과 SQL의 차이점(자료형), 자료형이 맞지않으면 에러,

 )



ex) id INT(11) NOT NULL AUTO_INCREMENT, = 칼럼이름이 id이고 자료형은 int형이다,

NOT NULL으로 값이 없는것을 허용하지않는다

각 id값을 다르게 하기 위해서 자동으로 증가해서 추가되도록 하는 AUTO_INCREMENT(자동증가 1)를 사용한다,

    식별자가 중복되지않도록



* ID는 값이 무조건 필요하므로  NOT NULL을 뒤에 추가해준다

*MySQL data type

   INT(m) : 정수

   BIGINT(m) : 큰 정수

        m은 숫자를 얼마까지 노출시킬지 결정하는 것 보통은 11을 지정함



 MySQL의 CRUD

 ( create, read, update, delete)



SQL의 INSERT 구문 (row추가하기)



*DESC 테이블명 하면 테이블의 구조가 나옴



1.SQL INSERT 구문

INSERT INTO 테이블명 (필드선택) VALUES('값');

여러개를 하려면 콤마를 통해 구문

ex) INSERT INTO 테이블명 (필드1,필드2,필드3,시간1) VALUES('필드1의값','필드2의값','필드3의값',NOW());

*현재시간을 넣으려면 VALUES에 NOW()를 넣으면 됨



? 추가한 데이터를 보려면 ? 



2. SQL SELECT구문 : 데이터 읽기

SELECT (projection) FROM 테이블명;

(projection) = 컬럼의 목록 / 모든 행을 다 보려면  ==  *

ex) SELECT id,title,created,author FROM topic;  ==  topic테이블의 id, title, created, author만 본다

2-1 author가 coqoa인 컬럼만 보고싶으면?

    SELECT *. FROM 테이블명 WHERE author='coqoa';

2-2 정렬? (ASC는 오름차순 정렬, DESC는 내림차순 정렬) 

    SELECT *. FROM 테이블명 WHERE author='coqoa' ORDER BY id DESC;  ==  id기준 내림차순 정렬

2-3 보여지는 데이터의 수를 제한하려면 ?

    SELECT *. FROM 테이블명 WHERE author='coqoa' ORDER BY id DESC LIMIT 2; == 보여지는 데이터 수 2로 제한



3. SQL UPDATE구문

    UPDATE 테이블명 SET 컬럼이름='변경사항', 또다른컬럼이름='변경사항' WHERE id=2;  ==id 가 2인행의 컬럼을 변경한다

    * WHERE를 항상 잘 사용하기



4. SQL DELETE구문

    DELETE (projection) FROM 테이블이름 WHERE id=5;  == id가 5인 projection을 삭제





관계형 데이터베이스

필요한 이유?

장점 : 변수와 비슷한 역할 :

1. 중복을 제거할 수 있다

2. 유지보수가 편해진다(수정, 제거, 첨가 등등..)

3. 같은속성이라도 다른 값이란 것을 확신할 수 있다



단점 : 복잡해진다

-> 단점을 해결하기 위해 저장은 분산하고 볼때는 합친다.



-테이블 이름 수정하기 

RENAME TABLE 테이블명 TO 바꿀테이블명;



- 테이블분리하기



- 관계형 데이터베이스의 꽃 JOIN

SELECT * FROM 테이블명 LEFT JOIN 결합할테이블명 ON 테이블.컬럼명 = 결합할테이블.컬럼명;

(ex. SELECT * FROM topic LEFT JOIN author ON topic.author_id = author.id;﻿



 * 결합하는 부분을 제외하고 깔끔하게 보고싶으면?

SELECT (projection) FROM 테이블명 LEFT JOIN 결합할테이블명 ON 테이블.컬럼명 = 결합할테이블.컬럼명;
-> amigous 에러가 뜨면 컬럼이 겹쳐서 애매하다는 뜻이므로 테이블명.컬럼 으로 명확하게 지정해준다 

(ex. SELECT topic.id,title,description.created,name,profile FROM topic LEFT JOIN author ON topic.author_id = author.id;)



- 인터넷과 데이터베이스의 관계



- MySQL 클라이언트

MySQL monitor : 어디에서나 사용할 수 있는 명령어 기반의 프로그램 / 어렵다

MySQL workbench : gui기반의 프로그램, 쉽다 / 서버컴퓨터들이 gui를 지원하지 않는다면 사용이 불가능하다, 다소 느리다,

* 명령어기반 / GUI기반을 적절하게 잘 혼용하는게 데이터베이스를 잘 다루는 방법
