<script>

// 声明式渲染，可以提高开发效率 vue2 语法
export default {
  data() {
    return {
      parentMessge: "Hello Vue.js!",
      items:["A","B","C","D","E"],
      myObject: {
        title: 'How to do lists in Vue',
        author: 'Jane Doe',
        publishedAt: '2016-04-10'
      }
    }
  },
  methods: {
  },
  watch: { 
  },
}

</script>

<template>
  <!-- 我们可以使用 v-for 指令基于一个数组来渲染一个列表。v-for 指令的值需要使用 item in items 形式的特殊语法，
    其中 items 是源数据的数组，而 item 是迭代项的别名： -->
    <div>
      <li v-for="item in items">
        {{item}}
      </li>

      <!-- 展示索引位置 -->
      <li v-for="(item, index) in items">
        {{parentMessge}} -- {{item}} -- {{index}}
      </li>

      <!-- v-for 与对象 -->
      v-for 与对象
      <!-- 你也可以使用 v-for 来遍历一个对象的所有属性。遍历的顺序会基于对该对象调用 Object.keys() 的返回值来决定。 -->
      <ul>
        <!-- 第一个参数表示值 -->
        <li v-for="value in myObject">
          {{value}}
        </li>
        <!-- 可以通过提供第二个参数表示属性名 (例如 key)： -->
        <li v-for="(value, key) in myObject">
          {{key}} === {{value}}
        </li>
        <!-- 第三个参数表示索引 -->
        <li v-for="(value, key, index) in myObject">
          {{key}} === {{value}} === {{index}}
        </li>
      </ul>

      在 v-for 里使用范围值
      <!-- v-for 可以直接接受一个整数值。在这种用例中，会将该模板基于 1...n 的取值范围重复多次。 -->
      <!-- 注意此处 n 的初值是从 1 开始而非 0。 -->
      <span v-for="n in 10">{{ n }}</span>

      <!-- <template> 上的 v-for -->
      <!-- 与模板上的 v-if 类似，你也可以在 <template> 标签上使用 v-for 来渲染一个包含多个元素的块。例如： -->
      <ul>
        <template v-for="item in items">
          <li>{{ item }}</li>
        </template>
      </ul>
    </div>

    通过 key 管理状态
    <div v-for="item in items" :key="item">
      {{item}}
    </div>

    <!-- 当你使用 <template v-for> 时，key 应该被放置在这个 <template> 容器上： -->
    <template v-for="item in items" :key="item">
      <li>{{item}}</li>
    </template>  

</template>

<style scoped>

</style>
