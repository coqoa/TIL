# if, else if로 조건에 만족하는 값 출력하기
파일로부터 정보를 받고 if / else if 문으로 조건에 만족하는 값을 출력한다.  
값을 출력하기 위해 int형의 menu라는 변수에 System.in을 매개변수로 가지는 scan 객체를 대입해 준다.  
반복적으로 값을 출력하기 위해 while 문으로 감싸준다.

1. 1을 입력 : 파일을 공백 단위로 받아온 데이터의 갯수를 출력  
2. 2를 입력 : 파일을 공백 단위로 받으며 모두 합친 값을 출력  
3. 3을 입력 : 1을 2로 나눈 값을 float형으로 출력한다  
4. 4를 입력 : break 문을 사용해서 while 문에서 탈출한다  
5. while 문이 끝나면 End를 출력한다  

- 문제점 : Avg는 Total/Count로 계산하는데 Total과 Count를 출력하기 이전에 AVG를 출력하면 NaN을 출력한다
  - 해결 방법은??  
  - ...
  
- while 문 밖에서 변수를 선언하면 반복해서 출력 시 값이 더해지는 문제가 발생하고   
	while 문 안에서 변수를 선언하면 매번 값을 초기화해서 Avg 값이 NaN으로 출력되는 문제가 생긴다
   - 해결 방법은??  
   - ...



#### if를 반복적으로 사용하는것과 else if를 사용하는것의 차이?
>if 문은 true/false를 판별해서 정해진 동작을 수행하는 것이고 else if는 조건이 false일 때 한 번 더 검사하는 것이다.  
>if 문만 반복적으로 사용하면 true/false 상관없이 모든 if 문을 검사할 것이고  
>else if 문을 사용한다면 참 값이 나오는 즉시 검사를 멈춘다.  




```java
package ex5.array;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.PrintStream;
import java.util.Scanner;

public class Ex2_AvgProgram {

	public static void main(String[] args) throws IOException {
		// ---<< main menu 입력 >>---
		Scanner scan = new Scanner(System.in);
		int menu;
		int count = 0;
		int total = 0;


		while (true) {
			
			File srcFile = new File("res/data.txt");
			FileInputStream srcFis = new FileInputStream(srcFile);
			Scanner fscan = new Scanner(srcFis);

			System.out.println("┌─────────────────────────────────┐");
			System.out.println("│             Main Menu           │");
			System.out.println("└─────────────────────────────────┘");
			System.out.println("1. Count");
			System.out.println("2. Total");
			System.out.println("3. Avg");
			System.out.println("4. Exit");
			System.out.println();
			System.out.print("숫자를 입력하세요 : ");

			menu = scan.nextInt(); // prompt가 뜬다

			if (menu == 1) {

				// --- <<count 계산하기 >> -----------------------------------------------
				while (fscan.hasNext()) {
					fscan.next();
					count++;
				}

				System.out.println("┌─────────────────────────────────┐");
				System.out.println("│              Count              │");
				System.out.println("└─────────────────────────────────┘");
				System.out.printf("Count is %d \n", count);
				System.out.println();
				System.out.println("─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─");
				System.out.println();

			} else if (menu == 2) {

				// --- <<total 계산하기 >> -----------------------------------------------
				while (fscan.hasNext()) {
					String x_ = fscan.next();
					// fout.print(x_);

					int x = Integer.parseInt(x_);
					total += x;
				}
//				fscan.close();
//				srcFis.close();

				System.out.println("┌─────────────────────────────────┐");
				System.out.println("│              Total              │");
				System.out.println("└─────────────────────────────────┘");
				System.out.printf("Total is %d \n", total);
				System.out.println();
				System.out.println("─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─");
				System.out.println();

			} else if (menu == 3) {
				// --- <<avg 계산하기 >> -----------------------------------------------

				double avg = total / (double) count;

				File copyFile = new File("res/data-avg.txt");
				FileOutputStream copyFos = new FileOutputStream(copyFile);
				PrintStream fout = new PrintStream(copyFos);

				fout.printf("avg is %.2f\n", avg);

				fout.close();
				copyFos.close();

				System.out.println("┌─────────────────────────────────┐");
				System.out.println("│               Avg               │");
				System.out.println("└─────────────────────────────────┘");
				System.out.printf("Avg is %f \n", avg);
				System.out.println();
				System.out.println("─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─");
				System.out.println();

				// ------------------------------------------------------------------

			} else if (menu == 4) {
				break;
			}
			fscan.close();
			srcFis.close();
			
		}
		System.out.println("┌─────────────────────────────────┐");
		System.out.println("│               END               │");
		System.out.println("└─────────────────────────────────┘");
	}

}
```



