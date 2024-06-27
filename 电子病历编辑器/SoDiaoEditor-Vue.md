Vue2版本
github地址：https://github.com/tlzzu/SoDiaoEditor-Vue.git（该版本编辑器核心内容部分未开源）

Vue3版本尚未开源代码.

# 集成
## 文件介绍
`data`目录：存放下拉框、单选框等数据。（可不设置该文件）
`dialogs`目录：用于存放`日期选择框`、`下拉框`等`html`代码，可根据已有的代码进行扩展。（**关键**）
`doc`目录：存放一些与该编辑器相关的配置信息介绍的`md`格式文档。（**关键，可参考这些文档进行配置**）
`js`目录：存放编辑器等的源代码。
`ueditor`目录：该病历编辑器就是基于`ueditor` 编辑器进行开发的，存放一些关于`ueditor`编辑器相关的，包含部分功能源码，例如：地图、链接等功能。

## 关键配置文件
文件：`sde.config.js`
如果修改sdeEditor文件夹的位置，同时也需要更改该文件中的`URL`.

## `SdeEditor`组件
配置信息都在：`sde.value = new SDE`中。
如果不需要某个功能，不在`toolbars`中填写就行。

# 存在问题
## 1. 本地环境下无法访问public里的静态文件

### 方法1（已尝试）
1、修改`根目录/build/plugin/index.ts`，注释掉：`vitePlugins.push(configHtmlPlugin(viteEnv, isBuild));` 这一行。
2、修改`根目录/index.html`文件，注释掉：`<title><%= title %></title>`

### 方法2（未尝试）
可以fork vite-plugin-html的代码修改下  
[![image](https://user-images.githubusercontent.com/11783658/219605846-dce087b3-ddb9-4979-8074-b5c3b8426899.png)](https://user-images.githubusercontent.com/11783658/219605846-dce087b3-ddb9-4979-8074-b5c3b8426899.png)  
发布并修改引用，将静态文件放到/public/static/目录下就可以访问了；  

### 方法3（未尝试）
直接把`package.json`中`vite-plugin-html`改为`vite-plugin-html-easy`
1、静态文件需要放到/public/static目录下，如/public/static/xxx.pdf  
2、访问地址为[http://xxx/static/xxx.pdf](http://xxx/static/xxx.pdf)

## 2.下载或上传xml功能报错
该功能在使用**病例控件**时才会报错，因为是编译后的js源码原因，暂不进行修改和扩展。
该编辑器提供上传和下载html的方法，所以新增控件上传模版和下载模版。
> 目前只支持`html`格式，可进行修改。
![[电子病历编辑器/1.png]]

## 3.打印功能可以使用，但配置不生效





# 注意
## 1.使用组件库无效





