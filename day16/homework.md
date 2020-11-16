```java
package day16.quiz;

class Unit { // 부모 클래스
	String name;
	int hp, att; // 체력, 공격력
	boolean alive; // true:아직 살아있음 (선택사항)
	
	public Unit() {}
	public Unit(String name) {
		this.name = name;
	}
	public Unit(String name, int hp, int att) {
		this.name = name;
		this.hp = hp;
		this.att = att;
		this.alive = true;
	}
	public void attack(Unit enemy) {
		
	}
	public boolean isAlive(int hp) {
		if(hp <= 0) {
			this.alive = false;
		}
		return alive;
	}
}
class Sniper extends Unit { // 자식 클래스
	// 객체 생성되면, 자동으로 name은 "저격수", hp는 400, att는 100
	Sniper(){
		name = "저격수";
		hp = 400;
		att = 100;
		alive = true;
	}
	@Override
	public void attack(Unit enemy) {
		// 1. 10% 확률로 헤드샷 (상대 즉사)
		if(isAlive(hp) == false) {
			return;
		}else if(Math.random() < 0.1) {
			enemy.hp = 0;
			isAlive(hp);
		}else {
		// 2. 나머지 확률로 평타(일반 공격, 상대 hp를 100만큼 깎는다.)
			enemy.hp -=100;
			isAlive(hp);
		}
	}
	public String toString() {
		return "유닛 : " + this.name + "\nhp : " + this.hp;
	}
}

class Tank extends Unit {
	// 객체 생성되면, 자동으로 name은 "탱크", hp는 4000, att는 50
	Tank(){
		name = "탱크";
		hp = 4000;
		att = 50;
		alive = true;
	}
	@Override
	public void attack(Unit enemy) {
		// 1. 30% 확률로 상대의 hp 30% 감소
		if(isAlive(hp) == false) {
			return;
		}else if(Math.random() < 0.3) {
			enemy.hp -= (enemy.hp * 30) / 100;
			isAlive(hp);
		}else {
		// 2. 나머지 확률로 평타(일반 공격, 상대 hp를 50만큼 깎는다.)
			enemy.hp -= 50;
			isAlive(hp);
			}
		}
	public String toString() {
		return "유닛 : " + this.name + "\nhp : " + this.hp;
		}
	}


public class Quiz02 {
	/*
	 * < Sniper VS Tank >
	 * - 저격수, 탱크 두 캐릭터 중 아무거나 랜덤하게 2개 생성
	 *   (탱크 vs 탱크, 저 vs 탱, 저 vs 저)
	 * - 두 객체가 서로 죽을 때까지 서로 공격을 반복
	 * - 첫번째, 혹은 두번째 플레이어가 이겼는지 마지막 승자 출력! 
	 *  e.g. 플레이어1(탱크)의 승리!
	 */
	public static void main(String[] args) {
		// 두 타입의 객체를 랜덤하게 2개 생성
		// 무한 반복문을 사용하여 둘 중 하나가 죽을 때까지 서로를 공격
		// 단, 죽은 객체가 공격하면 안됨
		
		Unit u1 = Math.random() > 0.5 ? new Sniper() : new Tank(); 
		Unit u2 = Math.random() > 0.5 ? new Sniper() : new Tank(); 
		
		while(true) {
			if(u1.hp > 0 && u2.hp > 0) {
				u1.attack(u2);
				u2.attack(u1);
			}else {
				break;
			}
			
		}
		System.out.println(u1.toString());
		System.out.println(u2.toString());
		
		System.out.println(u1.hp <= 0 ? "플레이어2 WIN!!" : "플레이어1 WIN!!");
	
//		while(true) {
//			u1.attack(u2);
//			if(u2.alive == false) {
//				System.out.println("플레이어1 WIN!!");
//				System.out.println(u1.toString());
//				System.out.println(u2.toString());
//				break;
//			}
//			u2.attack(u1);
//			if(u1.alive == false) {
//				System.out.println("플레이어2 WIN!!");
//				System.out.println(u1.toString());
//				System.out.println(u2.toString());
//				break;
//			}
//		}
	
	}
}		
```
