<!--
 * @Description: In User Settings Edi
 * @Author: your name
 * @Date: 2019-10-19 10:56:02
 * @LastEditTime: 2019-10-22 09:39:14
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
        * 无状态、受控组件、UI组件
        * 纯展示组件，这种组件只负责根据外部传入的props来展示，书写更简洁，执行效率更高
        * 特点
            * 只根据传入的props属性展示不同的UI效果
            * 组件不会被实例化，整体渲染性能得到提升
            * 组件不能访问this对象
            * 组件无法访问生命周期的方法
        * `function 组件名(参数){return <div>xxx</div>}`
    * class组件 
        * 有状态组件、非受控组件、容器组件
        * 类继承组件有更丰富的特性（state状态、生命周期等）
        ```js
            class 组件名 extends React.Component{
                render(){
                    return <h1>hello,world</h1>
                }
            }
        ```    
4. 组件中可嵌套组件

5. 组件属性props
    > props是一个对象，包含使用组件时的所有属性，属性必须为只读的，这一点非常重要，请严格遵守
    * 获取方式
        * 函数组件：通过参数props访问
        * 类组件：通过this.props访问
    * 定义默认属性：defaultProps
    > 通常情况下,我们需要为组件的某些属性设定默认值。就像HTML标签的属性也有默认值一样，（如form标签的method属性默认值是GET，input标签的type属性默认值是text）

    ```js
        MyComponent.defaultProps = {
            name:'laoxie'
        }
        //Es6写法
        //ES6默认不支持静态属性，需安装@babel/plugin-proposal-class-properties
        static defaultProps = {
            name:'laoxie'
        }
    ```
    * 属性的类型及校验（用于限制传入属性的数据类型）
        > 给组价设置静态字段propTypes来设置组件各个属性的类型检查器
        * React 内置数据类型检查器
        > 在React 16版本之后，PropTypes 从react包 分离到了prop-types包中

        ```js
            import PropTypes from 'prop-types';
            MyComponent.propTypes = {
                name:PropTypes.string
            }
        ```
        * 自定义属性验证器
            ```js
                MyComponent.propTypes = {
                    age:(props,propName,comName)=>{
                        if(props[propName]<18){
                            return new Error(propName + '必须大于等于18岁')
                        }
                    }
                }
            ```

6. 组件的状态         
> React会在state状态改变后自动执行组件中的render方法试图渲染
* 初始状态

    ```js   
        class MyComponent extends React.Component{
            constructor(){
                super(); //这行代码不能少
                this.state = {
                    isLiked:false
                }
            }
        }
    ```  
    
* 修改状态setState:
    * 格式：`setState(nextState[,callback])`
        * nextState:将要设置的新状态，该状态会和当前的state合并
        * callback:可选参数，回调函数。该函数会在setState设置成功，且组件重新渲染后调用
    * 依赖上次setState的结果    
    > 格式：`setState(fn [,callback])`
    > fn(pervState)

    ```js
        this.setState(preveState=>{
            return {
                num:pervState.num+1
            }
        })
    ```
    
    * 多次setState()合并
        > React内部会自动进行对比，得到最终结果后才渲染视图，所以并不需要担心多次进行setState会带来性能问题
        > PS: 调用setState()并不会马上修改state。而是进入到一个更新队列里面，所以不能在组件内部通过 `this.state.xx=xx`直接修改状态，因为修改后会被队列中的setState()替换 （如下两次输出都为false）

        ```js
            console.log(this.state.isLiked);//false
            this.setState({
                isLiked: true
            });
            console.log(this.state.checked);//false
        ```
    * 强制更新组件
    > 格式：foreUpdate(callback)

    ```
        forceUpdate()方法回事组件调用自身的render()方法重新渲染组件，组件的子组件也会调用自己的render(),一般来说，应该尽量避免使用foreceUpdate(),而仅从this.props和this.ssate中读取状态并由react触发render()调用 
    ```