### 时间戳换算

```js
let now = new Date();
 let year = now.getFullYear();
 let month = now.getMonth() + 1;
 let day = now.getDate();
 console.log(year + "-" + month + "-" + day)
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

### JS 哈希表的使用

```js
// 创建一个哈希表实例对象
const map = new Map()
// 判断数据是否在哈希表存在 存在返回true 不存在返回 false
map.has('要查询的字段')
// 获取哈希表内键值对的值
map.get('要查询的字段') // 返回该字段存在的值
// 往哈希表内添加字段
map.set('要添加的字段', '添加的值')
// 获取哈希表内的值
map.values()
// 获取哈希表内的 key
map.keys()
// 返回哈希表内的键值对
map.entries()
// 删除哈希表内的某个值
map.delete('要删除的字段')
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
        if(j + 1 === array.length) {
            continue
        }
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

### 深度监听

```vue
wacth: {
  监听对象: {
  	handler() {
  	  监听成功的操作
  	},
  	deep: true
  }
}
```

### 正则表达式

```tex
字符串.match(正则)：返回符合的字符串，若不满足返回null

字符串.search(正则)：返回搜索到的位置，若非一个字符，则返回第一个字母的下标，若不匹配则返回-1

字符串.replace(正则,新的字符串)：找到符合正则的内容并替换

正则.test(字符串)：在字符串中查找符合正则的内容，满足则返回true,反之为false
```

![微信截图_20230907152919](C:\Users\蔡怀彬\Desktop\笔记\image\java\微信截图_20230907152919.png)

![微信截图_20230907153004](C:\Users\蔡怀彬\Desktop\笔记\image\java\微信截图_20230907153004.png)

![微信截图_20230907155611](C:\Users\蔡怀彬\Desktop\笔记\image\java\微信截图_20230907155611.png)

### replace全局替换

```js
str.replace(/"/g, '')
```

#### 匹配HTML标签

```js
// 匹配 img 标签
let reg = /<img(?:(?!\/>).|\n)*?\/>/gm
let reg1 = /<img(?:(?!\/>).|\n)*?>/gm
// 匹配自定义标签
let reg = /<自定义(?:(?!<\/自定义>).|\n)*?<\/自定义>/gm
// 匹配img中 src 内的数据
let reg2 = /src=[\'\"]?([^\'\"]*)[\'\"]?/i
```



#### 路由传参

```js
import { useRouter } from 'vue-router'
// 发送方
$router.push({
    path: '/search',
    query: {
        userId: 123
    }
})
// 接收方
import { useRoute } from 'vue-router'
let userId = route.query.userI
```

### 迭代管理

```js
getTreeData(data) {
      for (var i = 0; i < data.length; i++) {
        if (data[i].children.length < 1) {
          data[i].children = undefined;
        } else {
          this.getTreeData(data[i].children);
        }
      }
      return data;
    },
```

### 设置元素全屏效果

```js
fullScreen() {
			//全屏
    		// full 为要全屏的节点元素
			var full = document.querySelector(".container");
			this.launchIntoFullscreen(full);
		},
		//全屏封装
		launchIntoFullscreen(element) {
			if (element.requestFullscreen) {
				element.requestFullscreen();
			} else if (element.mozRequestFullScreen) {
				element.mozRequestFullScreen();
			} else if (element.webkitRequestFullscreen) {
				element.webkitRequestFullscreen();
			} else if (element.msRequestFullscreen) {
				element.msRequestFullscreen();
			}
		},
		//退出全屏封装
		exitFullscreen() {
			if (document.exitFullscreen) {
				document.exitFullscreen();
			} else if (document.mozCancelFullScreen) {
				document.mozCancelFullScreen();
			} else if (document.webkitExitFullscreen) {
				document.webkitExitFullscreen();
			}
		},
		checkFull() {
			//判断浏览器是否处于全屏状态 （需要考虑兼容问题）
			//火狐浏览器
			var isFull =
				document.mozFullScreen ||
				document.fullScreen ||
				//谷歌浏览器及Webkit内核浏览器
				document.webkitIsFullScreen ||
				document.webkitRequestFullScreen ||
				document.mozRequestFullScreen ||
				document.msFullscreenEnabled;
			if (isFull === undefined) {
				isFull = false;
			}
			return isFull;
		},
```

### 判断是否是数组

```js
arr instanceof Array  // true |
```

![微信截图_20230718155451](C:\Users\蔡怀彬\Pictures\微信截图_20230718155451.png)

### 加载动画

```vue
<template>
  <div class="container">
    <div class="loading">
      <div class="dot" v-for="item in 36" :key="item"></div>
    </div>
  </div>
</template>

<style scoped lang="scss">
$ballSize: 13px;
$containerSize: 300px;
$ani-duration: 2000ms; 
.container {
  height: calc(100vh - 150px);
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid #ccc;
  box-sizing: border-box;
}
.loading {
  width: $containerSize;
  height: $containerSize;
  border: 1px solid #ccc;
  position: relative;
  // border-radius: 50%;
  padding: 50px;
  background-color: #65C7F3;
  // outline: 1px solid #fff;
}
.dot {
  position: absolute;
  left: 50%;
  top: 50%;
  width: $ballSize;
  height: $ballSize;
  perspective: 70px;
    // 开启 3D 效果
  transform-style: preserve-3d;
  // margin-left: -$ballSize / 2;
  // margin-top: -$ballSize / 2;
  transform: translate(-50%, -50%);
  // background: red;
  &::before,
  &::after {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 50%;
  }
  &::before {
    background: #000;
    top: -100%;
    animation: moveBlack $ani-duration infinite;
  }
  &::after {
    background: #fff;
    top: 100%;
    animation: moveWhite $ani-duration infinite;
  }

}
$n: 36; // 小球的数量
$pdeg: 360deg / $n; // 小球的间隔角度
@for $i from 1 through $n {
  .dot:nth-child(#{$i}) {
    transform: rotate(#{$i * $pdeg}) translateY(100px);
  }
}

@keyframes moveBlack {
  0% {
    animation-timing-function: ease-in;
  }
  25% {
    transform: translate3d(0, 100%, -$ballSize);
    animation-timing-function: ease-out;
  }
  50% {
    transform: translate3d(0, 200%, 0);
    animation-timing-function: ease-in;
  }
  75% {
    transform: translate3d(0, 100%, $ballSize);
    animation-timing-function: ease-out;
  }
}
@keyframes moveWhite {
  0% {
    animation-timing-function: ease-in;
  }
  25% {
    transform: translate3d(0, -100%, -$ballSize);
    animation-timing-function: ease-out;
  }
  50% {
    transform: translate3d(0, -200%, 0);
    animation-timing-function: ease-in;
  }
  75% {
    transform: translate3d(0, -100%, $ballSize);
    animation-timing-function: ease-out;
  }
}
@for $i from 1 through $n {
  .dot:nth-child(#{$i}) {
    transform: rotate(#{$i * $pdeg}) translateY(100px);
    &::before,
    &::after {
      animation-delay: -$ani-duration / $n * 6 * $i;
    }
  }
}

</style>

```

### 八大排序

#### 插入排序

```java
public static void main(String[] args) {
    int[] array = {3, 44, 38, 5, 47, 15, 36, 26, 27, 2, 46, 4, 19, 50, 48};
	// 只需要修改成对应的方法名就可以了
    insertionSort(array);

    System.out.println(Arrays.toString(array));
}
/**
 * Description: 插入排序
 *
 * @param array
 * @return void
 * @author JourWon
 * @date 2019/7/11 23:32
 */
public static void insertionSort(int[] array) {
	if (array == null || array.length <= 1) {
		return;
	}

	int length = array.length;

	// 要插入的数
	int insertNum;

	for (int i = 1; i < length; i++) {
		insertNum = array[i];
		// 已经排序好的元素个数
		int j = i - 1;
		while (j >= 0 && array[j] > insertNum) {
			// 从后到前循环，将大于insertNum的数向后移动一格
			array[j + 1] = array[j];
			j--;
		}

		// 将需要插入的数放在要插入的位置
		array[j + 1] = insertNum;
	}
}
```















```
:zoom="mapZoom"

mapZoom: 15,
userMapCenter: null,

this.getAddress();
--------
if (this.userMapCenter) {
        this.mapCenter = JSON.parse(JSON.stringify(this.userMapCenter));
      }

-----------
let isLon = !this.formData.longitude || this.formData.longitude === ""
      let isLat = !this.formData.latitude || this.formData.latitude === ""
      if (isLon && isLat) {
        if (this.userMapCenter) {
          this.mapCenter = JSON.parse(JSON.stringify(this.userMapCenter));
        }
      }

// 获取个性化地图点位
    getAddress() {
      if (sessionStorage.getItem("userInfo")) {
        let userInfo = JSON.parse(sessionStorage.getItem("userInfo"));
        // 获取地图级别
        if (userInfo.mapZoom.zoom) {
          this.mapZoom = userInfo.mapZoom.zoom;
        }
        if (userInfo.mapZoom.longitude && userInfo.mapZoom.latitude) {
          this.userMapCenter = {
            lng: userInfo.mapZoom.longitude,
            lat: userInfo.mapZoom.latitude
          };
        }
      }
    },
```

