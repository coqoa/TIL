# 콘솔 문자열 출력 PrintStream

문자를 출력하려면 OutputStream에서는 write( )함수를 썻다.   
write( )에는 KeyCode나 char형인 '문자'만 들어가기에 **문자열**을 표현하려면  
여러개의 write( )를 사용해야 하고, flush( )를 써야 출력이 가능하다는 단점이 있다.  
이러한 점들이 문자열을 표현하기에 비효율적이었고 print()를 사용하면 효율적으로 사용할 수 있다.

```java
System.out.print("어쩌구저쩌구");   
System.out.print("어쩌구저쩌구");  
System.out.print("어쩌구저쩌구");  
//어쩌구저쩌구어쩌구저쩌구1어쩌구저쩌구2
```
print( )함수는 이어서 쓴다
이를 내려 쓰기 우해선 두가지 방법이 있다  
1. escape문자 쓰기
2. println 쓰기  

- escape문자  
	> \b : 백스페이스  
	\t : 들여쓰기  
	\n : 새로운 행 삽입  
	\f : 다음페이지로  
	\r : 제일 왼쪽으로    
	\' : 홑따옴표 삽입  
	\": 이중따옴표 삽입  
	\\ : 역슬래쉬 삽입
    >
 

- println

```java
System.out.println("내려쓰기");   
System.out.println("내려쓰기1");  
System.out.println("내려쓰기2");
//내려쓰기
//내려쓰기1
//내려쓰기2
```

같은값을 각기 다른 형식으로 출력하기위해서는 printf와 지시자를 쓴다.  
(이어쓰기 때문에 escape문자 \n을 추가해줘야 줄바꿈이된다)
> ##### 지시자
> %b : 불리언형식  
> %d : 10진수  
> %o : 8진수  
> %x : 16진수  
> %f : 부동소수점  
> %e : 지수   
> %c : 문자  
> %s  : 문자열  

```java
System.out.printf("15 + 15 = %d \n", 30);   
System.out.printf("15 + 15 = %b \n", 30);   
System.out.printf("15 + 15 = %o \n", 30);   
System.out.printf("15 + 15 = %x \n", 30);   
System.out.printf("15 + 15 = %f \n", 30.0); //소수를 표시하지 않으면 에러
System.out.printf("15 + 15 = %e \n", 30.0); //소수를 표시하지 않으면 에
System.out.printf("15 + 15 = %c \n", '3'); // char형이므로 홑따옴표와 문자하나만 출력가능
System.out.printf("15 + 15 = %s \n", 30);   
//콘솔출력//
15 + 15 = 30 (10진수)
15 + 15 = true (boolean)
15 + 15 = 36 (8진수)
15 + 15 = 1e (16진수)
15 + 15 = 30.000000 (부동소수점)
15 + 15 = 3.000000e+01 (지수)
15 + 15 = 3 (문자)
15 + 15 = 30 (문자열)

```
