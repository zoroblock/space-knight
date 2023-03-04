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
    evenNumbers() {
      return this.numbers.filter(number => number % 2 === 0)
    },
    even(numbers) {
      return this.numbers.filter(number => number % 2 === 0)
    }
  },
  methods: {
  },
  watch: { 
  },
}

</script>

<!-- Vue 能够侦听响应式数组的变更方法，并在它们被调用时触发相关的更新。这些变更方法包括：
push()
pop()
shift()
unshift()
splice()
sort()
reverse() -->
<!-- 在计算属性中使用 reverse() 和 sort() 的时候务必小心！这两个方法将变更原始数组，
  计算函数中不应该这么做。请在调用这些方法之前创建一个原数组的副本： -->

<template>
    <div>
      <ul>
        <li v-for="n in evenNumbers">
            {{n}}
        </li>
      </ul>
      <ul v-for="numbers in sets">
        <li v-for="n in even(numbers)">{{ n }}</li>
      </ul>
    </div>
</template>

<style scoped>

</style>
