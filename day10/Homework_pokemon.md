```java
package day10.quiz;

import java.util.Scanner;

public class Pokemon {
	Scanner sc = new Scanner(System.in);
	
	String name;
	int lv, hp, pwr;
	
	
	
	void register() {
		System.out.println("==== 포켓몬 등록 ====");
		System.out.print("포켓몬 이름 : ");
		name = sc.next();
		System.out.print("포켓몬 레벨 : ");
		lv = sc.nextInt();
		hp = lv * 1000; 
		
		int a = (int)(Math.random() * 10);
		if(a >= 2) {
			pwr = lv * 2;
		}else {
			pwr = lv * 3;
		}
	}
	
	void printInfo() {
		System.out.println("==== 포켓몬 정보 ====");
		System.out.println("이름 : " + name);
		System.out.println("레벨 : " + lv);
		System.out.println("체력 : " + hp);
		System.out.println("공격력 : " + pwr);
	}
	
	void lvUp() {
		lv++;
		hp = lv * 1000; 
		
		int a = (int)(Math.random() * 10);
		if(a >= 2) {
			pwr = lv * 2;
		}else {
			pwr = lv * 3;
		}
	}
}

```
