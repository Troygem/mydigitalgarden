---
{"title":"C语言入门基础","dg-publish":true,"time":"2024/01/12","permalink":"/cs/c/c/","dgPassFrontmatter":true}
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
- 函数原型 —— 了解系统封装好的函数途径
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
**请使用 printf 函数，求解一个数字n得十进制表示的数字位数**
```c
#include <stdio.h>
int main() {
    int n;
    scanf("%d", &n);
    n = printf("%d", n);
    printf(" has %d digits\n", n)
    return 0;
}
```

**修改为循环读入模式**
```c
#include <stdio.h>
int main(){
    int n;
    while(scanf("%d",&n)!= EOF) { //EOF可以换成-1等负数
        printf(" has %d digits!\n",printf("%d",n));
    }
    return 0;
}
```


**上述代码循环读入时若按方向下键再回车，会陷入死循环，编写代码找原因**
```c
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

# 练习2
**写一个程序，读入一个字符串（可能包含空格），输出该字符串的字符数量。**
```c
#include<stdio.h>
int main(){
    char str[100] = {0};
    scanf("%s",str);
    printf("%s\n",str);
    return 0;
}
/*
当输入hello world时只输出hello
因为scanf是通过分隔符结束当前值的传递（区别两个参数）
分隔符：（tab键）\t  \n  空格符
*/
```

**如何把空格当作合格字符放进字符串当中?** 
运用正则表达式 —— [ ^\n ]    ==(把除了\\n以外的字符都读入字符串)==
```c
#include<stdio.h>
int main(){
    char str[100] = {0};
    while(scanf("%[^\n]s",str) != EOF) { //注意别漏了%
        printf("%s\n",str);  
    }
    return 0;
}
```

**发现会陷入死循环，修改程序检查原因**
```c
#include<stdio.h>
int main(){
    int ret = 0;
    char str[100] = {0};
    while((ret = scanf("%[^\n]s",str)) != EOF) {
        printf("%s ret = %d\n",str, ret);  
    }
    return 0;
}
```

**运行结果如下👇**
![image.png](https://s1.vika.cn/space/2024/01/12/f562d33928e340e591c5a2e0fe60fcf0)

**分析原因👇**
ret = 0 —— 说明后面的参数每次都没有成功读入str数组里面
使用`./a.out > out`查看结果 （标准输出重定向，将结果打印到自定义文件里）
![image.png](https://s1.vika.cn/space/2024/01/12/0ecaa872b0d841e2a536ef9a4b87f8cb)
**深入分析**
- 字符串输入是呈流式读入的（输入流），假设一个哨兵在检查字符串的内容`hello world\n`,读到`\n`时本轮读入结束，然后直接打印第一轮结果。
- 在第二轮读入时哨兵仍会卡在上一个`\n` —— 因为没人去接收它，所以会一直卡在那里停止结束，不断输出`str`里的内容
- 解决办法是干掉那个`\n`  —— 可以利用`getchar( );` 强行吞掉上一个字符
```c
 while((ret = scanf("%[^\n]s",str)) != EOF){
   getchar();
   printf("%s ret = %d\n",str, ret);  
 }
```

**非循环读入版本代码**
```c
#include<stdio.h>
int main(){
    int n;
    char str[100];
    scanf("%[^\n]s",str);
    n = printf("%s",str);
    printf(" has %d digits!\n",n);
    return 0;
}
```

# 补充
- **none code == none bug**
- **gets在工业当中禁止使用**（很危险，因为什么都可以读入）
- **scanf("`%[^\n]s`",str)中若改为scanf("`%[^\n]`",str)（缺少一个s）也可以读入，所以这个s是多余的吗，二者有何区别？**
	- ==回答==：s是多余的，s实际上会作为一个掩码字符，是否起作用与读入内容相关
	- ==例子1==：使用格式控制字符串`%[^\n]s`，读入内容：`hello world[换行]`，这种情况下督导`[换行]`以前都是`%[^\n]`这一部分在起作用。接下来到了`s`字符时，匹配到的是换行符，匹配失败，所以此时`s`字符并没有起作用，成了多余的字符。
	- ==例子2==：使用格式控制字符串`%3[^\n]s`，读入内容：`helslo world[换行]`，`%3[^\n]s`这一部分会读取前3个字符，也就是`hel`，接下来到了`s`字符时匹配到的是内容中的`s`字符，此时内容中的`s`字符就被吞掉了，下一次读取的时候，就是从`lo`这个位置开始读取。
	- ==总结==：从以上角度来看，该代码确实存在小bug，正确情况是修改为`%[^\n]\n`，即将s替换成`\n`

# 参考资料
> **维基百科**：格式化字符串
>
> **编码规范**：编码规范（`百度+谷歌编码规范`或 `阿里+谷歌编码规范`），范例
>
>**书籍**：C语言核心技术 （原书第2版） 机械工业出版社
> 	**学习建议**
> 		第三部分 基本工具（略读）
> 		第1-8章（快速浏览）
> 		第9-10章（精读）
> 		第11-15章（快速浏览）
> 		全书重新浏览一遍（加深印象）
> 		 

# 第一章代码演示
## printf家族
- `sprintf`中的`s` —— `str[ ]` （字符串拼接）
- `fprintf`中的`f` —— `file` （打印到文件）
```c
int main(){
    int n;
    char str[1000] = {0};
    scanf("%d",&n); // stdin
    printf("%d\n",n); //stdout stderr
    sprintf(str,"%d.%d.%d.%d",192,168,1,2);
    printf("str = %s\n", str);
    FILE *fout = fopen("output","w");
    fprintf(fout,"%s\n",str);//打印到moutput文件
    fprintf(stdout,"%s\n",str);//打印到标准输出中去
    return 0;
}
```

## stdout和stderr的区别
```c
FILE *fout = fopen("output","w");
fprintf(stdout,"stdout = %s\n",str);
fprintf(stderr,"stderr = %s\n",str);
```
<img src="https://s1.vika.cn/space/2024/01/12/8057f33eae194dc09d78889186acde53" alt="image.png" style="zoom:80%;" />
**相同点**：二者都会打印到在标准输出中（即控制台）
**不同点**：当用标准输出重定向时，只会打印标准错误输出，标准输出会重定向到自定义文件里，如下例子👇
<img src="https://s1.vika.cn/space/2024/01/12/59963a12ca834180851d68758f960fad" alt="image.png" style="zoom: 80%;" />

# 思考
**如何将标准错误重定向到自定义文件里?（Linux内容）**
```c
//将标准错误重定向到自定义文件
./a.out 2> xxx    

//将标准输出和错误都重定向到自定义文件
./a.out &> out4
./a.out > xxx 2>&1 

//文件和屏幕都打印标准输出和标准错误
./a.out 2>&1  | tee x
```

**重定向的好处**
好处：运行中的错误可以定义在一个文件，查看是否为空判断对错。