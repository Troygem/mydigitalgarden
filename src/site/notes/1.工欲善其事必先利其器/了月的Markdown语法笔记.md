---
{"title":"了月的markdown语法笔记","dg-publish":true,"time":"2024/01/12","permalink":"/1.工欲善其事必先利其器/了月的Markdown语法笔记/","dgPassFrontmatter":true}
---

# 1.Markdown的简介
Markdown是一种轻量级的标记语言，Markdown致力于让创作或者阅读文档变得更加容易
hyper text markup language(html)超文本标记语言

# 2.标题
**语法**： # （一级标题） ## （二级标题） ### （三级标题）......

**代码👇**：注意#后面要跟一个空格才会生效

```markdown
# 这是一级标题
## 这是二级标题
### 这是三级标题
......
```

**效果👇**：
# 这是一级标题
## 这是二级标题
### 这是三级标题

**快捷键**：
- crtl+数字1-5可以快速将所在行的标题文字调成对应级别的大小
- ctrl+加号/减号对标题级别进行加减

# 3.段落
**语法**：直接对文字的编辑 如需新建下一段落可直接换行或者在段落的末尾敲空格回车

**代码👇**：
```markdown
这是一个段落 
这是一个段落 
```

**效果👇**：
这是一个段落
这是一个段落

# 4.字体
**语法**：
1.粗体 用一对双星号包裹
2.删除线 用一对双飘号进行包裹
3.下划线 用一对u标签进行包裹
4.斜体 用一对双星号包裹

**代码👇**：
```markdown
**这是粗体**
~~这是删除线~~
<u>这是下划线</u>
*这是斜体*
```

**效果👇**：
**这是粗体**
~~这是删除线~~
<u>这是下划线</u>
_这是斜体_

# 5.分割线
**语法**：三个减号回车

**代码👇**：
```markdown
--- 回车
```

**效果👇**：

---

# 6.脚注
**说明**：脚注是对文本进行补充说明的

**代码👇**：
```markdown
[^spring boot]是一个技术
[^spring boot]:这是一个非常好用的框架
```

**效果👇**：
[^spring boot]是一个技术
[^spring boot]:这是一个非常好用的框架

# 7.列表
### **无序列表**
**代码👇**：
```markdown
* 空格
- 空格
```

**效果👇**：
1、只有同一级别
- 苹果
- 香蕉
- 橘子

2、含子级别
- 一级分类
	- 二级分类
	    - 三级分类

### 有序列表
**代码👇**：
```markdown
1.空格 （回车）
```

**效果👇**：
1. 第一标题
2. 第二标题
    - 这是内容
3. 第三标题

# 8.区别显示
**代码👇**：
```markdown
>回车
```

**效果👇**：
> 这是最外层区块
>
> > 这是内层
> >
> >  >这是更内层
>
> 

# 9.代码块显示
**代码👇**：
```markdown
```js/Java/C/C++/text
......
```

**效果👇**：
```js
function test (){
    alert("Hello, 了月");
}
```

```c#
public class Test(){
    public static void main(String[] args){
        Console.write("Hello,Amy");
    }
}
```

```c
#include <stdio.h>
int main(){
    printf("Hello,world\n");
    return 0;
}
```

# 10.链接
**代码👇**：
```markdown
www.baidu.com
[百度一下](https://www.baidu.com)
```

**效果👇**：
[www.baidu.com](www.baidu.com)
[百度一下](https://www.baidu.com/)

# 11.插入图片
**说明**：可以选择本地或在线图床，复制粘贴直接生成对应代码（按需修改属性）

**代码👇**：
```markdown
![自定义图片的路径]（图片的路径）
```

**效果👇**：
![girl.jpg](https://s1.vika.cn/space/2022/12/13/4bbc61059801493588ec5dab2b683ef4)

![star.jpg](https://images.hdqwalls.com/wallpapers/girl-playing-violin-in-space-4k-ss.jpg)

# 12.表格
**说明**：代码麻烦，建议直接快捷键生成（**Typora**里的是`Ctrl + T`）

**代码👇**：
```markdown
|表头|表头|表头|
|-|-|-|
|1|2|3|
|6|6|6|
|8|8|8|
```

**效果👇**：

|表头|表头|表头|
|---|---|---|
|1|2|3|
|6|6|6|
|8|8|8|
# 13.其他操作
**代码👇**：
```markdown
<kbd>Ctrl</kbd>  <kbd>shilft</kbd>
`ctrl`+`v` 粘贴
==这是重点== 高亮
```

**效果👇**：
<kbd>Ctrl</kbd>  <kbd>shilft</kbd>
`ctrl`+`v` 粘贴
==这是重点== 高亮