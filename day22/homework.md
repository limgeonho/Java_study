```java
package day22.quiz;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Scanner;
import java.util.Set;
import java.util.Map.Entry;

class Word{
	String word = "";
	String meaning = "";
	Word(){
		
	} 
//	Word(String word, String Maening){
//		this.word = word;
//		this.meaning = meaning;
//	}
	
	
}



public class Quiz02 {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		HashMap<String, String> wordList = new HashMap<>();
		
		String word, meaning;
		String find;
		String mean;
		String question, answer;
		
		int num = 0;
		
		String menu = "1.단어추가\n"
					+ "2.단어검색\n"
					+ "3.모든 단어 보기\n"
					+ "4.퀴즈 풀기\n"
					+ "0.종료";
	
		
		loop : while(true) {
			
			System.out.println(menu);
			int select = sc.nextInt();
			
			switch (select) {
				case 1:
						System.out.println("====단어 추가====");	
						
						System.out.println("영단어를 입력하세요.");
						word = sc.next();
						System.out.println("뜻을 입력하세요.");
						meaning = sc.next();
						
						wordList.put(word, meaning);
						
					break;
				case 2:
						System.out.println("====단어 검색====");
						
						System.out.println("검색할 단어를 입력하세요.");
						find = sc.next();
						
						if(!wordList.containsKey(find)) {
							System.out.println("미등록 단어입니다.");
						}else{
							mean = wordList.get(find);
							System.out.println(find + "의 뜻은  " + mean + "입니다.");
	
						}	
						
					break;
				case 3:
						System.out.println("====모든 단어 보기====");
						
						for(Entry<String, String> en : wordList.entrySet()) {
							System.out.println(en.getKey());
							System.out.println(en.getValue());
							System.out.println("=================");
						}
						
					break;
				case 4:
					
					
//						System.out.println("====퀴즈 풀기====");
//						num = (int)(Math.random()*wordList.size());
//						Set<String> keyWord = wordList.keySet();
//						Iterator<String> iter = keyWord.iterator();
//						
//						System.out.println(keyWord);
//						Word[] wTest = new Word[wordList.size()];
//						for(int i = 0; i< wordList.size(); i++) {
//							while(iter.hasNext()) {
//								wTest[i].word = iter.next();
//								wTest[i].meaning = wordList.get(keyWord);
//							}
//							
//						}
//						 
//						question = wTest[num].meaning; 
//						System.out.println(question + " 은 영어로?");
//						answer = sc.next();
//						
//						if(answer.equals(wTest[num].word)) {
//							System.out.println("정답!!!");
//						}else {
//							System.out.println("땡!!!");
//						}
						
//					=> 다시 해봐야..
						
						
						
					break;
				case 0:
						System.out.println("====종료====");
						
					break loop;
		
				default:
					System.out.println("잘못 입력하였습니다.");
					break;
			}
		}
		
	}
	
}

```
