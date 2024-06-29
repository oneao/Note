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
1、修改`根目录/build/vite/plugin/index.ts`，注释掉：`vitePlugins.push(configHtmlPlugin(viteEnv, isBuild));` 这一行。
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
1. 目前支持`html`格式，可进行修改。
![[电子病历编辑器/imgs/1.png]]
2. 也可以使用`sde.value.exportXML()`方法。
## 3.打印功能可以使用，但配置不生效.
### 3.1 分页符不生效
新增组件内的方法

# 注意
## 1.使用组件库无效
## 2.使用日期控件必须设置默认值
## 3.控件填过内容的变化
```html
===原始内容（未填写/选择）==============
<p>标签控件：
   <span class="sde-ctrl sde-label" id="BiaoQian" sde-type="label" title="" style="background-color: rgb(188, 255, 127);" sde-model="%7B%22desc%22%3A%22%22%7D">标签内容</span>
</p>
<p>单行文本：
   <span class="sde-ctrl" contenteditable="false" id="DanHangWenBen" sde-type="text" sde-right="." sde-model="%7B%22desc%22%3A%22%E5%8D%95%E8%A1%8C%E6%96%87%E6%9C%AC%E5%86%85%E5%AE%B9%22%2C%22required%22%3A0%2C%22strictverify%22%3A0%2C%22notdel%22%3A0%2C%22verify%22%3A%22%5E%5B0-9%5D*%24%22%2C%22mode%22%3A%22EDITOR%22%7D">
      <span class="sde-value" contenteditable="true" sde-left="[" sde-right="]" title="单行文本内容">单行文本内容</span>
   </span>
</p>
<p>下拉选择（单选）：
   <span class="sde-ctrl" contenteditable="false" id="SelectOne" sde-type="select" sde-right="." sde-model="%7B%22desc%22%3A%22%E5%8D%95%E9%80%89%22%2C%22required%22%3A0%2C%22multi%22%3A0%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22bindingdata%22%3A%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Apple%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22Orange%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%223%22%2C%22label%22%3A%22Banana%22%2C%22selected%22%3A0%7D%5D%2C%22remotedata%22%3Anull%7D" sde-isloadasyncdata="true" bindingdata="[{&quot;value&quot;:&quot;0&quot;,&quot;label&quot;:&quot;Apple&quot;,&quot;selected&quot;:0},{&quot;value&quot;:&quot;1&quot;,&quot;label&quot;:&quot;Orange&quot;,&quot;selected&quot;:0},{&quot;value&quot;:&quot;3&quot;,&quot;label&quot;:&quot;Banana&quot;,&quot;selected&quot;:0}]" sde-updatetime="2024-06-28T15:38:32.538Z">
      <span class="sde-value sde-select" contenteditable="true" sde-left="[" sde-right="]" title="单选">单选</span>
   </span>
</p>
<p>下拉选择（多选）：
   <span class="sde-ctrl" contenteditable="false" id="SelectMore" sde-type="select" sde-right="." sde-model="%7B%22desc%22%3A%22%E4%B8%8B%E6%8B%89%E5%A4%9A%E9%80%89%22%2C%22required%22%3A0%2C%22multi%22%3A1%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22bindingdata%22%3A%5B%7B%22value%22%3A%221%22%2C%22label%22%3A%22Apple%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%220%22%2C%22label%22%3A%22Orange%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%222%22%2C%22label%22%3A%22Banana%22%2C%22selected%22%3A0%7D%5D%2C%22remotedata%22%3Anull%7D" sde-isloadasyncdata="true" bindingdata="[{&quot;value&quot;:&quot;1&quot;,&quot;label&quot;:&quot;Apple&quot;,&quot;selected&quot;:0},{&quot;value&quot;:&quot;0&quot;,&quot;label&quot;:&quot;Orange&quot;,&quot;selected&quot;:0},{&quot;value&quot;:&quot;2&quot;,&quot;label&quot;:&quot;Banana&quot;,&quot;selected&quot;:0}]" sde-updatetime="2024-06-28T15:39:49.431Z">
      <span class="sde-value sde-select" contenteditable="true" sde-left="[" sde-right="]" title="下拉多选">下拉多选</span>
   </span>
</p>
<p>日期控件：
   <span class="sde-ctrl" contenteditable="false" id="RiQi" sde-type="date" sde-right="." sde-model="%7B%22desc%22%3A%22%E6%97%A5%E6%9C%9F%E5%86%85%E5%AE%B9%22%2C%22required%22%3A0%2C%22strictverify%22%3A0%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22min%22%3A%22%22%2C%22max%22%3A%22%22%2C%22format%22%3A%22%7Byyyy%7D-%7BMM%7D-%7Bdd%7D%20%7Bhh%7D%3A%7Bmm%7D%3A%7Bss%7D%22%2C%22defvalue%22%3A%222024-06-28%2012%3A00%3A00%22%7D">
      <span class="sde-value" contenteditable="true" sde-left="[" sde-right="]" title="日期内容">日期内容</span>
   </span>
</p>
<p>单选框：
   <span class="sde-ctrl" contenteditable="false" id="DanXuan" sde-type="radio" sde-right="." sde-model="%7B%22desc%22%3A%22%E5%8D%95%E9%80%89%E6%A1%86%22%2C%22required%22%3A0%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22bindingdata%22%3A%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D%5D%2C%22remotedata%22%3Anull%7D" sde-isloadasyncdata="true" bindingdata="%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D%5D" sde-updatetime="2024-06-28T15:40:43.126Z" sde-value="">
      <span class="sde-value" contenteditable="true" sde-left="[" sde-right="]" title="单选框">
         <label contenteditable="false">
            <input name="radio_d8358629" type="radio" value="%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D">Game</label>
         <label contenteditable="false">
            <input name="radio_d8358629" type="radio" value="%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D">游戏</label>
      </span>
   </span>
</p>
<p>多选框：
   <span class="sde-ctrl" contenteditable="false" id="Checkbox" sde-type="checkbox" sde-right="." sde-model="%7B%22desc%22%3A%22%E5%A4%9A%E9%80%89%E6%A1%86%22%2C%22required%22%3A0%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22bindingdata%22%3A%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%222%22%2C%22label%22%3A%22%E5%85%B6%E4%BB%96%22%2C%22selected%22%3A0%7D%5D%2C%22remotedata%22%3Anull%7D" sde-isloadasyncdata="true" bindingdata="%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%222%22%2C%22label%22%3A%22%E5%85%B6%E4%BB%96%22%2C%22selected%22%3A0%7D%5D" sde-updatetime="2024-06-28T15:41:17.509Z" sde-value="">
      <span class="sde-value" contenteditable="true" sde-left="[" sde-right="]" title="多选框">
         <label contenteditable="false">
            <input type="checkbox" value="%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D">Game</label>
         <label contenteditable="false">
            <input type="checkbox" value="%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D">游戏</label>
         <label contenteditable="false">
            <input type="checkbox" value="%7B%22value%22%3A%222%22%2C%22label%22%3A%22%E5%85%B6%E4%BB%96%22%2C%22selected%22%3A0%7D">其他</label>
      </span>
   </span>
</p>

== 更新后的（已填写/选择） =======
<p>标签控件：
   <span class="sde-ctrl sde-label" id="BiaoQian" sde-type="label" title="标签内容" style="background-color: rgb(188, 255, 127);" sde-model="%7B%22desc%22%3A%22%E6%A0%87%E7%AD%BE%E5%86%85%E5%AE%B9%22%7D">标签内容</span>
</p>
<p>单行文本：
   <span class="sde-ctrl" contenteditable="false" id="DanHangWenBen" sde-type="text" sde-right="." sde-model="%7B%22desc%22%3A%22%E5%8D%95%E8%A1%8C%E6%96%87%E6%9C%AC%E5%86%85%E5%AE%B9%22%2C%22required%22%3A0%2C%22strictverify%22%3A0%2C%22notdel%22%3A0%2C%22verify%22%3A%22%5E%5B0-9%5D*%24%22%2C%22mode%22%3A%22EDITOR%22%7D">
      <span class="sde-value" contenteditable="true" sde-left="[" sde-right="]" title="单行文本内容" _backups="717">7174</span>
   </span>
</p>
<p>下拉选择（单选）：
   <span class="sde-ctrl" contenteditable="false" id="SelectOne" sde-type="select" sde-right="." sde-model="%7B%22desc%22%3A%22%E5%8D%95%E9%80%89%22%2C%22required%22%3A0%2C%22multi%22%3A0%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22bindingdata%22%3A%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Apple%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22Orange%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%223%22%2C%22label%22%3A%22Banana%22%2C%22selected%22%3A0%7D%5D%2C%22remotedata%22%3Anull%7D" sde-isloadasyncdata="true" bindingdata="[{&quot;value&quot;:&quot;0&quot;,&quot;label&quot;:&quot;Apple&quot;,&quot;selected&quot;:0},{&quot;value&quot;:&quot;1&quot;,&quot;label&quot;:&quot;Orange&quot;,&quot;selected&quot;:0},{&quot;value&quot;:&quot;3&quot;,&quot;label&quot;:&quot;Banana&quot;,&quot;selected&quot;:0}]" sde-updatetime="2024-06-28T15:38:32.538Z" sde-value="[{&quot;value&quot;:&quot;1&quot;,&quot;label&quot;:&quot;Orange&quot;,&quot;selected&quot;:0}]">
      <span class="sde-value sde-select" contenteditable="true" sde-left="[" sde-right="]" title="单选">Orange</span>
   </span>
</p>
<p>下拉选择（多选）：
   <span class="sde-ctrl" contenteditable="false" id="SelectMore" sde-type="select" sde-right="." sde-model="%7B%22desc%22%3A%22%E4%B8%8B%E6%8B%89%E5%A4%9A%E9%80%89%22%2C%22required%22%3A0%2C%22multi%22%3A1%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22bindingdata%22%3A%5B%7B%22value%22%3A%221%22%2C%22label%22%3A%22Apple%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%220%22%2C%22label%22%3A%22Orange%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%222%22%2C%22label%22%3A%22Banana%22%2C%22selected%22%3A0%7D%5D%2C%22remotedata%22%3Anull%7D" sde-isloadasyncdata="true" bindingdata="[{&quot;value&quot;:&quot;1&quot;,&quot;label&quot;:&quot;Apple&quot;,&quot;selected&quot;:0},{&quot;value&quot;:&quot;0&quot;,&quot;label&quot;:&quot;Orange&quot;,&quot;selected&quot;:0},{&quot;value&quot;:&quot;2&quot;,&quot;label&quot;:&quot;Banana&quot;,&quot;selected&quot;:0}]" sde-updatetime="2024-06-28T15:39:49.431Z" sde-value="[{&quot;value&quot;:&quot;0&quot;,&quot;label&quot;:&quot;Orange&quot;,&quot;selected&quot;:0},{&quot;value&quot;:&quot;2&quot;,&quot;label&quot;:&quot;Banana&quot;,&quot;selected&quot;:0}]">
      <span class="sde-value sde-select" contenteditable="true" sde-left="[" sde-right="]" title="下拉多选">
         <span class="sde-val-item" sde-value="0">Orange</span>
         <span class="sde-val-item" sde-value="2">Banana</span>
      </span>
   </span>
</p>
<p>日期控件：
   <span class="sde-ctrl" contenteditable="false" id="RiQi" sde-type="date" sde-right="." sde-model="%7B%22desc%22%3A%22%E6%97%A5%E6%9C%9F%E5%86%85%E5%AE%B9%22%2C%22required%22%3A0%2C%22strictverify%22%3A0%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22min%22%3A%22%22%2C%22max%22%3A%22%22%2C%22format%22%3A%22%7Byyyy%7D-%7BMM%7D-%7Bdd%7D%20%7Bhh%7D%3A%7Bmm%7D%3A%7Bss%7D%22%2C%22defvalue%22%3A%222024-06-28%2012%3A00%3A00%22%7D">
      <span class="sde-value" contenteditable="true" sde-left="[" sde-right="]" title="日期内容">2024-06-28 12:00:00</span>
   </span>
</p>
<p>单选框：
   <span class="sde-ctrl" contenteditable="false" id="DanXuan" sde-type="radio" sde-right="." sde-model="%7B%22desc%22%3A%22%E5%8D%95%E9%80%89%E6%A1%86%22%2C%22required%22%3A0%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22bindingdata%22%3A%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D%5D%2C%22remotedata%22%3Anull%7D" sde-isloadasyncdata="true" bindingdata="%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D%5D" sde-updatetime="2024-06-28T15:40:43.126Z" sde-value="%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D">
      <span class="sde-value" contenteditable="true" sde-left="[" sde-right="]" title="单选框">
         <label contenteditable="false">
            <input name="radio_d8358629" type="radio" value="%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D" checked="checked">Game</label>
         <label contenteditable="false">
            <input name="radio_d8358629" type="radio" value="%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D">游戏</label>
      </span>
   </span>
</p>
<p>多选框：
   <span class="sde-ctrl" contenteditable="false" id="Checkbox" sde-type="checkbox" sde-right="." sde-model="%7B%22desc%22%3A%22%E5%A4%9A%E9%80%89%E6%A1%86%22%2C%22required%22%3A0%2C%22notdel%22%3A0%2C%22mode%22%3A%22EDITOR%22%2C%22bindingdata%22%3A%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%222%22%2C%22label%22%3A%22%E5%85%B6%E4%BB%96%22%2C%22selected%22%3A0%7D%5D%2C%22remotedata%22%3Anull%7D" sde-isloadasyncdata="true" bindingdata="%5B%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%222%22%2C%22label%22%3A%22%E5%85%B6%E4%BB%96%22%2C%22selected%22%3A0%7D%5D" sde-updatetime="2024-06-28T15:41:17.509Z" sde-value="%5B%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D%2C%7B%22value%22%3A%222%22%2C%22label%22%3A%22%E5%85%B6%E4%BB%96%22%2C%22selected%22%3A0%7D%5D">
      <span class="sde-value" contenteditable="true" sde-left="[" sde-right="]" title="多选框">
         <label contenteditable="false">
            <input type="checkbox" value="%7B%22value%22%3A%220%22%2C%22label%22%3A%22Game%22%2C%22selected%22%3A0%7D">Game</label>
         <label contenteditable="false">
            <input type="checkbox" value="%7B%22value%22%3A%221%22%2C%22label%22%3A%22%E6%B8%B8%E6%88%8F%22%2C%22selected%22%3A0%7D" checked="checked">游戏</label>
         <label contenteditable="false">
            <input type="checkbox" value="%7B%22value%22%3A%222%22%2C%22label%22%3A%22%E5%85%B6%E4%BB%96%22%2C%22selected%22%3A0%7D" checked="checked">其他</label>
      </span>
   </span>
</p>
```

## 4.如果需要导出和导入数据的功能
### 4.1 修改前端
导出数据功能已经做好，参考组件中的方法`extractDataFromHtml`
导入数据功能未做，可参考**注意->3**部分内容直接修改html，但是不太建议，可能有点麻烦。
==推荐使用后端统一处理==
### 4.2 修改后端
修改后端的话，那么就需要导入和导出xml的功能。
自带的导入/导出xml功能无法使用，需要自己新建控件并且参考`sdeEditor/doc/sde.api.md`文件。
`<html>`标签内容的内容都相同，可以根据`<controls>`标签的不同进行修改和处理。
可以在后端处理`xml文件`.可以使用`dom4j`解析`xml文件`。
**未填写数据**
![[电子病历编辑器/imgs/3.png]]
```xml
<?xml version="1.0" encoding="utf-8"?>

<xml>
  <controls>
    <id>BiaoQian</id>
    <type>label</type>
    <value>标签内容</value>
  </controls>
  <controls>
    <id>DanHangWenBen</id>
    <type>text</type>
    <value/>
  </controls>
  <controls>
    <id>SelectOne</id>
    <type>select</type>
    <value/>
  </controls>
  <controls>
    <id>SelectMore</id>
    <type>select</type>
    <value/>
  </controls>
  <controls>
    <id>RiQi</id>
    <type>date</type>
    <value/>
  </controls>
  <controls>
    <id>DanXuan</id>
    <type>radio</type>
    <value/>
  </controls>
  <controls>
    <id>Checkbox</id>
    <type>checkbox</type>
    <value/>
  </controls>
  <html>省略...</html>
</xml>
```

**已填写数据**
![[电子病历编辑器/imgs/2.png]]
```xml
<?xml version="1.0" encoding="utf-8"?>

<xml>
  <controls>
    <id>BiaoQian</id>
    <type>label</type>
    <value>标签内容</value>
  </controls>
  <controls>
    <id>DanHangWenBen</id>
    <type>text</type>
    <value>123</value>
  </controls>
  <controls>
    <id>SelectOne</id>
    <type>select</type>
    <value>
      <value>1</value>
      <label>Orange</label>
      <selected>0</selected>
    </value>
  </controls>
  <controls>
    <id>SelectMore</id>
    <type>select</type>
    <value>
      <value>0</value>
      <label>Orange</label>
      <selected>0</selected>
    </value>
    <value>
      <value>2</value>
      <label>Banana</label>
      <selected>0</selected>
    </value>
  </controls>
  <controls>
    <id>RiQi</id>
    <type>date</type>
    <value>2024-06-28 12:00:00</value>
  </controls>
  <controls>
    <id>DanXuan</id>
    <type>radio</type>
    <value>
      <value>0</value>
      <label>Game</label>
      <selected>0</selected>
    </value>
  </controls>
  <controls>
    <id>Checkbox</id>
    <type>checkbox</type>
    <value>
      <value>0</value>
      <label>Game</label>
      <selected>0</selected>
    </value>
    <value>
      <value>1</value>
      <label>游戏</label>
      <selected>0</selected>
    </value>
  </controls>
  <html>省略...</html>
</xml>

```