# Vue路由守卫

## 全局路由守卫
* 全局前置路由守卫`router.beforeEach`
```js
    const router = new VueRouter({...}) //创建一个路由实例
    router.beforeEach((to,from,next)=>{
        // ...
    })

    // to 指向将要去的目标
    // from 指向准备离开的路由
    // next 进入下个管道的方法

```
* 全局后置路由守卫`router.afterEach`
```js
    router.afterEach((to,from,next)=>{
        // ...
    })
```
* 路由独享的守卫
```js
    const router = new VueRouter({
        routes:[
            {
                path:'....',
                component:'...',
                beforeEnter:(to,from,next)=>{
                    // ...
                }
            }
        ]
    })
```
* 组件内的守卫
    * beforeRouteEnter
    * beforeRouteUpdate
    * beforeRouteLeave
```js
    const Foo = {
        template:`...`,
        beforeRouteEnter:(to,from,next)=>{
            // 在进入该组件对应的路由渲染之前执行
            // 无法获取当前实例this，因为组件还未创建
        },
        beforeRouteUpdate:(to,from,next)=>{
            // 相同组件之间动态路由之间的切换时执行
            // 路由动态参数    /foo/:id
            // /foo/1 切换至 /foo/2
        },
        beforeRouteLeave:(to,from,next)=>{
            // 在离开该组件对应的实例之前执行

        }
    }
```