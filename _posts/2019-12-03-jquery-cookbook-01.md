---
layout: post
title: "JQuery学习记录"
date: 2019-05-17 17:14:47
description: "JQuery学习记录"
tag: jquery
---


## 语录

1. 采用无干扰式JavaScript方法论的现代JavaScript程序通常只在DOM完全加载之后才执行JavaScript。


## FAQ

1. 在HTML种包含jQuery的程序库代码
> script标签

2. 在DOM加载之后，整个页面加载之前执行
```js
jQuery(document).ready(function(){
  // ready 定义一个DOM可以
}).
```

3. 用选择器和jQuery函数选择DOM元素

4. 在指定上下文种选择DOM元素

> 第二个参数指定上下文

5. 过滤DOM元素包装器集

6. 查找当前选择包装器集中的后代元素

7. 返回破坏性修改之前的选择

8. 将前一个选择集包含到当前选择集

9. 根据当前上下文遍历DOM获得新的DOM

10. 创建、操作和插入DOM元素

11. 删除DOM元素

12. 替换DOM元素

13. 克隆DOM元素

14. 获取、设置和删除DOM元素属性

15. 获取和设置HTML内容

16. 获取和设置文本内容

17. 在不造成全局冲突的情况下使用$别名
