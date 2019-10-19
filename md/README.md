<!--
 * @Description: In User Settings Edi
 * @Author: your name
 * @Date: 2019-10-19 10:56:02
 * @LastEditTime: 2019-10-19 14:52:01
 * @LastEditors: Please set LastEditors
 -->
# React 使用

1. 安装
    *   npm i create-react-app -g
2. 使用
    * 入口文件 `src 下的 index.js`
    * 引入
        * `import React from 'react'`
        * `import ReactDOM from 'react-dom'`
    * 挂在
        * `ReactDOM.render`方法
            * `(渲染内容(虚拟节点),挂载点)`
        * `React.createElement(type,[props],[...children])`    
            * `React.createElement('h1',null,'h5-1907')`
3. 组件
    * 组件名称必须首字母大写，React会将小写字母开头的组件视为原生DOM标签
    * 函数组件
        * `function 组件名(参数){return <div>xxx</div>}`
    * class组件 
        * 
```
class 组件名 extends React.Component{
    render(){
        return <h1>hello,world</h1>
    }
}
```    
4. 组件中可嵌套组件         