
# C语言开发知识体系图

## 开发前的准备

### C语言介绍
    C 语言是一门高级计算机编程语言，设计目标是提供一种能以简易的方式编译、处理低级存储器、产生少量的机器码以及不需要任何运行环境支持便能运行的编程语言。尽管 C 语言提供了许多低级处理的功能，但仍然保持着良好跨平台的特性，以一个标准规格写出的 C   语言程序可在许多电脑平台上进行编译，甚至包含一些嵌入式处理器以及超级电脑等作业平台。

### 搭建C语言集成开发环境
    Mac 系统用户体验非常好，文字渲染非常完美，正在被越来越多的人接受和使用，现在Mac系统用户数量已经非常可观，甚至有的企业直接要求所有人用 Mac 电脑办公(如:极客学院)，学会在 Mac 平台做 C 语言程序的开发也非常有必要。所以推荐大家在Mac下开发。
 
 * Mac 平台安装 Xcode 集成开发环境（只支持Mac）
 * Mac 平台使用 SublimeText 编写 C 语言程序（支持跨平台）
 * Mac 平台搭建 Eclipse CDT 集成开发环境（支持跨平台）
 * Mac 平台下搭建 CLion 集成开发环境（支持跨平台）

## C语言基础知识

### C语言常用的基本数据类型
基本数据类型是 C 语言开发的基本知识，在做 C 语言开发前必须要了解 C 语言的基本数据类型。

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
流程控制和循环是编程语言最基本的功能，也是必然的功能，只有学会了这些才能进行开发工作

 * if语句
 ```
    #include <stdio.h>
    #include <stdint.h>
    
    int main() {
    
        int32_t a = 8;
        int32_t b = 10;
    
        if (a > b) {
            printf("Max num is a: %d\n", a);
        } else {
            printf("Max num is b: %d\n", b);
        }
    
        return 0;
    }
 ```
 评分程序
 ```
    #include <stdio.h>
    #include <stdint.h>
    
    int main() {
    
        int32_t score = 60;
    
        if (score > 80) {
            printf("fine\n");
        }else if (score >= 60) {
            printf("ok\n");
        } else {
            printf("fail\n");
        }
    
        return 0;
    }
 ```
 * switch语句
 ```
    
    #include <sys/_types/_int32_t.h>
    #include <stdio.h>
    
    #define UP 1
    #define DOWN 2
    #define LEFT 3
    #define RIGHT 4
    
    int main() {
    
        int32_t dir = UP;
    
        switch (dir) {
            case UP:
                printf("Go Up\n");
                break;
            case DOWN:
                printf("Go Down\n");
                break;
            case LEFT:
                printf("Go Left\n");
                break;
            case RIGHT:
                printf("Go Right\n");
                break;
            default:
                printf("Dir unknown\n");
        }
    
        return 0;
    }

 ```
 * goto语句
 ```
    #include <stdio.h>
    
    int main(void) {
    
        int i = 0;
        label: printf("%d\n", i);
    
        i++;
    
        if (i <= 100) {
            goto label;
        }
    
        return 0;
    }

 ```
 * for循环
    ```
    #include <stdio.h>
    #include <stdint.h>
    
    int main() {
    
        //基本
        for (int i = 1; i <= 9; i++) {
            for (int j = 1; j <= 9; j++) {
                printf("%d*%d=%d\t", i, j, i * j);
            }
            printf("\n");
        }
    
        printf("======================\n");
    
        //九九乘法表条件: j<=i
        for (int i = 1; i <= 9; i++) {
            for (int j = 1; j <= i; j++) {
                printf("%d*%d=%d\t", i, j, i * j);
            }
            printf("\n");
        }
    
        printf("======================\n");
    
        //跳出多重循环： 可以使用goto语句加标签的形式，跳到后面指定的标签
        for (int i = 1; i <= 9; i++) {
            for (int j = 1; j <= i; j++) {
                printf("%d*%d=%d\t", i, j, i * j);
    
                if (i*j > 24) {
                    goto end;
                }
            }
            printf("\n");
        }
    
        end:
    
        return 0;
    }
    ```
    
 * while循环和do-while循环
 ```
    #include <stdio.h>

    int main() {
    
        int i=0;
        printf("======while======\n");
        while (i<10) {
            printf("%d\n", i);
            i++;
        }
    
        printf("======do-while======\n");
        //先执行后判断
        int j = 0;
        do {
            printf("%d\n", j);
            j++;
        }while(j<10);
    
        return 0;
    }
 ```
 
### C语言常用运算符
   关于函数库的使用可以参考：http://www.cplusplus.com/reference
 * 数学运算符
  ```
    #include <math.h>
    #include <stdio.h>
    #include <inttypes.h>
    
    int main() {
    
        int32_t a = (10+2-8)*9/3;
    
        printf("%d\n", a);
    
        printf("%f\n", sin(M_PI/2));
    
        return 0;
    }
  ```
 * 逻辑运算符
   一共有三种： 逻辑与(&&)、逻辑或(||)、逻辑非(!)
   ```
    #include <stdio.h>
    #include <stdint.h>
    
    #define MALE 1
    #define FEMALE 2
    
    int main() {
    
        int32_t score = 80;
    
        //逻辑与
        if (score >= 60 && score <= 100) {
            printf("OK\n");
        } else {
            printf("Fail or invalid score\n");
        }
    
        //逻辑或
        if (score < 60 || score > 100) {
            printf("Fail or invalid score\n");
        } else {
            printf("Ok\n");
        }
    
        //逻辑非
        int sex = MALE;
    
        if ( sex == MALE) {
            printf("The person is male\n");
        }else {
            printf("The person is female\n");
        }
    
        //下面的运行结果与上面的是一致的,只是通过非来做处理
        if (sex != MALE) {
            printf("The person is female\n");
        } else {
            printf("The person is male\n");
        }
    
        return 0;
    }
   ```
   
 * 位运算符
 
  ```
    &  位与
    |  位或
    ~  位反
    ^  异或
    >> 右移
    >> 左移
  ```

  ```
  #include <stdio.h>
  #include <stdint.h>
  
  int main() {
      
      int a = 0b10;    //二进制数字
      int b = 0b01;
  
      //位与: 只要有一个0,结果就是0
      printf("%d\n", a&b);    //结果:0
  
      //位或: 只要有一个是1的,结果就是1
      printf("%d\n", a|b);    //结果:1
  
      //位反
      uint8_t c = 1;  //内存的存储: 0b00000001 求反后  0b11111110
      uint8_t d = 0b11111110;
      c = ~c;
      //结果一直说明求反结果是对的
      printf("c: %d\n", c);
      printf("d: %d\n", d);
  
      //有符号求反
      int8_t e = 2;   // -128...-3,-2,-1,(这里是中轴线) 0,1,2,3...127
      e = ~e;
      printf("e: %d\n", e);
  
      //异或: 有差别结果就是1
      printf("a^b: %d\n", a^b);
  
      //左移: 相当于乘2
      //右移: 相当于除2
      int f= 1; //0b1, 0b10, 0b100
      int g = 8;
      printf("f: %d\n", f<<1);    //2
      printf("f: %d\n", f<<2);    //4
      printf("g: %d\n", g>>1);    //4
  
      return 0;
  } 
  ```
 * 位运算实例之提取颜色通道
   这个例子有点抽象
 ```
  #include <stdio.h>
  #include <stdint.h>
  
  int main() {
  
      //十六进制 ARGB(Alpha, Red, Green, Blue), 每个颜色是256个梯度0~256 前两位FF:完全不透明 后六位: FFFFFF 白色 000000黑色
      uint32_t color = 0xFFFEFAFB;
  
      //只取红色通道的值
      //0x00000000 11111110 00000000 00000000
      uint32_t tmp = color&0x00FF0000;    //0b11111110 & 0b11111111 = 0b11111110
      uint8_t  red = tmp >> 16;
      printf("%d\n", red);
  
      return 0;
  }
 ```
 
### C语言输入和输出

 * 输出字符和字符串
  ```
    #include <stdio.h>

    int main() {
    
        //输出字符
        char ch = 'A';
        putchar(ch);
    
        //输出字符串
        char str[] = "Hello World"; //声明字符串数组
        puts(str);
    
        return 0;
    }
  ```
 * 格式化输出
 ```
  #include <stdio.h>

  int main() {
  
      //printf 更多可参考: http://www.cplusplus.com/reference/cstdio/printf/
  
      printf("Hello World\n");
  
      printf("Number: %d, Unsigned Int:%u\n", 12, 20);    //十进制整型
  
      printf("%03d\n", 7);        //不够前面补0   007
      printf("%3d\n", 7);         //不够用空格补    7
      printf("%03d\n", 100);      //前面补0 100
      printf("%03d\n", 234);      //前面补0 234
  
      printf("%o\n", 8);  //输出8进制
  
      //二进制 0,1,2,3,4,5,6,7,8,9,10
  
      printf("%x\n", 15);  //十六进制 0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F,10
      printf("%X\n", 15);
  
      printf("%f\n", 3.14);    //浮点类型  3.140000
      printf("%.2f\n", 3.14);  //浮点类型  3.14
      printf("%.3f\n", 3.14);  //浮点类型  3.140
  
      printf("%c\n", 'A');    //输出字符,和putchar一样
  
      printf("%s\n", "Hello World");  //输出字符串
  
      return 0;
  }
 ```
 * 输入字符
 ```
  #include <stdio.h>

  int main() {
  
      puts("Please input a char");
  
      char inputChar = getchar();
  
      printf("User input is %c\n", inputChar);
  
      return 0;
  }
 ```
 * 格式化输入
 ```
  #include <stdio.h>

  int main() {
  
  
      //demo1: 输入字符, 非内存地址,所以scanf时要加上&
      char dist;
  
      printf("Please input a char \n");
  
      scanf("%c", &dist);
  
      printf("User input char is %c\n", dist);
  
      //demo2: 出入整数
      int a;
      printf("Please input a number\n");
      scanf("%d", &a);
      printf("User input number is %d\n", a);
  
      //demo3: 输入指定长度的字符串
      char buf[100];
      printf("Please input a string\n");
      scanf("%s", buf);   //直接就是一个内存地址,so 不用加 &
      printf("User input string is: %s\n", buf);
  
      return 0;
  }
 ```
 
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
