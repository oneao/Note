## 第一步：下载

```bash
npm install -D tailwindcss postcss autoprefixer
```

## 第二步：创建`tailwindcss.css`文件

添加下面的内容

```js
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
```

## 第三步：`main.js`中引入

```js
import "./assets/tailwindcss.css"
```

## 第四步：初始化

```bash
npx tailwindcss init -p
```


