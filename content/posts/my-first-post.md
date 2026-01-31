+++
date = '2026-01-29T12:27:19+08:00'
draft = false
title = 'My First Post'
+++

### 教程：

https://blog.eimoon.com/p/learn-hugo-blog-building-from-beginner-to-advanced/

### 主题设置：

Hugo 在 v0.124.0 版本之后彻底删除了 `.Site.Social` 这个用法。

#### 第一步：定位文件

报错通常出现在主题的导航栏、页脚或关于页面。

#### 第二步：替换代码

将所有找到的 **`.Site.Social`** 替换为 **`.Site.Params.Social`**。
