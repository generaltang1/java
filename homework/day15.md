Tourist

```java
package com.day15.quiz;

import javax.swing.JOptionPane;


/*
* Tourist 클래스
*   필드 : name, budget(예산), destination(목적지), +VIP(자료형 Tourist) 
*   메서드 : 생성자 여러개  
*   
* Quiz01 클래스 - main()
* 	메뉴) 
* 		1. 목적지 설정
* 		2. 여행객 추가 
* 		3. 모든 여행객 정보 보기
* 		4. 전체 예산 보기
* 		5. VIP 조회 
* 		0. 종료 
* 
*  여행객은 최대 5명까지 받는다.
*  모든 여행객의 목적지는 동일하다. 
*  예산이 가장 많은 여행객이 VIP다.
*/
/*
  여행객 한명씩 추가하기
  1. 마지막 인덱스 역할을 할 변수 1개 선언
  	int lastIdx = 0;
  	
  2.여행객 추가 할 때
    arr[lastIdx++] = new Tourist();
 */
class Tourist{
	String name;
	String destination;
	int budget;
	
	static int totalBudget;

	
	Tourist(){}
	Tourist(String n, int b){
		name = n;
		budget = b;
	}
	String getData() {
		return "이름 : " + name +"  " + "예산 : " + budget;
				
	}
	int calBudget() {
	      totalBudget += this.budget;
	      return totalBudget;
	   }
	
	}
public class Quiz01 { // static 연습 
	
	

	public static void main(String[] args) {
		
		String menu = "1. 목적지 설정 \n"
				+ "2. 여행객 추가 \n"
				+ "3. 모든 여행객 보기 \n"
				+ "4. 전체 예산 보기 \n"
				+ "5. VIP 조회 \n"
				+ "6. 종료하기 ";
		Tourist tr2 = new Tourist();
		Tourist[] tr  = new Tourist[5];
		String select;
		int lastIdx = 0;
		
		 loop: while(true) {
			select = JOptionPane.showInputDialog(menu);
			switch(select){
			case "1":
			JOptionPane.showInputDialog("목적지를 입력하시오.");
			JOptionPane.showMessageDialog(null, "목적지 등록 완료");
			break; 
		
			/*
			  여행객 한명씩 추가하기
			  1. 마지막 인덱스 역할을 할 변수 1개 선언
			  	int lastIdx = 0;
			  	
			  2.여행객 추가 할 때
			    arr[lastIdx++] = new Tourist();
			 */
			case "2":
				tr[lastIdx++] = new Tourist(JOptionPane.showInputDialog((lastIdx)+ "번 여행객의 이름"),
						Integer.parseInt(JOptionPane.showInputDialog((lastIdx) + "번 여행객 예산"))); 
				break;
				
			case "3":
				/*
				String tmp = "[여행객 정보]\n";
				for(int i =0; i < lastIdx; ++i) {
					if(tr[i] == null) {
						tmp = "등록된 여행객이 없습니다.";
						break;
					}
					tmp += tr[i].getData() + "\n";
				}
				*/
				
				String tmp = "[여행객 정보]\n";
				for(Tourist t : tr) {
					if(t == null) { 
						tmp = "등록된 여행객이 없습니다.";
						break;
					}
					tmp += t.getData() + "\n";
				}
				JOptionPane.showMessageDialog(null, tmp);
				break;
		
			case "4":
				int t = tr2.calBudget();
	            JOptionPane.showMessageDialog(null, t);
	            break;
				
			case "5": 	
				JOptionPane.showMessageDialog(null, "프로그램 종료");
				break loop;
		
			default:
			JOptionPane.showMessageDialog(null, "다시 입력하세요.");
			break;
				
			}//switch
			
			
		}//while
	}//main
}
```
