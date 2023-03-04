<script>
// Class 与 Style 绑定
// 声明式渲染，可以提高开发效率 vue2 语法
export default {
  data() {
    return {
      message: "Hello Vue.js!",
      isActice: true,
      error: {}, // null,
      classObj: {
        active: true,
        background: true
      },
      // 数组测试使用
      activeClass: 'active',
      backgroundClass: 'background',
    }
  },
  methods: { 
  },
  watch: { 
  },
  computed: {
    // 使用计算属性（也可以绑定一个返回对象的计算属性）
    classObjCom: function() {
      return {
        active: this.isActice && !this.error,
        background: this.error
      }
    }
  }
}

</script>

<template>
    <div>
      <!-- 第一种 放置字符串 -->
      <p class="active">Hello</p>
      <!-- 第二种 放置对象（可以多个对象, 切换多个 class） -->
      <p :class="{active: isActice, background: isActice}">Hello 001</p> 
      <!-- class 内部对象多的时候可以使用一个对象封装 -->
      <p :class="classObj">Hello 002 _ classObj</p> 

      <!-- :class="" 和 class="" 的内容会进行合并 -->
      <p :class="{active: isActice}" class="background"> World </p>

      <p :class="classObjCom">Hello 003 _ classObjCom</p> 

      <!-- 数组语法（不常用） -->
      <p :class="[activeClass, backgroundClass]">数组样式</p> 
      <p :class="[backgroundClass, {active: isActice}]">数组对象结合</p> 


      <button @click="isActice = !isActice"> 切换属性 001</button>
      <button @click="classObj.active = !classObj.active"> 切换属性 002 </button>

    </div>
</template>

<style scoped>

.active {
  color: red;
  font-size: 40px;
}

.background {
  background-color: #b47515;
}

</style>
