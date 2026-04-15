+++
date = '2026-04-15T14:04:49+08:00'
draft = false
title = 'BFC'
+++

`BFC`（Block Formatting Context）直译为 “块级格式化上下文”，它是页面上的一个隔离的独立容器 

## 创建 BFC： 

`float` 不为 `none`

`position: absolute` 或 `position: fixed`

`display: inline-block`

`overflow` 不为 `visible`，如 `hidden`、`auto`、`scroll`

## BFC 的作用

1. 防止 `margin-top / margin-bottom` 外边距塌陷

   ```html
   <style>
     .box {
       width: 200px;
       height: 50px;
       margin: 50px;
       border: 1px #fff solid;
     }
   </style>
   <body>
     <div class="container">
       <div class="box">box1</div>
     </div>
     <div class="container">
       <div class="box">box2</div>
     </div>
   </body>
   ```
   
   ```css
   .container {
     overflow: hidden; /* 触发BFC 解决以上边距重叠问题 */
   }
   ```

2. 清除内部浮动，解决父元素高度塌陷

   ```html
   <style>
     .container {
       border: 1px solid red;
       width: 400px;
     }
     .box {
       border: 1px green solid;
       float: left; /* 浮动导致父元素内容塌陷 */
       width: 100px;
       height: 100px;
       background: skyblue;
     }
   </style>
   <body>
     <div class="container">
       <div class="box"></div>
       <div class="box"></div>
       <div class="box"></div>
     </div>
   </body>
   ```

   ```css
   .container {
     border: 1px solid green;
     width: 400px;
     overflow: hidden;
     /* 添加overflow：hidden; 创建BFC，清除浮动所带来的塌陷 */
   }
   ```

3. 避免元素被浮动元素覆盖

   没有实际意义，实际开发不会这么用，只具有理论意义

   但要明白需要并排显示的盒子，要么都浮动，要么都不写，以下的写法是不合法规范的

   ```html
   <style>
     .float-div {
       float: left;
       width: 50px;
       height: 50px;
       border: 1px solid skyblue;
     }
     .normal-div {
       width: 200px;
       height: 200px;
       border: 1px solid skyblue;
     }
   </style>
   <body>
     <div class="float-div">box1</div>
     <div class="normal-div">box2</div>
   </body>
   ```

   ```css
   .normal-div {
     width: 200px;
     height: 200px;
     border: 1px solid skyblue;
     overflow: hidden; /* 触发了BFC */
   }
   ```

## 清除浮动企业解决方案

1. 让内部有浮动的父盒子形成 BFC，它就能关闭住内部的浮动。

   最好的方法就是 **`overflow: hidden;`** 

2. 给后面的父盒子设置 `clear: both;` 

   `clear` 表示清除浮动对自己的影响，`both` 表示左右浮动都清除 

3. 使用 `::after` 伪元素 给盒子添加最后一个子元素，并且给 `::after` 设置 `clear:both;` 强烈推荐使用 ！！！

   ```html
   <style>
     div {
       border: 1px solid red;
       margin-bottom: 20px;
     }
     /* 添加伪元素 ::after 匹配选中的元素的最后一个子元素 */
     .clearfix::after {
       content: "";
       clear: both;
       /* 转为块级元素 */
       display: block;
     }
     p {
       width: 100px;
       height: 100px;
       background-color: skyblue;
       margin-right: 10px;
       float: left;
     }
   </style>
   <body>
     <div class="clearfix">
       <p></p>
       <p></p>
     </div>
     <div class="clearfix">
       <p></p>
       <p></p>
     </div>
   </body>
   ```
