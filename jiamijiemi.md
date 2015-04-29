import java.awt.*;
import java.awt.event.*;
import java.io.*;
import javax.swing.*;
public class key extends JFrame {
int shu1;
JLabel jl1, jl2;
String cc;
JButton queding, xuanz, jiami, jiemi;
JTextField lujin, key;
JTextArea nr;
JRadioButton qu, xie;
ButtonGroup fz;
File f;
public key() {
   Container c = getContentPane();
   JPanel jp1 = new JPanel();
   jl1 = new JLabel("输入路径");
   lujin = new JTextField(15);
   xuanz = new JButton("选择");
   jp1.add(jl1);
   jp1.add(lujin);
   jp1.add(xuanz);
   c.add(jp1, BorderLayout.NORTH);
   nr = new JTextArea();
   c.add(new JScrollPane(nr), BorderLayout.CENTER);
   qu = new JRadioButton("写入");
   xie = new JRadioButton("取出", true);
   fz = new ButtonGroup();
   fz.add(qu);
   fz.add(xie);
   jl2 = new JLabel("密钥");
   key = new JTextField(15);
   jiami = new JButton("加密");
   jiemi = new JButton("解密");
   JPanel jp4 = new JPanel();
   jp4.setLayout(new GridLayout(2, 1, 5, 5));
   JPanel jp2 = new JPanel();
   jp2.add(jl2);
   jp2.add(key);
   jp2.add(jiami);
   jp2.add(jiemi);
   jp4.add(jp2);
   JPanel jp3 = new JPanel();
   queding = new JButton("确定");
   jp3.add(qu);
   jp3.add(xie);
   jp3.add(queding);
   jp4.add(jp3);
   c.add(jp4, BorderLayout.SOUTH);
   queding.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent event) {
     jian();
     if (qu.isSelected())
      shuchu();
     if (xie.isSelected())
      qu();   }  });
   xuanz.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent event) {
     JFileChooser fileChooser = new JFileChooser(); // 实例化文件选择器
     fileChooser
       .setFileSelectionMode(JFileChooser.FILES_AND_DIRECTORIES); // 设置文件选择模式,此处为文件和目录均可
     if (fileChooser.showOpenDialog(key.this) == JFileChooser.APPROVE_OPTION) { // 弹出文件选择器,并判断是否点击了打开按钮
      String fileName = fileChooser.getSelectedFile()
        .getAbsolutePath(); // 得到选择文件或目录的绝对路径
      lujin.setText(fileName);  } } });
   jiemi.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent event) {
     ObjectInputStream input;
     try {
 input = new ObjectInputStream(new FileInputStream(lujin
      .getText()));
      int mima = Integer.parseInt(key.getText());
      AA ac = (AA) input.readObject();
      if (ac.getShu() == mima) {
       nr.setText(ac.cc);
       shuchu();
      } else {
       nr.setText("错误的key");   }  }
 catch (Exception e) { // e.printStackTrace();
      nr.setText("无法解密"); }  } });
   jiami.addActionListener(new ActionListener() {
    public void actionPerformed(ActionEvent event) {
     AA a = new AA(nr.getText());
     key.setText(a.shu + "");
     try {
      ObjectOutputStream output = new ObjectOutputStream(
        new FileOutputStream(lujin.getText()));
      output.writeObject(a);
      output.flush();
      output.close();
      qu();
      baocun();
     } catch (Exception e) {// e.printStackTrace();
      nr.setText("必须选择加密文件保存地址，文件不存在或者无法加密文件,加密文件不能含有换行");   }  } });
   setSize(380, 350);
   setVisible(true);}
public void jian() {
   f = new File(lujin.getText());
   try {
    f.createNewFile();
   } catch (IOException e) {
    JOptionPane.showMessageDialog(null, "路径错误");   }}
public void shuchu() {
   try {
    FileOutputStream out = new FileOutputStream(f);
    byte buf[] = nr.getText().getBytes();
    try {
     out.write(buf);
     out.flush();
     out.close();
    } catch (IOException e) { // e.printStackTrace();
    } } catch (FileNotFoundException e) { // e.printStackTrace();
   }}
public void qu() {
   try {
    FileInputStream in = new FileInputStream(f);
    int a = (int) f.length();
    byte buf[] = new byte[a];
    try {
     int len = in.read(buf);
     if (len == -1)
      System.out.println("文件为空");
     else
      nr.setText(new String(buf, 0, len));
    } catch (IOException e) { // e.printStackTrace();
    }
   } catch (FileNotFoundException e) { // e.printStackTrace();
   }}
public static void main(String arge[]) {
   key s = new key();
   s.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);}
public String mzi() {
   String ccc = "";
   int zu[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
   for (int i = 0; i < 6; i++) {
    int second = (int) (Math.random() * 9);
    ccc += zu[second]; }
   return ccc;}
public void baocun() {
   AA a = new AA();
   shu1 = a.getShu();
   a.shu = shu1;}}
class AA implements Serializable {
String cc;
public int shu;
public AA() {}
public int getShu() {
   return shu;}
public void setShu(int shu) {
   this.shu = shu;}
public AA(String a) {
   cc = a;
   int zu[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
   for (int i = 0; i < 1000; i++) {
    int second = (int) (Math.random() * 9);
    shu += zu[second]; }
}}
