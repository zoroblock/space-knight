<script>

// 声明式渲染，可以提高开发效率 vue2 语法
export default {
  data() {
    return {
      numbers: [1, 2, 3, 4, 5],
      sets: [[ 1, 2, 3, 4, 5 ], [6, 7, 8, 9, 10]]
    }
  },
  computed: {
    // evenNumbers() {
    //   return this.numbers.filter(number => number % 2 === 0)
    // },
  },
  methods: {
    changeList() {
      // 第一个参数，开始插入或删除的位置下标
      // 第二个参数，删除的个数
      // this.numbers.splice(0) 全部删除
      // this.numbers.splice(0,1) // 删除第一个
      // this.numbers.splice(1,3) // 删除第二个到第四个

      // 插入元素
      // 第一个参数，开始插入或删除的位置下标
      // 第二个参数，0 ，后面接上需要插入的元素
      // this.numbers.splice(1,0,8,8,8,8,8)

      // 替换元素
      // 第一个参数，开始插入或删除的位置下标
      // 第二个参数，3, 需要替换元素的个数
      this.numbers.splice(1,3,8,8,8)
      this.numbers.sort();
      this.numbers.reverse();
      this.numbers.unshift(0); // 前插
      this.numbers.push(0);    // 后插
    }
  },
  watch: { 
  },
}

</script>

<!-- Vue 能够侦听响应式数组的变更方法，并在它们被调用时触发相关的更新。这些变更方法包括：
push()   数组末尾添加元素
pop()    数组末尾删除元素
shift()  数组开头删除元素
unshift() 数组开头添加元素
splice()  数组中间添加或删除元素
sort()    数组排序
reverse() 数组翻转  -->
<!-- 在计算属性中使用 reverse() 和 sort() 的时候务必小心！这两个方法将变更原始数组，
  计算函数中不应该这么做。请在调用这些方法之前创建一个原数组的副本： -->

<template>
    <div>
      <ul>
        <li v-for="n in numbers">
            {{n}}
        </li>
      </ul>
    </div>
    <button @click="changeList">改变数组</button>
</template>

<style scoped>

</style>
