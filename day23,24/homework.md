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
	
//		int age = sc.nextInt();
//		Set<Integer> keySet = students.keySet();
//		
//		int number = (age * 100);

		int kor, eng, math;
		String name;
		String rank;
		String tel;
	
		for(int i = 0; i < 3; i++) {
				HashMap<String, Object> student = new HashMap<>();
					
					System.out.println("학번을 입력하세요");
					int studentNum = sc.nextInt();
					
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
				
				students.put(studentNum, student);
			
		}
//				System.out.println(students);
		
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
								studentInfo1.append("[" + en.getKey() + "] : " + en.getValue().get("name") + " " + en.getValue().get("contact") + "\n");
							} 	
						}
						System.out.println(studentInfo1);
					
					break;
				
				case 3:
					System.out.println("1등 학생 보기");
					int[] arr = null;
					for(Entry<Integer, HashMap<String, Object>> en : students.entrySet()) {
						 arr = new int[] {((int) en.getValue().get("average"))};
					}
					
					int max = 0;
					for(int i = arr[0]; i < arr.length; i++) {
						if(arr[i] < max) {
							max = arr[i];
						}
					}
					StringBuffer studentInfo3 = new StringBuffer();
					for(Entry<Integer, HashMap<String, Object>> en : students.entrySet()) {
						if(en.getValue().get("average").equals(String.valueOf(max))){
							studentInfo3.append("[" + en.getKey() + "] : " + en.getValue().get("name") + " " + en.getValue().get("average") + "\n");
						}
					}
					System.out.println(studentInfo3);
									
					break;
				
				case 4:
					System.out.println("모든 학생 보기");
					StringBuffer studentInfo2 = new StringBuffer();
					for(Entry<Integer, HashMap<String, Object>> en : students.entrySet()) {
						studentInfo2.append("[" + en.getKey() + "] : " + en.getValue() + "\n");
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
		
}
==========================================================================================================================
package day24.quiz;

import java.util.Scanner;

class MyEmailPolicyException extends Throwable{
	public MyEmailPolicyException(String message) {
		super(message);
	}
	
	public MyEmailPolicyException() {
		super("잘못된 이메일 형식입니다.");
	}
}

class MyPasswordPolicyException extends Throwable{
	public MyPasswordPolicyException(String message) {
		super(message);
	} 
	
	public MyPasswordPolicyException() {
		super("잘못된 비밀번호 형식입니다.");
	}
}

class MyConfirmPasswordException extends Throwable {
	public MyConfirmPasswordException(String message) {
		super(message);
	}
	
	public MyConfirmPasswordException() {
		super("두 비밀번호가 일치하지 않습니다.");
	}
}

class User {
	
	interface Whitelist{
		// 유효한 서버 이름과 도메인을 따로 상수로 선언하면 유지보수가 편하다.  
		String[] VALID_MAIL_SERVER_NAMES = 
			{ "naver", "gmail", "hanmail", "nate"};
		
		String[] VALID_MAIL_SUFFIXES = 
			{"com", "co.kr", "net", "org" };
		String PASSWORD_REGEX = "^(?=.*[0-9])(?=.*[a-z])(?=.*[A-Z])(?=.*[@#$%^&+=])(?=\\S+$).{4,20}$";
		
		/*
		 * ^ # start-of-string 
		 * (?=.*[0-9]) # a digit must occur at least once
		 * (?=.*[a-z]) # a lower case letter must occur at least once 
		 * (?=.*[A-Z]) # an upper case letter must occur at least once 
		 * (?=.*[@#$%^&+=]) # a special character must occur at least once 
		 * (?=\S+$) # no whitespace allowed in the entire string 
		 * .{4,20} # anything, at least eight and less or equal to 20 places though 
		 * $ # end-of-string
		 */
	}
	
	
	private String id; // get
	private String email; // set, get
	private String password; // set, (get 대신 hiddenPassword) 
	
	public boolean setEmail(String email) throws MyEmailPolicyException{
		
		// null comparison
		if(null == email) {
			throw new MyEmailPolicyException("이메일을 등록해주세요.");
		}
		
		
		// email 양 공백 제거
		email = email.trim();
		
		
		// @ 를 포함하여야 한다.
		if(!email.contains("@")) {
			throw new MyEmailPolicyException("@를 포함하셔야 합니다.");
		}
		
		// trim이 되었고 @가 있는 이메일은  
		//  아이디가 없을 경우 무조건 맨 앞글자가 "@"일 것이다.
		if(email.indexOf("@") == 0) {
			throw new MyEmailPolicyException("아이디를 포함하셔야합니다.");
		}
		
		// com, co.kr, net 중 하나로 끝나야 한다
		String suffix = null;
		for(String s : Whitelist.VALID_MAIL_SUFFIXES) {
			if(email.endsWith(s)) {
				suffix = s;
				break;
			}
		}
		if(null == suffix) {
			throw new MyEmailPolicyException("com, co.kr, net 중 하나로 끝나야 합니다.");
		}
		
		// 메일서버(naver, gmail, hanmail 등) 이름을 포함해야 한다.
		boolean check = false;
		for(String server : Whitelist.VALID_MAIL_SERVER_NAMES) {
			if(email.endsWith("@" + server + "." + suffix)) {
				check = true;
				break;
			}
		}
		if(!check) {
			throw new MyEmailPolicyException("메일서버(naver, gmail, hanmail 등)를 포함하셔야 합니다.");
		}
		this.email = email;
		setId();
		return true;
	}
	public boolean setPassword(String password) throws MyPasswordPolicyException {
		if (!password.matches(Whitelist.PASSWORD_REGEX)) {
			throw new MyPasswordPolicyException("특수기호, 숫자, 대소문자 최소 1개씩을 포함하셔야 합니다.");
		}
		if(password.length() < 4 || password.length() > 20) {
			throw new MyPasswordPolicyException("비밀번호는 4 ~ 20자리여야 합니다.");
		}
		this.password = password;
		return true;
	}
	public boolean confirmPassword(String password) throws MyConfirmPasswordException {
		if(null == this.password) {
			throw new MyConfirmPasswordException("비밀번호를 입력하세요.");
		}
		return this.password.equals(password);
	}
	
	private void setId() {
		if(null == email) 
			return;
		// issell@naver.com 
		// 방법1 : split("@") ==> [ 'issell' , 'naver.com' ]
		// 방법2 : substring(0, indexOf("@"))
		
		// 방법1 
		// id = email.split("@")[0];
		
		// 방법2
		id = email.substring(0, email.indexOf("@"));
	}
	
	public String hiddenPassword() throws MyPasswordPolicyException{
		if(null == password) {  // pika1234 
			throw new MyPasswordPolicyException("비밀번호를 입력하세요.");
		}
		String temp = password.substring(0,2); // pi
		for(int i = 0; i < password.length()-2; ++i) { // "*" 를 총 6번 붙임
			temp += "*";
		}
		return temp; // pi******
	}
	
	@Override
	public String toString() {
		try {
			return "User [id=" + id + 
					", email=" + email + 
					", password=" + hiddenPassword() + "]";
		} catch (MyPasswordPolicyException e) {
			System.err.println("비밀번호를 입력하세요.");
		}
		return "비밀번호를 입력하세요.";
	}
}
public class Quiz02 {
	public static void main(String[] args) {
		User user = new User();
		Scanner sc = new Scanner(System.in); 
		
		// 이메일 입력 loop 
		while(true) {
			try {
				System.out.print("이메일 : ");
				String email = sc.next();
				if(!user.setEmail(email)) {
					continue;
				}
				break;
			} catch(MyEmailPolicyException e) {
				System.err.println(e.getMessage()); 
			}
			
		}
		while(true) {
			System.out.print("비밀번호 : ");
			String password = sc.next();
			try {
				if(!user.setPassword(password)) {
					continue;
				}
			} catch (MyPasswordPolicyException e) {
				System.err.println(e.getMessage());
			}
			
			System.out.print("한 번 더 : ");
			String temp = sc.next();
			try {
				if(!user.confirmPassword(temp)) {
					continue;
				}
			} catch (MyConfirmPasswordException e) {
				System.err.println(e.getMessage());
			}
			break;
		}
		System.out.println(user);
	}
}
```
