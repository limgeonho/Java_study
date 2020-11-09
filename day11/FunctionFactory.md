```java
package day11.quiz;

public class FunctionFactory {
	
	String strGugudan(int n) {
		String a = "";
		for(int i = 1; i < 10; i++) {
			a += n + " X " + i + " = " + n * i +"\n";
		}
		return a;
	}
	
	
	void printGugudan(int n) {
		for(int i = 1; i < 10; i++ ) {
			System.out.println(n + " X " + i + " = " + n*i);
		}
		return;

	}
	
	
	int getAverage(int kor, int eng, int math) {
		return (kor + eng + math) / 3;
	}
	
	
	String getRandomPokemon() {
		String[] pokemon = {"피카츄", "라이츄", "파이리", "꼬부기"};
		return pokemon[(int)((Math.random() * 4))]; 
	}
	
	
	int getMax(int[] arr) {
		int max = arr[0];
		for(int i = 1; i <arr.length; i++) {
			if(max < arr[i]) {
				max = arr[i];
			} 
		}
		return max;
	}
		
}

```
