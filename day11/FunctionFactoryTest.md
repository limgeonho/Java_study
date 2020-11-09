```java
package day11.quiz;

public class FunctionFactoryTest {

	public static void main(String[] args) {
		FunctionFactory ff = new FunctionFactory();
		
		
//		1. 입력받은 단 출력하기(1)
		
		String dan = ff.strGugudan(6);
		System.out.println(dan);
		
//		2. 입력받은 단 출력하기(2)
		
		ff.printGugudan(2);
		
//		3. 국, 영, 수 평균 출력하기
		
		int avg = ff.getAverage(90,85,100);
		System.out.println(avg);
		
//		4. 포켓몬 랜덤으로 출력하기
		
		String name = ff.getRandomPokemon();
		System.out.println(name);
		
//		5. 입력받은 배열 중 가장 큰 수 출력하기
		
		int[] arr = {10, 2, 4, 6, 2, 100, 15};
		int max = ff.getMax(arr);
		System.out.println(max);
		
		
	}

}
```
