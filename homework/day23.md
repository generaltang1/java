Nation 클래스 추가
 		- 필드 :  국가명(nation), 수도명(capital), 인구수(population)
 		- 생성자 : 마음대로 여러개
 		- getter, setter : 없어도 됨
 		- toString() 오버 라이드
 
 ```java
 package com.day23.homework;

public class Nation {
   private String nation;
   private String capital;
   private int population;
   
   public Nation(String nation, String capital, int population) {
      super();
      this.nation = nation;
      this.capital = capital;
      this.population = population;
   }
   
   @Override
   public String toString() {
      return "Nation [nation=" + nation + ", capital=" + capital + ", population=" + population + "]";
   }

   public String getNation() {
      return nation;
   }
   public void setNation(String nation) {
      this.nation = nation;
   }
   public String getCapital() {
      return capital;
   }
   public void setCapital(String capital) {
      this.capital = capital;
   }
   public int getPopulation() {
      return population;
   }
   public void setPopulation(int population) {
      this.population = population;
   }
   
}
 ```
 
 메인 클래스 
 		메인
 		- 메뉴
 			1. 국가 추가
 			2. 모든 국가 보기
 			3. 번호로 검색
 			4. 이름으로 검색
 			0. 종료 
      
 ```java
   package com.day23.homework;

import java.util.ArrayList;
import java.util.List;

import javax.swing.JOptionPane;


public class Homework01 {
   public static void main(String[] args) {
      String menu = "1. 국가 추가 \r\n" + "2. 모든 국가 보기 \r\n" + "3. 번호로 검색\r\n" + "4. 이름으로 검색\r\n" + "0. 종료";
      String select;
      List<Nation> list = new ArrayList<>();
      loop: while (true) {
         select = JOptionPane.showInputDialog(menu);
         switch (select) {
         case "0":
            JOptionPane.showMessageDialog(null, "프로그램 종료");
            break loop;
         case "1":
            list.add(new Nation(JOptionPane.showInputDialog("국가명"), JOptionPane.showInputDialog("수도명"),
                  Integer.parseInt(JOptionPane.showInputDialog("인구수"))));
            JOptionPane.showMessageDialog(null, "등록 완료!");
            break;
         case "2":
            StringBuilder sb = new StringBuilder("--- 국가 목록 ---\n");
            for (Nation e : list) {
               sb.append(e).append("\n"); // e.toString()
            }
            JOptionPane.showMessageDialog(null, sb.toString());
            break;
         case "3":
            int idx = Integer.parseInt(JOptionPane.showInputDialog("번호(0~" + (list.size() - 1) + ")"));
            if (idx < 0 || idx > list.size()) {
               JOptionPane.showMessageDialog(null, "잘못된 번호입니다.");
            } else {
               JOptionPane.showMessageDialog(null, list.get(idx));
            }
            break;
         case "4":
            String name = JOptionPane.showInputDialog("찾으실 국가명");
            Nation resultNation = null;
            for (Nation e : list) {
               if (e.getNation().equalsIgnoreCase(name)) {
                  resultNation = e;
                  break;
               }
            }
            JOptionPane.showMessageDialog(null, resultNation == null ? "미등록 국가" : resultNation);
            break;

         default:
            JOptionPane.showMessageDialog(null, "다시 선택하세요.");
            break;
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
