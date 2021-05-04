#포켓몬 과제

1.포켓몬 클래스
```java
package com.day11.homework;

public class Pokemon {
	
	String name;
	int level;
	int hp;
	
	void printInfo(){
		
		System.out.println("포켓몬 이름 : " + name);
		System.out.println("포켓몬 레벨 : " + level);
		System.out.println("포켓몬 hp : " + hp);
		System.out.println();
	}
}


```

2.메인 클래스
```java
package com.day11.homework;

public class Homework01 {

	public static void main(String[] args) {

		/*
		Pokemon 4마리 객체 생성
		1. name 저장
			"피카츄", "라이츄", "파이리", "꼬부기", "푸린", "치코리타"
			 중 1개를 랜덤하게 선택해서 저장 (중복 이름 가능)
			 
		2. level 저장
			1 ~ 100 중 랜덤하게 저장
			
		3. hp 저장
			70% 확률로 level의 100배, 30% 확률로 level의 150배 저장
			
		4. 저장된 4개의 포켓몬 인스턴스의 모든 정보 출력
		
	 */
		Pokemon p1, p2, p3, p4;
		
		p1 = new Pokemon();
		p2 = new Pokemon();
		p3 = new Pokemon();
		p4 = new Pokemon();
		
		//포켓몬 이름 배열생성
		String [] arr1 = {"피카츄", "라이츄", "파이리", "꼬부기", "푸린", "치코리타"};
		
		//1번 포켓몬
		p1.name = arr1[(int)(Math.random()*6)];	//이름 랜덤생성
		p1.level = (int)(Math.random()*100+1); //level 랜덤 생성
		p1.hp = Math.random()<= 0.7 ? p1.level*100 : p1.level*150;
		
		
		//2번 포켓몬
		p2.name = arr1[(int)(Math.random()*6)];	
		p2.level = (int)(Math.random()*100+1); 
		p2.hp = Math.random()<= 0.7 ? p2.level*100 : p2.level*150;
		
		//3번
		p3.name = arr1[(int)(Math.random()*6)];	
		p3.level = (int)(Math.random()*100+1); 
		p3.hp = Math.random()<= 0.7 ? p3.level*100 : p3.level*150;
		
		//4번
		p4.name = arr1[(int)(Math.random()*6)];	
		p4.level = (int)(Math.random()*100+1); 
		p4.hp = Math.random()<= 0.7 ? p4.level*100 : p4.level*150;
		
		p1.printInfo();
		p2.printInfo();
		p3.printInfo();
		p4.printInfo();

	}

}

```
