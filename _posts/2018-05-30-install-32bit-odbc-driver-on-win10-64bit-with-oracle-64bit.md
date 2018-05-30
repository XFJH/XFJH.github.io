---
layout: post
title: "为win10数据源安装oracle-32bit数据驱动"
date: 2018-05-29 17:58:00
description: "在win10-64bit系统兼容安装64bit和32bit的数据源驱动"
tag: win10 oracle data-driver 32bit
---

#### 开始环境
系统： win10 64bit
数据库： oracle 11gR2 64bit
数据源： 64bit

#### 需求
在使用informatica powerdesigner 过程中，添加数据源只支持32bit的数据源，需要在本地安装32bit数据源驱动来进行下一步的开发工作

在添加新的数据驱动过程中，不能影响以前的64bit驱动。

#### 安装步骤
1. 下载必要文件
  1. instantclient-basic-nt-11.2.0.4.0.zip
  2. instantclient-odbc-nt-11.2.0.4.0.zip
下载地址：http://www.oracle.com/technetwork/database/exadata/winsoft-085727.html

2. 安装数据驱动
  1. 解压两个文件到同一安装目录
      建议安装到oracle的安装目录下,我的Oracle安装目录：`D:\app\lenovo\product`
      安装后就是下面这样的，所有解压的文件都在instantclient_11_2文件夹里
      ``` cmd
      D:\app\lenovo\product
       |———————————————————11.2.0
       |———————————————————instantclient_11_2

      ```

  2. 在管理员权限下的cmd窗口执行安装

      ``` cmd
      D:\app\lenovo\product\instantclient_11_2>odbc_install.exe
      Oracle ODBC Driver is installed successfully.

      ```

3. 测试
  1. 打开`ODBC数据源管理程序（32bit)`查看`数据驱动`tab页下有没有新增驱动。默认是"Oracle in instantclient_11_2"
  2. 如果驱动程序的话，可以在`用户DSN`下创建数据源试试


ps😂:
odbc数据源管理程序（32bit）路径：`C:\WINDOWS\syswow64\odbcad32.exe`
odbc数据源管理程序（64bit）路径：`C:\WINDOWS\system32\odbcad32.exe`

摘抄自：https://blog.csdn.net/buxizhizhou530/article/details/45228665
