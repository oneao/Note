## 不使用 limit 、offset分页
### 存在问题
数据量小的情况下使用`limit`分页勉强可以，但是一旦数据量变大的情况下查询速度就会变得非常慢。因为在进行分页操作的时候，数据库就要进行**全表扫描（一些特殊情况下）** ，一般情况下， 会丢弃前 limit 条记录。这样就会消耗了大量的磁盘I/O，数据传输开销就会过大。

### 解决方法

**1.使用主键（唯一字段）和Limit**
原Sql语句：`select * from dual limit 10 offset 800001`
优化后的Sql语句：`select * from dual where id > 800000 limit 10` 
要使用这种基于游标的分页，需要有一个惟一的序列字段 (或多个)，比如唯一的整数 ID 或时间戳，但在某些特定情况下可能无法满足这个条件。
>参考网站：[https://blog.csdn.net/weixin_47428270/article/details/126584950](https://blog.csdn.net/weixin_47428270/article/details/126584950)

**2.利用覆盖索引优化**
**覆盖索引**：mysql的查询字段全部命中索引。
覆盖索引是非常快的,因为查询只需要在索引上进行查找,之后可以直接返回,而不用再回数据表拿数据.因此我们可以先查出索引的ID,然后根据Id拿数据.
`select * from (select id from dual limit 800000,1) a left dual job b on a.id = b.id;`
>参考网站：[https://blog.csdn.net/weixin_30513765/article/details/113296898](https://blog.csdn.net/weixin_30513765/article/details/113296898)
