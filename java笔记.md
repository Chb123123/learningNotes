## Java 基础

### 声明变量

- douber     表示声明的是一个浮点类型的数据

### 键盘输入

Scanner 声明的类，可以接收键盘输入的数字

1. 导包 ---- Scanner 这个类在哪

2. 创建对象-- 表示要开始使用 Scanner 这个类

3. 接收数据

   ```java
   // 导入 Scanner 这个包
   import java.util.Scanner;
   // 创建对象
   Scanner chr = new Scanner(System.in);
   // 将创建好的对象赋值给 i, j
   int i = chr.nextInt();
   ```


### 数值类型转换

```java
// 数值类型从小到大排序
byte => short => int => long => float => double
```

- 隐式转换(自动类型提升)，把一个取值范围小的类型转换为取值范围大的类型（当两种不同的数据类型进行计算时，取值范围小的会自动转为取值范围大的数据类型）

- 强制转换，把一个取值范围大的类型转为取值范围小的类型

