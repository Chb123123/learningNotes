### 创建 vite 项目

1. npm init vite-app "项目名称"
2. cd 项目路径
3. npm install
4. npm run dev

#### 计算属性

```js
import { ref, reactive, computed, watch } from 'vue'
// 简写形式 computed
 let fullName = computed(() => {
   return `${data.obj.firstName}${data.obj.lastName}`
 })
 // 完整形式 computed 考虑读 和 写
data.obj.fullName = computed({
  get() {
    return `${data.obj.firstName}-${data.obj.lastName}`
  },
  set(value) {
    const nameAll = value.split('-')
    data.obj.firstName = nameAll[0]
    data.obj.lastName = nameAll[1]
  }
})
```

#### 数据监听

```js
import { ref, reactive, computed, watch } from 'vue'
// 事件监听 监听多个数据
watch([sum,str], (newValue, oldValue) => {
  console.log(newValue, oldValue)
})
// 立即监听
watch(sum, (newVal, oldVal) => {
   console.log(newVal, oldVal)
}, {immediate: true})

// 深度监听
/*
  监听的数据是一个对象
  1、无法正确的获取 oldValue
  2、强制开启深度监听
*/ 
watch(person, (newVal, oldVal) => {
   console.log(newVal, oldVal)
}, { deep: true })

// 监听 reactive 定义的响应式数据中的一个属性 监听的数据是一个函数的返回值
watch(() => person.name, (newVal, oldVal) => {
  console.log(newVal, oldVal)
})
```

#### 数据监听 watchEffect

```js
// 全局监听 类似 computed
// watchEffect 注重过程 computed 注重结果
watchEffect(() => {
  let test = sum.value
  console.log('watchEffect 回调执行了', test)
})
```

#### vue3生命周期

1. beforecreated
2. created
3. beforeMount
4. mounted
5. beforeUpdate
6. updated
7. beforeUnmount 准备销毁
8. unmounted 销毁完成

#### hooks模块

将程序某个功能封装成一个模块，使用的时候导入，完成代码的简洁性和复用性

#### toRef

作用: 创建一个 ref 对象，其中 value 指向另一个对象的某个属性

语法: const name = toRef(person, 'name')

应用: 要将响应式对象中的某个属性单独提供给外部使用时

#### toRow 

将响应式的数据还原成最原始的数据

只能还原 reactive 创建的响应式数据

```js
let str = ref('张三')
console.log(str)
let toRowStr = toRow(str)
```

#### markRaw

作用：标记一个对象，使其永远不会成为响应式的

应用场景

1. 有些值不应该为响应式对象，例如复杂的第三方类库
2. 当渲染具有不可变数据源的大列表时，跳过响应式转换可以提高性能

#### customRef

1. 创建一个自定义的 ref 并对其依赖项跟踪和更新触发就行显式控制

```js
import { ref, customRef } from 'vue'
// let keyWord = ref('hello') // 使用 vue 提供的 ref
// let keyWord = customRef()  // 使用 customRef 自定义 ref
let keyWord = myRef('hello')
// 自定义一个 ref
function myRef(value) {
  console.log(value)
  let timer
  return customRef((track, trigger) => {
    return {
      get: function() {
        track() // 通知 vue 追踪 value的变化（提前通知 value 是有用的，需要修改）
        return value
      },
      set: function(newVal) { // newVal 为修改后的数据
        console.log(newVal)
        clearTimeout(timer)
        timer = setTimeout(() => { // 等 1s 在解析模板
          value = newVal
          trigger() // 通知 vue 重新解析模板
        }, 500)
      }
    }
  })
}
```

#### 组件之间共享数据 provide 与 inject

```js
//在祖组件使用 provide 在后代组件使用 inject
// 示例
// 祖组件
import { reactive, provide } from 'vue'
let carObj = reactive({
  name: 'car1',
  price: 20,
})
provide('car', carObj) // 给自己的后代组件传递数据

// 后代组件
import { inject } from 'vue'
let car = inject('car')
```

#### 响应式数据判断

1. idRef: 检查一个值是否为一个 ref 对象
2. isReactive：检查一个对象是否由 reactive 创建的响应式代理
3. isReadonly: 检查一个对象是否由 readonly 创建的只读代理
4. isProxy: 检查一个对象是否是由 reactive或 readonly 方法创建的代理
