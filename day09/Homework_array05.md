```java
package day09.quiz;

import java.util.Scanner;

public class Quiz03 {

	public static void main(String[] args) {
//		중-4: 대학생 새내기들의 90%는 자신이 반에서 평균은 넘는다고 생각한다. 당신은 그들에게 슬픈 진실을 알려줘야 한다.
//		첫째 줄에는 테스트 케이스의 개수 C가 주어진다.
//
//		둘째 줄부터 각 테스트 케이스마다 학생의 수 N(1 ≤ N ≤ 1000, N은 정수)이 첫 수로 주어지고, 
//		이어서 N명의 점수가 주어진다. 점수는 0보다 크거나 같고, 100보다 작거나 같은 정수이다.
		
		Scanner sc = new Scanner(System.in);
		System.out.print("학생수를 입력하세요 : ");
		int num = sc.nextInt();
		
		int[] score = new int[num];
		
		System.out.print("학생들의 점수를 입력하세요(0 <= n <= 100) : ");
		for(int i = 0; i < score.length; i++) {
			score[i] = sc.nextInt();
		}
		
		int total = 0;
		for(int i = 0; i < score.length; i++ ) {
			total += score[i];
		}
		
		int avg = 0;
		avg = total / num; 
		int cnt = 0;
		for(int i = 0; i < score.length; i++) {
			if(score[i] > avg) {
				cnt++;
			}
		}
		
		double percent = (cnt * 100.0) / num;
		System.out.println(Math.round(percent*1000) / 1000.0 + "%");
			
	}

}

```
