> 基于  `kali` 系统实现，不过步骤都类似。

下载地址：[https://maven.apache.org/download.cgi](https://maven.apache.org/download.cgi)

解压到指定文件夹内，进行环境变量配置。

```bash
sudo vim ~/.zshrc
# maven 环境
export MAVEN_HOME=/home/oneao/DevTools/apache-maven-3.8.8
export PATH=$MAVEN_HOME/bin:$PATH

source ~/.zshrc
```

执行 `mvn -v`检验是否安装成功。