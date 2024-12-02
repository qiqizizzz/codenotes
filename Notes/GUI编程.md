# 一、GUI基础

## 1.第一个`frame`窗口

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

## 2.Panel面板

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



# 二、AWT
