로또당첨 프로그램
```java
package com.day08.quiz;

import java.util.Arrays;
import java.util.Scanner;

public class QuizExtra02 {

	public static void main(String[] args) {
	Scanner sc = new Scanner(System.in);
		//로또 생성 프로그램.
	
			int [] lotto1 = new int[6]; //사용자에게 입력받을 로또 배열 생성
			for(int i = 0; i < 6; ++i) {
				System.out.println("로또번호를 입력하세요.");
				lotto1[i] = sc.nextInt();
				if(lotto1[i]>45 || lotto1[i]<1) {
					System.out.println("다시입력하세요.");
					--i;
				}
				
			}
			
			int tmp;
			//오름차순으로 바꿔준다.
			for(int a = 0; a < lotto1.length; ++a) {
				for(int b = a+1; b < lotto1.length; ++b) {
					if(lotto1[a]>lotto1[b]) { 
						tmp = lotto1[a];
						lotto1[a] = lotto1[b];
						lotto1[b] = tmp;
					}
				}
			}
			System.out.println(Arrays.toString(lotto1));
			
			int [] lotto2 = new int[6]; //로또 당첨번호 배열 생성
			
			for(int i = 0; i < 6; ++i) {
				lotto2[i] = (int)(Math.random()*45 +1);
				for(int j = 0; j < i; ++j) { // 중복된 것 제외
					if(lotto2[i]==lotto2[j]) {
						--i;
					}
				}
			}
			// 오름차순으로 정렬
			Arrays.sort(lotto2); //퀵소트 알고리즘으로 오름차순 변경
			
			System.out.println("로또 당첨번호는 " + Arrays.toString(lotto2));
			
			//당첨갯수
			int count = 0;
			for(int i = 0; i < 6; ++i) {
				for(int j=0; j < 6 ;++j) {
					if(lotto1[i] == lotto2[j]) {
						++count;
			}
				}
			}
			System.out.println("맞은 갯수는 : " + count+ "개 입니다.");
			
	}

}
```
2차원 배열
```java

package com.day10.quiz;

import java.util.Arrays;

public class Quiz02 {

	public static void main(String[] args) {

		/*
		 문제2.
		1 ~ 16 을 4 X 4 배열에 담고 
			
		(2-1)
		1	2	3	4
		5	6	7	8
		9	10	11	12
		13	14	15	16

		(2-2) // 행의 순서대로 
		1	5	9	13
		2	6	10	14
		3	7	11	15
		4	8	12	16

		(2-3)
		if문 사용
		
		1	2	3	4 <- 직진
		8	7	6	5 <- 후진
		9	10	11	12 <- 직진
		16	15	14	13 <- 후진

		 */
		//2-1 
		
		int[][] arr1 = new int[4][4];
		int a = 0;
		for(int 행 = 0; 행 < arr1.length; ++행) {
			for(int 열 = 0; 열 < arr1[행].length; ++열) {
				++a;
				arr1[행][열] = a;
				System.out.print(arr1[행][열] + "\t");
			}
			System.out.println();
		}
	
		System.out.println("2-2번");

		//2-2
		int[][] arr2 = new int[4][4];
		int b = 0;
		for(int 열 = 0; 열 < arr1.length; ++열) {
			for(int 행 = 0; 행 < arr1[열].length; ++행) {
				++b;
				arr1[열][행] = b;
				System.out.print(arr1[행][열] + "\t");
			}
			System.out.println();
		}
	
		
		
		//2-3
		
		System.out.println("2-3번");
		int[][] arr3 = new int[4][4];
		int c  = 0;
		int 행 = 0, 열 = 0;
		
		for(행 = 0; 행 < arr3.length; ++행) {
			for(열 = 0; 열 < arr3[행].length; ++열) {
				++c;
				arr3[행][열] = c;
			} //행렬 생성
			
			//짝수번째 행 정배열 
			if(행%2==0) {
				for(열=0; 열 < arr3[행].length; ++열) {
					System.out.print(arr3[행][열] + "\t");
				}
				System.out.println();
			}
			//홀수번째 행 역순배열 
			if(행%2==1) {
				for(열=arr3[행].length-1; 열 >=0; --열) {
					System.out.print(arr3[행][열] + "\t");
				}
				System.out.println();
			}
		
		}
		
		
		
	}//main

}



```

