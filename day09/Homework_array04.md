```java
package day09.quiz;

import java.util.Scanner;

public class Quiz03 {

	public static void main(String[] args) {
//		중-3: "김", "이", "박", "최", "한" 등의 대한민국 성씨를 저장할 배열을 만들고, 성씨들을 저장하세요.
//	       "피카츄", "라이츄", "파이리", "꼬부기", "버터풀", "야도란", "피죤투" 를 저장할 배열을 만들고 이름들을 저장하세요.
//	       1) 총 10개의 성+이름 조합을 출력하세요. ( Math.random()을 사용하며, 중복 조합을 허용합니다)

		Scanner sc = new Scanner(System.in);
		
		System.out.print("성씨의 개수를 입력하세요 : ");
		int nameCnt = sc.nextInt();
		String[] kor = new String[nameCnt];
		
		String[] poke = {"피카츄", "라이츄", "파이리", "꼬부기", "버터풀", "야도란", "피죤투"};
		
		System.out.println("성씨를 입력하세요 : ");
		for(int i =0; i< kor.length; i++) {
			kor[i] = sc.next();
		}
		
		int cnt = 0;
		while(cnt < 10) {
			System.out.println((String)kor[(int)(Math.random() * nameCnt)] + (String)poke[(int)(Math.random() * 7)]);
			cnt++;
		}
		
		
//	       2) 조합가능한 모든 이름을 출력하세요.		
		
		for(int i = 0; i < kor.length; i++) {
			for(int j = 0; j < poke.length; j++) {
				System.out.println((String)kor[i] + (String)poke[j]);
			}
		}
  }
}
```
