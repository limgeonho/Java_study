```java
package day17.quiz;

import java.util.Scanner;
/*
 *  Transportation 인터페이스 (교통수단 인터페이스)
	상수 : ??? 
	메서드 : 
		int getCharge(int age, int km)

 자식 클래스1 : Bus 
	필드 : X
	메서드 : 
		int getCharge(int age, int km) 오버라이드
			기본요금 : 1000 
			10km 당 100원 추가
			미성년자면 20% 할인
			책정된 요금을 리턴

 자식 클래스2 : Taxi 
	필드 : X
	메서드 : 
		int getCharge(int age, int km) 오버라이드
			기본요금 : 4000 
			10km 까지는 기본요금
			10km 초과되면 1km 당 100원 추가
			책정된 요금을 리턴

 자식 클래스3 : Subway
	필드 : X
	메서드 : 
		int getCharge(int age, int km) 오버라이드
			성인 기본 요금 : 1250 
			미성년자 기본 요금 : 720
			10km 당 성인은 100원 추가, 미성년자는 50원 추가
			책정된 요금을 리턴


 자식 클래스4 : Train
	필드 : X
	메서드 : 
		int getCharge(int age, int km) 오버라이드
			기본요금 : 15000 원
			30km 단위로 1000원씩 추가
			미성년자는 50% 할인
			책정된 요금을 리턴

Quiz 클래스 : 메인
	원하는 교통수단(버스, 전철, 택시, 기차)과 나이, 거리(km)를 입력 받고
	요금을 출력하세요.
 */
class Bus implements Transportation {

	@Override
	public int getCharge(int age, int km) {
		int charge = 1000;
		if (age > 19) {
			charge += (km * 10);
		} else {
			charge += ((km * 10) * 80) / 100;
		}
		return charge;
	}

}

class Taxi implements Transportation {

	@Override
	public int getCharge(int age, int km) {
		int charge = 4000;
		if (km > 10) {
			charge += (km * 100);
		}
		return charge;

	}

}

class Subway implements Transportation {

	@Override
	public int getCharge(int age, int km) {
		int charge = 0;
		if (age > 19) {
			charge = 1250 + (km * 10);
		} else {
			charge = 720 + (km * 5);
		}
		return charge;
	}

}

class Train implements Transportation {

	@Override
	public int getCharge(int age, int km) {
		int charge = 15000;
		if (age > 19) {
			charge += km * 330;
		} else {
			charge = (charge + (km * 330)) / 2; 
		}
		
		return charge;
	}

}

public class Quiz01 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int age;
		int km;
		System.out.println("====교통수단====" + "\n1.버스" + "\n2.택시" + "\n3.전철" + "\n4.기차");

		System.out.println("원하는 교통수단을 입력하세요.");
		String transportation = sc.next();

		System.out.println("나이를 입력하세요 : ");
		age = sc.nextInt();
		System.out.println("거리를 입력하세요 : ");
		km = sc.nextInt();

		Transportation t = null;

		switch (transportation) {
			case "버스":
				t = new Bus();
				break;
				
			case "택시":
				t = new Taxi();
				break;
				
			case "전철":
				t = new Subway();
				break;
				
			case "기차":
				t = new Train();
				break;
	
			default:
				System.out.println("잘못 입력하였습니다.");
				break;
	
			}
		if(t != null)
			System.out.println("요금은 : " + t.getCharge(age, km) + "원");

	}

}

```
