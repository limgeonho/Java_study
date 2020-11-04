```java
public class Quiz01 {

	public static void main(String[] args) {
/*
 *  < 제어문 최종 문제 - 구구단 게임 만들기 >
 *  규칙 : 
 *   	1. 사용자에게 원하는 판 수를 입력 받는다.
 *   	2. 입력 받은 판 수 만큼 구구단 문제를 낸다.
 *   	3. 정답 시 100점, 오답일 경우 -10점.
 *   	4. 모든 횟수가 종료되면 총점을 출력한다.
 *   	5. 정답률을 퍼센티지로 출력한다.(소숫점은 생략한다.)
 *   	6. 정답률이 80% 이상이면 "win"을, 그렇지 않으면 "lose"를 출력한다.
 */
	String num = JOptionPane.showInputDialog("판수를 입력하세요");	// 사용자에게 원하는 판 수를 입력받음
	int pNum = Integer.parseInt(num);	// 입력받은 판수는 String형으로 저장되기 때문에 int형으로 변환
	int score = 0;	// 점수는 최초에 0점으로 초기화
	int winCnt = 0;	// 정답률을 위해 이긴 판 수를 0으로 초기화
	String res;

	for(int n = 1; n <= pNum; n++) {
		int a, b;

		a = (int)(Math.random() * 8) +2;	// 정해진 판 수 만큼 랜덤의 숫자 2개를 뽑아서 문제를 냄
		b = (int)(Math.random() * 8) +2;

		int answer = a * b;	// 문제에 대한 정답

		String userAns = JOptionPane.showInputDialog(a + " X " + b + " = ");	// 문제를 보고 사용자가 입력한 정답을 String형으로 저장
		int pUserAns = Integer.parseInt(userAns);	// 입력받은 정답을 int형으로 변환

		if(answer == pUserAns) {	// 원래의 정답과 사용자가 입력한 정답이 같다면
			score += 100;	// 점수에는 +100
			winCnt ++;	// 이긴 횟수에 +1
			}else {
				score -= 10;	// 정답이 틀리다면 점수에 -10
			}
		}

		double percent =  ((double)winCnt / pNum) * 100;	// 정답률을 구함

		if(percent >= 80) {	// 정답률을 통해 80이상이면 win을 미만이면 lose를 String형 변수 res에 저장
			res = "WIN";
		}else{
			res = "LOSE";
		}

		JOptionPane.showMessageDialog(null, "총점 : " + score 
				+ "\n정답률 : " + (int)percent + "%"
				+ "\n" + res);	// 지금까지 구한 것들을 출력

	}

}
```
