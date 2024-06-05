## 拉取redis  
```bash
docker pull redis:6.2
```

## 创建映射文件  
```sh
mkdir -p /redis/conf /redis/data

touch /docker/redis/conf/redis.conf
```

配置文件地址:[https://redis.io/docs/management/config/](https://redis.io/docs/management/config/)

## 启动  
```bash
docker run --name redis6 -p 6379:6379 \
-v /home/oneao/Data/redis6/data:/data \
-v /home/oneao/Data/redis6/conf/redis.conf:/etc/redis/redis.conf \
-d redis:6.2 redis-server /etc/redis/redis.conf
```
设置开机自启
```bash
docker update --restart=always redis6 
```

## 设置远程登录

```
bind 0.0.0.0 # 应用连接需要开启这一步
protected-mode no 
daemonize no    # 设置yes为守护进程启动，会与docker run -d冲突，产生无法启动无报错的情况。
requirepass foobared # 密码
```

## 验证
```sh
docker exec -it redis6 sh # 进入容器
redis-cli # 开启redis
auth pass # 验证密码，如果出现 OK 即代表成功。
```

