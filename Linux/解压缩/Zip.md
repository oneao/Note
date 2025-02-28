## 压缩
安装

```
sudo apt-get install zip
```

压缩文件夹

```
zip -r test.zip test
```

将 `test`文件夹压缩为 `test.zip`
## 解压
在 Linux 中，解压 zip 压缩文件是一个常见的操作。为了解压 Zip 文件，我们可以使用 unzip 命令。unzip 命令是一个非常简单易用的工具，可以快速地解压 Zip 文件到指定目录。下面小哈将详细说道说道它：

### 1. 基本语法

unzip 命令的基本语法如下：

```
unzip 压缩文件名.zip -d 目标目录
```

- unzip: 表示解压 Zip 文件的命令。
- 压缩文件名.zip: 指定要解压的 Zip 压缩文件名。
- -d 目标目录: 指定解压后的目标目录。如果不指定该选项，文件将解压到当前工作目录。

### 2. 解压到当前目录

要将 Zip 文件解压到当前目录，只需执行以下命令：

```
unzip 压缩文件名.zip
```

例如，如果要解压名为 "archive.zip" 的 Zip 文件到当前目录，执行以下命令：

```
unzip archive.zip
```

### 3. 解压到指定目录

如果你希望将 Zip 文件解压到特定的目标目录，可以使用 -d 参数指定目标目录：

```
unzip 压缩文件名.zip -d 目标目录
```

例如，要将 "archive.zip" 解压到 "/home/user/documents" 目录，执行以下命令：

```
unzip archive.zip -d /home/user/documents
```

### 4. 查看 Zip 文件内容

如果你想查看 Zip 文件的内容列表，而不解压它，可以使用 -l 参数：

```
unzip -l 压缩文件名.zip
```

例如，要查看 "archive.zip" 文件的内容列表，执行以下命令：

```
unzip -l archive.zip
```

unzip 命令将显示 Zip 文件中的所有文件和目录。
