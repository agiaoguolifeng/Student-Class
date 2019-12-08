## 综合性实验  学生选课系统设计

## 实验目的
分析学生选课系统
使用GUI窗体及其组件设计窗体界面
完成学生选课过程业务逻辑编程
基于文件保存并读取数据
处理异常
## 实验要求
一、系统角色分析及类设计
例如：学校有“人员”，分为“教师”和“学生”，教师教授“课程”，学生选择课程。
定义每种角色人员的属性，及其操作方法。
属性示例：	人员（编号、姓名、性别……）
教师（编号、姓名、性别、所授课程、……）
			学生（编号、姓名、性别、所选课程、……）
			课程（编号、课程名称、上课地点、时间、授课教师、……）
## 实验代码
package classalter;
public class Course {
	private int id;
	private String name;
	private String place;
	private int time;
	private int mark;
	public String toString(){
//		System.out.println("Course toString is operating");
		return id+","+name+","+place+","+time+","+mark;
	}
	public Course(int id,String name,String place,int time,int mark){
		this.id=id;
		this.name=name;
		this.place=place;
		this.time=time;
		this.mark=mark;
	}
	
	
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getPlace() {
		return place;
	}
	public void setPlace(String place) {
		this.place = place;
	}
	public int getTime() {
		return time;
	}
	public void setTime(int time) {
		this.time = time;
	}
	public int getMark() {
		return mark;
	}
	public void setMark(int mark) {
		this.mark = mark;
	}
}
package classalter;
public class Personal {
	int id;
	String name;
	String sex;
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getSex() {
		return sex;
	}
	public void setSex(String sex) {
		this.sex = sex;
	}
	public String toString(){
//		System.out.println("toString is operating");
		return id+name+sex;
	}
	public Personal(int id,String name,String sex){
		this.id=id;
		this.name=name;
		this.sex=sex;
	}

}


package classalter;

public class Student extends Personal {


	private Course course;
	private Teather teather;
	
	public Course getCourse() {
		return course;
	}
	public void setCourse(Course course) {
		this.course = course;
	}
	public Teather getTeather() {
		return teather;
	}
	public void setTeather(Teather teather) {
		this.teather = (Teather) teather;
	}
	public void putcourse(){
		if(course==null){
			System.out.println("Not to choose course");
		}else{
		this.toString();
		}
	}
	public String toString(){
	
//		System.out.println("Student toString is operating");
		return id+name+sex+course+teather.getName();
	}
		
	
	public Student(int id, String name, String sex,Course course,Teather teather) {
		super(id, name, sex);
		
			this.course=course;
			this.teather=teather;
		
	
	}
	public Course delete() {
		return course=null;
	}


package classalter;

public class Teather extends Personal {
	private Course course;
	public String toString(){
		System.out.println("teather toString is operating");
		return id+name+sex+course;
	}
	public Teather(int id, String name, String sex,Course course) {
		super(id, name, sex);
		this.course=course;
	}

}


5
package classalter;

public class Test {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		// TODO Auto-generated method stub
		 Course course=new Course(2, "America", "new york",5,5);
		 Teather teather=new Teather(3, "MISS liu", "women",course);
		 Student student=new Student(1, "MR wang", "men",course,teather);
		 System.out.println(student.toString());
		 student.delete();
//		 student.setCourse(null);
//		 student.setTeather(null);
		 student.putcourse();
		 
	}
	

}

GUI测试类


package classalter;
import java.awt.Button;
import java.awt.Color;
import java.awt.FlowLayout;
import java.awt.Frame;
import java.awt.TextField;
import java.awt.Window;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;


public class TestFlowLayout {

    public static void main(String[] args) {

    	 Frame f = new Frame();//建立一个空窗口。
    	 f.setTitle("Frame WHERECOME du");
    	 FlowLayout fl = new FlowLayout();  //使用流布局
         f.setLayout(fl);//修改布局管理
         f.setSize(600, 300);//设置窗口大小,
         f.setLocation(300, 150);//设置窗口的初始位置
         f.setVisible(true);//显示窗口。
    	 

         f.addWindowListener(new WindowAdapter(){
 			public void windowClosing(WindowEvent e){
 				Window window=(Window)e.getComponent();
 				window.dispose();
 			}
 		});


 		TextField textField = new TextField();
 		textField.setBounds(200, 100, 200, 50);
 		textField.setBackground(Color.white);
 		MyActionListener myActionListener = new MyActionListener(textField);//创建一个按钮监听事件对象
 		f.add(textField);
 		Button button1= new Button("Choose couse");
 		Button button2= new Button("Back course");
 		button1.setBounds(100,100,100,100);
 		button1.setBackground(Color.orange);
 		button1.addActionListener(myActionListener);//添加myActionListener监听事件
 		f.add(button1);

 		button2.setBounds(300,300,300,300);
 		button2.setBackground(Color.red);
 		ActionListener myActionListener2=new MyActionListener2(textField);
		button2.addActionListener(myActionListener2);//添加myActionListener监听事件
 		f.add(button2);
        f.setLayout(null);//清空布局
    }
    	
}
class MyActionListener implements ActionListener{
	
	 Course course=new Course(1, "Java", "综合楼",3,3);
	 Teather teather=new Teather(1, "张老师", "男",course);
	 Student student=new Student(1, "郭力锋", "男",course,teather);
	private TextField textField;
 
	public MyActionListener(TextField textField) {
		super();
		this.textField = textField;
	}
	public void actionPerformed(ActionEvent e) {
		textField.setText(" " +student+ " ");
}
}
class MyActionListener2 implements ActionListener{
	
	private TextField textField;
	public MyActionListener2(TextField textField) {
		super();
		this.textField = textField;
	}
	public void actionPerformed(ActionEvent e) {
			textField.setText("not to chouse course");
	
	}
	
}
