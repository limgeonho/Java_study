```java
package day27.quiz;

import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

/*
 * Quiz01
 * 	-> 2단.txt ~ 9단.txt 구구단 텍스트 파일 생성
 */
public class Quiz01 {
	public static void main(String[] args) {
		FileWriter[] writer = null;
		
		try {

			writer = new FileWriter[8]; 
			
			for(int i = 2; i < 10; i++) {
			writer[i-2] =  new FileWriter(i + "dan.txt");
			
				for(int j = 1; j < 10; j++) {
					writer[i-2].write(i + " X " + j + " = " + (i * j) + "\n");
				}
			}
			
		} catch (IOException e) {
			e.printStackTrace();
		}finally {
			
			for(int i = 0 ; i < writer.length; i++) {
				try {
					if(null != writer[i]) {
						writer[i].close();
					}
					
					} catch (IOException e) {
						e.printStackTrace();
				}
			}
		}
				
	}
}
=============================================================================================================
package day27.quiz;

import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.io.Reader;

/*
 * Quiz02
 *  -> 사용자에게 '단'을 입력 받아 해당 구구단 txt 파일을 열고, 
 *     그 내용을 jop으로 출력 
 */
import java.util.Scanner;

import javax.swing.JOptionPane;


public class Quiz02 {
	public static void main(String[] args) {
		FileReader reader = null;
		Scanner sc = null;
		
		try {
			int inputDan = (int)Integer.parseInt(JOptionPane.showInputDialog("단을 입력하세요"));

			reader = new FileReader(inputDan + "dan.txt");			

			sc = new Scanner(reader);
						
			while(sc.hasNext()) {
				System.out.println(sc.nextLine());
				}
			}
	
		 catch (IOException e) {
				e.printStackTrace();
			}
		 finally {
			 try {
				 if(null != reader) {
					 reader.close();
				 }
				 if(null != sc) {
					 sc.close();
				 }
				 } catch (IOException e) {
					e.printStackTrace();
				}
			 }
		 }
		
	}
  =============================================================================================================
  package day27.quiz;

import java.io.FileWriter;
import java.io.IOException;
import java.text.SimpleDateFormat;
import java.util.Date;

import javax.swing.JOptionPane;

/*
 * Quiz03 
 * 	-> 사용자에게 exit를 입력 받을 때까지 모든 문자열을 jop으로 입력 받고 
 *     exit를 입력 하면 YYYYMMdd_HHmmss.txt 형식으로 log 파일을 생성하여
 *     사용자가 입력한 모든 문자열 저장
 */
public class Quiz03 {
	public static void main(String[] args) {
		SimpleDateFormat format = new SimpleDateFormat ( "YYYYMMdd_HHmmss");
				
		Date time = new Date();
				
		String time1 = format.format(time);
	
		FileWriter writer = null;
		try {
				writer = new FileWriter(time1+ ".txt", true);
			
			while(true) {
				
				String message = JOptionPane.showInputDialog("문자열을 입력하세요.");
				
				if(message.equals("exit")) {
					JOptionPane.showMessageDialog(null, "종료 후 저장!!");
					break;
				}else {
					
					writer.append(message + "\n");
				}
			}
		
		} catch (IOException e) {
			e.printStackTrace();
		}
		finally {
			try {
			if(null != writer) {
				writer.close();
				}
				}catch (IOException e) {
					e.printStackTrace();
				}
			}
		}
		
	}
	
```
