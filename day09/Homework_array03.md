```java
package day09.quiz;

import java.util.Scanner;

public class Quiz02 {

	public static void main(String[] args) {
    		Scanner sc = new Scanner(System.in);
		
		int[] dates = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}; 
		
		System.out.print("월을 입력하세요 :");
		int month = sc.nextInt();
		System.out.print("일을 입력하세요 :");
		int day = sc.nextInt();
		
		// 소요되는 일수
		int x = 0;
		for(int i = 0; i < month-1; i++) {
				x += dates[i];
		}
			x += day -1;
		System.out.println(x);
		
	
//		2) 시작월/일과 목표 월/일 을 각각 입력 받고 d-day 계산기를 만드세요.
//		   단, year는 입력받지 않기때문에 d-day의 최댓값은 364일로 가정합니다.
//		   예) 시작 : 9/26  목표 : 11/23  ==> 결과 : d-day 58 !!!
//		       시작 : 1/1 목표 : 12/31  ==> 결과 : d-day 364 !!!
//		       시작 : 12/31 목표 : 1/1  ==> 결과 : d-day 1 !!!
//		       시작 : 4/12 목표 : 4/11  ==> 결과 : d-day 364 !!!
//		   원리)
//			start : 1/1 ~ 시작 월/일까지 며칠이 소요되는지 계산합니다. 
//			end : 1/1 ~ 목표 월/일까지 며칠이 소요되는지 계산합니다. 
//			end-start 를 합니다. 
//			이때 음수가 나온다면 목표일이 시작일보다 앞서있다는 의미입니다. (즉 목표일이 이듬해)
//			이 경우 +365를 하면 됩니다.
		
		
		int start = 0;
		int end = 0;
		
		System.out.print("시작 월을 입력하세요 : ");
		int startMonth = sc.nextInt();
		System.out.print("시작 월을 입력하세요 : ");
		int startDay = sc.nextInt();
		
		System.out.print("목표 월을 입력하세요 : ");
		int endMonth = sc.nextInt();
		System.out.print("목표 일을 입력하세요 : ");
		int endDay = sc.nextInt();
		
			
		for(int i = 0; i < endMonth-1; i++) {
			end += dates[i];
		}
			end += endDay - 1;
		
		for(int i = 0; i < startMonth-1; i++) {
			start += dates[i];
		}
		start += startDay - 1;
		
		int dDay = 0;
		dDay = end - start;
		
		if(dDay > 0){
		System.out.println("d-day : " + dDay);
		}else if(dDay == 0) {
			System.out.println("d-day!!!");
		}else {
			System.out.println("d-day : " + (dDay + 365));
		}
		
	
	}

}
```
