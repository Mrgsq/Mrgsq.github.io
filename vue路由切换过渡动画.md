# vue路由切换过渡动画
* 设置`transition`
```vue
    <transition>
        <route-view>
        </route-view>
    </transition>
    
```
* 定义路由
```js
    const foo = {
        template:`
        <transition name='fade'>
        <div class='foo'>

        </div>
        </transition>
        `
        ,

    }
```
* 设置样式
```js
.fade-enter-active{
    
}
```