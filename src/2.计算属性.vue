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
  computed: { // 计算属性，只要依赖的数据没有发生变化，就不会重新计算(有缓存，提高性能)
    // 简写
    // reverseName: function() { // 计算属性的 getter 翻转字符串
    //   console.log('reverseName');
    //   return this.uname.split('').reverse().join('')
    // }  
    // 完整写法
    reverseName: {
      get:function(){
        return this.uname.split('').reverse().join('');
      },
      // 计算属性一般没有 set 方法，计算属性是只读属性
      // 基本不会用到（设置或者更改属性的时候用到）
      set:function(newValue) {
        console.log(newValue);
        // 更新值
        this.uname = newValue;
      }
    }
  },
  methods: {
    changeName: function() {
      this.uname = "李四"
    },
    changeColor: function() {
      this.id = "d2"
    },
    reverseNameMethod: function() { 
      console.log('reverseNameMethod');
      return this.uname.split('').reverse().join('')
    }  
  },
}

</script>

<template>
    <div style="width: 100;">
      <!-- js 表达式 -->
      <p>{{ uname.split('').reverse().join('') }} </p>
      <p>{{ uname.split('').reverse().join('') }} </p>
      <p>{{ uname.split('').reverse().join('') }} </p>
      <!-- 计算属性 -->
      <p>{{reverseName}}</p>
      <p>{{reverseName}}</p>
      <p>{{reverseName}}</p>
      <!-- 使用 methods -->
      <p>{{reverseNameMethod()}}</p>
      <p>{{reverseNameMethod()}}</p>
      <p>{{reverseNameMethod()}}</p>
      
      <!-- 修改名字 -->
    <button @click="uname='123'">修改名字</button>
    <button @click="reverseName='你好啊'">改变 reverseName </button>

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
