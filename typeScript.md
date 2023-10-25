### 初始化tsconig.josn文件

```
tsc --init
```

### 编译 ts 代码


```js
tsc 文件路径
```

### typeScript 基础

#### 定义 ts 变量

```typescript
let 变量:类型;
let 变量:类型 = 值;
function fn (参数:类型, 参数:类型) {}

// 函数返回值类型限制
function fn():number {}
```

#### typeScript 类型

|  类型  |       例子       |              描述              |
| :-----: | :---------------: | :----------------------------: |
| number |    1, -33, 1.5    |            任意数字            |
| string |  '你好', 'hello'  |           任意字符串           |
| boolean |    true, false    |             布尔值             |
|   any   |         *         |            所有类型            |
| 字面量 |      其本身      |    限制类型为定义的变量类型    |
| unknown |         *         |         类型安全的 any         |
|  void  | 空值（undefined） |             没有值             |
|  never  |      没有值      |          不能是任何值          |
| object |  { number: 10 }  |            对象类型            |
|  array  |    [1,  2, 3]    |              数组              |
|  tuple  |      [4, 5]      | 元素，TS新类型，固定长度的数组 |
|  enum  |    enum{a, b}    |         枚举，TS新类型         |

#### ts 编译选项

```typescript
tsc 文件名 -w   // -w 自动编译 只能监视单个文件

tsc -w // 监视目录下的所有文件 需要有配置文件 tsconfig.json
```

#### tsconfig.json 配置项

1. include 希望被编译的文件所在地址  `"include:" ['src/**/**', 'tests/**/*']`
2. exclude 定义需要排除在外的目录 `"exclude": ['/src/hello/']`
3. extends 定义被继承的配置文件 `"extends": "./config/base"`
4. files 指定被编译的文件列表,只有需要编译的文件时才会用到 `"files":['core.ts']`
5. compilerOptions(重点)
   ```typescript
   "target": "es6",       // 用来指定 ts 编辑的版本   
   // "lib": [],        // 用来指定浏览器当中需要使用的库 一般不使用
   "strict": true,    // 所有严格检查的总开关
   "module": "ES2015",   // 指定 要使用模块化的规范  
   // "allowJs": true,  // 是否对js文件进行编译   
   // "checkJs": true,   // 检查js代码是否符合语法规范 
   // "outFile": "./dist/app.js",       // 将编译后的文件合并为一个文件
    "outDir": "./dist",          // 用来指定编译后文件所在的路径  
   "removeComments": true,    // 是否移除编译后的注释  
   "noEmitOnError": true,  // 当有错误时不生成编译文件 
   / "noImplicitAny": true,    // 不允许隐式的 any 类型
   "noImplicitThis": true,    // 不允许不明确类型的 this   
   ```
