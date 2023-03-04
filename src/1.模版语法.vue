<script>

// 声明式渲染，可以提高开发效率 vue2 语法
export default {
  data() {
    return {
      uname: "张三",
      msg: "<h2>大标题</h2>",
      id:"d1",
      url:"https://testnet.bidshop.io/_next/image?url=%2Fimages%2Fheader%2Flogo.png&w=256&q=75",
      attributeName: "id",
      mouseEvent:"click"
    }
  },
}

</script>

<template>
    <div style="width: 100;">
      <p>{{ num }} </p>
      <p>{{ uname }} </p>
      <!-- 只展示一次 -->
      <p v-once> 只展示一次：{{ uname }} </p>
      <button @click="changeName">改变名字</button>
      <p>{{ msg }} </p>
      <!-- 内容以 html 形式展示 -->
      <p v-html="msg"></p>

      <!-- v-bind 绑定属性 -->
      <p v-bind:id="id">v-bind 绑定属性</p>
      <img v-bind:src="url" alt="">
      <button @click="changeColor">改变颜色</button>
      <!-- 使用 js 方法 -->
      <button @click="id='d2'">改变颜色</button>
      <p>{{ num + 1 }} </p>
      <!-- 字符串拼接 -->
      <p v-bind:id="id+1">js 字符串拼接</p>
      <p v-bind:id="`${id}1`">js 字符串拼接2</p>

      <!-- 语法糖 -->
      <p :id="id">v-bind 语法糖</p>
      <!-- v-on：监听 DOM 事件 -->
      <button v-on:click="changeName">改变名字</button>
      <!-- v-on：语法糖 是 @onclick="" -->
    
      <!-- 动态参数 -->
      <!-- 动态属性 -->
      <p v-bind:[attributeName]="id">动态参数</p>
      <button @click="attributeName='class'">字体变化</button>

      <!-- 动态事件 -->
      <button @[mouseEvent]="attributeName='class'">动态事件</button>
      <!-- 点击 动态事件mouseover 之后再去 动态事件 悬浮 有效果-->
      <button @click="mouseEvent='mouseover'">动态事件mouseover</button>
    </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  #d1 {
    color: red;
  }
  
  #d2 {
    color: blue;
  }

  .d1 {
    font-size: 30px;
  }

}
</style>
