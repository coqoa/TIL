# switch문 & break문 & continue문
예를들어 if문을 병렬적으로 100번 사용하면 참과 거짓값에 관계없이 100번 검사를 할 것이다  
이런 문제점을 해결하기위해 else if문을 사용한다면 참값이 나오면 즉시 검사를 멈추겠지만 70번째 조건이 참이라면 69번의 검사를 진행해야하는 단점이 있다

#### switch문 & break문
이런 문제점을 해결하기위해서 책의 목차같은 역할을 하는 switch문을 사용하면 된다.  
- break문을 사용해서 switch문에서 빠져나올 시점을 설정해준다.  
- case대신 default를 사용하면 설정하지 않은 입력값에 대해 수행될 코드를 설정할 수 있다.  
``` java
switch(조건식)
	case 1:
    	//조건식이 1일경우 수행될 코드
        break;// 코드수행후 switch문을 빠져나감
    
    case 2: 
    	//조건식이 2일경우 수행될 코드
    	break;
        
    case 3: 
    	//조건식이 2일경우 수행될 코드
        break;
        .
        .
        .
    default :
    	//범위 외의 값 입력시 수행될 코드
        
```

break문만 사용한다면 switch문만 빠져나올 수 있지만 중첩된 제어구조에서 원하는 곳까지 빠져나오려면 break에 라벨을 붙이면 된다.  

```java
EXIT: //EXIT라는 라벨사용

while(true){

  switch(조건식)
  //case 라벨:
  case 1:
    	//조건식이 1일경우 수행될 코드
        break;// 코드수행후 switch문을 빠져나감
    
  case 2: 
    	//조건식이 2일경우 수행될 코드
    	break;
        
  case 3: 
    	//조건식이 2일경우 수행될 코드
        break EXIT; // 코드수행후 EXIT라벨의 위치까지 빠져나감
}        
```

prompt로 입력받고 조건식에 맞는 코드를 수행하는 코드 예제

```java
package ex5;

import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import java.util.Scanner;

public class Ex3_AvgProgram {
	public static void main(String[] args) throws IOException {

      // --- << main menu 입력 >> -------------------
      Scanner scan = new Scanner(System.in);

      EXIT:
      while(true){
	      int menu;
	    	  
	      System.out.println("┌─────────────────────────────────┐");
	      System.out.println("│             Main Menu           │");
	      System.out.println("└─────────────────────────────────┘");
	      System.out.println("1. Count");
	      System.out.println("2. Total");
	      System.out.println("3. Avg");
	      System.out.println("4. Exit");
	      System.out.println();
	      System.out.println("숫자를 입력하세요.");
	      System.out.print(">");
	      menu = scan.nextInt();

	      switch(menu) {
	      
		      case 1:
			      // --- <<count 계산하기 >> -----------------------------------------------
		      {
			      int count = 0;
			      {
			         File srcFile = new File("res/data.txt");
			         FileInputStream srcFis = new FileInputStream(srcFile);
			         Scanner fscan = new Scanner(srcFis);
			
			         while (fscan.hasNext()) {
			            fscan.next();
			            count++;
			         }
			
			         fscan.close();
			         srcFis.close();
			      }
			      
			      System.out.println("┌─────────────────────────────────┐");
			      System.out.println("│               Count             │");
			      System.out.println("└─────────────────────────────────┘");
			      System.out.printf("Count is %d\n", count);
			      System.out.println("- - - - - - - - - - - - - - - - - - - -");
			      break;
		      }   
		      case 2:
			      // --- <<total 계산하기 >> -----------------------------------------------
		      {   
		    	  int total = 0;
			      {
			         File srcFile = new File("res/data.txt");
			         FileInputStream srcFis = new FileInputStream(srcFile);
			         Scanner fscan = new Scanner(srcFis);
			
			         while (fscan.hasNext()) {
			            String x_ = fscan.next();
			            // fout.print(x_);
			
			            int x = Integer.parseInt(x_);
			            total += x;
			         }
			         fscan.close();
			         srcFis.close();
			
			      }
			      
			      System.out.println("┌─────────────────────────────────┐");
			      System.out.println("│               Total             │");
			      System.out.println("└─────────────────────────────────┘");
			      System.out.printf("Total is %d\n", total);
			      System.out.println("- - - - - - - - - - - - - - - - - - - -");
			      break;
		      }     
			  case 3:
		      // --- <<avg 계산하기 >> -----------------------------------------------
			  {  
				  int count = 0;
				  {
			         File srcFile = new File("res/data.txt");
			         FileInputStream srcFis = new FileInputStream(srcFile);
			         Scanner fscan = new Scanner(srcFis);
			
			         while (fscan.hasNext()) {
			            fscan.next();
			            count++;
			         }
			         fscan.close();
			         srcFis.close();
				 }
				  
			     int total = 0;
			     {
				     File srcFile = new File("res/data.txt");
			         FileInputStream srcFis = new FileInputStream(srcFile);
			         Scanner fscan = new Scanner(srcFis);
			         
			         while (fscan.hasNext()) {
				        String x_ = fscan.next();
				        int x = Integer.parseInt(x_);
				        total += x;
				     }
			         fscan.close();
			         srcFis.close();
			     }  
			     
				 double avg = total / (double) count;
			      
			      System.out.println("┌─────────────────────────────────┐");
			      System.out.println("│              Average            │");
			      System.out.println("└─────────────────────────────────┘");
			      System.out.printf("Average is %.2f\n", avg);
			      System.out.println("- - - - - - - - - - - - - - - - - - - -");
			      break;
			  }
			  case 4:
				  System.out.println("┌─────────────────────────────────┐");
			      System.out.println("│                END              │");
			      System.out.println("└─────────────────────────────────┘");
				  break EXIT;
			 
			  default :
				 System.out.println("잘못 입력하셨습니다.");
	      }
 	   }
    }
}
//------<<출력내용>>------
┌─────────────────────────────────┐
│             Main Menu           │
└─────────────────────────────────┘
1. Count
2. Total
3. Avg
4. Exit

숫자를 입력하세요.
>1
┌─────────────────────────────────┐
│               Count             │
└─────────────────────────────────┘
Count is 14
- - - - - - - - - - - - - - - - - - - -
┌─────────────────────────────────┐
│             Main Menu           │
└─────────────────────────────────┘
1. Count
2. Total
3. Avg
4. Exit

숫자를 입력하세요.
>2
┌─────────────────────────────────┐
│               Total             │
└─────────────────────────────────┘
Total is 1118
- - - - - - - - - - - - - - - - - - - -
┌─────────────────────────────────┐
│             Main Menu           │
└─────────────────────────────────┘
1. Count
2. Total
3. Avg
4. Exit

숫자를 입력하세요.
>3
┌─────────────────────────────────┐
│              Average            │
└─────────────────────────────────┘
Average is 79.86
- - - - - - - - - - - - - - - - - - - -
┌─────────────────────────────────┐
│             Main Menu           │
└─────────────────────────────────┘
1. Count
2. Total
3. Avg
4. Exit

숫자를 입력하세요.
>4
┌─────────────────────────────────┐
│                END              │
└─────────────────────────────────┘


```

#### continue문 & break문
``` java

package ex5.array;

import java.io.IOException;
import java.util.Scanner;

public class con_bre_Program {

	public static void main(String[] args) throws IOException {
		
		int n = 0;

		Scanner scan = new Scanner(System.in);
		System.out.println("값을 공백으로 구분해서 6개 이상 입력해주세요");
			
		while(scan.hasNext()) {
				
			n=scan.nextInt();
			
			if(n<10) { //n의 값이 10미만이면 건너뛴다.
				continue;
			}
			if(n>200) { //n의 값이 200이상이면 while문에서 빠져나간
				break;
			}
			System.out.println(n);
		}
	}
}
//------<<출력결과>>------
값을 공백으로 구분해서 6개 이상 입력해주세요
1 3 20 199 201 30
20
199
//순서대로 값을 읽어서 10이상인 20, 199를 출력하고 201이 읽히는순간 break문이 실행되서 반복을 종료한다.
```
