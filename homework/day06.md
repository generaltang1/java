# Homework00

```java
package com.day06.homework;

import javax.swing.JOptionPane;

/*
Homework00
두 정수를 입력 받고 큰 수를 출력. 같으면 "같습니다"를 출력
*/
public class Homework00 {
	public static void main(String[] args) {
		String tmp;
		int n1, n2;
		
		tmp = JOptionPane.showInputDialog("정수1");
		n1 = Integer.parseInt(tmp);
		
		tmp = JOptionPane.showInputDialog("정수2");
		n2 = Integer.parseInt(tmp);
		
		if(n1 > n2) {
			JOptionPane.showMessageDialog(null, "n1(" + n1+ ")이 더 크다.");
		} else if(n1 < n2) {
			JOptionPane.showMessageDialog(null, "n2(" + n2+ ")가 더 크다.");
		} else {
			JOptionPane.showMessageDialog(null, "두 수는 같다.");
		}
	}
}
```
#Homework01
```java
package com.day06.homework;

import javax.swing.JOptionPane;

/*
Homework01
		
 정수 1개를 입력 받고,
 입력 받은 정수가 5의 배수인지 판별하세요.
		
 */
public class Homework01 {
	public static void main(String[] args) {
		String tmp;
		int num;
		
		tmp = JOptionPane.showInputDialog("정수");
		num = Integer.parseInt(tmp);
		
		if(num % 5 == 0) {
			JOptionPane.showMessageDialog(null, "5의 배수");
		} else {
			JOptionPane.showMessageDialog(null, "5의 배수가 아닙니다.");
		}
	}
}
```


