### 时间戳换算

```js
//一小时的时间戳
3,600,000
//一天的时间戳
86400000
//一个月的时间戳
2592000000
//一年的时间戳
31104000000

// 获取当天 0点的时间戳
this.startTime = new Date(new Date().toLocaleDateString()).getTime()
```

### 输入框样式

```html
 <el-input
      clearable
      style="width: 170px"
      type="primary"
      placeholder="超速比例"
      v-model="proportion"
      ></el-input>
```

### 随机数

```js
fullOpen(n,m) {
      var result = Math.random()*(m-n)+n;
      while(result == n) {
          result = Math.random()*(m-n)+n;
      }
      return result;
    },
```

### 创建随机数

```js
function geyRandom(min,max){
  	return Math.floor(Math.random() * (max - min + 1) + min)
}
```



### 销毁图表

```js
// 销毁图表实例
const myChart3 = echarts.init(document.getElementById('mainThree'));
myChart3.dispose()

// 清空图表样式
myChart.clear(); 
```

### 导出文件

```js
// 导出文件
this.$axios
        .get(
          `/smart/cmlid/server/alarm/record/out?deviceId=${this.deviceData}&projectId=${this.proData}&alarmLevel=${this.levelData}&alarmStatus=${this.alarmData}&startDate=${startDate}&endDate=${endDate}`,
          {
            responseType: "blob",
          }
        )
        .then((res) => {
          const fileName = "运行监测.xlsx";
          //   res.data:请求到的二进制数据
          const blob = new Blob([res.data], {
            type: "application/vnd.ms-excel",
          }); //1.创建一个blob
          const link = document.createElement("a"); //2.创建一个a链接
          link.download = fileName; //3.设置名称
          link.style.display = "none"; // 4.默认不显示
          link.href = URL.createObjectURL(blob); // 5.设置a链接href
          document.body.appendChild(link); //6.将a链接dom插入当前html中
          link.click(); //7.点击事件
          URL.revokeObjectURL(link.href); //8.释放url对象
          document.body.removeChild(link); //9.移除a链接dom
        })
        .catch((err) => {
          console.log(err);
          this.$message(err.data.message);
        });
```

### switch 应用

```js
// switch 判断成绩等级
fun() {
      const grade = 90

      switch (true){
        case grade >= 90:
          console.log('A')
          break;
        case grade >= 80:
          console.log('B')
          break;
        case grade >= 70:
          console.log('C')
          break;
        case grade >= 60:
          console.log('D')
          break;
        default:
          console.log('F')
      }
    }
```

### 样式

```vue

```

### Vue 修改样式方法

```vue
<div :style="{ color: styleColor, font-size: fontSize + 'px' }"></div>
<script>
	data() {
        return {
            styleColor: 'red',
            fontSize: 12
        }
    }
</script>

// 语法更加简洁
<div :style="style"></div>
<script>
	data() {
        return {
            style: {
                color: 'res',
                fontSize: '12px'
            }
        }
    }
</script>
```

### V-if 和 v-for 一起使用

```vue
<template v-for="item in items">
	<div v-if="item == fa">
        
    </div>
</template>
```

### sort 方法的使用

```js
// 从小到大排序
nums.sort((a,b)=>b-a)
```

### 冒泡排序

```js
// array 表示数组
// 从小到大排序
for(let i = 0; i < array.length; i++) {
	for (let j = 0; j < array.length; j++) {
		if(array[j] > array[j + 1]) {
			let temp = array[j]
			array[j] = array[j + 1]
			array[j + 1] = temp
		}
	}
}
```

### 网格布局

```less
// 固定的列宽
.wrapper {
  display: grid;
  /*  声明了三列，宽度分别为 200px 100px 200px */
  grid-template-columns: 200px 100px 200px;
  grid-gap: 5px;
  /*  声明了两行，行高分别为 50px 50px  */
  grid-template-rows: 50px 50px;
}

// 表示第一个列宽设置为 200px，后面剩余的宽度分为两部分，宽度分别为剩余宽度的 1/3 和 2/3
.wrapper-3 {
  display: grid;
  grid-template-columns: 200px 1fr 2fr;
  grid-gap: 5px;
  grid-auto-rows: 50px;
}

// 表示第一第三列为 100px，中间由浏览器决定长度
.wrapper-5 {
  display: grid;
  grid-template-columns: 100px auto 100px;
  grid-gap: 5px;
  grid-auto-rows: 50px;
}


```

### 浅拷贝和深拷贝的区别

浅拷贝：在栈内的简单数据类型直接重新开辟一个空间将数据拷贝一份，修改源数据不会将拷贝的数据修改，浅拷贝在堆内的复杂数据类型，拷贝的是堆内的数据地址，修改堆内的数据，拷贝的数据也会修改

赋值：当我们把一个对象赋值给一个新的变量时，赋的其实是该对象的在栈中的地址，而不是堆中的数据。也就是两个对象指向的是同一个存储空间，无论哪个对象发生改变，其实都是改变的存储空间的内容，因此，两个对象是联动的

深拷贝：深拷贝是将一个对象从内存中完整的拷贝一份出来,从堆内存中开辟一个新的区域存放新对象（新旧对象不共享同一块内存）,且修改新对象不会影响原对象（深拷贝采用了在堆内存中申请新的空间来存储数据，这样每个可以避免指针悬挂）

### 自适应方案

```vue
<script>
    
    /**
    js部分
    */
    mounted(){
        //初始化自适应  ----在刚显示的时候就开始适配一次
        handleScreenAuto();
        //绑定自适应函数   ---防止浏览器栏变化后不再适配
        window.onresize = () => handleScreenAuto();
    },
    deleted(){
        window.onresize = null;
    },
    methods: {
        //数据大屏自适应函数
        const handleScreenAuto = (): void => {
            const designDraftWidth = 1920;//设计稿的宽度
            const designDraftHeight = 960;//设计稿的高度
            //根据屏幕的变化适配的比例
            const scale = document.documentElement.clientWidth / document.documentElement.clientHeight < designDraftWidth / designDraftHeight ?
                (document.documentElement.clientWidth / designDraftWidth) :
                (document.documentElement.clientHeight / designDraftHeight);
            //缩放比例
            (document.querySelector('#screen') as any).style.transform = `scale(${scale}) translate(-50%)`;
        }
    }
</script>

/**
    html部分
 */
 <template>
     <div className="screen-wrapper">
        <div className="screen" id="screen">

        </div>
     </div>
 </template>


    /*
      CSS部分  --除了设计稿的宽高是根据您自己的设计稿决定以外，其他复制粘贴就完事
    */  
   <style>
         .screen-root {
    height: 100%;
    width: 100%;
    .screen {
        display: inline-block;
        width: 1920px;  //设计稿的宽度
        height: 960px;  //设计稿的高度
        transform-origin: 0 0;
        position: absolute;
        left: 50%;
        }
    }
   <style>

```

### promise 的注册

```
const pormise = new Pormise((resolve, reject) => {
	resolve(5)
})
```

### canvas 初始化

```html
<canvas 
    id="canvas" 
    width="600" 
    height="400">
  </canvas>
  <script>
    let canvas = document.querySelector('#canvas')
    let ctx = canvas.getContext('2d')
  </script>
```

### 多行文本显示

```css
    /* 多行文本溢出 */
    .intwolines{
        display: -webkit-box !important;
        overflow: hidden;

        word-break:break-all ;
        text-overflow: ellipsis;

        -webkit-box-orient: vertical;
        -webkit-line-clamp: 2;  
        /*  -webkit-line-clamp: num  想要几行展示都可设置 */
    }

```

### 原型和原型链

```tex
原型是什么？

每个函数在创建都有一个prototype(原型)，通过这个函数创建的实例对象会有一个_proto_(隐式原型)，创建的这个实例对象会继承这个函数的原型对象，通过这个函数创建的实例对象的原型和这个函数的原型本质上是一样的

原型可以解决的问题？

共享属性和方法?

谁有原型

函数 function prototype
对象: object _proto_

原型链：
当我们需要访问对象的某个属性时
先在对象本身查找 --> 构造函数中查找 --> 对象的原型 --> 构造函数的原型

```

