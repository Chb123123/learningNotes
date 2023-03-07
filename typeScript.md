### 编译 ts 代码

```js
tsc 文件路径
```

### typeScript 基础

#### 定义 ts 变量

```
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
