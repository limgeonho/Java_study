```java
package day23.quiz;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.Map.Entry;
import java.util.Scanner;
import java.util.Set;
import java.util.TreeMap;

/*

< 학생 관리 프로그램 >

step 1. 다음 학생들의 정보를 Map 에 저장하세요.(TreeMap<Integer, HashMap<String, Object>>)
key 는 학번(Integer)입니다.
주의) Student 클래스를 사용하지 않고 학생 정보도 Map을 사용합니다. 
{
	101 : {"name":"홍길동", "average":88, "grade":"B", "contact":"010-2222-1231"},
	102 : {"name":"김길동", "average":92, "grade":"A", "contact":"010-2231-1256"},
	103 : {"name":"김장미", "average":47, "grade":"F", "contact":"010-2512-7754"},
	...
}

학번          이름      평균      등급      연락처
101         홍길동      88       B        010-2222-1231
102         김길동      92       A        010-2231-1256
103         김장미      47       F        010-2512-7754
201         장아름      85       B        010-9966-3512
202         최영수      74       C        010-1111-3864
=> 얘는 그대로 입력미리하기

=>   step 2. (1)의 딕셔너리에 학생 3명의 정보를 입력 받아 추가 저장합니다.
    - 학생의 이름, 국, 영, 수, 학년, 연락처를 입력 받습니다.

    - 학년은 학번의 가장 앞자리에 해당합니다.
      예를 들어 딕셔너리에 저장된 2학년 학생이 4명이라면, 다음 2학년 학생의 학번은 205가 되어야 합니다.
  (1 <= 학년 <= 6)	
  (0 <= 학년 당 학생의 수 < 100)

    - 평균은 국,영,수 의 평균을 계산하여 저장합니다.
        *사용자에게 입력 받지 않습니다.

    - 등급은 평균에 따른 A, B, C, D, F 중 하나로 저장합니다.
        *사용자에게 입력 받지 않습니다.
        90 점 이상 : A
        80점 이상 ~ 90점 미만 : B
        70점 이상 ~ 80점 미만 : C
        60점 이상 ~ 70점 미만 : D
        60점 미만 : F

step 3. 사용자 메뉴를 출력합니다. (선택문제) - 무한루프이용
    1. 학번으로 검색
    2. 연락처 뒷번호로 검색**(선택)
    3. 1등 학생 보기**(선택)
    4. 모든 학생 보기**(선택)
    0. 종료

    1. 학번으로 검색
        학번을 입력 받고 해당 학생의 모든 정보를 출력합니다.
        미등록 학번인 경우 '미등록 학번'을 출력합니다.

    2. 연락처 뒷번호로 검색
        연락처 뒷번호 4자리를 입력 받아 연락처가 일치하는
        '모든' 학생들의 이름, 학년, 연락처를 출력합니다.

    3. 1등 학생 보기
        평균을 가지고 1등 학생을 찾아 해당 학생의 학번, 이름, 평균 점수를 출력합니다.
        공동 1등인 경우 학년이 가장 높은 학생을,
        그 중 같은 학년에 공동 1등이 있다면 그 학생들 모두를 출력하세요.

    4. 모든 학생 보기
        현재 등록되어있는 모든 학생들의 모든 정보를 출력하세요.

*/

public class Quiz02 {
	
	public static void main(String[] args) {
				
		HashMap<String, Object> student1 = new HashMap<>();
		HashMap<String, Object> student2 = new HashMap<>();
		HashMap<String, Object> student3 = new HashMap<>();
		HashMap<String, Object> student4 = new HashMap<>();
		HashMap<String, Object> student5 = new HashMap<>();

		Scanner sc = new Scanner(System.in);
		TreeMap<Integer, HashMap<String, Object>> students = new TreeMap<>();
	
		student1.put("name", "홍길동");
		student1.put("average", 88);
		student1.put("grade", "B");
		student1.put("contact", "010-2222-1231");
		students.put(101, student1);
		
		student2.put("name", "김길동");
		student2.put("average", 93);
		student2.put("grade", "A");
		student2.put("contact", "010-2231-1256");
		students.put(102, student2);
		
		student3.put("name", "김장미");
		student3.put("average", 47);
		student3.put("grade", "F");
		student3.put("contact", "010-2512-7754");
		students.put(103, student3);
		
		student4.put("name", "장아름");
		student4.put("average", 85);
		student4.put("grade", "B");
		student4.put("contact", "010-9966-3512");
		students.put(201, student4);
		
		student5.put("name", "최영수");
		student5.put("average", 74);
		student5.put("grade", "C");
		student5.put("contact", "010-1111-3864");
		students.put(202, student5);

		int kor, eng, math;
		String name;
		String rank;
		String tel;
	
		
		for(int i = 0; i < 3; i++) {
				HashMap<String, Object> student = new HashMap<>();
					
				System.out.println("학년을 입력하세요");
				int schoolAge = sc.nextInt();
				Set<Integer> keySet = students.keySet();
				
				int[] checkAge = new int[6];
				int age = 0;
				int sNum = 0;
				for(int s : keySet) {
					age = s / 100;
					switch (age) {
						case 1:
							checkAge[0]++;
							break;
						case 2:
							checkAge[1]++;
							break;
						case 3:
							checkAge[2]++;
							break;
						case 4:
							checkAge[3]++;
							break;
						case 5:
							checkAge[4]++;
							break;
						case 6:
							checkAge[5]++;
							break;
							
						default:
							System.out.println();
							break;
					}
				}
				sNum = (schoolAge * 100) + (checkAge[schoolAge-1]+1);
		
					System.out.println("이름을 입력하세요");
					name = sc.next();
					
				student.put("name", name);
					System.out.println("국어");
					kor = sc.nextInt();
					System.out.println("영어");
					eng = sc.nextInt();
					System.out.println("수학");
					math = sc.nextInt();
					int avg = 0;
					avg = (kor + eng + math) / 3;
				student.put("average", avg);
					if(avg > 90) {
						rank = "A";
					}else if(avg > 80) {
						rank = "B";
					}else if(avg > 70) {
						rank = "C";
					}else if(avg > 60) {
						rank = "D";
					}else {
						rank = "F";
					}
				student.put("grade", rank);
					System.out.println("전화번호를 입력하세요");
					tel = sc.next();
				student.put("contact", tel);
				
				students.put(sNum, student);
			
		}
		
		int checkStudentNum;
		String checkTelNum;
		int select;
		String menu = "1. 학번으로 검색\n" + 
					  "2. 연락처 뒷번호로 검색\n" + 
					  "3. 1등 학생 보기\n" + 
					  "4. 모든 학생 보기\n" + 
					  "0. 종료";
		
	loop:while(true) {
		System.out.println(menu);
		select = sc.nextInt();
			switch (select) {
				case 1:
					System.out.println("학번으로 검색");
					checkStudentNum = sc.nextInt();
					if(students.containsKey(checkStudentNum)) {
						System.out.println(students.get(checkStudentNum));
					}else {
						System.out.println("미등록 학번");
					}
					
					break;
				
				case 2:
					System.out.println("연락처 뒷번호로 검색");
					checkTelNum = sc.next();
						StringBuffer studentInfo1 = new StringBuffer();
						for(Entry<Integer, HashMap<String, Object>> en : students.entrySet()) {
							if(en.getValue().get("contact").toString().endsWith(checkTelNum)) {
								studentInfo1.append("학번 : " + en.getKey() + ", 이름 : " + en.getValue().get("name") + ", 연락처 : " + en.getValue().get("contact") + "\n");
							} 	
						}
						System.out.println(studentInfo1);
					
					break;
				
				case 3:
					System.out.println("1등 학생 보기");
					ArrayList<Integer> arr = new ArrayList<>();
					for(Entry<Integer, HashMap<String, Object>> en : students.entrySet()) {
						arr.add((Integer) en.getValue().get("average"));
					}
					
					int max = arr.get(0);
					for(int i = 0; i < arr.size(); i++) {
						if(max < arr.get(i)) {
							max = arr.get(i);
						}
					}
					
					StringBuffer studentInfo3 = new StringBuffer();
					for(Entry<Integer, HashMap<String, Object>> en : students.entrySet()) {
						if((Integer)en.getValue().get("average") == max){
							studentInfo3.append("학번 : " + en.getKey() + ", 이름 : " + en.getValue().get("name") + ", 평균 :  " + en.getValue().get("average") + "\n");
						}
					}
					System.out.println(studentInfo3);
									
					break;
				
				case 4:
					System.out.println("모든 학생 보기");
					StringBuffer studentInfo2 = new StringBuffer();
					for(Entry<Integer, HashMap<String, Object>> en : students.entrySet()) {
						studentInfo2.append("학번 [" + en.getKey() + "] : " + en.getValue() + "\n");
					}
					System.out.println(studentInfo2);
					
					break;
				
				case 0:
					System.out.println("종료");
					
					break loop;
	
				default:
					System.out.println("잘못 입력하셨습니다.");
					
					break;
				}
			}
		
	}
		

```
