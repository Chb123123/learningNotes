### webpack

从网络上下载 模块

```vue
// 打开终端 输入 npm install jquery -S
从网络上下载 jquery 文件
-S 是 --save 的简写
```

#### 安装 webpack 

npm install webpac -D

##### 配置 webpack

```vue
module.exports = {

mode: "development"   //mode 用来指定 构建模式  可选的有 development 和 production

development 在开发阶段 使用  打包速度快 但体积大

production 在上线阶段使用 打包速度慢 但体积小

}
```

##### 自定义打包入口与出口

```vue
const pash = require("path")

module.exports = {

entry.pash.join(__dirname,"./src/index.js") 打包文件路径

output: {

__dirname 表示文件的根目录

 path:path.join(__dirname, "/dist")  输出文件路径

folename: "bundle.js"  // 输出文件名称

}

}
```

##### webpack  插件

1. webpack-dev-sarver  // 每次修改源代码 webpack 就会自动进行项目的打包和构建

   插件的安装 ：npm install webpack-dev-server@3.11.2 -D

2. html-webpack-plugin 

   webpack 中的 HTML 插件 

   可以通过此插件制定 html 页面的内容

   webpack 只能打包 以 js 结尾的文件

   打包其他的文件会报错

##### 安装 css-loadle 插件

npm i style-loader css-loader -D

webpack 识别 css 文件会报错 这时就需要 css-loader 插件

##### 安装 less-loader 插件 

npm i less-loader less -D

```web-idl
module: {
        rules:[
            // 文件后缀名的匹配规则 
            {test: /\.css$/,use:['style-loader','css-loader','less-loader']},
            // {test: /\.less$/,use:['style-loader',]}
        ]
    }
```

##### 安装 url-loader 模块

npm i url-loader file-loader -D

```web-idl
// url-loader 的配置文件
module: {
        rules:[
            {test: /\.jpg|gif|png$/,use:['url-loader?limit=22229']}  //limit= 文件的大小 大于这个数不会转成 base64格式 
        ]
    }
```

##### 安装 babel-loader 模块

对应webpack 无法处理的 js 高级语法 需要使用这个模块

```web-idl
// 下载命令
// npm i babel-loader @babel/core @babel/plugin-proposal-decorators -D
// 配置文件
// 在文件的根目录创建一个 babel.config.js 文件
module.exports = {
    plugins: [["@babel/plugin-proposal-decorators",{legacy:true}]]
}
```

将 内存的 文件 添加到物理磁盘上面

```web-idl
 // 将以下代码添加到 package.json 文件中
 "scripts": {
    "dev": "webpack serve", // 开发环境下运行的 命令
    "build": "webpack --mode production"  // 项目发布时，运行 build 命令
  },
```

##### 将打包好的 js 文件放到 js 文件夹中

```web-idl
output: {
        path: path.join(__dirname,'dist'),
        // 生成的文件名
        filename: "js/bundle.js"
    },
```

##### 将打包好的 图片放到 打包好的 dist 文件下的 image 文件中

```web-idl
{test: /\.jpg|gif|png$/,use:{
                loader: 'url-loader',
                options:{
                    limit: 22228,
                    // 声明把打包生成的图片文件，存储到 dist 文件目录下 image 文件夹中
                    outputPath: 'image'
                }
            }},
 // 第二种写法 (提倡第二种)
 {test: /\.jpg|gif|png$/,use:["url-loader?limit=478&outputPath=image"]}
```

##### 每次打包先删除 旧版本的 dist 文件 

这样可以省略我们需要手动删除

```web-idl
//在webpack 配置文件中的头部 添加 
const { CleanWebpackPlugin } = require('clean-webpack-plugin');
//在 plugins 数组中添加 new CleanWebpackPlugin()
plugins: [new CleanWebpackPlugin()],
```

##### Source Map 

Source Map 就是一个信息文件 里面存储着位置信息 有了它 出错的时候直接显示源代码，而不是转换后的代码，方便后期的调试

```
devtool: 'eval-source-map',
```

##### @ 的原理和好处

导入文件 时 @ 符号表示从 src 的文件下从外往里查找  ../ 则是从里往外查找 @/

```
//webpack 不能直接识别 @ 需要配置
resolve 和 module 平级
resolve:{
        alias:{
            "@":path.join(__dirname,'./src/')
        }
    }

```

##### 删除webpack 里面 vue的组件 

```bash
npm uni i vue -S
```

##### 安装 vue 

```
npm i vue@要安装的版本 -S
```



### Vue 2

#### 什么是 Vue 

1. 构建用户界面

   用 Vue 往页面填充数据

2. 框架

   框架是一种现成的解决方案 程序员只能遵守框架的规范 去编写自己的业务代码

#### Vue 的主要特性

1. 数据驱动视图
2. 双向数据绑定

##### （1）数据驱动视图

1. 数据的变化会驱动视图的自动更新

   好处：程序员只管操作视图 页面结构会自动渲染

##### （2）双向数据绑定

1. 在网页中 from 表单负责采集数据 Ajax 负责提交数据

   js 数据的变化，会被自动渲染到页面上

   页面上表单采集的数据发生变化时，会被 Vue 自动获取到 并更新到 js 数据中

#### Vue 的实现原理

mvvm : 指的时 model view viewModel

1. model 表示当前页面所需要的 数据源
2. view 表示 当前页面所渲染的 DOM 结构
3. view Model 表示 Vue 的实例 它是 MVVM 的核心

#### Vue的六大指令

- 内容渲染指令
- 数据绑定指令
- 事件绑定指令
- 双向数据绑定
- 条件渲染指令
- 列表渲染指令

##### （1）内容指令

v-text 

标签会覆盖元素内原有的内容

{{ }} 插值表达式 

在实际开发中用的最多

v-html 

可以将标签添加到页面中 并且标签内可以添加样式

##### （2）属性绑定指令

注意：插值表达式只能用在内容中 不能用在属性中

v-bind: 属性元素 也可以简写成 ：

```vue
// 设置图片路径
<img v-bind:src="photo" alt="">
<script>
        const vm = new Vue({
            el: '.app',
            data: {
                tips: '输入用户名',
                photo: 'https://i1.hdslb.com/bfs/archive/19e5b1dab155924a3cff2c832cbfd802eb6a14de.jpg@672w_378h_1c.webp'
            }
        })
    </script>
```

```vue
// 需要进行字符串的拼接 需要用上单引号
<div :title="'box' +index">这是一个div</div>
```

##### （3）事件绑定指令

v-on:绑定事件的函数=“”

```vue
<div class="app">
        <p>cont 的值是：{{cont}}</p>
        <button @click="add(3)">+N</button>
    </div>
<script>
        const vm = new Vue({
            el: '.app',
            data:{
                cont: 1,
            },
            // 事件创建 函数
            methods: {
                add(n){
                    this.cont += n
                },
            }
        })
    </script>
```

##### 事件修饰符

```vue
<a href="http://www.baidu.com" @click.prevent="btn">跳转到百度首页</a> //阻止链接跳转
methods:{
                btn(e){
                    console.log('a被点击了')
                    console.log(e)
                    // e.preventDefault()
                }
            }
```

| 事件修饰符 | 说明                                                   |
| ---------- | ------------------------------------------------------ |
| .prevent   | 阻止事件的默认行为                                     |
| .stop      | 阻止事件的冒泡                                         |
| .capture   | 以捕获模式触发当前事件的处理函数                       |
| .once      | 绑定的事件只触发一次                                   |
| .self      | 只有在 event.target 是当前元素自身时触发的事件处理函数 |

##### 按键修饰符

```vue
<input type="text" name="" id="" @keyup.esc="key" @keyup.enter="getinput">
 <script>
        const vm = new Vue({
            el: '.box',
            data:{},
            methods:{
                //点击 esc 按键 清空 输入框的值
                key(e){
                    e.target.value = ''
                },
                // 点击回车按键 获取 输入框的值
                getinput(e){
                    console.log(e.target.value)
                }
            }
        })
    </script>
```

#### 双向数据绑定指令

##### 主要功能

主要用来 辅助开发者在不操作 DOM 的前提下 快速获取表单内的数据

v-model

```vue
<div class="box">
        <input type="text" v-model="username">
    </div>
    <script>
        const vm = new Vue({
            el: '.box',
            data:{
                username: 'zhangsan'
            }
        })
    </script>
```

v-mode 专用的修饰符

| 修饰符  | 作用                              | 示例                          |
| ------- | --------------------------------- | ----------------------------- |
| .number | 自动将用户输入的值转为数值类型    | <input v-model.number="age"/> |
| .trim   | 自动过滤用户输入的首尾空白字符    | <input v-model.trim="msg"/>   |
| .lazy   | 在 “change” 时而非 “input” 时更新 | <input v-model.lazy="msg"/>   |

#### 条件渲染指令

条件渲染指令主要用来辅助开发者 按需控制 DOM 的显示与隐藏 ，条件渲染指令有如下两个

v-if

v-if 如果条件不成立 则它会在页面上动态的删除元素，如果条件成立 则动态生成元素

v-show

v-show 条件成立 它的属性就会变为 display : block, 如果条件不成立 则它的 display 属性会变为 none

在需要频繁切换元素的显示与隐藏 的时候 v-show 性能会更好 

v-for

v-for 提供了列表渲染指令 用来辅助开发者 基于一个数组循环渲染一个列表结构 v-for 指令需要使用 item in inems 形式的特殊语法 其中：

- items是待循环的数组

- item　是被循环的每一项

  ```vue
   <div id="app">
          <table class="table table-bordered table-hover table-striped">
              <thead>
                  <th>id</th>
                  <th>性别</th>
                  <th>姓名</th>
              </thead>
              <tbody>
                  <!-- 官方推荐 在使用 v-for 最好再声明一个 key 属性 而且最好把 id 作为 key 的值-->
                  <!-- 官方对key 的值做了要求 只能是 字符串 或 数字 -->
                  <!-- key 的值不能重复 否则终端会报错 Duplicate keys detectec -->
                  <tr v-for="(item,index) in list" :key="item.id" :title="item.name">
                      <td>{{index}}</td>
                      <td>{{item.age}}</td>
                      <td>{{item.name}}</td>
                  </tr>
                  
              </tbody>
          </table>
          
      </div>
      <script>
          const vm = new Vue({
              // el 属性固定的写法 表示当前实例要控制页面上的那个区域 接收的值是一个选择器
              el: '#app',
              // data 对象就是要填充的数据
              data:{
                  username: 'zhangsan',
                  list: [{
                      id: 1,
                      age: 18,
                      name: '张三'
                  },{
                      id: 2,
                      age: 18,
                      name: '李四'
                  },{
                      id: 3,
                      age: 18,
                      name: '王五'
                  }]
              }
          })
      </script>
  ```


##### 向列表内添加元素

push 

```vue
// 新建一个对象
const obj = {
								id: this.nextId,
								name: this.branch,
								check: true,
								time: new Date(),
								remove: '删除'
							}
							// var name = this.branch;
							// console.log(this.brandlist);
							// 将新建的对象添加到 列表内
							this.brandlist.push(obj);
```

#### 过滤器

过滤器再　Vue 3 被取消了  只能再 Vue２　中使用

过滤器的使用 |  " 管道符"

过滤器要定义在 filters 的节点下面 与 data 是平级关系

管道符函数的前面那个数可以通过变量的形式获取 

必选要有返回值

全局过滤器

定义全局过滤器的方法

```javascript
// Vue.filter() 接收两个参数
// 第一个参数 全局过滤器的名字
// 第二个过滤器 是全局过滤器的 处理函数
Vue.filter('capitalize',function(val){
            const first = val.charAt(0).toUpperCase(0)
            const other = val.slice(1)
            return first + other
        })
```

如果全局过滤器与私有过滤器名称冲突了 调用的是私有的过滤器 就近原则

#### 侦听器

监听数据变化做一件事

监视数据的变化 针对数据的变化做出特点的操作

```vue
//侦听器函数必须放到 watch对象中
<div class="app">
        <input type="text" v-model="username">
    </div>
    <script>
        const vm = new Vue({
            el: '.app',
            data: {
                username: '张三',
            },
            medhods:{},
            watch:{
                username(newVal,oldVal){
                    // 监听到了数据的变化就会触发 函数
                    console.log(newVal,oldVal)
                }
            }
        })
    </script>
```

##### 侦听器的格式

1. 方法格式的监听器
   - 缺点1： 无法在进入页面的时候自动触发
   - 缺点2：如果侦听的是一个对象 如果对象内的属性发生了变化 不会触发侦听器
2. 对象格式的侦听器
   - 好处：可以通过 immediate 选项让侦听器自动触发
   - 好处2：可以通过 deep 选项让侦听器深度侦听对象中的每个属性的变化

```vue
// 对象格式侦听器
<div class="app">
        <input type="text" placeholder="输入用户名" v-model.trim.lazy="username">
        <!-- <input type="submit" value="注册"> -->
    </div>
    <script>
        const vm = new Vue({
            el: '.app',
            data:{
                username: "admin",
            },
            watch:{
                username:{
                    handler(newVal,oldVal){
                        // console.log(newVal,oldVal)
                        axios({
                            method: 'get',
                            url: "https://www.escook.cn/api/finduser/" + newVal
                        }).then(function(res){
                            // console.log(res)
                            if(res.status === 200){
                                console.log('用户名可用')
                            }else{
                                console.log('用户名不可用')
                            }
                        })
                    },
                    immediate: true,
                }
            },
        })
    </script>
```

##### 深度侦听器

```vue
watch:{
                // 如果要侦听的是对象的子属性 则必须包裹一层双引号
                "info.username"(newVal){
                    console.log(newVal)
                },
                immediate: true,
            }
```





#### 计算属性

特点

- 定义的时候 要被定义为方法
- 在使用计算属性的时候 当普通的属性使用即可

好处

- 实现了代码的复用
- 只要计算属性中依赖的数据发生变化了，则会计算属性会自动重新求值

```JavaScript
 computed:{
                // 动态生成 rgb 的函数
                rgb(){
                    return `rgb(${this.R},${this.G},${this.B})`
                }
            }
```

#### axios 的使用

```javascript
const vm1 = new Vue({
            el: '.app1',
            methods:{
                    async btn (){
                        // 获取 data的属性
                    const {data} =  await axios({
                        method: 'post',
                        url: 'http://www.liulongbin.top:3006/api/addbook',
                        data:{
                            bookname: '三国演义'
                        }
                    })
                    // 将data 的属性打印出来
                    console.log(data)
                },
                
            }
        })
```

##### async 和 await

axios 直接发起get 请求

```javascript
get.addEventListener('click',async function(){
            const {data: res} = await axios.get('http://www.liulongbin.top:3006/api/getbooks',{
                params:{id:4}
            })
            console.log(res.data)
        })
```

axios 直接发起 post 请求

```javascript
post.addEventListener('click',async function(){
            const {data:res} = await axios.post('http://www.liulongbin.top:3006/api/getbooks')
        })
```



#### 单页面应用程序

简称 SPA 指的是 Web 网站中只要唯一一个 html 页面 所有功能都在唯一一个页面内完成

##### vue-cli 

vue-cli 是标准的 Vue.js 的开发工具 简化了程序员 基于 webpack 创建工程化 Vue 的过程

官网   https://cli.vuejs.org/zh/

```
全局安装 vue-cli
npm install -g @vue/cli
```

##### vue-cli 创建项目

```bash
vue create 项目名称
```



##### vue 中 src 目录中的结构

```
assets 文件夹 存放项目中的静态文件 例如 css 样式表 图片资源
companies 文件夹 程序员封装的可复用的组件 都要放到 companies 目录下
main.js 是项目的路口文件整个项目的运行要先执行 main.js
```

##### vue 项目的运行流程

在工程化项目中 vue 要做的事情很简单 通过 main.js 把 App.vue 渲染到 index.html 指定的区域中

其中

- App.vue 用来编写待渲染的模板结构
- index.html 中需要预留一个 el 区域
- main.js 把 App.vue 渲染到 index.html 所预留的区域中

##### vue 组件 

vue 的三个组成部分

- templare  组件的模板结构
- script   组件 的 JavaScript 行为
- style  组件的样式

##### 使用 vue 组件

-  使用 import 语法导入需要的组件
-  使用 components 节点注册组件
-  以标签的形式使用刚才注册的组件

#### 注册全局组件

在 vue 项目下的main.js 文件下 通过 Vue.component() 方法 可以注册全局组件

```Vue
import Cont from "@/component/Count.vue"

Vue.comonent('MyCount',Count)
```

##### 自定义属性props

props 是自定义属性 允许使用者自定义属性 为当前组件定义初始值

props 的值是只读的 不能修改

##### 定义 props 的默认值

```vue
export default {
	props:{
		init :{
			default: 0;
		}
	}
}
```

##### required 的使用

```vue
init: {
      default: 0,
      // 使用type 定义属性 定义 init 的值必须为数组
      type: Number,
      // init 的值必须填 不填将会强制报错
      required: true,
    },
```

##### 样式冲突问题的解决方法

在style 的标签内添加一个 scoped 属性

表示在当前的页面元素自动添加一个 属性

##### 修改子组件的样式

只有在 less 语言 时可以使用

/deep/ 标签 {}

在使用第三方库的时候修改样式可以用到

#### 组件的生命周期

生命周期是指 一个组件从创建  > 运行 > 销毁 的整个阶段 强调的是一个时间段

##### created 生命周期 

```javascript
 // created 生命周期 函数非常常用
    // 经常在这生命周期里面 调用 methods 中的方法 请求服务器的数据
    created(){
        // console.log(this.info)
        // console.log(this.message)
        // console.log(this.show)
        console.log(this.initBooklist())
    },
```

#### vue 的生命周期

```javascript
<script>
export default {
    props:{
        info:{
            type: String,
        }
    },
    data(){
        return{
            message: 'hello Vue',
            books: '',
            flag: true,
        }
    },
    methods:{
        show(){
            console.log('创建了 Show')
        },
        initBooklist(){
            const xml = new XMLHttpRequest()
            xml.addEventListener('load',() =>{
                const result = JSON.parse(xml.responseText)
                console.log(result.data.length)
                this.books = result.data.length
            }),
            xml.open('get','http://www.liulongbin.top:3006/api/getbooks')
            xml.send()
            
        }
    },
    // 创建生命周期函数
    beforeCreate(){
        // console.log(this.info)
        console.log(this.message)
    },
    // created 生命周期 函数非常常用
    // 经常在这生命周期里面 调用 methods 中的方法 请求服务器的数据
    // 在这期间 props data methods 都是 可用的
    created(){
        // console.log(this.info)
        // console.log(this.message)
        // console.log(this.show)
        console.log(this.initBooklist())
    },
    // 第一次渲染 DOM 结构
    mounted(){
        console.log(this.$el)
        
    },
    // 将要根据变化过后 最新的数据重新渲染 组件的模板结构
    beforeUpdate(){
        // console.log(this.message)
    },
    // 当数据变化之后 为了操作最新的 DOM　结构　必须把代码写到　updted 元素里面
    updated(){
        console.log(this.message)
    },
    //  将要销毁的组件 此时尚未销毁 组价还处于 正常工作状态 
    // 销毁当前的 侦听器 子组件 时间监听
    beforeDestroy(){
        console.log(this.message)
    },
    // 当前组件已经完全被销毁 此组件的 DOM 结构在浏览器中完全被移除
    destroyed(){
        console.log('11')
    }
}
</script>
```

##### 子组件向父组件传递数据

子组件向父组件传递数据 需要使用 自定义数据 

```javascript
// 子组件的自定义事件
methods:{
        addcount(){
            this.count ++
            // 修改数据 通过创建自定义事件 $emit()
            this.$emit('addcount', this.count)
        }
    }
// 父组件的自定义 事件
methods:{
    getcount(val){
      this.countFromSon = val
    }
  }
// 父组件的标签
<MyRight @addcount="getcount"></MyRight>
```

##### 兄弟组件相互传输数据

兄弟组件之间数据共享方案是 EventBus

EventBus 的使用

1. 创建 eventBus.js 模块 并向外共享一个 Vue 的实例对象
2. 在数据发送方 调用bus.$emit("事件名称",要发送的数据) 方法触发 自定义事件
3. 在数据接收方，调用bus.$on("事件名称", 事件处理函数) 方法注册一个自定义事件

```javascript
// 兄弟组件 数据发送方
data(){
    return{
        meg: 'hello'
    }
}
// 兄弟组件 数据接收方
data(){
    return{
        msgFromLeft: ""
    }
}
```

#### ref 的引用

ref 用来 辅助开发者 在不依赖 jQuery的情况下 获取 DOM 元素组件的引用

##### ref的使用

```javascript
methods:{
    print(){
      // 在要操作的 DOM 元素标签内 定义一个 ref 的属性 
      // 在需要用到这个属性的时候 使用 this.$refs. 自定义属性 + 样式
      this.$refs.myh1.style.color = 'red'
    }
  }
```

##### $nextTick(function)  方法

等组件的 DOM 元素全部加载完成在执行的函数，从而保障 回调函数内的方法可以操作到最新的 DOM 元素

要延迟到最后执行的 事件 可以通过 this.$nextTick() 方法 



#### 动态组件

##### keep-alive 保持状态

防止组件被隐藏的时候销毁

使用方法：

```javascript
// 将要保持的组件包含到 keep-alive 标签内  
<keep-alive>
        <component :is="comName"></component>
      </keep-alive>
```

组件被缓存时会触发 deactivated 生命周期函数

组件被激活时会触发组件的 activated 生命周期函数

使用生命周期函数 要在子组件中使用 而不是在父组件中使用

##### keep-alive 的include 属性

可以指定哪些组件被缓存 哪些组件被销毁

使用方法

```vue
// 在 include 中 的组会被缓存 不在 include 内的组件会被销毁 不同的组件中 用逗号隔开
<keep-alive include="Left">
        <component :is="comName"></component>
      </keep-alive>
```

##### keep-alive 的 exclude 属性

include 属性是包含 exclude 属性是排除

哪个组件不想被 缓存 将组件名称 添加到 exclude 内

#### 插槽

什么是插槽：

插槽是 Vue 为组件的封装者提供的能力 允许开发者在组装组件时 把不确定的希望用户指定的部分定义为插槽

v-solt 的简写是 #

#### 自定义指令

##### directives

在每个 vue 组件中 可以在 directives 节点下声明自定义指令 

##### 私有自定义指令 

```vue
<h1 v-color="color">App组件</h1>
directives:{
  // 第定义一个 名为 color 的指令 指向一个配置对象
  // 当指令第一次被绑定到 元素上的时候 会立即触发 bind 函数
  color:{
    bind(el,binding){
      el.style.color =  binding.value
      console.log(el)
      
    },
    // 每次 DOM 更新的时候被调用
    update(el, binding){
      el.style.color = binding.value
    },
  },
},
```

##### 全局自定义指令 

 需要在 main.js 组件下定义

```javascript
// 定义一个全局自定义指令
Vue.directive('color', function(el, binding){
  el.style.color = binding.value
})
// 使用全局指令
<p v-color="'red'">使用全局自定义指令</p>
```

#### axios 的全局配置

```javascript
import axios from 'axios'

Vue.config.productionTip = false
// 在全局配置下导入 axios
Vue.prototype.$http = axios
// 在组件中发起请求不在需要导入 axios 模块 直接 this.$http 发起请求即可

// 全局配置 axios 请求的根路径 如果路径前面相同则可以直接省略
axios.defaults.baseURL = 'http://www.liulongbin.top:3006'
```

### 前端路由的概念与原理

#### 什么是路由

路由（英文：router）就是对应关系

Hash 地址 与 组件之间的对应关系

#### 前端路由的工作方式

1. 用户点击了页面上的路由链接
2. 导致了 URL 地址栏中的 Hash 值发生了变化
3. 前端路由监听到了 Hash 地址的变化
4. 前端路由把当前的 Hash 地址对应的组件渲染到浏览器中

#### 前端路由的对应关系

{ path: '#/home' , component: 'home'}

#### onhashchange 

当 hash 地址变化时 会触发该事件

#### vue-router 的基本使用

1. 安装 vue-router 包  （npm i npm-router -S）
2. 创建 路由模块
3. 导入并挂载路由模块
4. 声明路由链接和占位符

##### 创建路由模块

在src 源代码目录下新建一个 router 文件夹

在文件下面新建一个 index.js 的 router 模块的文件

```JavaScript
// 导入Vue
import Vue from 'vue'
// 导入 vue-router 包
import VueRouter from "vue-router"

// 调用 vue.use() 函数 把 VueRouter 安装为 Vue 插件
Vue.use(VueRouter)

// 创建路由的实例对象
const router = new VueRouter()

// 将创建好的路由实例对象向外共享
export default router
```

##### 路由模块中的 router-view

```JavaScript
// 导入需要的组件
import Home from "@/components/myHome.vue"
import Move from "@/components/myMove.vue"
import About from "@/components/myAbout.vue"

// 调用 vue.use() 函数 把 VueRouter 安装为 Vue 插件
Vue.use(VueRouter)

// 创建路由的实例对象
const router = new VueRouter({
  // routes 是一个数组 用来定义 hash 与 组件之间的对应关系
  routes: [
    {path:'/home', component: Home},
    {path:'/move', component: Move},
    {path:'/about', component: About}
  ]
})

// 在需要使用组件的地方插入 
<router-view></router-view>
```

##### 路由模块中的 router-link

```html
<!-- 在配置了 vue-router 之后 就可以使用 router-link 组件 -->
    <router-link to="/home">首页</router-link>
    <router-link to="/move">电影页</router-link>
    <router-link to="/about">详情页</router-link>
    <!-- <a href="#/home">首页</a>
    <a href="#/move">电影页</a>
    <a href="#/about">详细页</a> -->
```

##### 路由重定向

```javascript
// 路由从定向 用户访问的 hash地址为 / 时，默认访问, home组件
    {path: '/', redirect: "/home"},
```

##### 路由的嵌套

```javascript
// 在子组件中的路由要写在父组件的路由规则下面
{
      path: '/about',
      component: About,
      // 路由嵌套的重定向 指定地址跳转到新的地址
      redirect: '/about/tab1',
      // 路由的嵌套 子路由下的模块切换
      children: [
        { path: 'tab1', component: Tab1 },
        { path: 'tab2', component: Tab2 },
      ]
    },
```

##### 动态路由

```javascript
// :id 为占位符 
{ path: '/move/:id', component: Move, props: true},
```

获取当前动态路由的 id 

this.$route.params.id 

在 this.$route 中 pash 只是路径部分 不包含查询部分

this.$route.fullpash 中包含了 整个路径

##### 路由导航

在浏览器中，点击实现导航的方式，叫做声明式导航

- 普通网页中点击 <a></a>链接， vue项目中点击 <router-link></router-link> 都属于 声明式导航

在浏览器中，调用API方法实现导航的方式，叫做编程式导航

- 普通网页中调用 location.href 跳转到新页面的方式，属于编程式导航

#### vue-router 中常见的编程式导航 API

- this.$router.push(" hash地址 ") // 会增加一条历史记录
- this.$router.replace(" hash 地址 ")  // 不会增加历史记录
- this.$router.go( 数值 n )  // -1 表示后退到之前的历史记录 1 表示前进一格历史记录

##### 后退和前进的简化用法

this.$router.back()  // 后退一位

this.$router.forward()  // 前进一位历史记录

#### 导航守卫

```javascript
// 为 route 实例对象，声明一个全局前置守卫
// 只要发生了路由的跳转，就必然会触发 beforeEach 的回调函数
  router.beforeEach(function(to, from, next){
  // to 是将要访问的路由信息对象
  // from 是将要离开的路由信息对象
  // next 是一个函数，调用 next() 表示放行， 允许这次的路由导航
  next()
})
```

next 的三种调用方式

- 当用户拥有后台访问权限时，直接放行 next()
- 当用户没有后台访问权限时，强制跳转到登录页面 ，next(" /login ")
- 当用户没有后台访问权限，不允许跳转到后台主页： next( false )

#### Vuex的基本使用

##### 使用Vuex的好处

1. 能够在Vuex中集中管理共享数据，易于开发和后期的维护
2. 能够高效的实现组件之间的数据共享，提高开发效率
3. 存储在Vuex中的数据都是相应式的，能够实时保持数据与页面的同步

##### 什么样的数据适合存储到Vuex中

只有组件之间共享的数据，才有必要存储到Vuex中，对于组件中的私有数据存储在自身的data中即可

##### 使用Vuex中的数据

- this.$store.state.要使用的数据名称
- 导入Vuex组件，{ mapState }，创建一个计算属性函数 computed，展开运算符 ...mapState(['数据名称'])

Vuex中的action专门用来执行异步的代码

#### 储存 token

localStorage.setItem(' token ', ' Bearer xxx ')

