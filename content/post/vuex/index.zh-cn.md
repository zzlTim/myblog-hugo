---
title: vuex 
description: 仅供参考
date: 2024-04-21
slug: 
image: 2.jpg
categories:
    - VUE
    - 测试
# comments: true
---
大型应用往往跨越多个组件。通过多层嵌套传递参数十分复杂，并且Vue没有兄弟组件之间直接共享参数的方法。

[https://vuex.vuejs.org/zh/guide/](https://vuex.vuejs.org/zh/guide/)
VueX是专为Vue.js开发的状态管理库。集中式存储管理所有组件的状态
简单地说，VueX管理分散在Vue中的各组件的数据
npm install vuex@next  (下载最新的)

vue2--vuex3
vue3--vuex4

一般大项目才用
每个Vuex的核心都是一个store,与普通的全局对象不同的是，Vue数据和视图绑定，数据改变，绑定的视图也会被重新渲染。
store中的状态不允许直接修改，只能通过提交(commit)mutation这可以让我们跟踪状态的变化

Vuex：
State,Getter,Mutation（改变、转变）,Action,Module![状态管理](https://img-blog.csdnimg.cn/direct/4fc39808de9a4bcfbb95cc392860458b.png#pic_center)
State
可以使用this.$store.state.count访问数据源
也可以用mapstate辅助函数将其映射下来
修改state就要通过我们定义的方法去修改
mutation只能做一下同步操作，action可以异步操作
不太懂。。。

安装VUEX@3失败可能是因为证书过期了
[https://blog.csdn.net/qq_42761482/article/details/121018086](https://blog.csdn.net/qq_42761482/article/details/121018086)

通过commit修改store内容
```
<template>
  <div class="hello" >
    {{ this.$store.state.count }}
    <button @click="add">+1</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  methods:{
    add(){
      this.$store.commit("increment")
      //this.$store.state.count = this.$store.state.count + 1
    }
  }
}
</script>
```
还可以通过compute获取动态数据
```
<template>
  <div class="hello" >
    <!-- {{ this.$store.state.count }} -->
    {{ count }}
    <button @click="add">+1</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  computed: {
    count(){
      return this.$store.state.count
    }
  },
  methods:{
    add(){
      this.$store.commit("increment")
      //this.$store.state.count = this.$store.state.count + 1
    }
  }
}
</script>
```

也可以通过mapstate取数据,看不懂。。可以去看官网？
computed:mapState([
'count'
])

可能需要了解filter函数
```
getters:{
        doneTodos:state => {
            return state.todos.filter(todo => todo.done)
        }
    }
```

Helloworld也可以这么写，是映射，调用index里面写的getters
```
export default {
  name: 'HelloWorld',
  computed:{
    ...mapState([
      'count','todos'
    ]),
    ...mapGetters([
      'doneTodos'
    ])
  },
  
  methods:{
    add(){
      this.$store.commit("increment")
      //this.$store.state.count = this.$store.state.count + 1
    }
  }
}
</script>
```

