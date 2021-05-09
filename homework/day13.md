1.사각형 과제

Rectangle Class
```java
package com.day13.quiz;

public class Rectangle {

	int base;
	int height;
	
	void setData(int b,int h) {
		base = b;
		height = h;
		System.out.println("길이 : " + b);
		System.out.println("높이 : " + h);
		
	}
	
	int getArea() {
		return base * height;
	}
	int getCircum() {
		return (base+height)*2;
	}
}

```

Main Class
```java
package com.day13.quiz;

import javax.swing.JOptionPane;

public class Quiz01 {

	public static void main(String[] args) {
		//Rectangle
		Rectangle r1 = new Rectangle();
		
		String base = JOptionPane.showInputDialog("밑변 : ");
		String height = JOptionPane.showInputDialog("높이 : ");

		
		r1.setData(Integer.parseInt(base), Integer.parseInt(height));
		
		
		
		
		System.out.println("넓이 : " + r1.getArea());
		System.out.println("둘레 : " + r1.getCircum());
		
	}

}


```

2. MyMath 과제

MyMath Class

```java
package com.day13.quiz;

public class MyMath {
	
	
	int getTotal(int n1) {
		int sum = 0;
		for(int i=1; i <= n1; ++i) {
			sum = sum + i;
		}
		return sum;
	}
	String getGugudan(int n2) {
			String dan = null;
		for (int i = 1; i <= 9; i++) {
	           dan = dan + (n2 + "X" + i + "=" + (n2*i)) +'\n';
	        }
	        return dan;
	
	}
	
	
}

```

Main Class
```java
package com.day13.quiz;

import javax.swing.JOptionPane;

public class Quiz02 {

	public static void main(String[] args) {
		MyMath m1 = new MyMath();
		
		String menu = "1. 총합보기  \n"
				+ "2. 구구단 보기 \n"
				+ "3. 종료하기";
		//숫자 입력받기
		String a = JOptionPane.showInputDialog("숫자입력");
		
		while(true){
			String select = JOptionPane.showInputDialog(menu);
			
			//총합보기
			if("1".equals(select)) {
				int total = m1.getTotal(Integer.parseInt(a));
				System.out.println(total);
				
			}
			//구구단
			else if("2".equals(select)) {
				String Gugu = m1.getGugudan(Integer.parseInt(a));
				System.out.println(Gugu);
			}
			//종료하기
			else if("3".equals(select)) {
				JOptionPane.showMessageDialog(null, "프로그램을 종료합니다.");
				break;
			}
		}
				
	}

}
```
