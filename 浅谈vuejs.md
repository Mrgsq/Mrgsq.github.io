## 核心实现类
Observer: 它的作用是给对象的属性添加getter和setter,用于依赖收集和派发更新

Dep: 用于收集当前响应式对象的依赖关系，每个响应式对象包括子对象都拥有一个Dep实例（里面subs是Watcher实力数组），当数据有变更时，会通过dep.notify()通知各个watcher

## nextTick的原理
### JS运行机制
js执行都是单线程的，它是基于事件循环的。事件循环大致分为以下几个步骤：

1、所有同步任务都会在主线程上执行，形成一个执行栈。

2、主线程之外，还有一个“任务队列”，只要异步任务有了运行结果，就在“任务队列”之中放置一个事件。

3、一旦“执行栈”中的所有的同步任务执行完毕，系统就会读取“任务队列”，看看里面有哪些事件，那些对应的异步任务，于是结束等待状态，进入执行栈，开始执行。

4、主线程不断重复上面三个步骤

主线程的执行过程就是一个tick，而所有的异步结果都是通过“任务队列”来调度。消息队列中存放的是一个个的任务（task)。规范中规定task分为两大类，分别是“宏任务” 和 “微任务”。并且每个宏任务结束后都要清空微任务。
在浏览器环境中：

常见的宏任务有： setTimeout、MessageChannel、postMessage、setImmediate

常见的微任务有： MutationObserver 和 Promise.then

### 异步更新队列

可能你还没注意到，Vue在更新DOM时是异步执行的。只要侦听到数据变化，Vue将开启一个队列，并缓冲在同一个事件循环中发生的所有数据变更。

如果同一个watcher被多次触发，只会被推入到队列中一次。这种在缓冲时去除重复数据对于避免不必要的计算和DOM操作是非常重要的。

然后，在下一个的事件循环 “tick”中，Vue刷新队列并执行实际（已去重的）工作。

Vue在内部对异步队列尝试使用原生的Promise.then、MutationObserver 和 setImmediate,如果执行环境不支持，则会采用setTimeout(fn, 0)代替。

### 在vue2.5的源码中，macrotask降级的方案依次是：setImmediate、MessageChannel、setTimeout

vue的nextTick方法的实现原理

1、vue用异步队列的方式来控制DOM更新和nextTick回调先后执行

2、microtask因为其高优先级特性，能确保队列中的微任务在一次事件循环前被执行完毕

3、考虑兼容问题，vue做了microtask向macrotask的降级方法