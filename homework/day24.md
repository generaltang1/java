영단어장 프로그램

```java

package com.day24.quiz;
/*
 	< 영단어장 프로그램 >
 	: 영단어(String), 그의 뜻(String)  <~ 둘 중하나를 key로 설정하는데 마음대로
 	
 	<메뉴> 
 	1. 단어추가
 	2. 모든 단어 보기
 	3. 단어 검색 (영단어 검색)
 		있으면 : 그의 뜻
 		없으면 : 미등록 단어
 	4. 퀴즈
 		'뜻(한국어)' 을 문제로 내고, 사용자에게 영단어 입력 받기 (랜덤하게) 
 		정답/오답 출력
 		예) '사과'는 영어로? ~> apple ~> 정답!
 						 ~> home ~> 땡! 	
 	0. 종료
 	
 */

import java.util.Collection;
import java.util.Map;
import java.util.Map.Entry;
import java.util.Set;
import java.util.TreeMap;

import javax.swing.JOptionPane;

import com.day24.homework.Nation;

class Word{
	public Word(String en, String kr) {
		super();
		this.en = en;
		this.kr = kr;
	}
	String en;
	String kr;
	
	public String getEn() {
		return en;
	}
	public void setEn(String en) {
		this.en = en;
	}
	public String getKr() {
		return kr;
	}
	public void setKr(String kr) {
		this.kr = kr;
	}
	@Override
	public String toString() {
				return en + " : " + kr;
	}
	

}



public class Quiz01 {

	public static void main(String[] args) {
		

		Map<String, Word> Word = new TreeMap<>();
		String menu = "1. 단어 추가 \r\n" 
				+ "2. 모든 단어 "
				+ "보기 \r\n" 
				+ "3. 단어 검색(영단어 검색)\r\n" 
				+ "4. 퀴즈\r\n" 
				+ "0. 종료";
	      String select;
		loop: while(true) {
			 select = JOptionPane.showInputDialog(menu);
	         switch (select) {
	         case "0":
	        	 JOptionPane.showMessageDialog(null, "종료합니다");
	        	 break loop;
	         
	         
	         case "1":
	        	 String en = JOptionPane.showInputDialog("영어 입력");
	        	 String kr = JOptionPane.showInputDialog("뜻 입력");
	        	 
	        	 Word.put(en, new Word(en,kr));
	        	 JOptionPane.showMessageDialog(null, "등록 완료!");
	        	 break;
	        	 
	         case "2" :
	        	 JOptionPane.showMessageDialog(null, Word);
	        	 break;
	        
	         case "3" : 
	        	 String find = JOptionPane.showInputDialog("찾으실 단어를 입력하세요");
	        	 Word FindResult = null;
	        	 
	        	 Collection<Word> values = Word.values();
	        	 for(Word w : values) {
	        		 if(w.getEn().equals(find)) {
	        			 FindResult = w;
	        			 break;
	        		 }
	        	 }
	        	 JOptionPane.showMessageDialog(null, FindResult == null ? "없는 단어입니다." : FindResult);
	        	 break;
	        
	         case "4" :
	    
	        	 
			
	         }//while 
		}
	}// main

}
```
