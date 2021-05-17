< 익명 클래스 >

1. 익명 클래스란?
- 클래스의 선언과 객체 생성을 동시에 하기 때문에 단 한 번만 사용될 수 있고, 오직 하나의 객체만을 생성할 수 있는 일회용 클래스.
- 특징 : 
       1) 이름이 없기 때문에 생성자를 가질 수 없다.
       2) 단 하나의 클래스를 상속받거나 단 하나의 인터페이스만을 구현할 수 있다.
       3) 하나의 클래스로 상속받는 동시에 인터페이스를 구현하거나 둘 이상의 인터페이스를 구현할 수 없다.

2. 익명클래스를 이용하여 Transportation의 taxi, train, bus 등을 구현하기.

Transportation 인터페이스

```java
package com.day20.homework;

interface Transportation {
	int DEFAULT_ADULT_CHARGE = 1250;
	int DEFAULT_KID_CHARGE = 700;
	int getCharge(int age, int km);
}

```

Main 클래스

```java
package com.day20.homework;

import java.util.Scanner;

public class Homework01 {
	public static void main(String[] args) {
		
		Transportation Bus = new Transportation() {
			@Override
			public int getCharge(int age, int km) {
				int price = age >= 20 ? DEFAULT_ADULT_CHARGE : DEFAULT_KID_CHARGE;
				price += km / 10 * 100;
				if(age < 20) {
					price *= 0.8;
				}
				return price;
			}
		}; 
		
		Transportation Taxi = new Transportation() {
			@Override
			public int getCharge(int age, int km) {
				return 4000 + (km-10) * 100;
			}
		};
		
		Transportation Subway = new Transportation() {
			@Override
			public int getCharge(int age, int km) {
				int price = age >= 20 ? DEFAULT_ADULT_CHARGE : DEFAULT_KID_CHARGE;
				price += (km / 10) * (age >= 20 ? 100 : 50);
				return price;
			}
		};
		
		Transportation Train = new Transportation() {

			@Override
			public int getCharge(int age, int km) {
				int price = 15000;
				price += (km / 30) * 1000;
				if (age < 20) {
					price *= 0.5;
				}
				return price;
			}
			
		};
		
		Scanner sc = new Scanner(System.in);
		int km, age, tr;
		Transportation transportation = null;
		
		System.out.print("나이 : ");
		age = sc.nextInt();
		
		System.out.print("거리(km) : ");
		km = sc.nextInt();
		
		System.out.println("0. 버스\n1. 택시 \n2. 지하철 \n3. 기차");
		tr = sc.nextInt();
		
		switch (tr) {
		case 0:
			transportation = Bus;
			break;
		case 1:
			transportation = Taxi;
			break;
		case 2:
			transportation = Subway;
			break;
		case 3:
			transportation = Train;
			break;
		default:
			break;
		}
		
		if(transportation != null) {
			int price = transportation.getCharge(age, km);
			System.out.println("요금은 " + price + "원입니다.");
		}
		else {
			System.out.println("잘못된 교통수단입니다.");
		}
	}//main
}

```
