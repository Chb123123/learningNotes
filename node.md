### node基础语法

#### 打开文件：

```javascript
fs.readFile(puth[, options], callback)
```

#### 获取文件夹下的文件

```
fs.readdir(puth[, options], callback)
```

#### 写入文件

```javascript
fs.writeFile(file, data[, options], cailback)

//第一个参数, 必选参数，需要指定一个文件的路径字符串，表示文件的存放路径

//第二个参数，表示要写入的文件内容

//第三个参数，表示文件以什么编码格式写入，默认utf-8格式

//第四个参数 回调函数
```

#### path 路径拼接

- 获取路径中的文件名称

```node
path.join([...paths])
```

```
path.basename(path[, ext])
path 文件路径 
ext 筛选的文件名称
```

- 获取路径中的扩展名

```
path.extname(path)
path 为存放文件的路径
```

#### exec() 方法

```javascript
// 用于检索正则表达式
正则表达式语法.exec(string)
```

regStyle 提取内嵌的style标签

regScript 提取内嵌的 script 标签

### HTTP 模块

通过几行代码，搭建一个web服务器

#### 创建 web 服务器

1. 导入 http 模块

2. 创建 web 服务器实例

3. 为服务器绑定 request 事件

4. 启动服务器

   ```javascript
   const http = require('http')
   
   // 创建 web 服务器实例
   // 调用 http.createSever() 方法 
   const server = http.createServer()
   
   server.on('request', function(req, res) {
     const str = `数据请求类型为${req.method}, 请求地址为${req.url}`
     console.log(str)
     // 为了防止中文乱码的问题，需要设置响应头 Content-type 
     res.setHeader('Content-Type', 'text/html;charset=utf-8')
     // res.end()
     // 向客户端发起指定的内容， 并结束这次的请求处理过程
     res.end(str)
   })
   
   // 启动服务器
   server.listen(80, function() {
     console.log('http server runing at http://127.0.0.1')
   })
   ```

   ### 切换 npm 的下包镜像源
   
   查看当前下包的服务器地址
   
   npm config get registry 
   
   （https://registry.npmjs.org/）官方地址
   
   将下包的镜像源切换为淘宝镜像源
   
   npm config set registry=https://registry.npm.taobao.org/
   
   
   
   使用nrm 工具快速切换镜像源
   
   nrm ls 查看所有镜像源
   
   nrm use (镜像源名称 ：taobao)
   
   
   
   // 将md 文件转化为 html 页面
   
   npm install i5ting_toc -g
   
   
   
   i5ting_toc -f 要转换的md文件路径 -o
   

在开发自己的包时， 创建一个 README.md 文档， 文档应当包含六个内容

1. 安装方式
2. 导入方式
3. 创建的方法使用教程
4. 开源协议

在 npm 官方发布 自定义包时，先将下载包地址切换到 官方地址， 否则登入会失败

登入npm

npm login

1. 账号
2. 密码
3. 邮箱
4. 第一次登入的邮箱验证

切换包的根目录

将包发布在npm 

npm publish



删除已发布的包

npm unpublish 包名 --force 即可删除

npm unpunlish 只能删除 72 小时内发布的包

当包发布时间超过 72 小时就无法删除

删除的包在 24 小时以内是无法重复发布



### 通过 express 模块搭建服务器

#### 下载 express 模块

npm install express

#### 通过 express  模块搭建web 服务器

```js
// 导入 express 模块
const express = require('express')
// 创建 web 服务器
const app = express()
// 运行服务器
app.listen(80, function() {})
```

#### 监听 GET 与POST请求

```js
// get 请求的语法
// 参数 1: 客户端请求的 url 地址
// 参数 2: 请求对应的处理函数
//      req: 请求对象(包含了请求相关的属性与方法)
//      res: 相应的对象(包含了与响应相关的属性和方法)
app.get('/user', function(req, res) {
  // 向客户端发送 JSON 数据
  res.send({
    name: '张三',
    age: 18,
    gender: '男'
  })
})

// post 请求的语法
app.post('/user', function(req, res) {
  res.send('post请求成功')
})
```

#### 监听 客户端发送请求携带的参数

```js
app.get('/user', function(req, res) {
  // req.query 默认是一个空对象
  // 客户端使用 ?name=zz&age=20 这种查询字符串形式发送到服务器
  // 可以通过 req.query 对象访问到
  // 例如： req.query.name 或 req.query.age
  console.log(req.query)
  res.send({
    name: '张三'
  })
})
```

#### 获取 url 中的动态参数

```js
// 获取 url 中的动态参数
// URL 地址中， 可以通过 : 参数名的形式匹配动态参数值
app.get('/:id/:name', function(req, res) {
  // req.params 默认是一个空对象
  // 里面存放着通过 : 动态匹配到的参数值
  console.log(req.params)
  res.send(req.params)
})
```

#### 托管 静态资源

express.static()

通过它，我们可以 非常方便的创建一个静态资源服务器，例如 可以将 目录下的图片 css文件 javaScript文件对位开放访问

```js
// express.static('需要共享的资源路径')
app.use(express.static("./新闻"))
```

#### 挂载前缀路径

根据不同的路径访问不同的资源

```js
// 挂载路径前缀
app.use('/news', express.static("./新闻"))
app.use('/', express.static('./立雪杯比赛'))
```

#### 使用 nodemon

插件功能 ：当修改 node 源代码时， 不需要频繁的关闭服务器再重启服务器，当代码修改的时候，nodemon会自动重启项目

nodemon 下载

```
npm install nodemon -g
```



#### express 的路由

路由指的是 客户端请求与服务器处理函数之间的映射关系

express 路由分为 3 部分， 分别是 请求的类型、请求的URL 地址、处理函数

```js
app.METHOD(PATH, HANDLER)
```

#### 模块化路由

1. 创建路由模块对应的 js 文件
2. 调用 express.Router() 函数创建路由对象
3. 使用 module.express 向外共享路由对象
4. 使用 app.use() 函数注册路由模块

#### app.use()

app.use() 的作用就是来注册全局中间件

#### 全局生效的中间件

客户端发起的任何请求到达服务器之后，都会触发的中间件， 叫做全局生效中间件

#### 局部生效的中间件

不使用 app.use 定义的中间件叫局部中间件

```js
const m1 = function(req, res, next) {
  console.log('局部中间件')
  next()
}
// 局部中间件可以有多个，之间用逗号隔开
app.get('/', m1, function(req, res, next) {
  console.log('get请求成功')
  res.send('请求成功')
})
```

#### 中间件的分类

1. 应用级别的中间件
2. 路由级别的中间件
3. 错误级别的中间件
4. Express 内置的中间件
5. 第三方中间件

##### 错误级别的中间件

错误级别的中间件可以捕获接口的异常，防止程序不能正常运行

```js
app.get('/', function(req, res) {
  throw new Error('服务器发生故障')
  res.send('Home Page')
})

app.use((err, req, res, next) => {
  console.log('发生了错误' + err.message)
  res.send('Error' + err.message)
} )
```

错误级别的中间件必选写在所有中间件之后

##### 内置中间件

1. express.static() 快速托管静态资源
2. epxress.json 解析JSON 格式的数据请求
3. express.urlencoded 解析 URL-encoded 格式的数据请求体数据

使用 express.json 

```js
// 配置解析 application/json 格式数据的内置中间件
app.use(express.json())
```

配置解析 application/x-www-for-urlencoded 格式数据的中间件

```js
app.use(express.urlencoded({ extended: false }))
```

##### 自定义中间件

1. 自定义中间件
2. 监听 req 的 data 事件
3. 监听 req 的 end 事件
4. 使用 querystring 模块解析请求体数据
5. 将解析的数据对象挂载到 req.body
6. 将自定义中间件封装为模块

#### 解决接口跨域的问题

cors 解决跨域问题

1. 下载 cors  npm install cors

2. 导入 cors const cors = require('cors')

3. #### 在全局注册 cors app.use(cors())

##### CORS 跨域资源共享

###### （1）cors 响应头 Access-Control-Origin

```js
// 表示 请求只允许 http://chb.cn 地址通过
res.setHeader('Access-Control-Allow-Origin', 'http://chb.cn')

// 允许通过任何域的请求
res.setHeader('Access-Control-Allow-Origin', '*')
```

###### （2）Access-Control-Allow-Heades

![image-20221007215231206](C:\Users\蔡怀彬\AppData\Roaming\Typora\typora-user-images\image-20221007215231206.png)

###### (3) Access-Control-Allow-Methods

默认情况下 CORS 仅支持 客户端发起 GET, POST,HEAD 请求，如果希望客户端通过PUT, DELETE 等方式请求服务器资源，则需要在服务器端通过Access-Control-Allow-Methods来指明允许使用 HTTP 方法

```js
res.setHeader('Access-Control-Allow-Methods', 'POST, GET, DELETE')

// 允许所有请求方法
res.setHeader('Access-Control-Allow-Methods', '*')
```

##### 请求分类

###### 简单请求

![image-20221007220227206](C:\Users\蔡怀彬\AppData\Roaming\Typora\typora-user-images\image-20221007220227206.png)

###### 预检请求

![image-20221007220438176](C:\Users\蔡怀彬\AppData\Roaming\Typora\typora-user-images\image-20221007220438176.png)

###### 简单请求和预检请求的区别

简单请求的特点：客户端与服务器只会发生一个请求

#### 编写 JSONP 接口

1. 获取客户端发送过来的请求

2. 得到要通过JSONP形式发送给客户端的数据

3. 根据前两步得到的数据，拼接出一个函数调用的字符串

4. 把上一步拼接得到的字符串，响应给客户端的<script>标签进行解析执行

   ```js
   app.get('/api/jsonp', function(req, res){
     // 获取客户端发送过来的回调函数名称
     const funcName = req.query.callback
     // 得到要通过的 JSONP 形式发送给客户端的数据
     const data = { name: '张三', age: 22 }
     // 根据前两步得到的数据，拼接一个函数调用的字符串
     const scriptStr = `${funcName}(${JSON.stringify(data)})`
     // 把上一步拼接的字符串，响应给客户端的 <script>标签进行解析执行
     res.send(scriptStr)
   })
   
   ```


### 

### mysql 模块的基本使用

建立与 mysql 数据库的连接

```js
const mysql = require('mysql')

// 建立与 Mysql 数据库的连接
const db = mysql.createPool({
  host: "127.0.0.1",  // 数据库的ip地址
  user: "root", // 登入数据库的账号
  password: '123456',  // 登入数据库的密码
  database: 'demo-1' // 要连接的数据库
})
```

#### 测试mysql模块是否连接成功

```js
// 监测 mysql 模块能否正常工作
db.query('select 1', (err, results) => {
  if (err) {
    return console.log(err.message)
  }
  console.log(results)  // 只要能打印出 [ RowDatePacket { "1": 1 } ] 就证明 数据库连接成功
})
```

通过 mysql 模块插入数据

```js
// 定义一个要插入的用户信息对象
const userItem = { name: '老赵', age: 22 }
// 定义要执行的sql语句
const sqlStr = 'insert into usernameTable ( name, age ) values (?, ?)'
db.query(sqlStr,[ userItem.name, userItem.age ], (err, results) => {
  if(err) return console.log(err.message)
  // 只有 results.affectedRows = 1 时才算插入成功
  if(results.affectedRows == 1) {
    console.log('插入数据成功')
  }
})

```

通过数据更新数据

```js
// 更新数据的便捷方式 数据必选和数据库的列名称一一对应
const newUser = { name: '绿茶', age: 26, id: 1 }
const sqlStr = 'update usernameTable set ? where id = ?'

db.query(sqlStr,[ newUser, newUser.id ], (err, results) => {
  if(err) return console.log(err.message)
  // console.log(results)
  if(results.affectedRows === 1) {
    console.log('修改数据成功')
  }
})
```

删除数据

```js
// 标记删除
const sqlStr = 'update usernameTable set status = 1 where id = ?'
db.query(sqlStr, 1, (err, results) => {
  if(err) return console.log(err.message)
  if(results.affectedRows === 1) {
    console.log('删除成功')
  }
})

// 查询标记为 0 的数据
const sqlStr1 = 'select * from usernameTable where status = 0'
db.query(sqlStr1, (err, results) => {
  if(err) return console.log(err.message)
  console.log(results)
})
```

### 身份认证

#### session 认证

（1）http请求的 无状态性

http 请求的无状态性，指的是客户端 每次 http 请求都是独立的，连续多次请求没有直接关系，服务器不会主动保留每次的 HTTP 请求状态

身份认证 

web 专业术语 叫 Cookie

Cookie 是存储在用户浏览器中一段不超过 4kb 的字符串，它由一个名称（name）、一个值（value）和其他几个用于控制 Cookie 有效期、安全性、使用范围的可选属性组成

Cookie 的几大特性

1. 自动发送
2. 域名独立
3. 过期时限
4. 4kb 限制

使用 session 

安装 express-session 

npm install express-session

#### JWT 认证

JWT的组成部分

Header(头部)

Payladf(有效荷载)

Signature(签名)

Header.Payload.Signature



安装 JWT 相关的包

npm install jsonwebtoken express-jwt

jsonwebtoken 用于生成 JWT 字符串

express-jwt 用于将 JWT 字符串解析还原成 JSON 对象

##### 定义 secret 密钥

防止 jwt 字符串在网络传输中被破解，需要专门定义一个用于 加密和破解的 secret

```js
// 在登入成功后生成 JWT 字符串
// 登入接口
app.post('/api/login', function(req, res) {
  // 
  if(req.query.username !== 'admin' || req.query.password !== '123456') {
    return res.send({
      status: 400,
      message: '登入失败'
    })
  }
  // 在用户登入成功后 生成 JWT 字符串，通过token属性相应给 客户端
  res.send({
    status: 200,
    message: '登入成功',
    // 调用 jwt.sign()生成 jwt 字符串, 三个参数分别是 用户信息对象, 加密密钥, 配置对象有效期
    token: jwt.sign({ username: userinfo.username }, secretKey, { expiresIn: '30s' })
  })
})
```



### node 接口自动生成 api文档

安装 apidoc 模块

npm install apidoc -g

将 scr 下的文件 规定注释的文件转换为 api 文档

apidoc -i src/ -o apidoc/



#### 表单验证

joi 为表单中携带的每个数据项，定义验证规则

@escook/express-joi 来实现自动对表单数据进行验证的功能

@hapi/joi 使用方法

```js
// .string() 表示值必须是字符串
// alphanum() 表示值只能是包含 a-z A-Z 0-9 之间的字符串
// min(length) 最小长度
// max(length) 最大长度
// required() 值为必填项，不能为undefined 
// pattern(正则表达式) 值必须符合正则表达式的规则
```



#### 生成 token 数据

```JS
// 导入 jsonwebtoken 插件
// 在全局创建一个 config.js 文件
module.exports = {
  jwtSecretKey: 'caihuaibin No1'
}
// 在登入接口文件中导入 config.js 文件 和 jsonwebtoken 插件
const jwt = require('jsonwebtoken')
const config = requite('config.js路径')
// 获取用户信息 将不需要的数据剔除
const userInfo = { ...results[0], password: '', user_pic: '' }
// 生成 token 字符串
const tokenStr = jwt.sign(userInfo, config.jwtSecretKey, {
  expiresIn: '10h' // token有效期为10小时
})
// 登成功将生成的 token 数据返回给客户端
 res.send({
   status: 200,
   message: '登入成功',
   token: 'Bearer ' + tokenStr
 })

```

#### 解析 token 字符串

```js
// 安装 express-jwt 版本太高的 插件可能会报错 安装 @5.33
// 在 app.js 中导入 config.js 文件 和 express-jwt
const config = require('config.js文件路径')
const expressJWT = require('express-jwt')
// 使用 .unless() 指定哪些接口不需要 token 认证
app.use(expressJWT({ secret: config.jwtSecretKey }.unless({ path: [/^\/api\//] })))

// 在 app.js 错误中间件里捕获 token 认证失败后的错误
if(err.name === 'UnauthorizedError') return res.cc('token认证失败', 400)
```

​	

#### 将用户密码加密

```js
const bcrypt = require('bcryptjs')  // 导入插件
// 密码加密
const compareResult = bcrypt.hashSync('需要加密的数据', 10) // 10 表示长度
// 判断密码是否正确 user.password表示原密码 results[0].password表示数据库密码
const compareResult = bcrypt.compareSync(user.password, results[0].password) 
// 当上面的 compareResult 为 true 表示密码正确，false w
```

