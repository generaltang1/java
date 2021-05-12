Student 과제

Student 클래스
```java
package com.day16.quiz;

import javax.swing.JOptionPane;

/*
 * Student 클래스 만들기 
 
필드 : 이름, 국, 영, 수, 평균, 등급(gpa), 학년(grade) --> private
메서드 : 
	1) 생성자 
		Student()
		Student(이름)
		Student(이름, 국, 영, 수)
	2) getter
	3) setter
		setName(String name) ~> 10글자 이하만 저장
		setKr(int kr), setEn(), setMa() ~> 0점 이상 100점 이하만 저장
		setAvg() ~> 국, 영, 수 필드로 평균 계산 및 avg 필드에 저장
		setGqa() ~> 평균 가지고 A, B, C, D, F 중 1개를 gpa 필드에 저장
		setGrade() ~> 1 ~ 4 학년만 저장
	4) getInfo()
		모든 정보를 1개의 String 형태로 return
=====================================================================
메인메서드는 마음대로..
*/

public class Student {
	private String name;
	private int kr, en, ma;
	private double avg;
	private String gpa;
	private int grade;
	
	//생성자 
	Student(){}
	Student(String n){
		this.name = n;
	}
	Student(String n,int g ,int k, int e, int m){
		this.name = n;
		this.kr = k;
		this.en = e;
		this.ma = m;
		this.grade = g;
		this.setAvg();
		this.setGpa();
		
	}
	
	
	//name 
	public String getName() {
		return name;
	}
	public void setName(String n) {
		if(n.length() <= 10) {
		this.name = n;
		}
		else {
			JOptionPane.showMessageDialog(null,"10자 이하의 이름을 입력해주세요.");
		}
	}
	
	//점수 
	//국 
	public int getKr() {
		return kr;
	}
	public void setKr(int k) {
		if(k >=0 && k <=100) {
		this.kr = k;
		}
	}
	
	//영 
	public int getEn() {
		return en;
	}
	public void setEn(int e) {
		if(e >=0 && e <=100) {
			this.en = e;
			}
	}
	
	//수 
	public int getMa() {
		return ma;
	}
	public void setMa(int m) {
		if(m >=0 && m <=100) {
			this.ma = m;
			}
	}
	
	//평균 
	public double getAvg() {
		return avg;
	}
	public void setAvg() {
		this.avg = (this.kr + this.en + this.ma) / 3.0;	
		}
	
	//등급 
	public String getGpa() {
		return gpa;
	}
	public void setGpa() {
		 
		switch ((int) this.avg / 10) {
		case 10:
		case 9:
			this.gpa = "A";
			break;
		case 8:
			gpa= "B";
			break;
		case 7:
			gpa = "C";
			break;
		case 6:
			gpa = "D";
			break;
		default:
			gpa = "F";
		}
	}
	
	//학년 
	public int getGrade() {
		return grade;
	}
	
	public void setGrade(int g) {
		if(g >=1 && g <= 4) {
		this.grade = g;
		}
	}
	//출력 
	String getInfo() {
		return this.name+ "/학년" + grade + "/" + this.kr + "/" + en + "/" + ma 
				+ "/평균 " + avg + "/등급 " + gpa ;
	}
	

}

```


Main 클래스
```java
package com.day16.quiz;

import javax.swing.JOptionPane;



public class Quiz01 {

	public static void main(String[] args) {
		String menu = "1. 3명 학생 정보 입력 \n" + "2. 3명 학생 정보 보기 \n" + "3. 종료 ";
		String select;
		Student[] st = new Student[3]; // {null, null, null}

		loop: while (true) {
			select = JOptionPane.showInputDialog(menu);
			switch (select) {
			case "1":
				for (int i = 0; i < st.length; ++i) {
					st[i] = new Student(JOptionPane.showInputDialog((i + 1) + "번 학생 이름"),
							Integer.parseInt(JOptionPane.showInputDialog((i + 1) + "번 학생 학년")),
							Integer.parseInt(JOptionPane.showInputDialog((i + 1) + "번 학생 국어")),
							Integer.parseInt(JOptionPane.showInputDialog((i + 1) + "번 학생 영어")),
							Integer.parseInt(JOptionPane.showInputDialog((i + 1) + "번 학생 수학")));
				}
				break;
			case "2":
				String tmp = "[학생 정보]\n";
				for(Student s : st) {
					if(s == null) { // null-comparison
						tmp = "등록된 학생이 없습니다.";
						break;
					}
					tmp += s.getInfo() + "\n";
				}
				JOptionPane.showMessageDialog(null, tmp);
				break;
			case "3":
				JOptionPane.showMessageDialog(null, "프로그램 종료");
				break loop;
			default:
				JOptionPane.showMessageDialog(null, "다시 입력하세요.");
				break;
			}
		}
	}

}

```
