<!--
 * @Author: your name
 * @Date: 2019-10-23 22:10:42
 * @LastEditTime: 2019-10-23 22:39:11
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edi
 * @FilePath: \Mrgsq.github.io\webpack.md
 -->
# 如何利用webpack配置react环境

## 创建目录
* 根目录下创建src文件夹

## 安装依赖
* 进入src目录 打开cmd
* 初始化 npm init
* 安装如下依赖
    
    ```js
        react、react-dom
        webpack、webpack-dev-server、webpack-cli
        @babel-loader、@babel/core、@babel/preset-react
        css-loader、style-loader、sass-loader、node-sass
        clean-webpack-plugin、
        html-webpack-plugin
    ```
* 安装完成之后
    * 在src根目录下创建一个配置文件 `webpack.config.js`    
    * 添加一个APP.js ,模板文件 template.html ,样式文件APP.css,入口文件 main.js
* 在`webpack.config.js`配置文件中完成如下配置
    ``` js
    const path = require('path') //引入路径模块
    const HtmlWebpackPlugin = require('html-webpack-plugin');
    const {CleanWebpackPlugin} = require('Clean-webpack-plugin')
  module.exports =   {
        //入口文件
        entry: './src/main.js',

        //webpack打包输出文件
        output:{
            path:path.join(__dirname,'./dist'), //打包后生成的文件夹
            filename:'bundle-[name]-[hash:5].js',
            <!-- publicPath:'./' -->
        },
        //测试服务器
        devServer:{
            contentBase:path.join(__dirname,'./src/')
            
        },
        //加载器
        module:{   
            rules:[ //设置需要的文件
                {
                    test:/\.jsx?$/, //利用正则找出文件
                    use:[{
                        loader:'babel-loader',
                        options:{
                            presets:['@babel/presets-react']
                        }
                    }]
                },
                {
                    test:/\.css/,
                    use:['style-loader','css-loader']
                },
                {
                    test:/\.scss$/ , //scss文件
                    use:['style-loader','css-loader','sass-loader']
                }
            ]
        },
        plugins:[
            //删除dist文件夹
            new CleanWebpackPlugin(),

            //创建dist文件
            new HtmlWebpackPlugin({  
                template :'./src/template.html'
            })
        ]
    }
    ```
