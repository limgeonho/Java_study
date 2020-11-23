```java
package day21.quiz;

import java.text.DecimalFormat;
import java.util.ArrayList;
import java.util.Scanner;

class Nation{
	private String name; 
	private String capital;
	private long population;

	
	public String getName() {
		return name;
	}
	
	public void setName(String name) {
		this.name = name;
	}
	
	public String getCapital() {
		return capital;
	}
	
	public void setCapital(String capital) {
		this.capital = capital;
	}
	
	public long getPopulation() {
		
		return population;
	}
	
	public void setPopulation(long population) {
		this.population = population;
	}
	
	public Nation() {
	}
	
	public Nation(String name, String capital) {
		super();
		setName(name);
		setCapital(capital);
	}

	public Nation(String name, String capital, long population) {
		super();
		setName(name);
		setCapital(capital);
		setPopulation(population);
	}
	
	public String toString() {
		return "국가명 : " + getName() + ", 수도명 : " + getCapital() + ", 인구수 : " + getPopulationdf() + "명";
	}
	
	public String getPopulationdf() {
		DecimalFormat df = new DecimalFormat("#,###.##");
		String fPopulation = df.format(getPopulation());
		return fPopulation;
	}

}

public class Quiz01 {
	/*
	 * < 국가 관리 프로그램 >
		0. Nation 클래스 
			필드 : 국가명(nation)  수도명(capital)  인구수(population) ==> 모두 private 
			메서드 : 	
				Nation() 
				Nation(국가, 수도)
				Nation(국가, 수도, 인구수)
				getter, setter 
				toString() 오버라이드 
		
		1. ArrayList 객체 생성 (Nation 객체들을 저장할 창고 객체) 
		
			
		2. 메뉴 띄우기
			1) 국가 추가   ==> 국가명, 수도명, 인구수 입력 받아 Nation 객체 생성 후 ArrayList에 add()
			2) 모든 국가 보기	==> 현재 등록된 국가들을 모두 출력 (for문과 Nation.toString() 활용)
			3) 국가 검색 	==> 국가명을 입력 받고, 해당 국가가 있으면 수도, 인구수 출력
					    없으면 "미등록 국가"
				            인구수는 ',' 추가 ( 예) 100,000,000 명 ) 
			0) 종료 
		
	 */
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		String name, capital;
		long population;
		String checkName;
		Nation nations = new Nation();
		ArrayList list = new ArrayList();
	
		loop: while(true) {
			System.out.println("메뉴를 선택하세요"
								+ "\n1. 국가 추가"
								+ "\n2. 모든 국가 보기"
								+ "\n3. 국가 검색"
								+ "\n0. 종료");

		int select = sc.nextInt();
		switch (select) {
				case 1:
					System.out.println("국가명을 입력하세요.");
					name = sc.next();
					System.out.println("수도명을 입력하세요.");
					capital = sc.next();
					System.out.println("인구수를 입력하세요.");
					population = sc.nextLong();
					
					nations = new Nation(name, capital, population);	
					
					list.add(nations);
					
					break;
				
				case 2:
					System.out.println("====입력된 모든 국가====");
					for(Object s : list) {
						System.out.println(s);
					}
					break;
				
				case 3:
					System.out.println("국가를 입력하세요.");
					checkName = sc.next();
					
					for(int i = 0; i < list.size(); i++) {
						Nation n = (Nation) list.get(i);
						if(n.getName().equals(checkName)){
							System.out.println(n.getName() + "의 수도명 : " + n.getCapital() + " , 인구수 : " + n.getPopulationdf());
							break;
						}else {
								System.out.println("미등록 국가입니다.");
								break;
							}
						}
					break;
				
				case 0:
					System.out.println("종료하였습니다.");
					break loop;
				 
				default:
					System.out.println("잘못 입력하였습니다.");
					break;
				}
		}	
		
	}

}
```
