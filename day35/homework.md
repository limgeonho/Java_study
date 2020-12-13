```java
package day35.quiz;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.Scanner;


public class Quiz01 {
	private static final String URL = "jdbc:mysql://127.0.0.1/testdb";
	private static final String ID = "testdba";
	private static final String PASSWORD = "test1234";
	private Connection connection;
	private PreparedStatement preparedStatement;
	private ResultSet resultSet;
	
	public Quiz01() throws SQLException {
		Scanner scan = new Scanner(System.in);
		
		String sql = "CREATE TABLE pokemonQuiz(\r\n" + 
				"	name VARCHAR(40) PRIMARY KEY NOT NULL,\r\n" + 
				"	level INT(5) NOT NULL,\r\n" + 
				"	ap INT(6),\r\n" + 
				"	hp INT(6)\r\n" + 
				");";
		preparedStatement = connection.prepareStatement(sql);
		
		preparedStatement.execute();
		System.out.println("pokemonQuiz 테이블 저장완료!");
		loop:while(true) {
			System.out.println("1. 포켓몬 등록하기"
						   + "\n2. 포켓몬 조회하기"
						   + "\n3. 종료하기");
			
			int select = scan.nextInt();
			switch (select) {
				case 1:
					try {
					connection = DriverManager.getConnection(URL, ID, PASSWORD);
					System.out.println("[포켓몬 등록]");
					System.out.println("이름을 입력하세요.");
					String name = scan.next();
					System.out.println("레벨을 입력하세요.");
					int level = scan.nextInt();
					
					String setPokemon = "INSERT INTO pokemonQuiz VALUES(" + "\'" + name + "\'" + ", " + level + ", " + level / 2 + ", " + level * 100 + ")";
					
					preparedStatement = connection.prepareStatement(setPokemon);
					
					preparedStatement.execute();
					
					System.out.println("pokemon" + " [" + name + "] " + "정보 저장완료!");
					
					} catch (SQLException e) {
						e.printStackTrace();
					} finally {
						try {
							if(preparedStatement != null)
								preparedStatement.close
								();
							if(connection != null)
								connection.close();
						} catch(SQLException e) {
							e.printStackTrace();
						}
					}
					break;
					
				case 2:
					try {
						connection = DriverManager.getConnection(URL, ID, PASSWORD);
						System.out.println("조회할 포켓몬을 입력하세요.");
						String checkPokemon = scan.next();
						
						String searchPokemon = "SELECT level, ap, hp FROM pokemonQuiz WHERE name = \'" + checkPokemon + "\'";
						preparedStatement = connection.prepareStatement(searchPokemon);
						resultSet = preparedStatement.executeQuery();
						
						while(resultSet.next()) {
							
							int level2 = resultSet.getInt(1);
							int ap2 = resultSet.getInt(2);
							int hp2 = resultSet.getInt(3);
													
							System.out.println("[" + checkPokemon + "] LV : " + level2 + " , AP : " + ap2 + " , HP : " + hp2);
						} 
						System.out.println("미등록 포켓몬입니다!");
					}catch (SQLException e) {
						e.printStackTrace();
					} finally {
						try {
							if(preparedStatement != null)
								preparedStatement.close();
							if(connection != null)
								connection.close();
						} catch(SQLException e) {
							e.printStackTrace();
						}
					
					}
					break;
					
				case 3:
					System.out.println("[프로그램 종료!]");
					break loop;	
					
				default:
					System.out.println("잘못 입력하였습니다.");
					break;
					
				}
			}
		}	

	public static void main(String[] args) {
		try {
			new Quiz01();
		} catch(Exception e) {e.printStackTrace();}
	}
}
===================================================================================================================
package day35.quiz;

import java.awt.BorderLayout;
import java.awt.FlowLayout;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextField;

public class Quiz02 extends JFrame{
	private JLabel label1 = new JLabel("이름");
	private JLabel label2 = new JLabel("레벨");
	private JLabel label3 = new JLabel("체력");
	private JLabel label4 = new JLabel("공격력");
	
	private JTextField textField1 = new JTextField();
	private JTextField textField2 = new JTextField();
	private JTextField textField3 = new JTextField();
	private JTextField textField4 = new JTextField();
	
	private JPanel panel1 = new JPanel();
	private JPanel panel2 = new JPanel();
	private JPanel panel3 = new JPanel();
	private JPanel panel4 = new JPanel();
	private JPanel panel5 = new JPanel();
	
	private JButton button = new JButton("계산");
	
	ActionListener listener = new ActionListener() {
		
		@Override
		public void actionPerformed(ActionEvent e) {
			int hp = Integer.parseInt(textField2.getText()) * 100; 
			int ap = Integer.parseInt(textField2.getText()) / 2;
			textField3.setText(String.valueOf(hp));
			textField4.setText(String.valueOf(ap));
		}
	};
	
	private void initNamePanel() {
		panel1.setLayout(new GridLayout(1, 2));
		panel1.add(label1);
		panel1.add(textField1);
	}
	
	private void initLevelPanel() {
		panel2.setLayout(new GridLayout(1, 2));
		panel2.add(label2);
		panel2.add(textField2);
	}

	private void initCheck() {
		panel5.setLayout(new BorderLayout());
		panel5.add(button, BorderLayout.EAST);
		button.addActionListener(listener);
	}

	private void initHpPanel() {
		panel3.setLayout(new GridLayout(1, 2));
		panel3.add(label3);
		panel3.add(textField3);
	}
	
	private void initApPanel() {
		panel4.setLayout(new GridLayout(1, 2));
		panel4.add(label4);
		panel4.add(textField4);
	}
	
	Quiz02() {
		super("포켓몬 GUI!!");
		
		setSize(200, 200);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setLayout(new GridLayout(5, 1));
		
		initNamePanel();
		initLevelPanel();
		initCheck();
		initHpPanel();
		initApPanel();
		
		add(panel1);
		add(panel2);
		add(panel5);
		add(panel3);
		add(panel4);
		
		setVisible(true);
		
	}
	
	public static void main(String[] args) {
		new Quiz02();
	}
}


```
