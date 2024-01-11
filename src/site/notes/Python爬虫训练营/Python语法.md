---
{"title":"Python","dg-publish":true,"permalink":"/python/python/","dgPassFrontmatter":true}
---


**变量**：相当于只能存放一个东西的盒子（注意命名规范）

**相等判断**：\==（值是否相等），is（类型和值是否都相等）

**打印操作**：print()
```python
name = 6  
print(name)  
print(1,2,3,4)  
print(1+2)  
print('1+2=',1+2)
```

**输入操作**：input()，程序运行到该方法时会暂停等待输入

name = input()  
troy  
name

**定义字符串**：

单引号定义（允许存在双引号），双引号定义（允许存在单引号）

三重引号定义字符串，支持换行（可分为三重单引号和三重双引号）

**字符串格式化**：format 和 f-string是常见的两种方式

name = 'ayu'  
age = 30  
s1 = '你好，我叫{name}，我今年{age}岁了，请多多指教'  
print(s1.format(name=name, age=age))  
s2= f'你好，我叫{name}，我今年{age}岁了，请多多指教'  
print(s2)

**字符串常量**：string是py中内置的库，包含很多字符串操作，下面是它内置的字符串常量

import string  
​  
string.ascii_uppercase  
string.ascii_lowercase  
string.ascii_letters  
string.digits

**随机生成字符串**：利用字符串常量和random库

import string  
import random  
​  
s = string.ascii_letters + string.digits  
numbers = random.sample(s, 10)  
''.join(numbers)  
'|'.join(numbers)  
','.join(numbers)

**字符串切片**

s="Python"  
s[0]='P'  
s[3]='h'  
s[o]='o'  
s[n]='n'  
s[:]='Python'  
s[0:]='Python'  
s[:6]='Python'  
s[1:4]='yth'

**字符串操作常用方法**

|方法名|作用|
|---|---|
|len（str）|返回str字符串的长度|
|str.find(s, beg=0, end=len(str))|在原始字符串中搜索s字符串|
|str.lower()|将字符串中所有的大写字符转为小写|
|str.upper()|将字符串中所有的小写字符转为大写|
|str.strip([chars])|删除字符串两端的空格和指定字符|
|str.split(s)|以s为分隔符分割原字符串|
|str.replace(old, new)|将字符串中的old替换为new|

**列表（list）**：可以理解为一组变量盒子

#如何获取l列表对象最后的值  
l[len(l)-1]  或 l[-1]  
​  
#利用切片去取 【) —— 闭区间和开区间  
l[开始下标:结束下标]   
如l=[1,2,3,4]   取l[1:3]得到2，3  取l[-3,-1]得到2，3  
如l=[[1,2],[1,3]  取l[0][1]得到2

**列表的增删查改操作**

|方法名|作用|
|---|---|
|list.append(obj)|将obj对象添加到列表末尾|
|list.extend(new_list)|在列表末尾添加新的|
|list.count(obj)|统计某个元素在列表中出现的次数|
|list.index(obj)|从列表中找出obj第一次出现的位置|
|list.insert(index,obj)|将obj对象插入到列表中|
|list.remove(obj)|删除列表中的第一个匹配的obj对象|
|list.pop()|删除列表中最后一个元素|
|len(list)|列表元素个数|

**元组（tuple）**：将列表的中括号改为小括号 —— 如 **l=(1,2,3)** 或者 **l = 1,2,3**

**元组的特点**：不能修改单个值 —— 报错，但可以直接替换整个元组 如 **l=(1,2,3) l=(4,5,6)** —— 修改的是变量本身而非元组

**获取变量的唯一标识**：**id()** 如 a=(1,2,3) id(a) —— 元组修改后id变化，列表修改后id不变

**可视化代码网址**：pythontutor.com

![image-20240109162400314](file:///D:/%E7%99%BE%E5%BA%A6%E4%BA%91/CS/%E6%A2%81%E5%8D%8E%E7%9A%84%E7%BC%96%E7%A8%8B%E4%B8%96%E7%95%8C/Python/%E5%BD%AD%E6%B6%9BPython%E7%88%AC%E8%99%AB%E8%AE%AD%E7%BB%83%E8%90%A5.assets/image-20240109162400314.png?lastModify=1704948436)

![image-20240109162552743](file:///D:/%E7%99%BE%E5%BA%A6%E4%BA%91/CS/%E6%A2%81%E5%8D%8E%E7%9A%84%E7%BC%96%E7%A8%8B%E4%B8%96%E7%95%8C/Python/%E5%BD%AD%E6%B6%9BPython%E7%88%AC%E8%99%AB%E8%AE%AD%E7%BB%83%E8%90%A5.assets/image-20240109162552743.png?lastModify=1704948436)

**字典**：通过大括号将元素括起来，其中的元素分别由key（键）和value（值）组成，无序

通过get方法回去字典中的值，如果设定默认值时找不到就返回默认值，未设置默认值则找不到返回none

my = {’name': 'ayu', 'age': 22, 'interest': 'code'}  
my['name']  ——  ‘ayu’  
my.get['name',0]  
my.get['aaa',0]      

**字典的常用方法**

|方法名|作用|
|---|---|
|dict.clear()|删除字典中所有元素|
|dict.copy()|浅拷贝当前字典|
|key in dict|判断某个key是否存在于字典中|
|dict.keys()|当前字典所有key的可迭代对象|
|dict.values()|当前字典所有values的可迭代对象|
|pop(key)|删除字典中key对应的元素|

**集合（set）**：无序且不存在重复元素，重复元素会被删除，如animals = {'cat', 'dog'}

**集合的常用方法**：
如果不确定删除的元素是否存在 —— 最好使用discard

|方法名|作用|
|---|---|
|set.add()|向集合中添加元素|
|set.update(list)|想集合中添加多个元素|
|set.remove(obj)|删除集合中的obj元素|
|set.pop()|随机移除集合中的元素|
|set.discard()|删除集合中指定元素，该元素不在集合中不报错|
|set.clear()|删除集合中所有元素|

**妙用集合不可重复的特性**

给数据去重 —— 将其他容器对象中的数据进行去重

l = 【1，2，3，2，2，2，3，3，3，1，1，2，3】  
s = set(l)  
s 变为 {1，2，3}

**set集合运算**

|运算操作|运算符|含义|例子|
|---|---|---|---|
|取交集|&|取两集合公共的元素|set1 & set2|
|取并集|\||取两集合全部的元素|set1 \| set2|
|取差集|-|取一个集合中另一个集合中没有的元素|set1 - set2|
|对称差集|^|取集合A与集合B中不属于A&B的元素|set1 ^ set2|

**浅拷贝和深拷贝**
==变量并非盒子==：py中的变量是引用型变量，变量的内存空间存的是值对应的内存地址而非值本身，当访问变量时会获取其存储的内存地址，再通过该地址获取其中的值

==变量是便利贴==： py的赋值语句是从右向左运行的，即先创建具体值再将值分配给对应变量，相当于贴上变量的便利贴