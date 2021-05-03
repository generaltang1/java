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
