```java
package day13.quiz;

public class Student {
	private String name;
	private int kr, en, ma;
	private double avg;
	private String grade = "F";

	// 생성자
	public void setName(String name) {
		this.name = name;
	}
	
	public String getName() {
		return name;
	}
	
	public void setKor(int kr) {
		this.kr = kr;
		setMean();
		}
	
	public int getKor() {
		return kr;
	}
	
	public void setEng(int en) {
		this.en = en;
		setMean();
	}
	
	public int getEng() {
		return en;
	}
	
	public void setMath(int ma) {
		this.ma = ma;
		setMean();
	}
	
	public int getMath() {
		return ma;
	}
	
	public void setAvg(double avg) {
		this.avg = avg;
	}
	
	public double getAvg() {
		return avg;
	}
	
	public void setGrade(String grade) {
		this.grade = grade;
	}
	
	public String getGrade() {
		return grade;
	}
	
	
	
	public Student(String name) {
		this.name = name;
	}

	public Student(int k, int e, int m) {
		this(null, k, e, m);
	}
	
	public Student(String name, int k, int e, int m) {
		setData(name, k, e, m);
	}
	
	

	public void setData(String name, int k, int e, int m) {
		setName(name);
		setKor(k);
		setEng(e);
		setMath(m);
		setMean();
	}

	private void setMean() {
		avg = (kr + en + ma) / 3.;
		setGrade();
	}

	private void setGrade() {
		switch ((int)(avg/10)) {
		case 10:
		case 9:
			grade = "A"; 
			return;
		case 8:
			grade = "B";
			return;
		case 7:
			grade = "C";
			return;
		case 6:
			grade = "D";
			return;
		default:
			grade = "F";
		}
	}

	public String getData() {
		return "이름 : " + name + "\n"
				+ "국/영/수 : " + kr + "/" + en + "/" + ma + "\n"
				+ "평균 : " + avg + "\n"
				+ "등급 : " + grade;
	}
	public void printData() {
		System.out.println(getData());
	}
}

package day13.quiz;

import java.util.Scanner;

public class StudentMain {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		Student[] students = new Student[4]; // { null, null, null, null }
		
		String name;
		int kr, en, ma;
		
		for(int i = 0; i < students.length; ++i) {
			System.out.println((i+1) + "번 학생 이름 : ");
			name = sc.next();
			
			System.out.println("국, 영, 수 : ");
			kr = sc.nextInt();
			en = sc.nextInt();
			ma = sc.nextInt();
			
			students[i] = new Student(name, kr, en, ma);
					
			students[i].setName(name);
			students[i].setKor(kr);
			students[i].setEng(en);
			students[i].setMath(ma);
		}
		
		for(Student s : students) {
			s.printData();
		}
		
	}
}
=================================================================================================================================
package day13.quiz;

public class Pokemon {
	private String name;
	private int level;
	private int hp;
	private int ap;
	
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getLevel() {
		return level;
	}
	public void setLevel(int level) {
		this.level = level;
	}
	public int getHp() {
		return hp;
	}
	public void setHp(int hp) {
		this.hp = hp;
		levelUp();
	}	// hp는 어짜피 입력받는 레벨에 따라 정해지는 것인데 굳이 필요한가...?
	public int getAp() {
		return ap;
	}
	public void setAp(int ap) {
		this.ap = ap;
		levelUp();
	}
	
	
	
	public Pokemon(String name) {
		setName(name);
	}
	
	// 생성자 
	public Pokemon(String name, int level) {
		setInfo(name, level);
	}
	
	
	public Pokemon() {
	}
	
	// setInfo()
//	인자값 : 이름, 레벨
//	하는 일 : 인자로 들어온 값들을 멤버변수 name, level 에 모두 저장 
//		체력은 레벨의 1000배
//		공격력은 레벨의 1.5배 (20% 확률로 2배)
//	리턴값 : X
	public void setInfo(String name, int level) {
		setName(name);
		setLevel(level);
		reset();
	}
	
	// getInfo()
//	인자값 : X
//	하는 일 : "XXX / Lv. @@ / HP. ####" 형태로 name, level, hp 의 값들을 하나의 문자열로 표현
//	리턴값 : "XXX / Lv. @@ / HP. ####" 형태의 문자열
	public String getInfo() {
		return name + 
				" / Lv. " + level + 
				" / HP. " + hp + 
				" / AP. " + ap;
	}
	
	// levelUp()
//	인자값 : X
//	하는 일 : level을 1증가
//	리턴값 : 증가된 level
	public int levelUp() {
		++level;
		reset();
		return level;
	}
	
	// + 추가 메서드 : 레벨 기반으로 hp, ap 리셋
	private void reset(){
		this.hp = this.level * 1000;
		this.ap = (int)(this.level * ( Math.random() < 0.8 ? 1.5 : 2));
	}
	
	
	// isAlive()
//	인자값 : X
//	하는 일 : 객체의 생사여부 확인( 체력이 0 이하면 죽음 )
//	리턴값 : 살아있으면 true, 아니면 false
	public boolean isAlive() {
		return hp > 0;
	}
	
	// attack()
//	인자값 : 적 포켓몬 객체 (Pokemon형)
//	하는 일 : 상대 포켓몬의 체력을 이 객체의 공격력만큼 감소
//		10% 확률로 치명타 (공격력 X 1.5배)
//	리턴값 : 없음
	public void attack(Pokemon enemy) {
		enemy.hp -= Math.random() < 0.1 ? ap * 1.5 : ap;
	}
	
}

package day13.quiz;

import java.util.Scanner;

public class PokemonMain {
	public static void main(String[] args) {
		Pokemon p1 = new Pokemon("피카츄");
		
		Pokemon p2 = new Pokemon("라이츄", 100);
		
		Pokemon p3 = new Pokemon();
		
		p3.setInfo("파이리", 20);
		
		System.out.println(p3.getInfo());
		
		p3.attack(p2);
		System.out.println(p2.getHp());
		
		
		
		System.out.println(p1.getInfo());
		System.out.println(p2.getInfo());
		
		Scanner sc = new Scanner(System.in);
		System.out.print("이름, 레벨 : ");
		
		String name = sc.next();
		int level = sc.nextInt();
		
		p1.setInfo(name, level);
		
		//p1.name = sc.next();
		//p1.level = sc.nextInt();
		//  ==> p1.hp, p1.ap 도 따로 수정해줘야 함! 
		
		
		System.out.println("수정 후 p1 : " + p1.getInfo());
		
		System.out.println("p1의 레벨업! 결과 : " + p1.levelUp());
		System.out.println("p2의 레벨업! 결과 : " + p2.levelUp());
		
		System.out.println("레벨 업 후 p1 : " + p1.getInfo());
		System.out.println("레벨 업 후 p2 : " + p2.getInfo());
		
		p1.attack(p2);
		System.out.println("p1의 공격 후 p2의 남은 체력 : " + p2.getHp());
	}
}
```
