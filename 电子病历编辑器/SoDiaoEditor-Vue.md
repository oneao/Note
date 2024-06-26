Vue2版本
github地址：https://github.com/tlzzu/SoDiaoEditor-Vue.git（该版本编辑器核心内容部分未开源）

Vue3版本尚未开源代码

## 集成
`SdeEditor`组件内容如下：==待做==

# 存在问题
## 1. 本地环境下无法访问public里的静态文件

### 方法1（已尝试）
1、修改 `根目录/build/plugin/index.ts`，注释掉：`vitePlugins.push(configHtmlPlugin(viteEnv, isBuild));` 这一行。
2、修改`根目录/index.html`文件，注释掉：`<title><%= title %></title>`

### 方法2（未尝试）
可以fork vite-plugin-html的代码修改下  
[![image](https://user-images.githubusercontent.com/11783658/219605846-dce087b3-ddb9-4979-8074-b5c3b8426899.png)](https://user-images.githubusercontent.com/11783658/219605846-dce087b3-ddb9-4979-8074-b5c3b8426899.png)  
发布并修改引用，将静态文件放到/public/static/目录下就可以访问了；  

### 方法3（未尝试）
直接把`package.json`中`vite-plugin-html`改为`vite-plugin-html-easy`
1、静态文件需要放到/public/static目录下，如/public/static/xxx.pdf  
2、访问地址为[http://xxx/static/xxx.pdf](http://xxx/static/xxx.pdf)

## 2.下载xml功能报错
该功能在使用**病例控件**时才会报错，因为是编译后的js源码原因，暂不进行修改和扩展。
该编辑器提供上传和下载html的方法。所以采用扩展该功能代码。







