---
{"title":"OB使用提醒","dg-publish":true,"time":"2024/01/12","permalink":"/0.Tips/OB使用提醒/","dgPassFrontmatter":true}
---

# 1.OB笔记导出pdf文件
经过测试，选择小报用纸最佳。

# 2.关于Digital Garden的push
- 文件夹和文档命名最好以英文命名（或者非纯中文） —— 纯中文名容易出现**永久链接permalink**冲突。
    - 解决方法 ：文件夹使用数字字母组合的名字，笔记名可以继续用中文，但要在YAML区写入 **dg-permalink: “中文笔记名”**
- 如果文档属性写了键，必须补充值 —— 即**键值对**必须成对出现，否则可能出现Eleventy构建过程中的错误导致无法更新。