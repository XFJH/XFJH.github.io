---
layout: post
title: "关系表设计三范式"
date: 2018-05-31 22:47:00
description: "关系表设计三范式"
tag: database design theory concept
---

## 格式简介：  
【表名】（__主键字段A__, 字段B， 字段C， 字段D）

## 数据库涉及三范式：
1. 第一范式(1NF)：原子性，列不可再分

2. 第二范式(2NF)：完全主键依赖。首先是 1NF，另外包含两部分内容，一是表必须有 <b>一个</b>主键；二是没有包含在主键中的列必须完全依赖于主键，而不能只依赖于主键的一部分。

  例如：订单明细表【OrderDetail】（__OrderID__，__ProductID__，UnitPrice(单价)，Discount(折扣)，Quantity(数量)，ProductName(产品名)），满足第一范式，但不满足第二范式。

    <i>原因是: 单价,数量这个两个字段依赖的是, 产品ID, 而不是 订单ID跟产品ID;</i>

    拆分后满足2NF:  

    订单详情表：【OrderDetail】（__OrderID__，ProductID，Discount，Quantity）  
    商品表：  【Product】（__ProductID__，UnitPrice , ProductName）

3. 第三范式(3NF)：只依赖主键，消除传递依赖。首先是2NF, 然后是任何非主属性不依赖于其他非主属性。

  例如：
  满足2NF的订单表【Order】（__OrderID__，OrderDate，CustomerID，CustomerName，CustomerAddr，CustomerCity），不满足3NF.

    <i>原因是: 订单信息表内有客户信息的传递依赖, 如果客户信息变更的化,要修改订单表的多条记录,
    订单下的客户信息应该另存一张表</i>

    拆分后满足3NF:  

    订单表：【Order】（__OrderID__，OrderDate，CustomerID）  
    顾客表：【Customer】（__CustomerID__，CustomerName，CustomerAddr，CustomerCity）
