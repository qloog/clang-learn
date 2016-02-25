# C语言学习之路

C 语言是一门高级计算机编程语言，设计目标是提供一种能以简易的方式编译、处理低级存储器、产生少量的机器码以及不需要任何运行环境支持便能运行的编程语言。尽管 C 语言提供了许多低级处理的功能，但仍然保持着良好跨平台的特性，以一个标准规格写出的 C   语言程序可在许多电脑平台上进行编译，甚至包含一些嵌入式处理器以及超级电脑等作业平台。


# C语言开发知识体系图

## 开发前的准备

### C语言介绍
### 搭建C语言集成开发环境

## C语言基础知识

### C语言常用的基本数据类型

* 常量和变量

  变量  int a = 10;  
  
  常量: 使用define或const来声明, 全部要大写  
  
  define: 在编译时会被自动替换为对应值  
  const: 可以指定常量的类型，一般推荐此方法, 不容易出错
  
  ```
  //#define MY_AGE = 25
  const int MY_AGE1 = 25;
  
  int main() {
    printf("My age is: %d\n", MY_AGE);
    printf("My age is: %d\n", MY_AGE1);
    return 0;
  }
  
  ```
  
* 整型

    ```
    #include <iostream>
    
    int main() {
      
      int a = 10;   //使用4个字节来存储
      int b = -10;
      long long c = 20;  //如果是 long c=20  32位 4字节， 64位8字节, long long 就32、64 都是8个字节
      
      printf("a=%d, b=%d, c=%d\n", a,b,c);
      
      int d = 0b100;  //二进制
      int e = 0xB;    //十六进制 11
      int f = 010;    //8进制 18
      
      //无符号类型
      unsigned int g = 12;
      unsigned long long g = 13;
      printf("%d\n", g);
      
      int32_t h = 10;
      int8_t i = 127;  1个字节  存256个，  -128~127 或 0~255
      uint8_t j = 255;
      int64_t k = 1000; //全平台通用
      printf("i=%d, j=%d, k=%d\n", i,j,k);
      
      return 0;
      
    }
    ```

* 实型数据

  ```
  #include <stdint.h>
  
  int main(void)
  {
      float a = 3.1;  //单精度, 4字节， 32位
      double b = 3.1; //双精度， 8字节， 64位
      long double c = 3.1;  //长双精度， 16字节， 128位
      
      printf("a=%f, b=%f, c=%Lf", a, b, c);
  
      return 0;
  }
  ```

* 字符型数据

  ```
  字符常量
  换行：\n  printf("Hello\nWorld");
  回车：\r  printf("Hello\rWorld");
  退格：\b  printf("Hello\bWorld");  //需要在终端下执行效果可见，类似CLion的ide环境不行
  制表符：\t  printf("Hello\tWorld\nHaha\t\bupt");
  换页符：\f  printf("Hello\fWorld\n");
  
  字符变量
  char ch = 'A';
  printf("%d\n", ch); //输出65
  printf("%c\n", ch+32); //输出a,  因为大小写刚好差32，所以可以用来做字母大小写的转换
  ```

* typedef 自定义类型
 
 ```
    #include <stdio.h>
    #include <stdint.h>
    
    typedef int64_t test_long;
    typedef char test_char;
    typedef uint8_t test_char1;
    
    int main() {
    
        test_long a = 20;
        printf("%d\n", a);
        
        test_char b = 'A';
        printf("%c\n", b);
        
        test_char1 c = 'c';
        printf("%c\n", c);
    
        return 0;
    }

 ```

### 流程控制和循环
### C语言常用运算符
### C语言输入和输出
### C语言数组
### C语言字符串操作
### C语言函数

## C语言进阶

### C语言常用的预处理
### C语言指针的用法
### 结构体和共同体
### C语言中的文件操作

## C语言编程实践

### C语言五子棋游戏项目分析与系统设计
### C语言五子棋游戏项目模块设计与实现
