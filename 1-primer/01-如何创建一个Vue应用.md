# 如何创建一个基于Vue的App

## 1、引入`vue.js`
|   方案   |                         方法                         |
| :------: | :--------------------------------------------------: |
| 线上CDN  | `<script src="https://unpkg.com/vue@next"></script>` |
| 线下下载 |                `npm install vue@next`                |
|   ...    |                         ...                          |

## 2、必要起步文件
```html
<!-- index.html -->
```

```js
// main.js
```

## 3、极简代码结构
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8"/>
        <title>Vue Mastery</title>

        <!-- 1、线上方案引入 Vue.js -->
        <script src="https://unpkg.com/vue@3.0.11/dist/vue.global.js"></script>
    </head>
    <body>
        <!-- 2、id 为 "app" 的 <div> -->
        <div id="app"></div>

        <!-- 3.2、引入 vue 应用的实例 -->
        <script src="./main.js"></script>

        <!-- 4、将 vue 应用实例与 html 相链接 -->
        <script>
            const mountedApp = app.mount('#app')
            // [此 ‘app’ 来自 ./main.js 下的同名 ‘app’]
            //  index.html ==>         <div id='app></div>
            //                                   |
            //                      app.mount('#app')
            //                       |
            //  main.js ==>   const app = Vue.createApp({})
        </script>
    </body>
</html>
```

```js
// 3.1 创建名为 app 的 Vue 应用实例
const app = Vue.createApp({/*见[ createApp 的参数 ]*/})
```
`createApp 的参数 —— `[ createApp 的参数](https://v3.cn.vuejs.org/api/global-api.html#%E5%8F%82%E6%95%B0)

`createApp 的方法 ——` [ createApp 的方法](https://v3.cn.vuejs.org/api/application-api.html#%E5%BA%94%E7%94%A8-api)

| 方法名  | 参数  |   返回值   | 用法  |        示例         |
| :-----: | :---: | :--------: | :---: | :-----------------: |
| `mount` |   -   | 根组建实例 |   -   | `app.mount('#app')` |
