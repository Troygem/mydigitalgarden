---
{"title":"C语言入门基础","dg-publish":true,"permalink":"/c/c/","dgPassFrontmatter":true}
---

# 学习C语言的理由
* C语言简单（相较机器语言，汇编语言）
* C生万物 如：操作系统（类似死循环的程序）由C语言实现
* 仅支持一种编程范式（面向过程）
* 学好C语言，学其他语言事半功倍

# 记住两个等式
- 程序 = 算法 + 数据结构
- 程序设计 = 算法 + 数据结构 + 一种编程范式

# 前置知识
- 函数原型：了解系统封装好的函数途径
- std = standard（标准）
- io = in out (输入 输出)

# printf函数
>**头文件**：stdio.h
  **原型**：int printf(const char \*format, . . . );
	  const修饰字符串不可修改
  **format** : 格式控制==字符串==（char * 类型）
	  **作用**：控制打印相关变量的方式：十进制，浮点数，字符串等等
  **. . .**：可变参数列表
  **返回值**：输出字符的数量（成功打印字符的个数）

**例子**  
```c  
printf("%d",n);   
//打印机结果为 123
//当前所看到的123并非整型值123，而是三个字符1，2，3    
//此时printf的返回值应该为3
```

# scanf函数

>**头文件**：stdio.h
  **原型**：int scanf(const char \*format, . . . );
	  const修饰字符串不可修改
  **format** : 格式控制==字符串==（char * 类型）
	  **作用**：控制打印相关变量的方式：十进制，浮点数，字符串等等
	  %d(格式控制字符串)，&n——>相关参数的地址
  **. . .**：可变参数列表
  **返回值**：输出字符的数量（成功打印字符的个数）
	  非负数均合法，0表示成功读入零个参数，-1是第一个不合法的值

**例子**
```c
scanf("hello");
//当前读入字符串hello不读入任何参数（变量），合法但不过一般没人这么写

scanf("%d",&n);
//此时成功读入参数为 1（有多少个格式控制符则参数值返回相应数目）

while(scanf( )!=EOF)  
//EOF == end of file 判断是否读到文件的末尾( 它对应得十进制返回值为 -1 )
//也可把EOF换为-1等负数
```

# 练习1
```c
//请使用 printf 函数，求解一个数字n得十进制表示的数字位数
#include <stdio.h>
int main() {
    int n;
    scanf("%d", &n);
    n = printf("%d", n);
    printf(" has %d digits\n", n)
    return 0;
}

//修改为循环读入模式
#include <stdio.h>
int main(){
    int n;
    while(scanf("%d",&n)!= EOF) { //EOF可以换成-1等负数
        printf(" has %d digits!\n",printf("%d",n));
    }
    return 0;
}

//上述代码循环读入时若按方向下键再回车，会陷入死循环，编写代码找原因
#include<iostream>
using namespace std;

int main(){
    int n, ret;
    while((ret = scanf("%d",&n))!= EOF) {
        printf(" has %d digits! ret = %d\n",printf("%d",n), ret);
    }
    return 0;
}
```

**重复上述操作，运行结果如下**
![image.png](https://s1.vika.cn/space/2024/01/11/0adb2ca7556e411ba9b283dc639f865a)
**分析原因**：Linux下一切皆文件，按向下箭头相当于输入一个字符，由于某些原因该字符没有成功读入进变量，从而产生死循环


