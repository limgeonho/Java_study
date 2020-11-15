```java
package day15.quiz;

import java.text.DecimalFormat;
import java.util.Scanner;

/*
 * 부모 클래스 : Student 
 *  1) 필드 : 학생이름, 나이, 학교명
 *  2) 메소드 :
 *   	ㄱ. 생성자 
 *   		- 디폴트 생성자(기본생성자)
 *   		- 학생이름, 나이, 학교명 3개 넣고 생성되도록 
 *   	ㄴ. getters
 *   	ㄷ. setters
 * 자식 클래스1 : ElementaryStudent
 *  1) 추가할 필드 : 국어점수, 영어점수, 학부모 연락처
 *  2) 메소드 : 
 *   	ㄱ. 생성자 
 *   		- 학생이름, 나이, 학교명
 *   		- 학생이름, 나이, 학교명, 학부모 연락처
 *   		- 학생이름, 나이, 학교명, 국어점수, 영어점수
 *		ㄴ. getters
 *		ㄷ. setters
 * 자식 클래스2 : MiddleSchoolStudent
 *  1) 추가할 필드 : 국어점수, 영어점수, 수학점수, 평균점수		
 *  2) 메소드 : 
 *  	ㄱ. 생성자 
 *  		- 학생이름, 나이, 학교명, 국어점수, 영어점수, 수학점수
 *  		  (평균 자동 계산)
 *  	ㄴ. getters
 *  	ㄷ. setters
 * 자식 클래스3 : HighSchoolStudent
 *  1) 추가할 필드 : 국어점수, 영어점수, 수학점수, 평균점수, 내신등급	
 *  2) 메소드 : 
 *  	ㄱ. 생성자 
 *  		- 학생이름, 나이, 학교명, 국어점수, 영어점수, 수학점수
 *  		  (평균 자동 계산)
 *  	ㄴ. getters
 *  	ㄷ. setters
 */
class Student{
	protected String name;
	protected int age;
	protected String schoolName;

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		if(age < 8 || age > 18) {
			return;
		}
		this.age = age;
	}

	public String getSchoolName() {
		return schoolName;
	}

	public void setSchoolName(String schoolName) {
		this.schoolName = schoolName;
	}

	public Student() {
		
	}
	
	public Student(String name, int age) {
		setName(name);
		setAge(age);
	}
	
	public Student(String name, int age, String schoolName) {
		setName(name);
		setAge(age);		
		setSchoolName(schoolName);
	}
	
	public void setInfo(String schoolName) {
		setSchoolName(schoolName);
	}
		
	public String toString() {
		return "학생이름 : " + name + "\n나이 : " + age + "\n학교명 : " + schoolName; 
	}
}

class ElementaryStudent extends Student{
	protected int kor;
	protected int eng;
	protected String parentNumber;
	
	public int getKor() {
		return kor;
	}
	public void setKor(int kor) {
		this.kor = kor;
	}
	public int getEng() {
		return eng;
	}
	public void setEng(int eng) {
		this.eng = eng;
	}
	public String getParentNumber() {
		return parentNumber;
	}
	public void setParentNumber(String parentNumber) {
		this.parentNumber = parentNumber;
	}
	
	public ElementaryStudent(String name, int age) {
		super(name, age);
	}
		
	public ElementaryStudent(String name, int age, String schoolName) {
		super(name, age, schoolName);
	}
	
	public ElementaryStudent(String name, int age, String schoolName, String parentNumber) {
		super(name, age, schoolName);
		setParentNumber(parentNumber);
	}
	
	public ElementaryStudent(String name, int age, String schoolName, int kor, int eng) {
		super(name, age, schoolName);
		setKor(kor);
		setEng(eng);
	}
	
	public void setInfo(String schoolName, String parentNumber, int kor, int eng) {
		setSchoolName(schoolName);
		setParentNumber(parentNumber);
		setKor(kor);
		setEng(eng);
	}
		
	public String toString() {
		return "학생이름 : " + name + "\n학교명 : " + schoolName + "\n학부모번호 : " + parentNumber 
				+ "\n국어 : " + kor	+ "\n영어 : " + eng;
	}
}

class MiddleSchoolStudent extends ElementaryStudent{
	protected int math;
	protected double avg;
	
	public int getMath() {
		return math;
	}
	public void setMath(int math) {
		this.math = math;
	}
	protected double getAvg() {
		return avg;
		 
	}
	protected void setAvg(int kor, int eng, int math) {
		avg = (kor + eng + math) / 3.0;
		
		
	}
	
	public MiddleSchoolStudent(String name, int age) {
		super(name, age);
	}
	public MiddleSchoolStudent(String name, int age, String schoolName, int kor, int eng, int math) {
		super(name, age, schoolName, kor, eng);
		setMath(math);
	}
	
	public void setInfo(String schoolName, String parentNumber, int kor, int eng, int math) {
		setSchoolName(schoolName);
		setParentNumber(parentNumber);
		setKor(kor);
		setEng(eng);
		setMath(math);
		setAvg(kor, eng, math);
	}
	
	public String toString() {
		DecimalFormat df = new DecimalFormat("#.##");
		
		return "학생이름 : " + name + "\n학교명 : " + schoolName + "\n학부모번호 : " + parentNumber 
				+ "\n국어 : " + kor	+ "\n영어 : " + eng + "\n수학 : " + math 
				+ "\n평균 : " + (df.format(avg));
	}
}

class HighSchoolStudent extends MiddleSchoolStudent{
	protected String rank;

	private String getRank() {
		return rank;
	}

	private void setRank(double avg) {
		if(avg > 90) {
			rank = "A 등급";
		}else if(avg > 80) {
			rank = "B 등급";
		}else if(avg > 70) {
			rank = "C 등급";
		}else if(avg > 60) {
			rank = "D 등급";
		}else {
			rank = "E 등급";
		}
	}
	
	public HighSchoolStudent(String name, int age) {
		super(name, age);
	}
	
	public HighSchoolStudent(String name, int age, String schoolName, int kor, int eng, int math) {
		super(name, age, schoolName, kor, eng, math);
	}
	
	public void setInfo(String schoolName, String parentNumber, int kor, int eng, int math) {
		setSchoolName(schoolName);
		setParentNumber(parentNumber);
		setKor(kor);
		setEng(eng);
		setMath(math);
		setAvg(kor, eng, math);
		setRank(avg);
	}
	
	public String toString() {
		DecimalFormat df = new DecimalFormat("#.##");
		return "학생이름 : " + name + "\n학교명 : " + schoolName + "\n학부모번호 : " + parentNumber 
				+ "\n국어 : " + kor	+ "\n영어 : " + eng + "\n수학 : " + math 
				+ "\n평균 : " + (df.format(avg)) + "\n등급 : " + rank;
	}
}

public class Quiz02 {
//	메인 클래스 : Quiz02
//	 *  - 이름과 나이를 입력 받음
//	 *  - 나이에 따른 객체 생성 (예. 13 -> new ElementaryStudent())
//	 *  - 각 객체의 필드를 입력 받아서 저장 
//	 *    예. 중학생이면
//	 *    	  학교명, 국어점수, 영어점수, 수학점수 입력 받음
//	 *  - 결과 출력
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		String name;
		int age;
		String schoolName;
		String parentNumber;
		int kor, eng, math;
				
		System.out.println("이름을 입력하세요.");
		name = sc.next();
		System.out.println("나이를 입력하세요.");
		age = sc.nextInt();
		
		if(age > 7 && age < 13) {
			ElementaryStudent es = new ElementaryStudent(name, age);
			
			System.out.println("학교명 / 학부모 번호 / 국어점수 / 영어점수");
			schoolName = sc.next();
			parentNumber = sc.next();
			kor = sc.nextInt();
			eng = sc.nextInt();
			
			es.setInfo(schoolName, parentNumber, kor, eng);
			
			System.out.println(es.toString());
			
		}else if(age > 12 && age < 16) {
			MiddleSchoolStudent ms = new MiddleSchoolStudent(name, age);
			
			System.out.println("학교명 / 학부모 번호 / 국어점수 / 영어점수 / 수학점수");
			schoolName = sc.next();
			parentNumber = sc.next();
			kor = sc.nextInt();
			eng = sc.nextInt();
			math = sc.nextInt();
			
			ms.setInfo(schoolName, parentNumber, kor, eng, math);
			
			System.out.println(ms.toString());
			
		}else if(age > 15 && age < 20) {
			HighSchoolStudent hs = new HighSchoolStudent(name, age);
			
			System.out.println("학교명 / 학부모 번호 / 국어점수 / 영어점수 / 수학점수");
			
			schoolName = sc.next();
			parentNumber = sc.next();
			kor = sc.nextInt();
			eng = sc.nextInt();
			math = sc.nextInt();
			
			hs.setInfo(schoolName, parentNumber, kor, eng, math);
			
			System.out.println(hs.toString());
						
		}else {
			System.out.println("다시 입력하세요.");
		}

	}

}
```
