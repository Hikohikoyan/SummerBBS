<template>
  <div id="app">
<div id="headtitle" style="height: max-content;">SummerBBS</div>
<el-menu 
:default-active="activeIndex"
 class="headbox" 
 mode="horizontal"
 style="padding-left: 25%;"
  @select="handleSelect">
  <el-menu-item index="1">首页</el-menu-item>
  <el-submenu index="2">
    <template slot="title">版块</template>
    <el-menu-item index="2-1">版块1</el-menu-item>
    <el-submenu index="2-2">
      <template slot="title">版块2</template>
      <el-menu-item index="2-3-1">发表新贴</el-menu-item>
    </el-submenu>
  </el-submenu>
    <el-submenu index="3">
    <template slot="title">版块</template>
    <el-menu-item index="3-1">版块1</el-menu-item>
    <el-submenu index="3-2">
      <template slot="title">版块2</template>
      <el-menu-item index="3-3-1">发表新贴</el-menu-item>
    </el-submenu>
  </el-submenu>
  <el-menu-item index="4" disabled>个人中心</el-menu-item>
</el-menu>
    <loginbox username="you" v-bind:islogin='false'></loginbox>
    <router-view></router-view>
  </div>
</template>

<script>
import loginbox from "./components/login.vue"
export default {
  name:"app",
  components:{
    loginbox,
    },
  data() {
      return {
        activeIndex: '1',
        activeIndex2: '1',
      };
      },
    methods: {
            handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }
      }
}
</script>

<style>

body,#app,.el-container{
    margin: 0;
    padding: 0%;
}
#headtitle{
  background-color: #385d9f;
  font-size: 6rem;
  color: white;
  text-align: center;
  padding-top: 60px;
  padding-bottom: 60px;
}
ul.headbox.el-menu--horizontal.el-menu{
  height: max-content !important;
}
ul.headbox.el-menu--horizontal.el-menu>li,ul.headbox.el-menu--horizontal.el-menu>li .el-submenu__title{
font-size: 2rem !important;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
  width: 100%;
}
</style>
