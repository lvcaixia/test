/*登陆界面的实现*/
package selfstudy;

import selfstudy.Study;

import java.awt.Button;//import java.awt.*;

import java.awt.Frame;

import java.awt.Label;

import java.awt.TextField;

import java.awt.event.ActionEvent;

import java.awt.event.ActionListener;

import java.awt.event.WindowAdapter;

import java.awt.event.WindowEvent;

import java.sql.Connection;

import java.sql.DriverManager;

import java.sql.ResultSet;

import java.sql.Statement;

public class loading extends Frame implements ActionListener{

	private Label l1,l2;
	
	private TextField t1,t2;
	
	private	Button b1,b2,b3;
	
	public loading(){
	
		l1=new Label("登录名");
		
		l2=new Label("密码 ");
		
		t1=new TextField(20);
		
		t2=new TextField(20); 
		
		b1=new Button("登陆");
		
		b2=new Button("注册");
		
		b3=new Button("管理员登陆");
		
		b1.addActionListener(this);        //添加按钮监听器
		
		b2.addActionListener(this);
		
		b3.addActionListener(this);
		
		setLayout(null);                   //将默认的布局管理器设置为空，自定义布局
		
		add(l1);
		
		l1.setBounds(150, 120, 40,20);
		
		add(t1);
		
		t1.setBounds(200, 120, 150, 20);
		
		add(l2);
		
		l2.setBounds(150, 160, 40, 20);
		
		add(t2);
		
		t2.setBounds(200, 160, 150, 20);
		
		add(b1);
		
		b1.setBounds(150,200,50,50);
		
		add(b2);
		
		b2.setBounds(220, 200, 50,50);
		
		add(b3);
		
		b3.setBounds(300, 200, 80, 50);
		
	}
	
	public void actionPerformed(ActionEvent e1) {
	
		// TODO 自动生成的方法存根
		
		if(e1.getSource()==b3)
		
		{try
		
		{
			Class.forName( "sun.jdbc.odbc.JdbcOdbcDriver");//引入桥接连接方法
			
			String source = "jdbc:odbc:testDB";
			
			Connection con = DriverManager.getConnection(source);//创建连接对象
			
			Statement  stmt = con.createStatement() ;//创建指令
			
			String sql = "SELECT ID,pass FROM ADMIN";
			
			ResultSet rs = stmt.executeQuery(sql);//创建结果集
			
			while(rs.next()){
			
				String id=rs.getString(1);//得到数据库中的ID，赋值给字符串id
				
				String pass=rs.getString(2);//得到数据库中的pass，赋值给字符串pass
				
				String user,password;
				
				user=t1.getText();//得到用户输入的用户名
				
				password=t2.getText();//得到用户输入的密码
				
				if(user.equals(id)&&password.equals(pass)){//密码的匹配
				
					adminmanage AAA=new adminmanage();
					
					AAA.setTitle("我要上自习");//设置窗体的名称
					
					AAA.setVisible(true);//窗体显示可见
					
					AAA.setSize(500,500);//设置窗体大小
					
					AAA.addWindowListener(new WindowAdapter()
			{//添加窗体的窗口的监听器，采用适配器
			
				public void windowClosing(WindowEvent windowevent) {
				
					System.exit(0);
					
					}
					});
					this.setVisible(false);
					
		}
			}
		}
		catch(Exception e)//异常处理
		
		{e.printStackTrace();}
		
		}
		
		if(e1.getSource()==b1)
		{
			try
			
			{
				Class.forName( "sun.jdbc.odbc.JdbcOdbcDriver");//引入桥接连接方法
				
				String source = "jdbc:odbc:testDB";
				
				Connection con = DriverManager.getConnection(source);//创建连接对象
				
				Statement  stmt = con.createStatement() ;//创建指令
				
				String sql = "SELECT ID,pass FROM Name";
				
				ResultSet rs = stmt.executeQuery(sql);//创建结果集
				
				while(rs.next()){
				
					String id=rs.getString(1);//得到数据库中的ID，赋值给字符串id
					
					String pass=rs.getString(2);//得到数据库中的pass，赋值给字符串pass
					
					String user,password;
					
					user=t1.getText();//得到用户输入的用户名
					
					password=t2.getText();//得到用户输入的密码
					
					if(user.equals(id)&&password.equals(pass)){//密码的匹配
					
						Study AAA=new Study();
						
						AAA.setTitle("我要上自习");//设置窗体的名称
						
						AAA.setVisible(true);//窗体显示可见
						
						AAA.setSize(500,500);//设置窗体大小
						
						AAA.addWindowListener(new WindowAdapter()
						
						{//添加窗体的窗口的监听器，采用适配器
						
					public void windowClosing(WindowEvent windowevent) {
					
						System.exit(0);
						
						}
						});
						
						this.setVisible(false);
						
				}
			}
			}
			catch(Exception e)//异常处理
			
			{e.printStackTrace();}
			
			}
			
		if(e1.getSource()==b2)
		
		{
			Register RRR=new Register();
			
			RRR.setTitle("注册");
			
			RRR.setVisible(true);
			
			RRR.setSize(500, 500);
			
			RRR.addWindowListener(new WindowAdapter() {//添加窗体的窗口的监听器，采用适配器
			
				public void windowClosing(WindowEvent windowevent) {
				
					System.exit(0);
					}
					});
			this.setVisible(false);
			
		}
		
	}
	public static void main(String[] args) {
	
		// TODO 自动生成的方法存根
		
		loading TEST=new loading();
		
		TEST.addWindowListener(new WindowAdapter() {
		
			public void windowClosing(WindowEvent windowevent) {
			
			System.exit(0);
			
			}
			});
		TEST.setTitle("登陆");
		
		TEST.setSize(500,500);
		
		TEST.setVisible(true);
		
	}
}




/*_______________________________________________________________________________






*/
package selfstudy;

import java.awt.*;

import java.awt.event.ActionEvent;

import java.awt.event.ActionListener;

import java.awt.event.WindowAdapter;

import java.awt.event.WindowEvent;

import java.sql.PreparedStatement;

import java.sql.ResultSet;

import java.sql.Statement;

import java.sql.Connection;

import java.sql.DriverManager;

public class Register extends Frame implements ActionListener {

	private Label l0,l1,l2;
	
	private TextField t1,t2;
	
	private Button b1,b2;
	
	private	String registername,registerpass;
	
	public Register(){
		l0=new Label("用户注册");
		
		l1=new Label("请输入您要注册的用户名");
		
		l2=new Label("请输入您的密码");
		
		t1=new TextField(20);
		
		t2=new TextField(20);
		
		b1=new Button("注册");
		
		b2=new Button("返回登陆");
		
		registername=new String();
		
		registerpass=new String();
		
		setLayout(null);
		
		add(l0);
		
		l0.setBounds(200, 20, 50, 50);
		
		add(l1);
		
		l1.setBounds(70,100,150,30);
		
		add(t1);
		
		t1.setBounds(220, 100, 100, 30);
		
		add(l2);
		
		l2.setBounds(70, 150, 100, 30);
		
		add(t2);
		
		t2.setBounds(220, 150, 100, 30);
		
		add(b1);
		
		b1.setBounds(180, 200, 40, 40);
		
		b1.addActionListener(this);
		
		add(b2);
		
		b2.setBounds(300, 200, 60, 40);
		
		b2.addActionListener(this);
		
	}
	public void actionPerformed(ActionEvent e) {
	
		// TODO 自动生成的方法存根
		
		if(e.getSource()==b1)
		
		{				
			String strUpdate="INSERT INTO Name(ID,pass)VALUES(?,?)";
			
			registername=t1.getText();
			
			registerpass=t2.getText();
			
			System.out.println(registername);
			
			System.out.println(registerpass);
			try
			
			{
				Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
				
				String source = "jdbc:odbc:testDB";
				
				Connection con=DriverManager.getConnection(source);
				
				PreparedStatement stmt=con.prepareStatement(strUpdate);
				
				String strID=registername;
				
				String strpass=registerpass;
				
				stmt.setString(1, strID);
				
				stmt.setString(2, strpass);
				
				stmt.executeUpdate();
				
			}
			catch(Exception e1)
			
			{e1.printStackTrace();}
			
		}
		
		if(e.getSource()==b2)
		{
		
			loading LLL=new loading();
			
			LLL.setTitle("注册");
			
			LLL.setVisible(true);
			
			LLL.setSize(500, 500);
			
			LLL.addWindowListener(new WindowAdapter() {//添加窗体的窗口的监听器，采用适配器
			
				public void windowClosing(WindowEvent windowevent) {
				
					System.exit(0);
					
					}
					});
					
			this.setVisible(false);}
			

		}
	public static void main(String[] args) {
	
	
		// TODO 自动生成的方法存根
		Register AAA=new Register();
		
		AAA.addWindowListener(new WindowAdapter() {
		
			public void windowClosing(WindowEvent windowevent) {
			
			System.exit(0);
			}
			
			});
		AAA.setTitle("注册");
		
		AAA.setVisible(true);
		
		AAA.setSize(500, 500);
		
	}

}



/*_______________________________________________________________________________________



*/
package selfstudy;

import java.awt.*;

import java.awt.event.ActionEvent;

import java.awt.event.ActionListener;

import java.awt.event.WindowAdapter;

import java.awt.event.WindowEvent;

import java.sql.PreparedStatement;

import java.sql.Connection;

import java.sql.DriverManager;

public class adminmanage extends Frame implements ActionListener {

	private Label l0,l1,l2,l3,l4;
	
	private TextField t1,t2,t3,t4;
	
	private Button b1,b2;
	
	private	String freshname,freshtime,freshdate,freshcontainer;
	
	public adminmanage(){
	
		l0=new Label("教室管理");
		
		l1=new Label("新增空间闲教室名称");
		
		l2=new Label("教室空闲时间");
		
		l3=new Label("教室空闲日期");
		
		l4=new Label("教室的容量");
		
		t1=new TextField(20);
		
		t2=new TextField(20);
		
		t3=new TextField(20);
		
		t4=new TextField(20);
		
		b1=new Button("确认添加");
		
		b2=new Button("返回登陆");
		
		freshname=new String();
		
		freshtime=new String();
		
		freshdate=new String();
		
		freshcontainer=new String();
		
		setLayout(null);
		
		add(l0);
		
		l0.setBounds(200, 20, 50, 50);
		
		add(l1);
		
		l1.setBounds(70,100,150,30);
		
		add(t1);
		
		t1.setBounds(220, 100, 100, 30);
		
		add(l2);
		
		l2.setBounds(70, 150, 100, 30);
		
		add(t2);
		
		t2.setBounds(220, 150, 100, 30);
		
		add(l3);
		l3.setBounds(70, 200, 100, 30);
		
		add(t3);
		
		t3.setBounds(220, 200, 100, 30);
		
		add(l4);
		l4.setBounds(70, 250, 100, 30);
		
		add(t4);
		
		t4.setBounds(220, 250, 100, 30);
		
		add(b1);
		
		b1.setBounds(180, 300, 60, 40);
		
		b1.addActionListener(this);
		
		add(b2);
		
		b2.setBounds(300, 300, 60, 40);
		
		b2.addActionListener(this);
		
	}
	public void actionPerformed(ActionEvent e) {
	
		// TODO 自动生成的方法存根
		
		{				
			String strUpdate="INSERT INTO people(name,time,date,container) VALUES (?,?,?,?)";
			
			freshname=t1.getText();
			
			freshtime=t2.getText();
			
			freshdate=t3.getText();
			freshcontainer=t4.getText();
			
			System.out.println(freshname);
			
			System.out.println(freshtime);
			
			try
			{
				Class.forName("sun.jdbc.odbc.JdbcOdbcDriver");
				
				String source = "jdbc:odbc:testDDBB";
				
				Connection con=DriverManager.getConnection(source);
				
				PreparedStatement stmt=con.prepareStatement(strUpdate);
				
				String strname=freshname;
				
				String strtime=freshtime;
				
				String strcontainer=freshcontainer;
				
				stmt.setString(1, strname);
				
				stmt.setString(2, strtime);
				
				stmt.setString(3, strdate);
				
				stmt.setString(4, strcontainer);
				
				stmt.executeUpdate();
			}
			catch(Exception e1)
			{e1.printStackTrace();}
		}
		if(e.getSource()==b2)
		{
			loading LLL=new loading();
			
			LLL.setTitle("登陆");
			
			LLL.setVisible(true);
			
			LLL.setSize(500, 500);
			
			LLL.addWindowListener(new WindowAdapter() {//添加窗体的窗口的监听器，采用适配器
			
				public void windowClosing(WindowEvent windowevent) {
				
					System.exit(0);
					
					}
					});
			this.setVisible(false);}
			

		}
	public static void main(String[] args) {
	
		// TODO 自动生成的方法存根
		
		adminmanage AAA=new adminmanage();
		{
			public void windowClosing(WindowEvent windowevent) {
			
			System.exit(0);
			}
			
			});
		AAA.setTitle("教室管理");
		
		AAA.setVisible(true);
		
		AAA.setSize(500, 500);
		
	}

}


/*____________________________________________________________________________________


*/

package selfstudy;

import java.awt.Choice;

import java.awt.Color;

import java.awt.Frame;

import java.awt.event.ItemEvent;

import java.awt.event.ItemListener;


public class choose extends Frame implements ItemListener{

	public  static Choice choosedate;
	
	public static Choice choosetime;
	
	public static String choose1;//将choose中用户选定的内容存放在静态数据choose中
	
	public static String choose2;//同上
	
	public choose()
	{
	
	choosedate =new Choice();
	add(choosedate);
	
	choosedate.setBackground(Color.lightGray);
	
	choosedate.addItem("  ");
	
	choosedate.addItem("周一");//添加choice中内容
	
	choosedate.addItem("周二");
	
	choosedate.addItem("周三");
	
	choosedate.addItem("周四");
	
	choosedate.addItem("周五");
	
	choosedate.addItem("周六");
	
	choosedate.addItem("周日");
	
	choosedate.addItemListener(this);
	
	choosetime =new Choice();
	
	add(choosetime);
	choosetime.setBackground(Color.lightGray);
	
	choosetime.addItem("          ");
	
	choosetime.addItem("7:50~9:25");
	
	choosetime.addItem("9:25~11:15");
	
	choosetime.addItem("11:15~12:00");
	
	choosetime.addItem("12:00~13:30");
	
	
	choosetime.addItem("13:30~15:05");
	
	
	
	choosetime.addItem("15:05~15:55");
	choosetime.addItem("15:55~17:40");
	
	choosetime.addItem("17:40~19:00");
	
	choosetime.addItem("19:00~21:25");
	
	choosetime.addItem("21:30~22:30");
	
	choosetime.addItemListener(this);
	}
	
	
	public void itemStateChanged(ItemEvent e1) {
	
		// TODO 自动生成的方法存根
		if(e1.getSource()==choosedate)
		
		{
			Choice temp1=(Choice)e1.getSource();
			
			choose1 = temp1.getSelectedItem();//将用户选择的日期赋值到choose1中
			
		}
		
		if(e1.getSource()==choosetime)
		
		{//String choose2=choosetime.getSelectedItem();
		
			Choice temp2=(Choice)e1.getSource();
			
			choose2=temp2.getSelectedItem();//将用户选定的时间段赋值到choose2
			
		}
	}


	public static void main(String[] args) {
	
		// TODO 自动生成的方法存根
		
		choose ch1=new choose();
		
	}
}




/*___________________________________________________________________________________


*/

package selfstudy;
import selfstudy.choose;

import java.awt.Button;

import java.awt.Color;

import java.awt.Font;

import java.awt.Frame;


import java.awt.GridLayout;

import java.awt.Label;


import java.awt.Panel;

import java.awt.TextArea;

import java.awt.event.ActionEvent;

import java.awt.event.ActionListener;

import java.awt.event.WindowAdapter;

import java.awt.event.WindowEvent;

import java.sql.Connection;

import java.sql.DriverManager;

import java.sql.ResultSet;

import java.sql.Statement;
public class Study extends Frame implements ActionListener {

	private Button btn;
	
	private TextArea showresult;
	
	private Panel studypanel; 
	
	private Label l0,l1,l2,l3;
	
	public Study()
	
	{
		choose ch=new choose();
		
		studypanel =new Panel();
		
		btn =new Button();
		
		btn=new Button(String.valueOf("inquire"));//给按钮加上名称
		
		
		btn.addActionListener(this);
		
		l0=new Label("自习室查询");
		
		l0.setBackground(Color.orange);//设置label l0的背景色为橘黄色
		
		l0.setFont(new Font("serif",Font.PLAIN,20));//设置l0的字体为宋体，字号大小为20
		
		l1= new Label("您选择的星期为");
		
		l1.setBackground(Color.orange);
		
		l2=new Label("您选择的时间是");
		
		l2.setBackground(Color.orange);
		
		setLayout(null);//将默认的布局管理器设置为空，采用用户自定义方式布局
		
		add(l0);
		l0.setBounds(240, 50, 110, 40);//设置awt组件的在窗体中的位置和自身的大小
		
		add(l1);
		
		l1.setBounds(70, 120, 90,20);
		
		add(ch.choosedate);
		
		ch.choosedate.setBounds(230, 120, 130, 130);
		
		add(l2);
		
		l2.setBounds(70, 160, 90, 20);
		
		add(ch.choosetime);
		
		ch.choosetime.setBounds(230, 160, 130, 130);
		
		add(studypanel);
		
		studypanel.setBounds(230, 200, 120, 40);
		
		studypanel.setLayout(new GridLayout(1,1));//设置面板的布局为网格状布局
		
		studypanel.add(btn);
		
		l3=new Label("空闲的教室有：");
		
		l3.setBackground(Color.lightGray);
		
		l3.setFont(new Font("serif",Font.PLAIN,20));
		
		add(l3);
		
		l3.setBounds(70,250, 150, 30);
		
		showresult=new TextArea();
		
		add(showresult);
		
		showresult.setBounds(70, 300, 350, 200);
		
	}
	public void actionPerformed(ActionEvent e) {
	
		// TODO 自动生成的方法存根
		
		if(e.getSource()==btn)
		{	
			try
			{
				Class.forName( "sun.jdbc.odbc.JdbcOdbcDriver");//创建桥接方式，ACCESS桥接方式
				
				String source = "jdbc:odbc:testDDBB";
				
				Connection con = DriverManager.getConnection(source);//创建连接对象
				
				Statement  stmt = con.createStatement() ;//创建指令
				
				String sql = "SELECT name,container,time,date FROM people";
				
				ResultSet rs = stmt.executeQuery(sql);//创建结果集
				
				while(rs.next())
				
				{
					String name1=rs.getString(1);//得到数据库中name
					
					String container=rs.getString(2);//得到教室容量
					
					String time1=rs.getString(3);//得到教室的时间
					
					String date1=rs.getString(4);//得到教室的日期
					if(choose.choose1.equals(date1)&&choose.choose2.equals(time1))//用户选择的日期和时间与数据库中的数据就行比较
					
					showresult.append(name1+"       
					"+"教室的容量为"+container+"\r\n");//在文本区域中输入空闲的教室的名字和教室的容量，然后换行
					showresult.setFont(new Font("serif",Font.PLAIN,20));
					
					
					System.out.println(name1);
					
					System.out.println(container);
					
				}
			}
			catch(Exception e2)
			
			{e2.printStackTrace();}
			
			}
		}
	public static void main(String[] args) {
	
		// TODO 自动生成的方法存根
		Study inquireroom = new Study();
		
		inquireroom.addWindowListener(new WindowAdapter() {
		
			public void windowClosing(WindowEvent windowevent) {
			
			System.exit(0);
			}
			});
		inquireroom.setTitle("我要上自习");
		
		inquireroom.setSize(500,550);	
		
		inquireroom.setVisible(true);
		
	}
}

