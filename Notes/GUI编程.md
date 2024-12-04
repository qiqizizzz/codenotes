# 一、GUI基础



# 二、AWT

## 2.1 组件和容器

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



## 2.2布局管理器

### **1.流式布局**

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

### **2.东西南北中**

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

### **3.表格布局(Grid)**

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

## 2.3 事件监听

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

## 2.4 输入框TextFiled监听

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

