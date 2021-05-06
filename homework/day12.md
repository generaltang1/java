Method 과제.


MyMethod 클래스
```java
package com.day12.homework;

public class MyMethod {
	
	/*
	함수명 : get_average()
    인자 : 국, 영, 수
    하는 일 : 세 과목의 평균 구하기
    리턴 : 평균
	 */
	
	double get_average(int kr,int en,int ma){
		return (kr+ en +ma)/3;
	}
	
	/*
	함수명 : print_stars()
    인자 : 정수
    하는 일 : 해당 정수 개수만큼 '*'을 출력
    리턴 : 없음
	 */
	void print_stars(int stars) {
		for(int a = 0; a < stars; ++a) {
		System.out.print("*");
		}
	}
	
	/*
	함수명 : greet()
    인자 : 이름, 나이
    하는 일 :
        미성년자인 경우 : XX(아)야, 안녕? 를 return
        성인인 경우 : XX님, 안녕하세요? 를 return
    리턴 : 위 둘 중 하나의 문장(String)
	 */
	
	String greet(String name, int age) {
		if(age <= 20) {
			return name + "(아)야, 안녕?";
		}
		else {
			return name + "님, 안녕하세요?";
		}
	}
	
	/*
	    함수명 : calc
    인자 : 정수 2개, 단어 1개
    하는 일 :
        인자로 들어온 단어가 +, -, *, /, %, **, // 인 경우
            해당 단어에 따른 연산 수행
        그 외
            '잘못된 기호'를 출력 후
            연산 결과는 0
    리턴 : 연산 결과
	 */
	double calc(int num1, String c, int num2) {
		double result = 0;
		switch(c){
		case "+" :
			result =  num1 + num2;
			break;
		
		case "-" : 
			result = num1 - num2;
			break;
		
		case "*" : 
			result = num1 * num2;
			break;
		
		case "/" : 
			result = (double)num1 / (double)num2;
			break;
		
	    default :
	    	result = 0;
	    	System.out.println("잘못된 연산입니다. ");
		};
		
		return result;
	}
	
}
```

homework01 main 클래스
```java
package com.day12.homework;

import java.util.Scanner;

/*
 MyMethod 클래스를 만들고 
 그 안에 다음 메서드들을 정의하세요.

Homework01 메인 클래스
 MyMethod 에 정의된 메서드를 모두 최소 1회씩 호출하세요. (자유롭게)

------------------------------------------------------
    함수명 : get_average()
    인자 : 국, 영, 수
    하는 일 : 세 과목의 평균 구하기
    리턴 : 평균
------------------------------------------------------
    함수명 : print_stars()
    인자 : 정수
    하는 일 : 해당 정수 개수만큼 '*'을 출력
    리턴 : 없음
------------------------------------------------------
    함수명 : greet()
    인자 : 이름, 나이
    하는 일 :
        미성년자인 경우 : XX(아)야, 안녕? 를 return
        성인인 경우 : XX님, 안녕하세요? 를 return
    리턴 : 위 둘 중 하나의 문장(String)
------------------------------------------------------
    함수명 : calc
    인자 : 정수 2개, 단어 1개
    하는 일 :
        인자로 들어온 단어가 +, -, *, /, %, **, // 인 경우
            해당 단어에 따른 연산 수행
        그 외
            '잘못된 기호'를 출력 후
            연산 결과는 0
    리턴 : 연산 결과
 */
public class Homework01 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		MyMethod method = new MyMethod();
		
		//1번 get_average()
		
		System.out.println("국어점수 : ");
		int kr = sc.nextInt();
		
		System.out.println("영어점수 : ");
		int en = sc.nextInt();
		
		System.out.println("수학점수 : ");
		int ma = sc.nextInt();
		

		double avg = method.get_average(kr,en,ma);
		System.out.println("평균" + avg);
		 
		//2번 print_stars
		method.print_stars(10);
		System.out.println("");
		
		//3번 greet()
		String message = method.greet("이태행", 50);
		System.out.println(message);
		
		//4번 calc
		System.out.println("정수1 : " );
		int num1 = sc.nextInt();
		System.out.println("연산기호 : " );
		String c = sc.next();
		System.out.println("정수2 : " );
		int num2 = sc.nextInt();
    
    
		double cr = method.calc(num1,c, num2);
		System.out.println(cr);

	}

}

```
