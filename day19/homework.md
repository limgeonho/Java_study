```java
package day19.quiz;

import java.util.Scanner;

public class Quiz01 {
	/*
	 * 1. 사용자가 -1을 입력할 때까지 문자열을 입력 받고
	    1) 입력된 문자열 중 소문자 'a'의 개수를 출력하세요.
	    2) 비출력문자(공백,엔터 등)을 제외한 문자의 총 개수를 출력하세요.
	    3) 단어의 개수를 출력하세요.
	 */
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		System.out.println("문자열을 입력하세요.");
		String str = sc.nextLine();
		if(str.equals("-1")) {
				return;
			}else {
				// 문자열 중 a의 개수
				String[] spStr = str.split("");
				int cnt = 0;	
				for(String s : spStr) {
						if(s.equals("a")) {
							cnt++;
						}
					}
				System.out.println("a의 개수 : " + cnt);
				
				// 공백을 제외한 문자의 개수
				String tStr = str.trim();
				String rStr = tStr.replaceAll(" ","");
				System.out.println("공백을 지운 문자열 : " + rStr);
				
				System.out.println("문자의 개수 : " + rStr.length() + "개");
				
				// 단어의 개수 
				String[] wordStr = str.split(" ");
				System.out.println("단어의 개수 : " + wordStr.length + "개");
			}
		
	}
}

===========================================================================================================

package day19.quiz;

import java.util.Scanner;
class Email{
	private String email;

	public String getEmail() {
		return email;
	}

	public void setEmail(String email) {
		
		if(!email.contains("@")) {
			System.out.println("다시 입력하세요.");
			return;
		} 
		if(!email.endsWith("com")&&!email.endsWith("co.kr")&&!email.endsWith("net")) {
			System.out.println("다시 입력하세요.");
			return;
		}
		if(!email.contains("naver")&&!email.contains("gmail")&&!email.contains("hanmail")) {
			System.out.println("다시 입력하세요.");
			return;
		}
		if(email.contains(" ")) {
			email = email.replaceAll(" ", "");
			this.email = email;
		}
			this.email = email;
	}
}
class Password{
	private String password;
	
	public String getPassword() {
		return password;
	}

	public void setPassword(String password) {
		char[] pw = password.toCharArray();
		if(pw.length < 4 || pw.length > 20) {
			System.out.println("다시 입력하세요.");
			return;
		}
		this.password = password;
	}
}	

public class Quiz02 {
	/*
	 * 2. 회원가입과정은 다음과 같습니다.
		1) 이메일을 입력 받는다.
		2) 비밀번호를 2번 입력받는다.
		
	    이때 다음 조건에 충족하면 저장, 그렇지 않으면 해당 항목을 재입력 받으세요
	 	1) 이메일 조건
			- @ 를 포함하여야 한다.
			- com, co.kr, net 중 하나로 끝나야 한다
			- 메일서버(naver, gmail, hanmail 등) 이름을 포함해야 한다.
			- 아이디가 있어야 한다.
			- 공백이 있다면 제거한다.
			
		2) 비밀번호 조건
			- 4자 이상 20자 이하여야 한다.
			- (선택사항) 특수기호, 숫자, 대소문자가 최소 1개씩 모두 있어야 한다. (String 클래스의 matches()사용)
			- 두 비밀번호가 동일해야 한다.
	
	   모두 정상적인 입력을 받았다면 사용자의 id, 패스워드, 이메일을 출력하세요.
		1) id 는 이메일의 @ 앞 부분을 추출합니다.
		2) 비밀번호는 앞 두 글자만 출력하고 나머지는 '*'로 대체합니다.
			예) pika1234 ==> pi******
		3) 이메일은 모두 출력합니다.
	 */
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		Email email = new Email();
		while(true) {
			if(email.getEmail() == null) {
				System.out.println("이메일 입력");
				String e = sc.nextLine();
				
				email.setEmail(e);
				
			}else {
				break;
			}
		}
		
		Password password1 = new Password();
		Password password2 = new Password();
		while(true) {
			if(password1.getPassword() == null || password2.getPassword() == null) {
				System.out.println("비밀번호입력 1차");
				String pw1 = sc.next();
				System.out.println("비밀번호입력 2차");
				String pw2 = sc.next();
				
				password1.setPassword(pw1);
				password2.setPassword(pw2);
			}break;
		}
		
		while(true) {
			if(password1.getPassword().equals(password2.getPassword())) {
				System.out.println("비밀번호 저장 성공!");
				break;
				}else {
					System.out.println("1차 비밀번호와 2차 비밀번호가 다릅니다.");
					System.out.println("비밀번호 다시 입력");
					String pw3 = sc.next();
					password2.setPassword(pw3);
				}
		}
		String id[] = email.getEmail().split("@");
		System.out.println("사용자 id : " + id[0]);
		System.out.println("사용자 이메일 : " + email.getEmail());
		
		String[] secretPassword = password1.getPassword().split("");
		for(int i = 2; i < secretPassword.length; i++) {
			secretPassword[i] = "*";
		}
		
		System.out.print("사용자 비밀번호 : ");
		for(String s : secretPassword) {
			System.out.print(s);
		} 
		
	}
}
```
