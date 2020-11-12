```java
package day14.quiz;
/*
 * Tourist 클래스
 *   필드 : name, budget(예산), destination(목적지)
 *   메서드 : 생성자 여러개 ... 
 *   		getter, setter, ...
 *   		public String toString() 
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
 *  
 */
public class Tourist {
	private String name;
	private int budget;
	private static String destination;
	
	
	public void setName(String n) {
		this.name = n;
	}
	
	public String getName() {
		return name;
	}
	
	public void setBudget(int b) {
		this.budget = b;
	}
	
	public int getBudget() {
		return budget;
	}
	
	public static void setDestination(String d) {
		Tourist.destination = d;
	}
	
	public static String getDestination() {
		return destination;
	}
	
	public Tourist() {
		
	}
		
	public Tourist(String n, int b) {
		setAddTourist(n, b);
	}
	
	public Tourist(String n, int b, String d) {
		setName(n);
		setBudget(b);
		setDestination(d);
	}
	
	public String toString() {
		return "이름 : " + name + "\n예산 : " + budget + "원\n목적지 : " + destination + "\n===============";
	}
	
	private void setAddTourist(String n, int b) {
		setName(n);
		setBudget(b);
	}
	
}
===================================================================================================================================
package day14.quiz;

import java.util.Scanner;

public class Quiz01 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		Tourist[] tourists = new Tourist[5]; 
		
		String dest;
		String name;
		int lastIdx = -1;
		int budget;
		String menu = "메뉴를 선택하세요."
						+ "\n1. 목적지설정"
						+ "\n2. 여행객 추가"
						+ "\n3. 모든 여행객 정보 보기"
						+ "\n4. 전체 예산 보기"
						+ "\n5. VIP조회"
						+ "\n0. 종료";
	
		loop : while(true) {
			System.out.println(menu);
			int select = sc.nextInt();
			switch (select) {
				case 1:
					System.out.println("<목적지를 설정>");
					dest = sc.next();
					Tourist.setDestination(dest);
					break;
				
				case 2:
					if(lastIdx + 1 == tourists.length) {
						System.out.println("여행객이 꽉 참!");
					}else {
						System.out.println("<여행객을 추가>\n이름을 입력하세요 : ");
						name = sc.next();
						System.out.println("예산을 입력하세요");
						budget = sc.nextInt();
						
						tourists[++lastIdx] = new Tourist(name, budget);
					}
					break;
				case 3:
					System.out.println("<모든 여행객 정보 보기>");
					for(int i = 0; i < lastIdx+1; i++) {
						System.out.println(tourists[i].toString());
					}
					break;
				
				case 4:
					System.out.println("<전체 예산 보기>");
					for(int i = 0; i < lastIdx+1; i++) {
						System.out.println((i+1) + "번째 여행객의 예산 : " + tourists[i].getBudget() + "원");
					}
					break;
				
				case 5:
					System.out.println("<VIP 조회>");
					int max = 0;
					for(int i = 0; i < lastIdx+1; i++) {
						if(max < tourists[i].getBudget()) {
							max = tourists[i].getBudget();
						}
					}
					for(int i = 0; i < lastIdx+1; i++) {
						if(max == tourists[i].getBudget()) {
							System.out.println("VIP : " + tourists[i].getName());
						}
					}
					break;
		
				case 0:
					System.out.println("종료");
					break loop;
		
				default:
					System.out.println("잘못 입력하셨습니다.");
					continue;
			}
		
		}
		
	}

}
```
