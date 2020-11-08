```java
package day09.quiz;

import java.util.Scanner;

public class Quiz05 {

	public static void main(String[] args) {
//		중-6: 로또생성기 만들기 
//		step1) 사용자에게 1 ~ 45 중 6개의 숫자를 입력 받습니다.
//		step2) 컴퓨터는 로또 번호 6개를 생성합니다. 배열의 크기는 6이고 int형입니다.
//		step3) 1 ~ 45 중 6개의 숫자를 배열에 담습니다. 중복된 원소가 있으면 안됩니다.
//		step4) (구현 가능하다면) 오름차순 정렬을 합니다.
//		step5) 배열 결과를 출력합니다.
//		step6) 사용자가 몇 개의 번호를 맞췄는지 출력하세요.
		
		Scanner sc = new Scanner(System.in);
		
		int[] lotto = new int[6];
		System.out.println("숫자를 입력하세요 : ");
		for(int i = 0; i < lotto.length; i++) {
			lotto[i] = sc.nextInt();
		}
		
		int tmp = 0;
		for(int i = 0; i < lotto.length; i++) {
			for(int j = i+1; j < lotto.length; j++) {
				if(lotto[i] > lotto[j]) {
					tmp = lotto[i];
					lotto[i] = lotto[j];
					lotto[j] = tmp;
				}
			}	
		}
			
		int[] lottoAns = new int[6];
		
		for(int i = 0; i <lottoAns.length; i++) {
			lottoAns[i] = (int)(Math.random() * 45) + 1; 
			for(int j = 0; j < i; j++) {
				if(lottoAns[i] == lottoAns[j]) {
					i--;
				}
			}
		}
			
		int temp = 0;
		for(int i = 0; i < lottoAns.length; i++) {
			for(int j = i+1; j < lottoAns.length; j++) {
				if(lottoAns[i] > lottoAns[j]) {
					temp = lottoAns[i];
					lottoAns[i] = lottoAns[j];
					lottoAns[j] = temp;
				}
			}
		}
			
		int cnt = 0;
		for(int i = 0; i < lotto.length; i++) {
			for(int j = 0; j < lottoAns.length; j++) {
				if(lotto[i] == lottoAns[j]) {
					cnt++;
				}
			}
		}
		 
		System.out.println("당첨개수는 " + cnt + "개 입니다.");
		
	}

}

```
