```java
package day09.quiz;

import java.util.Scanner;

public class Quiz01 {

	public static void main(String[] args) {
//		하-1 : int형 6칸 짜리 배열을 생성하세요.
		
		int[] arr = new int[6];
		
		
//		하-2 : 다음 출력 결과를 예상하세요.
		int[] a = new int[2]; 
		System.out.println(a[0]); // 답 :  0
		System.out.println(a[1]); // 답 :  0

		double[] b = new double[2];
		System.out.println(b[0]); // 답 :  0.0
		System.out.println(b[1]); // 답 :  0.0

		String[] c = new String[2];
		System.out.println(c[0]); // 답 :  null
		System.out.println(c[1]); // 답 :  null


		char[] d = new char[2];
		System.out.println(d[0]); // 답 :  
		System.out.println(d[1]); // 답 :  


		boolean[] e = new boolean[2];
		System.out.println(e[0]); // 답 :  false
		System.out.println(e[1]); // 답 :  false
		
		
//		하-3 : 사용자에게 배열의 칸 개수를 입력 받고, 해당 정수의 크기만큼 정수형 배열을 생성하세요.
		Scanner sc = new Scanner(System.in);
		int num = sc.nextInt();
		
		int[] arrThree = new int[num];
		
		for(int i = 0; i < arrThree.length; i++) {
			System.out.print(arrThree[i] + " ");
		}
		
		System.out.println();
//		 하-4 : (3)번에서 생성된 배열에 다음 기능을 추가하세요.
//			ㄱ. 0 ~ n-1 까지의 숫자를 배열에 순서대로 저장하세요.
//				입력 : 3  ===> 결과 : [0, 1, 2]
//				입력 : 5  ===> 결과 : [0, 1, 2, 3, 4]
//			ㄴ. 배열의 가장 마지막 원소부터 0번 원소까지 역순으로 출력하세요.
//			ㄷ. for문을 사용하여 배열에 저장된 실제 원소들을 역순으로 재배치 하세요. (난이도 중)
//			    sysout(배열[0]); // 3
//			    sysout(배열[1]); // 2
//			    sysout(배열[2]); // 1
//			    sysout(배열[3]); // 0
//			   (for문을 쓰되 for문의 실행 횟수가 n/2이 되도록하세요. 
//		         (5칸 배열이면 2회만에, 10칸 배열이면 5회만에 for문이 종료되도록))

		for(int i = 0; i < arrThree.length; i++) {
			arrThree[i] = i;
			System.out.print(arrThree[i] + " ");
		}
		
		System.out.println();
		
		for(int i = arrThree.length-1; i >= 0; i--) {
			arrThree[i] = i;
			System.out.print(arrThree[i] + " ");
		}
		
		System.out.println();
		
		int tmp = 0;
	
		for(int i = 0; i < (num / 2); i++) {
			tmp = arrThree[i];
			arrThree[i] = arrThree[num-(i+1)];
			arrThree[num-(i+1)] = tmp;
			}
		for(int g : arrThree) {
			System.out.print(g + " ");
		}
			
			
//			하-5 : 사용자에게 배열의 칸 개수를 입력 받고, 해당 정수의 크기만큼 String형 배열을 생성하고
//			입력 : 3  ===> 결과 : [ null, null, null ] 
//			입력 : 5  ===> 결과 : [ null, null, null, null, null ]
//			
//			사용자에게 입력받은 단어들을 순차적으로 배열에 저장하세요.  
						
		int n = sc.nextInt();
		
		String[] arrSt = new String[n];

		for(int i = 0; i < arrSt.length; i++) {
			arrSt[i] = sc.next();
		}
		
		for(String f : arrSt) {
			System.out.print(f + " ");
		}
		
		
	}

}
```
