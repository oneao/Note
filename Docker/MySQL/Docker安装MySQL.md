拉取镜像

``` bash
docker pull mysql:8.0.20
```

创建文件夹

``` bash
sudo mkdir -p ~/Data/mysql/{data,logs,conf}
```

创建 `my.cnf`配置文件

```
# Copyright (c) 2017, Oracle and/or its affiliates. All rights reserved.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 2 of the License.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301 USA

#
# The MySQL  Server configuration file.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

[mysqld]
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
datadir         = /var/lib/mysql
secure-file-priv= NULL
# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0

# Custom config should go here
!includedir /etc/mysql/conf.d/

# 时区设置
default-time_zone = '+8:00'
```

运行容器

``` bash
docker run --restart=always -d \
	-v /home/oneao/Data/mysql8/conf/my.cnf:/etc/mysql/my.cnf \
	-v /home/oneao/Data/mysql8/logs:/logs \
	-v /home/oneao/Data/mysql8/data:/var/lib/mysql  \
	-p 3306:3306 --name mysql8 \
	-e MYSQL_ROOT_PASSWORD=root mysql:8.0.20
```

设置开机自启
```bash
docker update --restart=always mysql8
```


```
docker run --restart=always -d \
	-v /home/oneao/Data/mysql8/conf:/etc/mysql/conf.d \
	-v /home/oneao/Data/mysql8/logs:/logs \
	-v /home/oneao/Data/mysql8/data:/var/lib/mysql  \
	-p 3306:3306 --name mysql8 \
	-e MYSQL_ROOT_PASSWORD=root mysql:8.0.20 \
	-init-connect="SET collation_connection=utf8mb4_0900_ai_ci" --init-connect="SET NAMES utf8mb4" --skip-character-set-client-handshake

docker run --name mysql -v /mydata/mysql/log:/var/log/mysql -v /mydata/mysql/data:/var/lib/mysql -v /mydata/mysql/conf:/etc/mysql/conf.d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql --init-connect="SET collation_connection=utf8mb4_0900_ai_ci" --init-connect="SET NAMES utf8mb4" --skip-character-set-client-handshake

```