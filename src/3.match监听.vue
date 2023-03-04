<script>

// 声明式渲染，可以提高开发效率 vue2 语法
export default {
  data() {
    return {
      message: "你好",
      age: 0,
      user:{
        name:"张三",
        age: 18,
      }
    }
  },
  methods: {
  },
  watch: { // 监听数据变化
    // 第一种写法
    // 每当 message 发生变化时，这个函数就会运行
    // message:function(newVal, oldVal){ // 一个数据变化影响多个数据
    //   console.log(newVal," -- ", oldVal)
    //   // 执行异步或开销较大的操作时，使用这个选项，而不是在数据变化时直接使用
    //   if(newVal.length < 5 || newVal.length > 10){
    //     console.log("长度不符合要求");
    //   }
    // },
    // 第二种写法
    message: {
      immediate: true, // 初始化立即执行
      handler: function(newVal) {
        if(newVal.length < 5 || newVal.length > 10) {
          console.log("长度不符合要求");
        }
      }
    },
    // 监听不到对象属性变化，需要使用深度监听
    // user: function(newVal) {
    //   console.log(newVal);
    // },
    // 第一种写法
    // user: { // deep 深度监听
    //   handler: function(newVal) {
    //     console.log(newVal);
    //   },
    //   deep: true // 是否深度监听, 监听器会一层层的往下遍历，给对象的每个属性都加上监听器
    // }
    // 第二种优化写法，使用字符串形式进行优化
    "user.name": { // deep 深度监听
      handler: function(newVal) {
        console.log(newVal);
      },
      deep: true // 是否深度监听, 监听器会一层层的往下遍历，给对象的每个属性都加上监听器
    }  
  },
}

</script>

<template>
    <div>
      <p>{{ message }}</p>
      <button @click="message='你好'">改变 message </button>
      <!-- v-model 双向绑定 -->
      <input type="text" v-model="message">

      <p>{{ user.name }}</p>
      <button @click="user.name='李四'">改变name </button>

    </div>
</template>

<style scoped>

</style>
