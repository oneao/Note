`VITE+VUE3+TS+AXIOS+PINIA`

==未完成，可直接参考`https://github.com/oneao/Vue3_QuickStart.git`==


## 1 创建项目
### 1.1 初始化项目
```bash
npm init vite@latest
```
1. ` Need to install the following packages: create-vite@5.3.0 Ok to proceed? (y)` 是否需要安装`create-vite`，输入`y`
2. 输入项目名称
3. 输入包名
4. 选择使用什么框架`Vue`,`React`等
5. 选择使用`js`还是`ts`

### 1.2 安装依赖
```bash
npm i
```

### 1.3 启动项目
```bash
npm run dev
```

### 1.4 修改vite.config.ts文件
首先执行命令
```bash
npm install @types/node --save-dev
```
修改`vite.config.ts`文件
```js
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import { resolve } from 'path'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  //解决“vite use `--host` to expose”
  base: './',	//不加打包后白屏
  server: {             
    host: '0.0.0.0',	
    port: 8090,      
    open: true
  },
  resolve:{   
    //别名配置，引用src路径下的东西可以通过@如：import Layout from '@/layout/index.vue'
    alias:[   
      {
        find:'@',
        replacement:resolve(__dirname,'src') 
      }
    ]
  }
})
```
### 1.5 修改`tsconfig.json`文件
```json
{
  "compilerOptions": {
    "target": "ESNext",
    "useDefineForClassFields": true,
    "module": "ESNext",
    "moduleResolution": "Node",
    "strict": true,
    "jsx": "preserve",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "esModuleInterop": true,
    "lib": ["ESNext", "DOM"],
    "skipLibCheck": true,
    "noEmit": true,
    // 允许字符串用作下标
    "suppressImplicitAnyIndexErrors": true,
     "baseUrl": ".",			
     "paths": {					
      "@/*":[					
        "src/*"					
      ]							
     }
  },
  "include": ["src/**/*.ts", "src/**/*.d.ts", "src/**/*.tsx", "src/**/*.vue"],
  "references": [{ "path": "./tsconfig.node.json" }],
  // ts排除的文件
  "exclude":["node_modules"]
}
```

## 2 配置Router路由

### 2.1 安装vue-router
执行命令,默认安装最新版本，可使用`@`指定版本。
```bash
npm install vue-router
```
### 2.2 新建router配置文件
在`src`下新建`router/index.ts`文件
添加以下内容
```js
import { createRouter, createWebHistory, RouteRecordRaw } from 'vue-router'  
  
const routes: Array<RouteRecordRaw> = [  
    {  
        //路由初始指向  
        path: '/',  
        name: 'App',  
        component:()=>import('../App.vue'),  
    }  
]  
  
const router = createRouter({  
    history: createWebHistory(),  
    routes  
})  
  
export default router
```
### 2.3 修改`main.ts`文件
```js
import { createApp } from 'vue'  
import App from './App.vue'  
import router from './router'  
  
createApp(App).use(router).mount('#app')
```

### 2.4 修改`App.vue`文件
```html
<script setup lang="ts">  
</script>  
  
<template>  
  <router-view></router-view>
</template>  

<style scoped>  
  
</style>
```

## 3 配置Axios请求
### 3.1 安装axios
