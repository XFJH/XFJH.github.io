---
layout: post
title: "ORACLE添加监控删除记录触发器"
date: 2018-05-29 17:58:00
description: "创建一个删除记录后就触发的触发器,记录下客户端IP"
tag: oracle create trigger delete record
---

```SQL
-- 创建备份表
create table delete_bak as
select security_number, seq_no  -- 字段
from tab_name  -- 表名
where 1 > 2;

-- 添加删除时间
ALTER TABLE delete_bak ADD record_deleted_date date;
ALTER TABLE delete_bak ADD FROM_IP VARCHAR2(100);

create or replace trigger TRG_delete_bak
  before delete on tab_name -- 表名
  for each row
DECLARE
  amount NUMBER;
begin
  select count(*) INTO AMOUNT from  delete_bak;
  IF AMOUNT < 3 THEN
    insert into delete_bak(security_number, seq_no, Record_Deleted_Date, From_Ip)
     values
    (:old.security_number, :old.seq_no, sysdate, SYS_CONTEXT('USERENV', 'IP_ADDRESS'));
  END IF;
end;
```

## 知识点:

* 创建触发器
* 触发器BEGIN-END语句块中,不能又DDL语句(因为DDL内置一个commit),所以才会有`AMOUNT < 3`
写的比较死的写法
