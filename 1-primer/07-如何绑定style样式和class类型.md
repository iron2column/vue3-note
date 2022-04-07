# 07-如何绑定style样式和class类型

> `:class="{ 类型名:布尔变量｜布尔值 }"`
> 

> `:style="{ 驼峰样式名:样式值, '破折样式名':样式值, 样式对象名 }"`

<br><br><br>

---
- [Class 与 Style 绑定](https://v3.cn.vuejs.org/guide/class-and-style.html#class-%E4%B8%8E-style-%E7%BB%91%E5%AE%9A)
---

<br><br><br>

---
## 类型绑定——class绑定

### 1、绑定单个类名
1. `styles.css`
    ```css
    /* styles.css */
    .DEFAULT{}
    .active{}
    ```
2. `main.js`
    ```js
    // main.js
    const app = Vue.createApp({
        data():{
            return{
                isAcitve:true,
            }
        }
    }).mount('#app')
    ```
3. `index.html`
    ```html
    <!-- main.js -->
    <div id="app">
        <!-- 布尔值 -->
        <div class="DEFAULT" :class="{active:true}"></div>
        <!-- 布尔变量 -->
        <div class="DEFAULT" :class="{active:isActive}"></div>
        <!-- 三元运算符 -->
        <div class="DEFAULT" :class="[isActive ? actice : '' ]"></div>
    </div>
    ```

<br><br><br>


### 2、绑定多个类名
1. `styles.css`
    ```css
    /* styles.css */
    .DEFAULT{}
    .active{}
    .text-warning{}
    ```
2. `main.js`
    ```js
    // main.js
    const app = Vue.createApp({
        data(){
            return{
                isActive:true,
                shouldWaring:false
            }
        }
    }).mount('#app')
    ```

3. `index.html`
    ```js
    // main.js
    const app = Vue.createApp({
        data(){
            return{
                // 1.类名的布尔变量
                isActive: true,
                shouldWaring: false,
                
                // 2. 类名集合的对象
                clzObject:{
                    active: true,
                    'text-warning':false,
                },

                // 3. 类名属性
                activeClass: 'active',
                textClass: 'text-warning'
            }
        }
    }).mount('#app')
    ```

    ```html
    <!-- index.html -->
    <div id="app">
        <!-- 1. 类名布尔变量：驼峰式类名 破折式类名 -->
        <div class="DEFAULT" :class="{ active: isActive, 'text-warning':shouldWaring }"></div>

        <!-- 2. 类名集合的对象：对象形式 -->
        <div class="DEFAULT" :class="clzObject"></div>

        <!-- 3. 类名的属性：数组形式 -->
        <div class="DEFAULT" :class="[activeClass,textClass]"></div>
        <div class="DEFAULT" :class="[isActive ? 'activeClass' : '', textClass]"></div>
        <div class="DEFAULT" :class="[{active: isActive}, textClass]"></div>


    </div>
    ```
---

<br><br>
<br><br>

## 样式绑定——style绑定

```css
/* styles.css */
.color-circle {} 
```
```js
// main.js
const app = Vue.createApp({
    date(){
        return{
            // 1
            colors: ['green','blue','red'],
            // 2
            oneStyle: {
                fontSize: '14px',
                color: 'yellow'
            }
        }
    }
})
```
```html
<!-- index.html -->
<div id="app">
    <!-- 1. 动态赋予样式属性的值 -->
    <div v-for="color in colors" :style="{backgroundColor: color}"></div>
    <div v-for="color in colors" :style="{'background-color': color}"></div>

    <!-- 2. 以对象的形式通过data传递多个样式 -->
    <div v-for="color in colors" :style="oneStyle"></div>

</div>
```