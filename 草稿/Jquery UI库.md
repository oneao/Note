# Layui 
纯原生前端`UI`库，无侵入方式，和`jquery`没有关联。**比较推荐，国内开发**
网站：[https://layui.dev/](https://layui.dev/)
使用案例：通过`class`来进行设置样式。
```html
<button type="button" class="layui-btn">默认按钮</button>
```
![[Pasted image 20240730092756.png]]
## Bootstrap
3版本包括以下版本需要依赖jquery，4版本以上不需要依赖jquery.
网站：[https://v5.bootcss.com/docs/getting-started/introduction/](https://v5.bootcss.com/docs/getting-started/introduction/)
使用案例：通过`class`来进行设置样式。
```html
<button type="button" class="btn btn-primary">Primary</button>
```
![[Pasted image 20240730092732.png]]\
## Easy UI
通过jQuery或HTML5使用EasyUI
### 使用HTML声明组件
```html
<div class="easyui-dialog" style="width:400px;height:200px"
    data-options="
        title:'My Dialog',
        iconCls:'icon-ok',
        onOpen:function(){}">
    dialog content.
</div>
```
官网：[https://www.jeasyui.cn/](https://www.jeasyui.cn/)
样式一般。

## TopJUI
基于最新稳定版JQuery EasyUI重构
==收费==
参考网站：[https://demo.topjui.com/](https://demo.topjui.com/)

## Semantic UI
类似 Layui，组件比较多
官网：[https://semantic-ui.com/introduction/getting-started.html](https://semantic-ui.com/introduction/getting-started.html)

## bulma
类似 Layui，组件比较少，样式美观
官网：[https://bulma.zcopy.site/](https://bulma.zcopy.site/)

