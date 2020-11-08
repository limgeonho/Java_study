```java
package day10.quiz;

import java.util.Scanner;

public class PokemonTest {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		
		Pokemon[] pokemon = new Pokemon[5];
		pokemon[0] = new Pokemon();
		pokemon[1] = new Pokemon();
		pokemon[2] = new Pokemon();
		pokemon[3] = new Pokemon();
		pokemon[4] = new Pokemon();
		
		
		while(true) {
			System.out.println("======= 메뉴 ======="
					+ "\n"
					+ "\n메뉴를 선택하세요 : "
					+ "\n1. 포켓몬 등록"
					+ "\n2. 모든 포켓몬 보기"
					+ "\n3. 레벨업"
					+ "\n4. 종료");
						
			int num = sc.nextInt();
		switch (num) {
			case 1:
				for(int i = 0; i < pokemon.length; i++) {
					pokemon[i].register();
				}
				break;
				
			case 2: 
				for(int i = 0; i< pokemon.length; i++) {
					pokemon[i].printInfo();
				}
				break;
				
			case 3: 
				System.out.println("======= 레벨업 ^>^ ======="
						+ "\n"
						+ "\n방법을 선택하세요"
						+ "\n1. 모든 포켓몬 레벨업"
						+ "\n2. 인덱스 선택 포켓몬 레벨업"
						+ "\n3. 이름 선택 포켓몬 레벨업");
								
				int select = sc.nextInt();
				
				switch (select) {
					case 1:
						System.out.println("모든 포켓몬 레벨업 ~!!!!!!!");
						
						for(int i = 0; i< pokemon.length; i ++) {
							pokemon[i].lvUp();
						}
						break;
						// 공격력이랑 체력도 올라가야함
					case 2:
						System.out.println("인덱스를 입력하세요 : ");
						
						int idx = sc.nextInt();
						pokemon[idx].lvUp();
						break;
	
					case 3: 
						System.out.println("레벨업 하고 싶은 포켓몬 이름 입력 : ");
						int noPokeCnt = 0;
						String selectName = sc.next();
						
						for(Pokemon e : pokemon) {
							if(e.name.contains(selectName)) {
								System.out.println(selectName + "레벨업 ~");
								e.lvUp();
							}else {
								noPokeCnt++;
							}
						}
						if(noPokeCnt == 5) {
							System.out.println(selectName + "은/는 미등록 포켓몬입니다.");
						}
						break;
					}
			case 4: 
				System.out.println("종료되었습니다.");
				return;
			}
		
		}
		
	}

}

```
