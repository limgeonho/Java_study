```java
package day09.quiz;

import java.util.Scanner;

public class Quiz04 {

	public static void main(String[] args) {
		
//		중-5: 호텔관리 프로그램 만들기 
//		step1) 사용자에게 호텔의 방 개수를 입력 받습니다.
//		step2) 방개수와 동일한 크기의 배열을 생성합니다. (5개면 5칸짜리 배열 생성)
//	        step3) 사용자 메뉴를 메시지로 보여주고 메뉴를 선택 받습니다.
//	            < 메뉴 >
//	            1. 체크인
//	            2. 체크아웃
//	            3. 현황 보기
//	            0. 종료하기
//	    
//	            1. 체크인
//	                방 호수(1번부터 시작)를 입력 받습니다.
//	                방이 이미 입실 중이면 "입실 중인 방은 체크인 하실 수 없습니다."를 출력하세요.
//	                빈 방인 경우 "입실 완료!"를 출력하고 메뉴로 돌아갑니다.
//	            2. 체크아웃
//	                방 호수(1번부터 시작)를 입력 받습니다.
//	                방이 빈 방이면 "빈 방은 체크아웃 하실 수 없습니다."를 출력하세요.
//	                체크인 상태인 경우 "퇴실 완료!"를 출력하고 메뉴로 돌아갑니다.
//	            3. '방호수 - 상태'를 출력합니다.
//	                출력 예)
//	                    1호 : 빈 방
//	                    2호 : 입실 중
//	                    3호 : 입실 중
//	                    4호 : 빈 방
//	                    5호 : 빈 방
//	            0. 종료
//	                반복을 종료하고 '영업 종료' 를 출력합니다.
//
//		    (힌트 : 사용자가 4호에 입실한다면 [3]번칸에 1을 저장하고 퇴실한다면 0을 저장합니다. 즉 투숙객이 있음은 1로 없으면 0으로 표시합니다.)
//
//	        step4) 사용자가 메뉴에서 0을 입력할 때까지 (3) 과정을 진행합니다.
		
		
		Scanner sc = new Scanner(System.in);
		
		System.out.print("호실 개수를 선택하세요 : ");
		int num = sc.nextInt();
		
		int[] room = new int[num];
		
		for(int i = 0; i < room.length; i++) {
			room[i] = 0;
		}
				
		while(true) {
			System.out.println("======<메뉴>======"
					+ "\n"
					+ "\n메뉴를 선택하세요 : "
					+ "\n1. 체크인"
					+ "\n2. 체크아웃"
					+ "\n3. 현황 보기"
					+ "\n4. 종료하기");
			
			int select = sc.nextInt();
			
			switch (select) {
			case 1:
				System.out.print("체크인할 호수를 선택하세요 : ");
				int roomNumCheckIn = sc.nextInt() - 1;
					if(room[roomNumCheckIn] == 0) {
						room[roomNumCheckIn] = 1;
						System.out.println("입실 완료!");
					}else {
						System.out.println("입실 중인 방은 체크인 하실 수 없습니다.");
					}
				break;
				
			case 2: 
				System.out.print("체크아웃할 호수를 선택하세요 : ");
				int roomNumCheckOut = sc.nextInt() - 1;
					if(room[roomNumCheckOut] == 1) {
						System.out.println("퇴실 완료!");
						room[roomNumCheckOut] = 0;
					}else {
						System.out.println("빈 방은 체크아웃 하실 수 없습니다.");
					}
				break;
				
			case 3:
				System.out.println("방 호수 상태");
				for(int i = 0; i< room.length; i++) {
					if(room[i] == 0) {
						System.out.println((i+1) + "호 : 빈 방");
					}else {
						System.out.println((i+1) + "호 : 입실 중");
					}
				}
				break;
				
			case 4:
				System.out.println("영업 종료!");
				return;
			}
		}
				
	}

}

```
