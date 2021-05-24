Nation 클래스 추가
 		- 필드 :  국가명(nation), 수도명(capital), 인구수(population)
 		- 생성자 : 마음대로 여러개
 		- getter, setter : 없어도 됨
 		- toString() 오버 라이드
 		
 		메인
 		- 메뉴
 			1. 국가 추가
 			2. 모든 국가 보기
 			3. 번호로 검색
 			4. 이름으로 검색
 			0. 종료 
      
 ```java
      package com.day23.quiz;

import java.util.ArrayList;
import java.util.List;

import javax.swing.JOptionPane;



 
class Nation{
	String nation;
	String capital;
	int population;
	@Override
	public String toString() {
		return "국가 : " + nation + "/ 수도 : " + capital + "/ 인구 : " + population;
	}
	Nation(String nation, String capital, int population){
		this.nation = nation;
		this.capital = capital;
		this.population = population;
		
	}
	
}
public class Quiz01 {
	
	public static void main(String[] args) {
		String select;
		String message = null;
		
		List<Nation> list1 = new ArrayList<>();
		String menu = "1. 국가추가\r\n"
				+ "2. 모든 국가보기\r\n"
				+ "3. 번호로 검색\r\n"
				+ "4. 이름으로 검색\r\n"
				+ "0. 종료 ";
		
		
		menu: while(true) {
			
			
			select = JOptionPane.showInputDialog(menu);
			switch(select) {
			
			case "1" : 
				String nation = JOptionPane.showInputDialog("국가 : ");
				String capital = JOptionPane.showInputDialog("수도 : ");
				int population = Integer.parseInt(JOptionPane.showInputDialog("인구 : "));
				list1.add(new Nation(nation, capital, population));
				break;
				
			case "2" : 
				if(list1 == null) {
					message += "등록된 국가가 없습니다.";
					JOptionPane.showMessageDialog(null, message);
					break;
				}
				else {
				JOptionPane.showMessageDialog(null, list1);
				break;
				}
				
				
			case "3" :
				int num = Integer.parseInt(JOptionPane.showInputDialog("국가 번호"));
				Object o = list1.get(num);
				if(o==null) {
					message += "해당 번호의 국가가 존재하지 않습니다. ";
					JOptionPane.showMessageDialog(null, message);
					break;
				}
				else {JOptionPane.showMessageDialog(null,"국가 번호 : \t"+ num+"\t"+  o);
						break;
				}
			
			case "4" : 
				Object nn = JOptionPane.showInputDialog("검색할 국가명을 입력하세요");
				
				if(list1.contains(nn)==false) {
					System.out.println("존재하지 않은 국가명입니다.");
					break;
				}
				else {
					JOptionPane.showInputDialog(nn);
				}
				
			case"5" :
				JOptionPane.showMessageDialog(null, "프로그램 종료");
				break menu;
			
				
				
			}
		}
	}

}
```
      
      
로또 생성 프로그램

 ```java
      package com.day23.quiz;

import java.util.TreeSet;

public class Quiz02 {
	public static void main(String[] args) {
		// 로또 생성기 : 
		// 중복없이 1 ~ 45 중 6개의 숫자 뽑기
		// 오름차순 정렬 
		// 결과 출력
		TreeSet<Integer> lotto = new TreeSet<Integer>();
		for(int i = 0; lotto.size() < 6; ++i) {
			lotto.add((int)(Math.random() * 45) + 1);
			
		}
		System.out.println(lotto);
	}
}

      ```
