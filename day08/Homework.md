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

======================================================================================================================================================================

public class Quiz03 {

	public static void main(String[] args) {
//		1. Scanner를 사용하여 6개의 데이터를 입력 받고, 이들을 nums 배열에 저장
		
		Scanner sc = new Scanner(System.in);	// 입력생성
		int nums[] = new int[6];	// 6칸짜리 배열생성
		
		for(int i = 0; i < nums.length; i++) {	// 생성한 배열에 6개의 정수 입력 후 저장
			nums[i] = sc.nextInt();
		}
		
		
//		2. 입력 받은 값 중, 20 이상 100 이하인 원소만 출력
		 
		System.out.println("20 이상 100 이하인 원소 ");
		
		for(int e : nums) {				// 확장된 for문을 활용해서 출력
			if(e >= 20 && e <= 100) {	// if문을 활용해서 20이상이며 100미만인 정수들을 출력
				System.out.println(e + " ");	
			}
		}
		
		
//		3. 입력 받은 값 중, 최댓값과 최솟값을 출력
		int max = nums[0];	// 처음 최댓값을 num[0]으로 저장(어짜피 0번째부터 for문이 시작하니까)
		int min = nums[0];	// 처음 최솟값을 num[0]으로 저장(어짜피 0번째부터 for문이 시작하니까)
		
		for(int i = 1; i < nums.length; i++) {
			if(max < nums[i]) {		// num[i]에서 순차적으로 비교되는 값이 이전의 값보다 크면 max에 저장 
				max = nums[i];
			}
			if(min > nums[i]) {		// num[i]에서 순차적으로 비교되는 값이 이전의 값보다 작으면 min에 저장 
				min = nums[i];
			}
		}
		System.out.println("최댓값 : " + max);	// 최댓값 출력
		System.out.println("최댓값 : " + min);	// 최솟값 출력
		
		
//		4. 오름차순(작은->큰)으로 정렬하여 모든 원소를 출력  ==> 버블 정렬 알고리즘 검색해서 ... 
		
		int temp;
		
		for(int i = nums.length; i>0; i--) {
			for(int j = 0; j < i-1; j++) {
				if(nums[j] > nums[j+1]) {
					temp = nums[j];
					nums[j] = nums[j+1];
					nums[j+1] = temp;	// 임시의 temp 변수를 만들어서 작은 값과 큰값의 자리를 바꾸기 위해 사용
				}
			}
		}
		
		for(int i = 0; i < nums.length; i++) {
			System.out.println(nums[i] + " ");
		}
	
	}

}

```
