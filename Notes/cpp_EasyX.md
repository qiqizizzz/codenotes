# 一、基础

## 1.介绍

[easyx图形界面库](https://easyx.cn/)

[easyx手册](https://docs.easyx.cn/zh-cn/intro)

EasyX Graphics Library 是针对 Visual C++ 的免费绘图库，支持 VC6.0 ~ VC2022，简单易用，学习成本极低，应用领域广泛。目前已有许多大学将 EasyX 应用在教学当中。

## 2.准备工作

### 1.导入图形化界面库

```c++
#include<easyx.h>
//或者是
#include<graphics.h>
```

**`<easyx.h>`**:

- 属于 EasyX 图形库，是一个基于 Windows 平台的简单易用的图形库。
- 专为 C++ 初学者设计，封装了许多常用的图形功能，语法简洁，适合快速上手。
- 仅适用于 Windows 平台，依赖于 GDI（Windows 图形设备接口）。
- 需要在编译器（如 Visual Studio）中配置 EasyX 库。

**`<graphics.h>`**:

- 属于传统的 Borland Graphics Interface（BGI），最初由 Turbo C 提供。
- 功能较为基础，部分现代系统可能不直接支持。
- 跨平台支持较差，通常用于教学或早期的图形应用开发。
- 在现代编译器中可能需要额外的配置或兼容层。

**EasyX** 是国内开发者常用的图形库，活跃度较高，文档与教程丰富。

**BGI/graphics.h** 已较为过时，主要用于学习和怀旧目的。

### 2.环境

VS2022

## 3.界面的基本创建

### 1. 创建一个窗口

[initgraph](https://docs.easyx.cn/zh-cn/initgraph)

```c++
#include<cstdio>
#include<easyx.h>
#include<graphics.h>
using namespace std;
int main()
{
	initgraph(800, 450);  //直接这样创建的话会一闪而过，直接消失
	while (1)
	{
		//死循环，可以使该窗口不会消失
	}

	return 0;
}
```

### 2.设置字体和内容

> 注意:若设置字体时报错，则右键项目属性，在**配置属性**中的**高级**中找到**字符集**，选择**使用多字节字符集**

```c++
#include<iostream>
#include<graphics.h>
using namespace std;
int main()
{
    initgraph(800, 450);  //直接这样创建的话会一闪而过，直接消失
    
    settextstyle(72, 0, "隶书");//72代表字号，0代表自适应

    outtextxy(20, 100, "睡觉");//输出文本,20为x轴坐标,100为y轴坐标
    
    cleardevice(); //使用当前背景色清空绘图设备

    while (1)
    {
        //死循环，可以使该窗口不会消失
    }

    return 0;
}
```

### 3.导入媒体库

```c++
#include<mmsystem.h>//导入系统多媒体头文件
#pragma comment(lib,"winmm.lib")//用来告诉链接器将 winmm.lib 文件链接到当前程序中。
```

**`#include <mmsystem.h>`**

- **作用**：
  这是一行预处理指令，用来引入 **Windows 多媒体 API** 的头文件。
- 头文件功能
  - 定义了一系列与多媒体操作相关的函数、数据类型和宏。
  - 包括以下功能：
    - 播放声音：`PlaySound()`。
    - 控制多媒体设备：如播放音乐文件、录音等。
    - 定时器：`timeGetTime()` 等高精度计时函数。

**`winmm.lib`** 

- 是 **Windows 多媒体 API** 的静态链接库。

它提供了多媒体函数的实现（如 `PlaySound()`），而头文件 `mmsystem.h` 仅定义了这些函数的声明。

没有这个库，程序在链接阶段会出现未定义引用（undefined reference）的错误。
