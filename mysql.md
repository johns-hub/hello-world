```shell
  $ show open tables where in_use>0;
  $ show processlist;
  $ SHOW CREATE TABLE test;
  
  $ select * from temp where id in (select max(id) from temp group by id)
```
