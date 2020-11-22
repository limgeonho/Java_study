```java
package day20.quiz;

import java.util.Calendar;
import java.util.Scanner;

/*
1. 디데이 계산기를 만드세요.
  시작년월일 입력 --> 목표 년월일 입력 ---> D-Day XX!!! 
*/
public class Quiz01 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		Calendar dCal = Calendar.getInstance();
		Calendar stCal = Calendar.getInstance();
		
		System.out.println("목표년을 입력하세요.");
		int dYear = sc.nextInt();
		System.out.println("목표월을 입력하세요.");
		int dMonth = sc.nextInt();
		System.out.println("목표일을 입력하세요.");
		int dDate = sc.nextInt();
				
		System.out.println("시작년을 입력하세요.");
		int stYear = sc.nextInt(); 
		System.out.println("시작월을 입력하세요.");
		int stMonth = sc.nextInt();
		System.out.println("시작일을 입력하세요.");
		int stDate = sc.nextInt();
		
		dCal.set(dYear, dMonth-1, dDate);
		stCal.set(stYear, stMonth-1, stDate);
		
		long dDaySec = (dCal.getTimeInMillis() - stCal.getTimeInMillis());
		
		long dDay = dDaySec/ (24*60*60*1000);
		System.out.println("D-Day까지 D-" + dDay + 1 + "일");
		
		
	}
}
========================================================================================================
package day20.quiz;

import java.time.DayOfWeek;
import java.util.Calendar;
import java.util.Scanner;

/*
 * 2. 년, 월을 입력 받고 해당 월을 달력형태로 출력하세요. (토요일마다 줄바꿈이 일어나도록)
 2020 10
 일	월	화	수	목	금	토
				1	2	3
 4	5	6	7	8	9	10
 11	12	13	14	15	16	17
 18	19	20	21	22	23	24
 25	26	27	28	29	30	31 	
 */
public class Quiz02 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		 
		String[] days = {"", "일", "월", "화", "수", "목", "금", "토"};
		
		Calendar stCal = Calendar.getInstance();
		Calendar endCal = Calendar.getInstance();
		
		System.out.println("년을 입력하세요.");
		int year = sc.nextInt();
		System.out.println("달을 입력하세요");
		int month = sc.nextInt();
		
		stCal.set(year, month-1, 1);
		endCal.set(year, month, 1);
		endCal.add(Calendar.DATE, -1);
		
		
		int num = stCal.get(Calendar.DAY_OF_WEEK);
		
		int startDay = stCal.get(Calendar.DATE);
		int lastDay = endCal.get(Calendar.DATE);
//		System.out.println(startDay);
//		System.out.println(lastDay);
		
		
		
		System.out.println("==== " + year + "년 " + month + "월  ====");
		System.out.println("일\t월\t화\t수\t목\t금\t토");
		
		for(int j = 1; j < num; j++) {
			System.out.print("\t");
		}
		
		for(int i = startDay ; i < lastDay+1; i++) {
			stCal.set(year, month-1, i);
				if(stCal.get(Calendar.DAY_OF_WEEK) % 7 != 0) {
					System.out.print(i + "\t");
				}else {
					System.out.print(i + "\n");
				}
		}	
	}		
}
```
