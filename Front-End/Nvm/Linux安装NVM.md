nvm全英文也叫node.js version management，是一个nodejs的版本管理工具。nvm和n都是node.js版本管理工具，为了解决node.js各种版本存在不兼容现象可以通过它可以安装和切换不同版本的node.js。

载压缩包

```bash
cd /
wget https://github.com/nvm-sh/nvm/archive/refs/tags/v0.39.1.tar.gz
```

解压

```bash
mkdir -p /.nvm
tar -zxvf nvm-0.39.0.tar.gz -C /.nvm
```

配置环境

```bash
vim ~/.zshrc
```

在~/.zshrc的末尾，添加如下语句：

```bash
export NVM_DIR="$HOME/.nvm/nvm-0.38.0"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

使能配置

```bash
source ~/.zshrc
```

使用NVM安装node v8.16.0

```bash
nvm install 8.16.0
```

切换node版本

```bash
nvm use 14.17.3

nvm use --delete-prefix v12.1.0 # 使用删除 prefix
```

设置默认版本

```bash
nvm alias default v18.16.0
```

设置淘宝镜像源

```bash
npm config set registry http://registry.npmmirror.com
```