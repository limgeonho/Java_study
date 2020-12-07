```java
package day29.quiz;

import java.awt.BorderLayout;
import java.awt.FlowLayout;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.FileWriter;
import java.text.SimpleDateFormat;
import java.util.Calendar;
import java.util.Date;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JOptionPane;
import javax.swing.JPanel;
import javax.swing.JTextArea;
import javax.swing.JTextField;

//class MyButton extends JButton{
//	private String menuName;
//	private int price;
//	
//	MyButton(String menuName, int price){
//		this.menuName = menuName;
//		this.price = price;
//	}
//
//	MyButton(String menuName){
//		this.menuName = menuName;
//	}
//	
//	public String getMenuName() {
//		return menuName;
//	}
//
//	public void setMenuName(String menuName) {
//		this.menuName = menuName;
//	}
//
//	public int getPrice() {
//		return price;
//	}
//
//	public void setPrice(int price) {
//		this.price = price;
//	}
//	
//	
//	
//}
class TimeThread extends Thread{
	public String realTime;

	@Override
	public void run() {
		SimpleDateFormat format = new SimpleDateFormat("YYYY/MM/dd HH:mm:ss");
		
		while(true) {
			try {
				realTime = format.format(new Date());
//				System.out.println(realTime);
				
				Thread.sleep(1000);
				
			} catch (InterruptedException e) {
				e.printStackTrace();
			}
		}
	}
} 

public class Quiz01 extends JFrame {
	
	
	private JPanel northPanel = new JPanel();
	private JPanel southPanel = new JPanel();

	private JPanel westPanel = new JPanel();
	private JButton buttonSave = new JButton("저장하기");
	private JButton buttonLoad = new JButton("불러오기");
	private JButton buttonPay = new JButton("결제하기");
	private JTextArea textArea = new JTextArea();
	private JTextField textPayment = new JTextField();
	private JTextField timeField = new JTextField();
	

	SimpleDateFormat priceFormat = new SimpleDateFormat("HH:mm:ss");
	SimpleDateFormat saveFormat = new SimpleDateFormat("YYYYMMdd_HHmmss");
	SimpleDateFormat currentFormat = new SimpleDateFormat("YYYY/MM/dd HH:mm:ss");
	
	
	
	private JButton[] menus = {
						new JButton("아메리카노"),
						new JButton("카페라떼"),
						new JButton("카푸치노"),
						new JButton("바닐라라떼"),
						new JButton("캬라멜 마끼아또")
						};
 
	private int[] prices = {3000, 3500, 4000, 4500, 5000};

	int[] cnt = new int[5];
	
	ActionListener getPrice0 = new ActionListener() {
		
			@Override
			public void actionPerformed(ActionEvent e) {
					long time = System.currentTimeMillis();
					String realTime = priceFormat.format(time);
					String name = menus[0].getText();
					cnt[0]++;
					textArea.append(name+ " : " + prices[0] + "원  [" + realTime + "]\n");
					textPayment.setText("총 결제액 : " + String.valueOf(cnt[0]*prices[0] + cnt[1]*prices[1] + cnt[2]*prices[2] + cnt[3]*prices[3] + cnt[4]*prices[4]) + "원");
					}
		};
		
	ActionListener getPrice1 = new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {

					long time = System.currentTimeMillis();
					String realTime = priceFormat.format(time);
					String name = menus[1].getText();
					cnt[1]++;
					textArea.append(name+ " : " + prices[1] + "원  [" + realTime + "]\n");
					textPayment.setText("총 결제액 : " + String.valueOf(cnt[0]*prices[0] + cnt[1]*prices[1] + cnt[2]*prices[2] + cnt[3]*prices[3] + cnt[4]*prices[4]) + "원");					
					}
		};
		
	ActionListener getPrice2 = new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
					long time = System.currentTimeMillis();
					String realTime = priceFormat.format(time);
					String name = menus[2].getText();
					cnt[2]++;
					textArea.append(name+ " : " + prices[2] + "원  [" + realTime + "]\n");
					textPayment.setText("총 결제액 : " + String.valueOf(cnt[0]*prices[0] + cnt[1]*prices[1] + cnt[2]*prices[2] + cnt[3]*prices[3] + cnt[4]*prices[4]) + "원");
					
					}
		};
		
	ActionListener getPrice3 = new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
					long time = System.currentTimeMillis();
					String realTime = priceFormat.format(time);
					String name = menus[3].getText();
					cnt[3]++;
					textArea.append(name+ " : " + prices[3] + "원  [" + realTime + "]\n");
					textPayment.setText("총 결제액 : " + String.valueOf(cnt[0]*prices[0] + cnt[1]*prices[1] + cnt[2]*prices[2] + cnt[3]*prices[3] + cnt[4]*prices[4]) + "원");
					
					}
		};
		
	ActionListener getPrice4 = new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
					long time = System.currentTimeMillis();
					String realTime = priceFormat.format(time);
					String name = menus[4].getText();
					cnt[4]++;
					textArea.append(name+ " : " + prices[4] + "원  [" + realTime + "]\n");
					textPayment.setText("총 결제액 : " + String.valueOf(cnt[0]*prices[0] + cnt[1]*prices[1] + cnt[2]*prices[2] + cnt[3]*prices[3] + cnt[4]*prices[4]) + "원");
					
					}
		};

	
	
		
	private void initWestPanel() {
		
		westPanel.setLayout(new GridLayout(5,1));
		for(int i = 0; i < menus.length; i++) {
			westPanel.add(menus[i]);
			
		}
		menus[0].addActionListener(getPrice0);
		menus[1].addActionListener(getPrice1);
		menus[2].addActionListener(getPrice2);
		menus[3].addActionListener(getPrice3);
		menus[4].addActionListener(getPrice4);
		
		
	}
	
	private void initNorthPanel() {
		northPanel.setLayout(new FlowLayout());
		northPanel.add(buttonSave);
		northPanel.add(buttonLoad);
		northPanel.add(buttonPay);
		buttonSave.addActionListener(save);
		buttonPay.addActionListener(pay);
		
	}
	
	private void initSouthPanel() {
		southPanel.setLayout(new BorderLayout());
		southPanel.add(textPayment, BorderLayout.WEST);

		southPanel.add(timeField, BorderLayout.EAST);
		
		
	}

	///////////////////////////////////////////////////////////////////////////////////////////////////////////////
	ActionListener pay = new ActionListener() {
		
		@Override
		public void actionPerformed(ActionEvent e) {
			textArea.setText(null);
			textPayment.setText(null);
			for(int i = 0; i < cnt.length; i++) {
				cnt[i] = 0;
			}
			JOptionPane.showMessageDialog(Quiz01.this, "결제완료!!");
			
		}
	};
	
		
	ActionListener save = new ActionListener() {
		
		@Override
		public void actionPerformed(ActionEvent e) {
			
			
			FileWriter writer = null;
				try {
					long time = System.currentTimeMillis();
					String saveTime = saveFormat.format(time);
					writer = new FileWriter(saveTime + ".txt");
					String message = textArea.getText();
					String totalPrice = textPayment.getText();
					writer.write(message + totalPrice);
					JOptionPane.showMessageDialog(Quiz01.this, "저장완료!!");
					
				}catch(Exception e1) {
					e1.printStackTrace();
				}finally {
					try {
						if(null != writer) {
							writer.close();
						}
						}catch(Exception e2) {
							e2.printStackTrace();
						}
					}
					
		}
	};
	
	///////////////////////////////////////////////////////////////////////////////////////////////////////////////
	
	
	public Quiz01() {
		super("======== 카페 ========");
		TimeThread th = new TimeThread();
		th.start();
		
		timeField.setText(th.realTime);
		setSize(1200, 800);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		this.setLayout(new BorderLayout());
		
		initWestPanel();
		initNorthPanel();
		initSouthPanel();
	
		
		add(westPanel, BorderLayout.WEST);
		add(northPanel, BorderLayout.NORTH);
		add(southPanel, BorderLayout.SOUTH);
		add(textArea, BorderLayout.CENTER);
	
		setVisible(true);
	}
	
	public static void main(String[] args) {
		
		new Quiz01();
		
		
	}
}
```
