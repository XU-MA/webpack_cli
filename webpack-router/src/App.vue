<template>
  <div id="app">
    <img src="./assets/logo.png" @click="fn">
    <router-link to="/">首页</router-link>
    <router-link to="/helloRouter">HelloRouter</router-link>
    <router-link :to="{name: 'User',params:{id:'123',time:123}}">灵活版to属性配置</router-link>
    <router-view></router-view>
    <router-view name='b'></router-view>
  </div>
</template>

<script>
export default {
  name: 'App',
  created(){
    // this.$router : 看vue-router的全部路由
    // this.$route : 看当前所在的路由
    console.log(this.$router)
    console.log(this.$route)
  },
  // 观测当前动态路由的数据变更
  watch:{
    '$route' (newVal, oldVal) {
      console.log(newVal)
    }
  },
  methods:{
    fn () {
      // 字符串
      // this.$router.push('helloRouter')
      // 对象
      // 注意：他是叠加的 ---error
      // this.$router.push({ path: 'user/9527/set/9527' })
      // 命名路由
      // this.$router.push({ name: 'User', params: { id: 123, time: 9527 }})
      // 带查询参数，变成 /register?plan=private
      // this.$router.push({ path: 'HelloRouter', query: { name: 'name' }})
      this.$router.go(-1)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
