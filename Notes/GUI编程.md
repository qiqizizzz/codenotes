# 一、GUI基础

## 1.概念解析

**JFrame** – java的GUI程序的基本思路是以JFrame为基础，它是屏幕上window的对象，能够最大化、最小化、关闭。

**JPanel** – Java图形用户界面(GUI)工具包swing中的面板容器类，包含在javax.swing 包中，可以进行嵌套，功能是对窗体中具有相同逻辑功能的组件进行组合，是一种轻量级容器，可以加入到JFrame窗体中。

**JLabel** – JLabel 对象可以显示文本、图像或同时显示二者。可以通过设置垂直和水平对齐方式，指定标签显示区中标签内容在何处对齐。默认情况下，标签在其显示区内垂直居中对齐。默认情况下，只显示文本的标签是开始边对齐；而只显示图像的标签则水平居中对齐。

**JTextField** –一个轻量级组件，它允许编辑单行文本。

**JPasswordField** – 允许我们输入了一行字像输入框，但隐藏星号(*) 或点创建密码(密码)

**JButton** – JButton 类的实例。用于创建按钮类似实例中的 "Login"。

# 二、AWT

抽象窗口工具包AWT（Abstract Window Toolkit）是java提供的建立图形用户界面GUI的开发包，AWT可用于Java的Applet 和 Application 中。java.awt包提供了基本的GUI设计工具，主要包括组件（Component）、容器（Container）和布局管理器（LayoutManager）三个概念。

## 2.1 组件和容器

容器是Component的子类，一个容器可以容纳多个组件，并使他们成为一个整体。容器可以简化图形化界面的设计，以整体结构来布置界面，所有的组件都可以通过add()方法加入容器中。

有三种类型的容器：`Window`、`Panel`、`ScrollPane`

- `Window`类：是不依赖其他容器而独立存在的容器。他有两个子类，分别是Frame类和Dialog类。Frame类用于创建一个具有标题栏的框架窗口作为程序的主要界面，Dialog类用于创建一个对话框，实现与用户的信息交换。

- `Panel`类：也是一个容器，但是他不能单独存在，只能存在于其他容器(window或其子类)中，一个panel对象代表了一个长方形的区域，在这个区域中可以容纳其他组件，在程序中通常会使panel来实现一些特殊的布局。

- `ScrollPane`类：用于实现单个子组件的自动水平和/或垂直滚动的容器类。因此该类创建的对象也是一个容器，称为滚动面板。


常用的容器有：`Panel`、`Frame`、`Applet`

### 1.第一个`frame`窗口

```java
Frame frame=new Frame("我的第一个Java图像界面窗口");

 //需要设置可见性
frame.setVisible(true);

//设置窗口大小 w h
frame.setSize(400,400);

//设置背景颜色 Color
frame.setBackground(new Color(85,150,68));

//弹出的初始位置
frame.setLocation(200,200);

//设置大小固定
frame.setResizable(false);
```

**注意**：无法正常关闭。

```java
//创建类来调用类创建多个窗口
public class text2 {
    public static void main(String[] args) {
        MyFrame myFrame1 = new MyFrame(100, 100, 200, 200, Color.blue);
        MyFrame myFrame2 = new MyFrame(300, 100, 200, 200, Color.yellow);
        MyFrame myFrame3 = new MyFrame(100, 300, 200, 200, Color.red);
        MyFrame myFrame4 = new MyFrame(300, 300, 200, 200, Color.MAGENTA);
    }
}

class MyFrame extends Frame {
    static int id=0;

    public MyFrame(int x,int y,int w,int h,Color color){
        super("MyFrame+"+(++id));
        setBackground(color);
        setBounds(x,y,w,h);
        setVisible(true);
    }
}
```

### 2.Panel面板

`Panel`是一种透明的容器，既没有标题，也没有边框。它不能作为最外层的容器单独存在，首先必须先作为一个组件放置在其他容器中，然后再把它当做容器。

```java
public static void main(String[] args)
    {
        Frame frame=new Frame();
        Panel panel=new Panel();
        //设置布局
        frame.setLayout(null);

        //坐标
        frame.setBounds(300,300,500,500);
        frame.setBackground(new Color(40,161,35));

        //panel设置坐标,相对于frame
        panel.setBounds(50,50,400,400);
        panel.setBackground(new Color(193,15,60));

        //frame.add(panel)
        frame.add(panel);

        frame.setVisible(true);

        //监听事件,监听窗口关闭事件 System.exit(0)
        //适配器模式:
        frame.addWindowListener(new WindowAdapter() {
            //窗口点击关闭的时候需要做的事情
            @Override
            public void windowClosing(WindowEvent e) {
                //结束程序
                System.exit(0);
            }
        });
    }
```

### 3.基本组件

awt组件库中还有很多比较常用的组件，如：按钮（Button）、复选框（Checkbox）、复选框组（CheckboxGroup）、下拉菜单（Choice）、单行文本输入框（TextField）、多行文本输入框（TextArea）、列表（List）、对话框（Dialog）、文件对话框（Filedialog）、菜单（Menu）、MenuBar、MenuItem、Canvas等；

```java
import java.awt.Button;
import java.awt.Checkbox;
import java.awt.CheckboxGroup;
import java.awt.Choice;
import java.awt.FlowLayout;
import java.awt.Frame;
import java.awt.GridLayout;
import java.awt.List;
import java.awt.Panel;
import java.awt.TextArea;
import java.awt.TextField;
 
public class ComponentTest {
 
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Frame frame = new Frame("基本组件测试");
        frame.setBounds(100, 100, 600, 300);
        GridLayout gl = new GridLayout(4,2,5,5); //设置表格为3行两列排列，表格横向间距为5个像素，纵向间距为5个像素
        frame.setLayout(gl);
        
        //按钮组件
        Button but1 = new Button("测试按钮");
        Panel pn0 = new Panel();
        pn0.setLayout(new FlowLayout());
        pn0.add(but1);
        frame.add(pn0);
        
        //复选框组件
		Panel pn1 = new Panel();
		pn1.setLayout(new FlowLayout());
		pn1.add(new Checkbox("one",null,true));
		pn1.add(new Checkbox("two"));
		pn1.add(new Checkbox("three"));
		frame.add(pn1);
		
		//复选框组（单选）
		Panel pn2 = new Panel();
		CheckboxGroup cg = new CheckboxGroup();
		pn2.setLayout(new FlowLayout());
		pn2.add(new Checkbox("one",cg,true));
		pn2.add(new Checkbox("two",cg,false));
		pn2.add(new Checkbox("three",cg,false));
		frame.add(pn2);
        
		//下拉菜单
		Choice cC = new Choice();
		cC.add("red");
		cC.add("green");
		cC.add("yellow");
        frame.add(cC);
        
        //单行文本框
  		Panel pn3 = new Panel();
  		pn3.setLayout(new FlowLayout());
        TextField tf = new TextField("",30); //30列长度
        pn3.add(tf);
        frame.add(pn3);
        
        //多行文本框
        TextArea ta = new TextArea();
        frame.add(ta);
        
        //列表
        List ls = new List();
        ls.add("a");
        ls.add("b");
        ls.add("c");
        ls.add("d");
        frame.add(ls);
        frame.setVisible(true);
	}
 
}
```

### 4.Menu组件

```java
import java.awt.Frame;
import java.awt.Menu;
import java.awt.MenuBar;
import java.awt.MenuItem;
 
public class MenuDemo {
 
	private Frame f;
	public MenuDemo(){
		f = new Frame("测试菜单");
		f.setBounds(100, 100, 200, 200);
		//Menu无法直接添加到容器中，只能直接添加到菜单容器中
		MenuBar mb = new MenuBar(); //创建菜单容器
		f.setMenuBar(mb);
		//添加菜单
		Menu m1 = new Menu("File");
		Menu m2 = new Menu("Edit");
		Menu m3 = new Menu("Help");
		mb.add(m1);
		mb.add(m2);
		mb.add(m3);
		
		//添加菜单项
		MenuItem mi1 = new MenuItem("Save");
		MenuItem mi2 = new MenuItem("Load");
		MenuItem mi3 = new MenuItem("Quit");
		m1.add(mi1);
		m1.add(mi2);
		m1.addSeparator(); //添加分隔线
		m1.add(mi3);
		f.setVisible(true);
	}
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
		MenuDemo md = new MenuDemo();
	}
	
}
```



## 2.2布局管理器

为了实现跨平台并获得动态的布局效果，java将容器内的所有组件安排给一个“布局管理器”负责管理，如：排列顺序、组件大小、位置、当窗口移动或调整大小后组件变化等功能授权给对应的容器布局管理器来管理。

布局管理器的相关类主要包括：java.awt.FlowLayout、java.awt.BorderLayout、java.awt.GridLayout、java.awt.GradLayout、java.awt.GridBagLayout。

### **1.FlowLayout-流式布局管理器**

组件从左到右、从上到下，一个挨一个的放在容器中。（Panel和Applet的默认容器布局）如果容器足够宽，第一个组件先添加到容器中第一行的最左边，后续的组件依次添加到上一个组件的右边，如果当前行已放置不下该组件，则放置到下一行的最左边。

```java
		Frame frame=new Frame();

        //组件-按钮
        Button button1=new Button("button1");
        Button button2=new Button("button2");
        Button button3=new Button("button3");

        //设置为流式布局
        frame.setLayout(new FlowLayout());
        //frame.setLayout(new FlowLayout(FlowLayout.CENTER)); --默认状态
        //frame.setLayout(new FlowLayout(FlowLayout.LEFT));  --靠左
        //frame.setLayout(new FlowLayout(FlowLayout.RIGHT)); --靠右

        frame.setSize(200,200);

        //把按钮添加上去
        frame.add(button1);
        frame.add(button2);
        frame.add(button3);

        frame.setVisible(true);
```

### **2.BorderLayout-边框布局管理器**

按照东、西、南、北、中放组件。（Window/Frame/Dialog的默认容器布局）BorderLayout布局管理器把容器分成5个区域：North，South，East，West和Center，每个区域只能放置一个组件。

```java
		Frame frame=new Frame();

        Button east=new Button("East");
        Button west=new Button("West");
        Button south=new Button("South");
        Button north=new Button("North");
        Button center=new Button("Center");

        frame.add(east,BorderLayout.EAST);
        frame.add(west,BorderLayout.WEST);
        frame.add(south,BorderLayout.SOUTH);
        frame.add(north,BorderLayout.NORTH);
        frame.add(center,BorderLayout.CENTER);

        frame.setSize(200,200);
        frame.setVisible(true);
```

### **3.GridLayout-网格布局管理器**

使容器中各个组件呈网格状布局，平均占据容器的空间。

```java
		Frame frame=new Frame("TestGridLayout");

        Button btn1=new Button("btn1");
        Button btn2=new Button("btn2");
        Button btn3=new Button("btn3");
        Button btn4=new Button("btn4");
        Button btn5=new Button("btn5");
        Button btn6=new Button("btn6");

        //设置表格布局
        frame.setLayout(new GridLayout(3,2));

        frame.add(btn1);
        frame.add(btn2);
        frame.add(btn3);
        frame.add(btn4);
        frame.add(btn5);
        frame.add(btn6);

        frame.pack();
        frame.setVisible(true);
```

> **实例：**(制作一个如效果图的图形化按钮界面)

```java
		Frame frame=new Frame("Text");
        frame.setVisible(true);
        frame.setSize(200,200);
        frame.setLocation(300,400);
        frame.setBackground(Color.black);
        frame.setLayout(new GridLayout(2,1));

        Panel p1=new Panel(new BorderLayout());
        Panel p2=new Panel(new GridLayout(2,1));
        Panel p3=new Panel(new BorderLayout());
        Panel p4=new Panel(new GridLayout(2,2));
        
        p1.add(new Button("East-1"),BorderLayout.EAST);
        p1.add(new Button("West-1"),BorderLayout.WEST);
        p2.add(new Button("p2-button-1"));
        p2.add(new Button("p2-button-2"));
        p1.add(p2,BorderLayout.CENTER);

        p3.add(new Button("East-2"),BorderLayout.EAST);
        p3.add(new Button("West-2"),BorderLayout.WEST);
        for(int i=0;i<4;i++)
        {
            p4.add(new Button("p4-button-"+i));
        }
        p3.add(p4,BorderLayout.CENTER);
        frame.add(p1);
        frame.add(p3);
```

> 效果图

<img src="..\img\gui_panel.png" alt="gui_panel" style="zoom: 50%;" />如图所示

### 4.CardLayout-卡片布局管理器

```java
import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.CardLayout;
import java.awt.Frame;
import java.awt.Panel;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
 
public class CardLayoutDemo {
	Frame f = new Frame("测试窗口");
	String[] names = { "第一张", "第二张", "第三张", "第四张", "第五张" };
	Panel p1 = new Panel(); //显示的面板
 
	public void init() {
		final CardLayout c = new CardLayout(); //卡片局部
		p1.setLayout(c); //面板布局使用卡片布局
		for (int i = 0; i < names.length; i++) {
			p1.add(names[i], new Button(names[i])); //设置面板的名字和组件
		}
		Panel p = new Panel(); //创建一个放按钮的面板
 
		// 控制显示上一张的按钮
		Button previous = new Button("上一张");
		//为按钮添加监听
		previous.addActionListener(new ActionListener() {
			@Override
			public void actionPerformed(ActionEvent arg0) {
				c.previous(p1);
			}
		});
 
		// 控制显示下一张的按钮
		Button next = new Button("下一张");
		next.addActionListener(new ActionListener() {
			@Override
			public void actionPerformed(ActionEvent arg0) {
				c.next(p1);
			}
		});
 
		// 控制显示第一张的按钮
		Button first = new Button("第一张");
		first.addActionListener(new ActionListener() {
			@Override
			public void actionPerformed(ActionEvent arg0) {
				c.first(p1);
			}
		});
 
		// 控制显示最后一张的按钮
		Button last = new Button("最后一张");
		last.addActionListener(new ActionListener() {
			@Override
			public void actionPerformed(ActionEvent arg0) {
				c.last(p1);
			}
		});
 
		// 控制根据Card显示的按钮
		Button third = new Button("第三张");
		third.addActionListener(new ActionListener() {
			@Override
			public void actionPerformed(ActionEvent arg0) {
				c.show(p1, "第三张");
			}
		});
 
		p.add(previous);
		p.add(next);
		p.add(first);
		p.add(last);
		p.add(third);
		f.add(p1);
		f.add(p, BorderLayout.SOUTH);
 
		f.pack(); //紧凑排列
		f.setVisible(true);
	}
 
	public static void main(String[] args) {
		new CardLayoutDemo().init();
	}
 
}
```

### 5.GridBagLayout-网格包布局管理器

```java
import java.awt.Button;
import java.awt.Frame;
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
 
public class GridBagLayoutDemo {
 
	private Frame f = new Frame("GridBagLayout Test");
	private GridBagLayout gbl = new GridBagLayout();
	private GridBagConstraints gbc = new GridBagConstraints();
	
	private Button[] btns = new Button[10];
	
	private void addButton(Button btn) {
		gbl.setConstraints(btn, gbc);
		f.add(btn);
	}
	
	
	public void init() {
		for (int i = 0; i < 10; i++) { // 先初始化10个按钮
			btns[i] = new Button("button" + i);
		}
		f.setLayout(gbl); // 设定框架的布局模式
		
		//为了设置如果组件所在的区域比组件本身要大时的显示情况
		gbc.fill = GridBagConstraints.BOTH; // 使组件完全填满其显示区域
		//NONE：不调整组件大小。
        //HORIZONTAL：加宽组件，使它在水平方向上填满其显示区域，但是不改变高度。
        //VERTICAL：加高组件，使它在垂直方向上填满其显示区域，但是不改变宽度。
		//BOTH：使组件完全填满其显示区域。
		
		gbc.weighty = 1; // 该方法是设置组件水平所占用的格子数，如果为0，就说明该组件是该行的最后一个,为1则只占一格
		
		// 第1行的4个按钮
		gbc.weightx = 1; // 该方法设置组件水平的拉伸幅度，如果为0就说明不拉伸，不为0就随着窗口增大进行拉伸，0到1之间
		addButton(btns[0]);
		addButton(btns[1]);
		addButton(btns[2]);
		gbc.gridwidth = GridBagConstraints.REMAINDER; // 该组件是该行的最后一个，第4个添加后就要换行了
		addButton(btns[3]);
		
		// 第2行1个按钮，仍然保持REMAINDER换行状态
		addButton(btns[4]);
		
		//第3行
		gbc.gridwidth = 2; //按钮分别横跨2格
		gbc.weightx = 1;  //该方法设置组件水平的拉伸幅度
		addButton(btns[5]);
		gbc.gridwidth = GridBagConstraints.REMAINDER;
		addButton(btns[6]);
		
		// 按钮7纵跨2个格子，8、9一上一下
		gbc.gridheight = 2; //按钮7纵跨2格
		gbc.gridwidth = 1;  //横跨1格
		gbc.weightx = 1;    //该方法设置组件水平的拉伸幅度
		addButton(btns[7]); // 由于纵跨2格因此纵向伸缩比例不需要调整，默认为1*2格，比例刚好
		
		gbc.gridwidth = GridBagConstraints.REMAINDER;
		gbc.gridheight = 1;
		gbc.weightx = 1;
		addButton(btns[8]);
		addButton(btns[9]);
		
		f.pack();
		f.setVisible(true);
	}
	
	public static void main(String[] args) {
		new GridBagLayoutDemo().init();
	}
 
 
}
```

## 2.3 事件

与AWT有关的所有事件类都由AWTEvent类派生，它是EventObject类的子类。这些AWT事件分为两大类：低级事件和高级事件。低级事件是指基于组件和容器的事件，当一个组件上发生事件，如鼠标进入、点击、拖放或组件的窗口开关等都是低级事件。高级事件是语义事件，它不可以和特点的动作相关联，而依赖于触发此类事件的类，如选中项目列表中的某一项就会触发ActionEvent事件。

> **低级事件：**

- `ComponentEvent` 构件事件，构件尺寸的变化以及移动·
- `ContainerEvent` 容器事件，构件增加，移动
- `WindowEvent` 窗口事件，关闭窗口，窗口闭合，图标化
- `FocusEvent` 焦点事件，焦点的获得与丢失
- `KeyEvent` 键盘事件，键按下，释放
- `MouseEvent` 鼠标事件，鼠标点击，移动

> **高级事件（语义事件）：**

- `ActionEvent` 动作事件，按键按下，TextField中按下Enter键
- `AdjustmentEvent` 调节事件，在滚动条上移动滑块以调节数值
- `ItemEvent` 项目事件，选择项目，不选择“项目改变”
- `TextEvent` 文本事件，文本对象改变

> **事件适配器**

java语言为一些`Listener`接口提供了适配器类。适配器类提供了一些简单的实现或空实现，可以缩短程序代码，有时候我们并不需要实现接口中所有的方法，但是类呢只支持单继承，对于多种监听器就无法采用事件适配器了，而接口支持多继承，则更大程度上给与我们自己发挥的空间。

### 1.事件监听

```java
public class GUI_text {
    public static void main(String[] args)
    {
        //按下按钮,触发一些事件
        Frame frame=new Frame();
        frame.setVisible(true);
        frame.setSize(1000,1500);
        frame.setLocation(300,400);
        Button button=new Button();
        //因为,addActionListener()需要一个ActionListerner,所以我们需要构造一个ActionListerner
        MyActionListener myActionListener=new MyActionListener();
        button.addActionListener(myActionListener);

        frame.add(button,BorderLayout.CENTER);
        frame.pack();

        windowClose(frame);//关闭窗口
    }
    //关闭窗体的事件
    private static void windowClose(Frame frame){
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
//事件监听
class MyActionListener implements ActionListener{
    public void actionPerformed(ActionEvent e)
    {
        System.out.println("你好呀");
    }

}
```

> **实例：**(两个按钮监听一个事件)

```java
public class GUI_text {
    public static void main(String[] args) {
        Frame frame=new Frame("开始-停止");
        Button button1=new Button("start");
        Button button2=new Button("stop");

        //可以显示的定义触发会返回的命令,如果不显示定义,则会走默认的值.
        button2.setActionCommand("button2-stop");

        MyMonitor myMonitor=new MyMonitor();

        button1.addActionListener(myMonitor);
        button2.addActionListener(myMonitor);

        frame.add(button1,BorderLayout.NORTH);
        frame.add(button2,BorderLayout.SOUTH);

        frame.pack();
        frame.setVisible(true);
    }
}
class MyMonitor implements ActionListener{

    @Override
    public void actionPerformed(ActionEvent e){
        //e.getActionCommand() 获得按钮的信息
        System.out.println("按钮被点击了:msg=>"+e.getActionCommand());
        if(e.getActionCommand().equals("start")){
            System.out.println("我是SRART");
        }
        else {
            System.out.println("我是其他");
        }
    }
}
```

### 2.鼠标监听

> 想要实现鼠标画画

```java
package GUI;

import java.awt.*;
import java.awt.event.MouseAdapter;
import java.awt.event.MouseEvent;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;
import java.util.ArrayList;
import java.util.Iterator;

public class text5 {
    public static void main(String[] args) {
        MyFrame1 myFrame1=new MyFrame1("画图");
        myFrame1.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}

class MyFrame1 extends Frame{
    ArrayList points;

    public MyFrame1(String title){
        super(title);
        setBounds(200,200,400,300);
        //存鼠标点击的点
        points=new ArrayList<>();

        setVisible(true);
        //鼠标监听器,正对这个窗口
        this.addMouseListener(new MyMouseListener());
    }

    @Override
    public void paint(Graphics g) {
        //画画,监听鼠标的事件
        Iterator iterator=points.iterator();
        while (iterator.hasNext()){
            Point point=(Point) iterator.next();
            g.setColor(Color.BLUE);
            g.fillOval(point.x,point.y,10,10);
        }
    }

    //添加一个点到界面上
    public void addPaint(Point point){
        points.add(point);
    }

    //适配器模式
    private class MyMouseListener extends MouseAdapter{
        //鼠标 按下,弹起,按住不放
        @Override
        public void mousePressed(MouseEvent e) {
            MyFrame1 frame=(MyFrame1) e.getSource();
            //点击的时候会在界面上产生一个点
            //这个点就是鼠标的点
            frame.addPaint(new Point(e.getX(),e.getY()));

            //每次点击鼠标都需要重新画一遍
            frame.repaint();//刷新
        }
    }
}
```

### 3.窗口监听

```java
package GUI;

import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class text6 {
    public static void main(String[] args) {
        new WindowFrame();
    }
}

class WindowFrame extends Frame{
    public WindowFrame(){
        setBackground(Color.blue);
        setBounds(200,300,400,500);
        setVisible(true);

        //匿名内部类
        this.addWindowListener(new WindowAdapter() {
            //关闭窗口
            @Override
            public void windowClosing(WindowEvent e) {
                System.out.println("windowClosing");
                System.exit(0);
            }

            //打开窗口
            @Override
            public void windowActivated(WindowEvent e) {
                System.out.println("windowActivated");
                WindowFrame source=(WindowFrame) e.getSource();
                source.setTitle("被激活了");
            }
        });
    }
}
```

### 4.键盘监听

```java
package GUI;

import java.awt.*;
import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class text7 {
    public static void main(String[] args) {
        new KeyFrame();
    }
}

class KeyFrame extends Frame{
    public KeyFrame(){
        setBounds(1,2,300,400);
        setVisible(true);

        this.addKeyListener(new KeyAdapter() {
            //键盘按下
            @Override
            public void keyPressed(KeyEvent e) {
                //获得键盘下的键是哪一个,当前的码
                int keyCode=e.getKeyCode();  //不需要去记这个数值,直接用静态属性 VK_XXX
                System.out.println(keyCode);
                if(keyCode==KeyEvent.VK_UP){
                    System.out.println("你按下了上键");
                }
                //根据按下不同操作,产生不同结果:
            }
        });
        this.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
}
```

### 5.输入框TextFiled监听

```java
public class GUI_text {
    public static void main(String[] args) {
        new MyFrame2();
    }
}

class MyFrame2 extends Frame{
    public MyFrame2(){
        TextField textField=new TextField();
        add(textField);

        //监听这个文本框输入的文字
        MyActionListener2 myActionListener2=new MyActionListener2();
        //按下enter,就会触发这个输入框的事件
        textField.addActionListener(myActionListener2);

        //设置替换编码
        textField.setEchoChar('*');

        setVisible(true);
        pack();
    }
}

class MyActionListener2 implements ActionListener{
    @Override
    public void actionPerformed(ActionEvent e) {
        TextField field=(TextField) e.getSource();     //获得一些资源,返回的一个对象
        System.out.println(field.getText());   //获得输入框的文本
        field.setText("");//设置文本框为"",即清空文本框
    }
}
```

#### 简易加法计算器

**1.普通实现**

```java
package GUI;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class text3 {
    public static void main(String[] args) {
    new Caculator();
    }
}

class Caculator extends Frame{
    public Caculator(){
        //3个文本框
        TextField t1=new TextField(10);
        TextField t2=new TextField(10);
        TextField t3=new TextField(20);

        //1个按钮
        Button button=new Button("=");
        button.addActionListener(new MyCaculator(t1,t2,t3));

        //1个标签
        Label label=new Label("+");

        //布局
        setLayout(new FlowLayout());
        add(t1);add(label);add(t2);add(button);add(t3);

        pack();//自适应
        setVisible(true);
    }
}

//监听器类
class MyCaculator implements ActionListener {
    //获取三个变量
    private TextField num1,num2,num3;
    public MyCaculator(TextField num1,TextField num2,TextField num3)
    {
        this.num1=num1;
        this.num2=num2;
        this.num3=num3;
    }
    @Override
    public void actionPerformed(ActionEvent e) {
        //获得加数和被加数
        int n1=Integer.parseInt(num1.getText());
        int n2=Integer.parseInt(num2.getText());

        //将这个值加法运算后，放到第三个框
        num3.setText(""+(n1+n2));
        //清除前两个框
        num1.setText("");
        num2.setText("");
    }
}
```

**2.完全改造为面向对象方法(组合)**

```java
package GUI;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class text3 {
    public static void main(String[] args) {
    new Caculator();
    }
}

class Caculator extends Frame{
    TextField t1; 
    TextField t2; 
    TextField t3; 
    public Caculator(){
        //3个文本框
        t1=new TextField(10);
        t2=new TextField(10);
        t3=new TextField(20);

        //1个按钮
        Button button=new Button("=");
        button.addActionListener(new MyCaculator(this));  

        //1个标签
        Label label=new Label("+");

        //布局
        setLayout(new FlowLayout());
        add(t1);add(label);add(t2);add(button);add(t3);

        pack();//自适应
        setVisible(true);
    }
}

//监听器类
class MyCaculator implements ActionListener { 
    //获取计算器这个类,在一个类中组合另一个类
    Caculator caculator=null;
    public MyCaculator(Caculator caculator){
        this.caculator=caculator;
    }
    @Override
    public void actionPerformed(ActionEvent e) {
        int n1=Integer.parseInt(caculator.t1.getText());
        int n2=Integer.parseInt(caculator.t2.getText());
        caculator.t3.setText(""+(n1+n2));
        caculator.t1.setText("");
        caculator.t2.setText("");
    }
}
```

**3.内部类**

```java
package GUI;

import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class text3 {
    public static void main(String[] args) {
    new Caculator();
    }
}

class Caculator extends Frame{
    TextField t1;
    TextField t2;
    TextField t3;
    public Caculator(){
        //3个文本框
        t1=new TextField(10);
        t2=new TextField(10);
        t3=new TextField(20);

        //1个按钮
        Button button=new Button("=");
        button.addActionListener(new MyCaculator());

        //1个标签
        Label label=new Label("+");

        //布局
        setLayout(new FlowLayout());
        add(t1);add(label);add(t2);add(button);add(t3);

        pack();//自适应
        setVisible(true);
    }
    //内部类最大的好处,可以畅通无阻的访问外部的属性和方法.
    private class MyCaculator implements ActionListener {
        @Override
        public void actionPerformed(ActionEvent e) {
            int n1=Integer.parseInt(t1.getText());
            int n2=Integer.parseInt(t2.getText());
            t3.setText(""+(n1+n2));
            t1.setText("");
            t2.setText("");
        }
    }
}
```

## 2.4 画笔paint

```java
package GUI;

import java.awt.*;
import java.awt.event.WindowAdapter;
import java.awt.event.WindowEvent;

public class text4 {
    public static void main(String[] args) {
        mypaint mypaint=new mypaint();
        mypaint.loadFrame();
    }
}
class mypaint extends Frame{
    public void loadFrame(){
        setVisible(true);
        setBounds(200,200,600,500);
        addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });
    }
    @Override
    public void paint(Graphics g) {
        //画笔,需要有颜色,画笔可以画画
        g.setColor(Color.GREEN);
        g.drawOval(200,300,100,100);
        g.fillOval(100,100,100,100);  //画一个实心的圆
    }
}
```

# 三、Swing

Swing 是一个为Java设计的GUI工具包。

Swing是JAVA基础类的一部分。

Swing包括了图形用户界面（GUI）器件如：文本框，按钮，分隔窗格和表。

Swing提供许多比AWT更好的屏幕显示元素。它们用纯Java写成，所以同Java本身一样可以跨平台运行，这一点不像AWT。它们是JFC的一部分。它们支持可更换的面板和主题（各种操作系统默认的特有主题），然而不是真的使用原生平台提供的设备，而是仅仅在表面上模仿它们。这意味着你可以在任意平台上使用JAVA支持的任意面板。轻量级组件的缺点则是执行速度较慢，优点就是可以在所有平台上采用统一的行为。

## 2.1 窗体

```java
package GUI;

import javax.swing.*;
import java.awt.*;

public class text8 {
    public static void main(String[] args) {
        new MyJFrame().init();
    }
}

class MyJFrame extends JFrame{
    public void init(){
        this.setBounds(10,10,200,300);
        this.setVisible(true);

        JLabel label=new JLabel("你好,我是柒柒子~");
        this.add(label);

        //让文本标签居中 设置水平对齐
        label.setHorizontalAlignment(SwingConstants.CENTER);

        //获得一个容器
        Container container=this.getContentPane();
        /*这行代码的作用是获取当前 JFrame 对象的内容面板，并将其引用保存在 container 变量中，以便可以在后续的代码中方便地使用这个内容面板来添加其他组件。*/
        container.setBackground(Color.YELLOW);

        //关闭窗口
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
}
```

## 2.2 弹窗

```java
package GUI;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.beans.PropertyChangeListener;

public class DialogDemo extends JFrame {
        public DialogDemo() {
            this.setVisible(true);
            this.setSize(700, 500);
            this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

            //JFrame 放东西,容器
            Container container = this.getContentPane();
            //绝对布局
            container.setLayout(null);

            //按钮
            JButton button = new JButton("点击弹出一个对话框");//创建
            button.setBounds(30, 30, 200, 50);

            //点击这个按钮的时候,弹出一个弹窗
            button.addActionListener(new ActionListener() {//监听器
                @Override
                public void actionPerformed(ActionEvent e) {
                    //弹窗
                    new MyDialogDemo();
                }
            });
            container.add(button);
        }

        public static void main(String[] args) {
            new DialogDemo();
        }
    }
//弹窗的窗口
class MyDialogDemo extends JDialog{
    public MyDialogDemo(){
        this.setVisible(true);
        this.setBounds(100,100,500,500);
        //this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

        Container container=this.getContentPane();
        container.setLayout(null);

        container.add(new Label("我是柒柒子~"));
    }
}
```

## 2.3 常用标签

### 1.Icon

```java
package GUI;

import javax.swing.*;
import java.awt.*;

//图标,需要实现类,Frame继承
public class IconDemo extends JFrame implements Icon {
    private int width;
    private int height;

    public IconDemo(){} //无参构造

    public IconDemo(int width,int height){
        this.width=width;
        this.height=height;
    }

    public void init(){
        IconDemo iconDemo=new IconDemo(15,15);
        //图标放在标签,也可以放在按钮上
        JLabel label=new JLabel("icontest",iconDemo,SwingConstants.CENTER);

        Container container=getContentPane();
        container.add(label);

        this.setBounds(15,15,200,330);
        this.setVisible(true);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        IconDemo iconDemo=new IconDemo();
        iconDemo.init();
    }

    @Override
    public void paintIcon(Component c, Graphics g, int x, int y) {
        g.fillOval(x,y,width,height);
    }

    @Override
    public int getIconWidth() {
        return this.width;
    }

    @Override
    public int getIconHeight() {
        return this.height;
    }
}
```

### 2.ImageIcon

```java
package GUI;

import javax.swing.*;
import java.awt.*;
import java.net.URL;

public class ImageIconDemo extends JFrame {
    public ImageIconDemo(){
        //获取图片的地址
        JLabel label=new JLabel("ImageIcon");
        URL url=ImageIconDemo.class.getResource("1.png");

        ImageIcon imageIcon=new ImageIcon(url);
        label.setIcon(imageIcon);
        label.setHorizontalAlignment(SwingConstants.CENTER);

        Container container=getContentPane();
        container.add(label);

        setVisible(true);
        setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
        setBounds(100,100,200,200);
    }

    public static void main(String[] args) {
        new ImageIconDemo();
    }
}
```

## 2.4 面版

```java
//JPane
package GUI;

import javax.swing.*;
import java.awt.*;

public class JPaneDemo extends JFrame {
    public JPaneDemo(){
        Container container=this.getContentPane();

        container.setLayout(new GridLayout(2,1,10,10));  //hgap是左右间距,vgap是上下间距

        JPanel panel1=new JPanel(new GridLayout(1,3));
        JPanel panel2=new JPanel(new GridLayout(1,2));
        JPanel panel3=new JPanel(new GridLayout(2,1));
        JPanel panel4=new JPanel(new GridLayout(3,2));

        panel1.add(new JButton("1"));
        panel1.add(new JButton("1"));
        panel1.add(new JButton("1"));
        panel2.add(new JButton("2"));
        panel2.add(new JButton("2"));
        panel3.add(new JButton("3"));
        panel3.add(new JButton("3"));
        panel4.add(new JButton("4"));
        panel4.add(new JButton("4"));
        panel4.add(new JButton("4"));
        panel4.add(new JButton("4"));
        panel4.add(new JButton("4"));
        panel4.add(new JButton("4"));

        container.add(panel1);
        container.add(panel2);
        container.add(panel3);
        container.add(panel4);

        this.setVisible(true);
        this.setSize(500,500);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }
    public static void main(String[] args) {
        new JPaneDemo();
    }
}
```

## 2.5 按钮

### 1.图片按钮

```java
package GUI;

import javax.swing.*;
import java.awt.*;
import java.net.URL;

public class JButtonDemo01 extends JFrame {
    public JButtonDemo01(){
        Container container=this.getContentPane();
        //将一个图片变为图标
        URL resource=JButtonDemo01.class.getResource("1.png");
        Icon icon=new ImageIcon(resource);

        //把这个图标放在按钮上
        JButton button=new JButton();
        button.setIcon(icon);
        button.setToolTipText("图片按钮");

        //add
        container.add(button);

        this.setVisible(true);
        this.setSize(500,300);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new JButtonDemo01();
    }
}
```

### 2.单选框

```java
package GUI;

import javax.swing.*;
import java.awt.*;
import java.net.URL;

public class JButtonDemo01 extends JFrame {
    public JButtonDemo01(){
        Container container=this.getContentPane();

        //单选框
        JRadioButton jButton1=new JRadioButton("jButton1");
        JRadioButton jButton2=new JRadioButton("jButton2");
        JRadioButton jButton3=new JRadioButton("jButton3");

        //分组,使得单选框只能选一个
        ButtonGroup bg=new ButtonGroup();
        bg.add(jButton1);
        bg.add(jButton2);
        bg.add(jButton3);

        container.add(jButton1,BorderLayout.CENTER);
        container.add(jButton2,BorderLayout.SOUTH);
        container.add(jButton3,BorderLayout.NORTH);

        this.setVisible(true);
        this.setSize(500,300);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new JButtonDemo01();
    }
}
```

### 3.多选框

```java
package GUI;

import javax.swing.*;
import java.awt.*;
import java.net.URL;

public class JButtonDemo01 extends JFrame {
    public JButtonDemo01(){
        Container container=this.getContentPane();

        JCheckBox jCheckBox1=new JCheckBox("1");
        JCheckBox jCheckBox2=new JCheckBox("2");
        JCheckBox jCheckBox3=new JCheckBox("3");

        container.add(jCheckBox1,BorderLayout.CENTER);
        container.add(jCheckBox2,BorderLayout.SOUTH);
        container.add(jCheckBox3,BorderLayout.NORTH);

        this.setVisible(true);
        this.setSize(500,300);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new JButtonDemo01();
    }
}
```

### 4.下拉框

```java
package GUI;

import javax.swing.*;
import java.awt.*;

public class Text01 extends JFrame {
    public Text01(){
        Container container=this.getContentPane();
        JComboBox status=new JComboBox();

        status.addItem(null);
        status.addItem("正在热映");
        status.addItem("已下架");
        status.addItem("待上映");

        container.add(status);
        this.setVisible(true);
        this.setBounds(100,100,500,500);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new Text01();
    }
}
```

### 5.列表框

```java
package GUI;

import javax.swing.*;
import java.awt.*;

public class Text01 extends JFrame {
    public Text01(){
        Container container=this.getContentPane();

        //生成列表的内容
        String[] s={"jianbing","shibendan","nie"};
        //列表中需要放入内容
        JList jList=new JList(s);
        container.add(jList);

        this.setVisible(true);
        this.setBounds(100,100,500,500);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new Text01();
    }
}
```

### 6.文本框

```java
package GUI;

import javax.swing.*;
import java.awt.*;

public class Text01 extends JFrame {
    public Text01(){
        Container container=this.getContentPane();

        JTextField textField=new JTextField("hello");
        JTextField textField1=new JTextField("world",20);

        container.add(textField,BorderLayout.NORTH);
        container.add(textField1,BorderLayout.SOUTH);

        this.setVisible(true);
        this.setBounds(100,100,500,500);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new Text01();
    }
}
```

### 7.密码框

```java
package GUI;

import javax.swing.*;
import java.awt.*;

public class Text01 extends JFrame {
    public Text01(){
        Container container=this.getContentPane();

        JPasswordField jPasswordField=new JPasswordField();
        jPasswordField.setEchoChar('*');
        container.add(jPasswordField);

        this.setVisible(true);
        this.setBounds(100,100,500,500);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new Text01();
    }
}
```



### 8.文本域

```java
//JScrollPane
package GUI;

import javax.swing.*;
import java.awt.*;

public class JScrollDemo extends JFrame {
    public JScrollDemo(){
        Container container=this.getContentPane();

        //文本域
        JTextArea textArea=new JTextArea(20,50);
        textArea.setText("你好呀");

        //Scroll面板
        JScrollPane scrollPane=new JScrollPane(textArea);
        container.add(scrollPane);

        this.setVisible(true);
        this.setBounds(100,100,300,350);
        this.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);
    }

    public static void main(String[] args) {
        new JScrollDemo();
    }
}
```



# 四、实例

## 1.用户登录框

```java
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JPasswordField;
import javax.swing.JTextField; 
public class SwingLoginExample {
    
    public static void main(String[] args) {    
        // 创建 JFrame 实例
        JFrame frame = new JFrame("Login Example");
        // Setting the width and height of frame
        frame.setSize(350, 200);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        /* 创建面板，这个类似于 HTML 的 div 标签
         * 我们可以创建多个面板并在 JFrame 中指定位置
         * 面板中我们可以添加文本字段，按钮及其他组件。
         */
        JPanel panel = new JPanel();    
        // 添加面板
        frame.add(panel);
        /* 
         * 调用用户定义的方法并添加组件到面板
         */
        placeComponents(panel);

        // 设置界面可见
        frame.setVisible(true);
    }

    private static void placeComponents(JPanel panel) {

        /* 布局部分我们这边不多做介绍
         * 这边设置布局为 null
         */
        panel.setLayout(null);

        // 创建 JLabel
        JLabel userLabel = new JLabel("User:");
        /* 这个方法定义了组件的位置。
         * setBounds(x, y, width, height)
         * x 和 y 指定左上角的新位置，由 width 和 height 指定新的大小。
         */
        userLabel.setBounds(10,20,80,25);
        panel.add(userLabel);

        /* 
         * 创建文本域用于用户输入
         */
        JTextField userText = new JTextField(20);
        userText.setBounds(100,20,165,25);
        panel.add(userText);

        // 输入密码的文本域
        JLabel passwordLabel = new JLabel("Password:");
        passwordLabel.setBounds(10,50,80,25);
        panel.add(passwordLabel);

        /* 
         *这个类似用于输入的文本域
         * 但是输入的信息会以点号代替，用于包含密码的安全性
         */
        JPasswordField passwordText = new JPasswordField(20);
        passwordText.setBounds(100,50,165,25);
        panel.add(passwordText);

        // 创建登录按钮
        JButton loginButton = new JButton("login");
        loginButton.setBounds(10, 80, 80, 25);
        panel.add(loginButton);
    }

}
```

