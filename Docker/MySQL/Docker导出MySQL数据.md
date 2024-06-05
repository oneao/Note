
## 导出指定数据库 表结构及数据

``` bash
 docker exec -it  mysql_mysql_1 mysqldump -uroot -proot 数据库名 > /tmp/user.sql
```

## 只导出数据 不导出结构

```bash
mysqldump　-t　数据库名　-uroot　-p　>　xxx.sql
docker exec -it  mysql_mysql_1 mysqldump -t -uroot -proot 数据库名 > /tmp/user.sql
```

## 只导结构不导数据

```bash
mysqldump　--opt　-d　数据库名　-u　root　-p　>　xxx.sql
docker exec -it  mysql_mysql_1 mysqldump --opt -d -uroot -proot 数据库名 > /tmp/user.sql
```

## 导出特定表的结构

```bash
mysqldump　-uroot　-p　-B　数据库名　--table　表名　>　xxx.sql
docker exec -it  mysql_mysql_1 mysqldump -B -uroot -proot 数据库名 --table '表名' > /tmp/user.sql
```