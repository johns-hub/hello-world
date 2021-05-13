```mysql
  #查询锁表
  show open tables where in_use>0;
  show processlist;
  
  #查询建表语句
  SHOW CREATE TABLE test;
  
  #ID去重
  select * from temp where id in (select max(id) from temp group by id)
  
  #创建唯一索引
  ALTER TABLE `user` ADD CONSTRAINT uk_name UNIQUE(NAME);  
```

