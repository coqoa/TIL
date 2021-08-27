# 자바스윙 사용해보기

```java

package ex8.game.basic1;

import java.awt.Canvas;
import java.awt.Event;
import java.awt.Graphics;
import java.awt.Image;
import java.awt.Toolkit;

public class GameCanvas extends Canvas{
	
	Image img;
	int dx = 0;
	int dy = 0;
	
	public GameCanvas() {
		Toolkit tk = Toolkit.getDefaultToolkit();
		img = tk.getImage("res/images/Adams_The_Tetons_and_the_Snake_River.jpeg");
	}
	
	@Override
	public boolean mouseDown(Event evt, int x, int y) {//mouseDown1
		System.out.println("클릭");
		if(x >= dx && x <= dx+200 && y >= dy && y <= dy+200) { // 조건에 맞으면  dx와 dy를 200 추가해준다 
			dy+=200;
			dx+=200;
			repaint(); //화면을 다시그려서 변화를 표시해줘야함
		}
		return true;
	}
	
	@Override
	public void paint(Graphics g) {
		
//		g.drawLine(10, 10, 100, 100);
		
//		g.drawOval(100, 100, 300, 300);

//		g.fillOval(100, 100, 50, 50);

//		g.drawImage(img, 0, 0, this);
		//	Toolkit클래스를 통해 이미지를 로드 할 수 있다
		//	GameCanvas()함수 생성	하고 Toolkit을 넣어주면 한번 로드하고 참조해서 사용한다.
		
//		g.drawImage(img, 0, 0, 300, 300, this); // 너비, 높이로 크기를 설정할 수 있음
		
//		g.drawImage(img, 0, 0, 200, 200, 0, 0, 200, 200, this); //활용도가 높음 (전체가 아닌 일부 이미지만 출력하는 방법)
		// 앞의 4숫자는 출력할 부분 기준점, 뒤의 4숫자는 잘라서 쓸 소스이미지의 좌표

//		 g.drawImage(img, 0, 0, 200, 200, 0, 0, 200, 200, this); // 소스파일의 0,0,200,200 크기만큼의 이미지를 윈도우에  0,0,200,200의 크기에 표시한다
//		 g.drawImage(img, 200, 200, 400, 400, 200, 0, 400, 200, this);// 소스파일 200,0,400,200의 이미지를 윈도우200,200,400,400에 표시한다
		
//		g.drawImage(img, 0, 0, 200, 200, 0, 0, 200*2, 200*2, this); // 1:1비율이라 200x200의 크기에 400x400의 이미지가 출력됨(이미지축소)
		
		//클릭시 이동하도록 mouseDown()함수 사용
		
//		g.drawImage(img, dx, dy, dx+200, dy+200, 
//				200, 200, 400, 400, this);// 이미지의 위치를 변수로 설정해놓고 mouseDown함수를 통해 조건식이 맞으면 이동시킨다
		
        
        
// *문제* 소스파일의 이미지를 200x200사이즈로 나누고 (1,2,3,4) (3142)형식으로 그려라
		g.drawImage(img, 200, 0, 400, 200, 
							0, 0, 200, 200, this);//1
		g.drawImage(img, 200, 200, 400, 400, 
							200, 0, 400, 200, this);//2
		g.drawImage(img, 0, 0, 200, 200, 
							0, 200, 200, 400, this);//3
		g.drawImage(img, 0, 200, 200, 400, 
							200, 200, 400, 400, this);// 4
	}
}


```
