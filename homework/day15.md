Tourist 클래스

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
public class Tourist {
	String name;
	int budget;
	static String destination;
	static Tourist vip;
	
	// 기본생성자 (매개변수가 없는 생성자)
	Tourist(){}
	Tourist(String name, int budget){
		this.name = name;
		this.budget = budget;
		if(vip == null || this.budget > vip.budget ) {
			vip = this;
		}
	}
	
	String getInfo() {
		return name + "/" + budget + "원";
	}
}
```
Main 클래스

```java
import javax.swing.JOptionPane;

public class Homework01 {
	
	static final int MAX = 5;
	
	public static void main(String[] args) {
		String menu = "1. 목적지 설정\r\n"
				+ "2. 여행객 추가 \r\n"
				+ "3. 모든 여행객 정보 보기\r\n"
				+ "4. 전체 예산 보기\r\n"
				+ "5. VIP 조회 \r\n"
				+ "0. 종료 ";
		String select;
		String message;
		String name;
		int budget;
		Tourist[] array = null;
		int lastIdx = -1;
		int sum = 0;
		
		menu: while(true) {
			select = JOptionPane.showInputDialog(menu);
			switch(select) {
			case "0":
				JOptionPane.showMessageDialog(null, "프로그램 종료");
				break menu;
			case "1":
				Tourist.destination = 
					JOptionPane.showInputDialog("목적지 입력");
				break;
			case "2":
				name = JOptionPane.showInputDialog("이름"); 
				budget = Integer.parseInt(JOptionPane.showInputDialog("예산"));
				
				if(array == null) {
					array = new Tourist[MAX]; 
				}
				if(lastIdx + 1 == MAX) {
					JOptionPane.showMessageDialog(null, "수용 인원 초과");
					break;
				}
				array[++lastIdx] = new Tourist(name, budget);
				break;
			case "3":
				message = "--- 여행객 현황 ---\n"
						+ "목적지 : " + Tourist.destination + "\n";
				if(array == null) {
					message += "등록된 여행객이 없습니다.";
				}
				else {
					// array = {0x10, 0x20 , 0x30 , null , null}
					
					for(Tourist t : array) {
						if(t == null) {
							break;
						}
						message += t.getInfo() + "\n"; 
					}
				}
				JOptionPane.showMessageDialog(null, message);
				break;
			case "4":
				for(Tourist t : array) {
					if(t == null) {
						break;
					}
					sum += t.budget;
				}
				JOptionPane.showMessageDialog(null, "총 " + sum + "원");
				break;
			case "5":
				if(array == null) {
					message = "등록된 여행객이 없습니다.";
				}
				else {
					///////////////////////////
					/// 방법 1 (vip 변수를 static으로 뺌)	
					message = "VIP : " + Tourist.vip.getInfo();
					///////////////////////////
					/// 방법 2
//					Tourist vip = array[0];
//					for(Tourist t : array) {
//						if(vip.budget < t.budget) {
//							vip = t;
//						}
//					}
//					message = "VIP : " + vip.getInfo();
					///////////////////////////
					/// 방법 3
//					int vipIdx = 0;
//					for(int i = 0; i < vipIdx; ++i) {
//						if(array[vipIdx].budget < array[i].budget) {
//							vipIdx = i;
//						}
//					}
//					message = "VIP : " + array[vipIdx].getInfo();
				}
				JOptionPane.showMessageDialog(null, message);
				break;
			default:
				JOptionPane.showMessageDialog(null, "다시 입력하세요.");
			}
		}
	}
}
```
