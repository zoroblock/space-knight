<script>
// 绑定内联样式
// 声明式渲染，可以提高开发效率 vue2 语法
export default {
  data() {
    return {
      activeColor: 'red',
      fontSize: '30px',
      bgColor: 'yellow',
      styleObj: {
        color:'red', 
        fontSize:'30px', 
        'background-color': 'green'
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
    <div>
      <!-- 放置字符串 -->
      <p style="color: aqua;"> hello </p>
      <!-- 放置对象 推荐使用驼峰命名的属性，使用 css 原生属性需要添加引号 eg:'background-color' -->
      <p :style="{color:activeColor, fontSize:fontSize, 'background-color': bgColor}"> hello1 </p>
      <!-- 放置对象 -->
      <p :style="styleObj"> hello2 </p>
      <!-- 数组语法 -->
      <p :style="[styleObj, {border:'5px solid blue'}]"> hello2 </p>
    </div>
</template>

<style scoped>

</style>
