```java
//		1. Scanner를 사용하여 6개의 데이터를 입력 받고, 이들을 nums 배열에 저장
		Scanner sc = new Scanner(System.in);
		
		nums[0] = sc.nextInt();
		nums[1] = sc.nextInt();
		nums[2] = sc.nextInt();
		nums[3] = sc.nextInt();
		nums[4] = sc.nextInt();
		nums[5] = sc.nextInt();
//		2. 입력 받은 값 중, 20 이상 100 이하인 원소만 출력
		
		for(int e : nums) {
			if(e >= 20 && e<= 100) {
				System.out.println("20 이상 100 이하인 원소 : " + e);
			}
		}
```
