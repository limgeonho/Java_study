```java
package day12.quiz;
/*
 * 클래스 : Rectangle
 *  - 필드(멤버변수) : base, height
 *  - 메소드 
 *    1) setData() : 두 정수를 인자값으로 받아, 객체의 base, height에 각각 저장
 *    2) getArea() : 넓이를 리턴
 *    3) getCircum() : 둘레를 리턴
 * 
 * 메인 클래스 : Quiz01
 *  - Rectangle 객체 1개 생성 
 *  - JOptionPane을 사용하여 밑변, 높이를 입력 받고, 
 *    Rectangle 객체에 저장 (setData() 사용)
 *  - 이 사각형 객체의 넓이와 둘레를 메소드를 사용하여 출력 (getArea(), getCircum())
 */

import javax.swing.JOptionPane;

class Rectangle{
	int base;
	int height;
	
	void setData(int b, int h) {
		base = b;
		height = h;
	}
	
	int getArea(int b, int h) {
		return b * h;
	}
	
	int getCircum(int b, int h) {
		return (b + h) * 2;
	}
	
}

public class Quiz01 {
	public static void main(String[] args) {
		
		Rectangle rec = new Rectangle();
		
		int b = Integer.parseInt(JOptionPane.showInputDialog("밑변"));
		int h = Integer.parseInt(JOptionPane.showInputDialog("높이"));
		
		rec.setData(b, h);
		
		System.out.println("넓이 : " + rec.getArea(b, h));
		System.out.println("둘레 : " + rec.getCircum(b, h));
		
	}
}
===============================================================================================================================
package day12.quiz;
/*
 * 클래스 : Student
 *  필드 : 이름, 국, 영, 수, 평균, 등급
 *  메소드 : 
 *    0) 생성자 : 
 *       Student(String name) : name 만 저장 
 *       Student(int k, int e, int m) : name 은 "없음", 국영수는 k, e, m 값을 저장. 평균, 등급도 계산되어 저장
 *       Student(String name, int k, int e, int m) : 이름,국영수는 name, k, e, m 값을 저장. 평균, 등급도 계산되어 저장
 *    
 *    1) setData() : 이름, 국, 영, 수를 인자값으로 받아, 해당 필드에 모두 저장
 *    2) setMean() : 객체가 가지고 있는 국, 영, 수를 가지고 평균을 계산하여 평균 필드에 저장
 *    3) setGrade() : 객체가 가지고 있는 평균을 가지고 등급을 저장 
 *       90이상 : A
 *       80이상 ~ 90미만 : B
 *       70이상 ~ 80미만 : C
 *       60이상 ~ 70미만 : D
 *       60미만 : F
 * 	  4) printData() : 객체의 모든 정보(이름, 국, 영, 수, 평균, 등급)를 sysout
 * 
 *  메인 클래스 : Quiz03
 *   4명의 학생 객체를 배열로 선언하고 
 *   반복문을 사용하여 학생들의 이름, 국, 영, 수를 입력 받음
 *   입력이 끝나면 모든 학생의 정보를 출력
 */

import java.util.Scanner;

class Student{
	String name;
	String rank;
	int kor, eng, math;
	double avg;
	
	Student(String n){
		name = n;
	}
	Student(int k, int e, int m){
		kor = k;
		eng = e;
		math = m;
		avg = (kor + eng + math) / 3.0;
		if(avg >= 90) {
			rank = "A";
		}else if(avg >= 80){
			rank = "B";
		}else if(avg >= 70) {
			rank = "C";
		}else if(avg >= 60) {
			rank = "D";
		}else {
			rank = "F";
		}
		return;
	}
	Student(String n, int k, int e, int m){
		name = n;
		kor = k;
		eng = e;
		math = m;
		avg = (kor + eng + math) / 3.0;
		if(avg >= 90) {
			rank = "A";
		}else if(avg >= 80){
			rank = "B";
		}else if(avg >= 70) {
			rank = "C";
		}else if(avg >= 60) {
			rank = "D";
		}else {
			rank = "F";
		}
		return;
	}
	
	
	void setData(String n, int k, int e, int m) {
		name = n;
		kor = k;
		eng = e;
		math = m;
		return;
	}
	
	double setMean() {
		avg = (kor + eng + math) / 3.0;
		return avg;
	}
	
	String setGrade(double avg) {
		if(avg >= 90) {
			rank = "A";
		}else if(avg >= 80){
			rank = "B";
		}else if(avg >= 70) {
			rank = "C";
		}else if(avg >= 60) {
			rank = "D";
		}else {
			rank = "F";
		}
		return rank;
	}
	
	String printDate() {
		return "이름 : " + name + "\n국어 : " + kor + ", 영어  : " + eng + ", 수학 : " + math + "\n평균 : " + avg + 
				"\n등급 : " + rank;
		
	}
	
		
}
public class Quiz02 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
//		Student[] st = {new Student(), new Student(), new Student(), new Student() };
//			
//		for(int i = 0; i < st.length; i++) {
//			System.out.println("국영수 점수");
//			String n = sc.next();
//			int k = sc.nextInt();
//			int e = sc.nextInt();
//			int m = sc.nextInt();
//			st[i].setData(n, k, e, m);
//			st[i].setMean();
//			st[i].setGrade(st[i].setMean());
//		}
//		
//		for(int i =0; i < st.length; i++) {
//			System.out.println("====학생정보====");
//			System.out.println(st[i].printDate());
//		}
		
//		Student st1 = new Student(10,20,30);
//		System.out.println(st1.printDate());
		
		Student[] st = {new Student("피카츄",10, 20, 30),
						new Student("파이리",100, 90, 80),
						new Student("꼬부기",50, 60, 70),
						new Student("라이츄",55, 90, 70)};
		
		for(int i = 0; i < st.length; i++) {
			System.out.println(st[i].printDate());
		}
		
	}
}
===============================================================================================================================
package day12.quiz;
/*
 * Pokemon 클래스 
	멤버변수 : name, level, hp(체력), ap(공격력)
	멤버메서드 : 
		0. Pokemon(name)
			name을 등록 
		   Pokemon(name, level)
			name, level 등록
			체력은 레벨의 1000배
			공격력은 레벨의 1.5배 (20% 확률로 2배)
		1. setInfo()
			인자값 : 이름, 레벨
			하는 일 : 인자로 들어온 값들을 멤버변수 name, level 에 모두 저장 
				체력은 레벨의 1000배
				공격력은 레벨의 1.5배 (20% 확률로 2배)
			리턴값 : X

		2. getInfo()
			인자값 : X
			하는 일 : "XXX / Lv. @@ / HP. ####" 형태로 name, level, hp 의 값들을 하나의 문자열로 표현
			리턴값 : "XXX / Lv. @@ / HP. ####" 형태의 문자열

		3. levelUp()
			인자값 : X
			하는 일 : level을 1증가
			리턴값 : 증가된 level

		4. isAlive()
			인자값 : X
			하는 일 : 객체의 생사여부 확인( 체력이 0 이하면 죽음 )
			리턴값 : 살아있으면 true, 아니면 false

		5. attack()
			인자값 : 적 포켓몬 객체 (Pokemon형)
			하는 일 : 상대 포켓몬의 체력을 이 객체의 공격력만큼 감소
				10% 확률로 치명타 (공격력 X 1.5배)
			리턴값 : 없음
 */
class Pokemon{
	String name;
	int level, hp;
	double ap;
	
	Pokemon(String n){
		this.name = n;
	}
	
	Pokemon(String n, int lv){
		this.name = n;
		this.level = lv;
		this.hp = lv * 1000;
		this.ap = (int)(Math.random() * 10) + 1 >= 3 ? (lv * 1.5) : (lv * 2);
	}
	
	void setInfo(String n, int lv) {
		this.name = n;
		this.level = lv;
		this.hp = lv * 1000;
		this.ap = (int)(Math.random() * 10) + 1 >= 3 ? (lv * 1.5) : (lv * 2);
	}
	
	String getInfo() {
		return name + " / Lv. " + level + " / HP. " + hp;
	}

	int levelUp() {
		return this.level++;
	}
	
	boolean isAlive() {
		boolean alive = true;
			if(hp <= 0) {
				alive = false;
			}else{
				alive = true;
			}
		return alive;
	}
	
	void attack(Pokemon enemyP) {
		enemyP.hp -= ((int)(Math.random() * 10) + 1 == 1) ? this.ap * 1.5 : this.ap;
		return;
	}
	
}

public class Quiz03 {
	public static void main(String[] args) {
		Pokemon p1 = new Pokemon("피카츄", 10);	// 생성자를 통해 객체 생성
		Pokemon p2 = new Pokemon("파이리", 20);	// 생성자를 통해 객체 생성
		
		p1.levelUp();	// p1 레벨업
		
		System.out.println(p1.getInfo());	// 객체에 담긴 데이터 출력
		
		System.out.println(p2.getInfo());	// 객체에 담긴 데이터 출력
		
		p2.attack(p1);	// p2가 p1을 공격하는 메서드 실행
		System.out.println(p1.getInfo());	// 공격을 받은 p1객체의 정보를 출력
		
		System.out.println(p1.isAlive());	// isAlive 메서드 실행
	
	}
}
```
