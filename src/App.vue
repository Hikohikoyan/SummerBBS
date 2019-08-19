<template>
  <div id="app">
    <div id="userstatus">
      <svg t="1563726236798" @click="check_islogin" v-if="loginstatus==false" class="user_icon" id="noneuser"
        viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="3136" width="64" height="64">
        <path
          d="M511.965867 605.252267a259.754667 259.754667 0 0 1-185.002667-76.663467c-49.425067-49.425067-76.629333-115.131733-76.629333-185.002667s27.204267-135.5776 76.629333-185.002666a259.9936 259.9936 0 0 1 185.002667-76.629334c69.905067 0 135.611733 27.204267 185.0368 76.629334 49.390933 49.425067 76.629333 115.131733 76.629333 185.002666s-27.2384 135.5776-76.629333 185.002667a259.6864 259.6864 0 0 1-185.0368 76.663467z m0-461.243734a199.850667 199.850667 0 0 0-199.611734 199.5776 199.850667 199.850667 0 0 0 199.611734 199.611734 199.816533 199.816533 0 0 0 199.611733-199.611734 199.816533 199.816533 0 0 0-199.611733-199.5776z m0 0"
          p-id="3137" fill="#ffffff"></path>
        <path
          d="M930.645333 942.011733a31.0272 31.0272 0 0 1-30.139733-23.790933A397.653333 397.653333 0 0 0 512 611.6352h-0.4096a398.336 398.336 0 0 0-210.807467 60.347733 30.993067 30.993067 0 1 1-32.836266-52.599466 459.844267 459.844267 0 0 1 243.575466-69.802667H512c53.0432 0 105.028267 8.942933 154.589867 26.5216a459.946667 459.946667 0 0 1 132.9152 74.001067 461.346133 461.346133 0 0 1 161.3824 253.713066 31.095467 31.095467 0 0 1-30.242134 38.1952z m0 0M93.354667 942.011733a31.061333 31.061333 0 0 1-30.208-38.1952 458.6496 458.6496 0 0 1 69.461333-155.5456 31.061333 31.061333 0 0 1 43.178667-7.816533 31.061333 31.061333 0 0 1 7.816533 43.2128 394.410667 394.410667 0 0 0-60.074667 134.519467 31.1296 31.1296 0 0 1-30.173866 23.825066z m0 0"
          p-id="3138" fill="#ffffff"></path>
      </svg>
      <svg t="1563726017792" @click="check_islogin" v-if="loginstatus==true" class="user_icon" id="inuser"
        viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2797" width="64" height="64">
        <path
          d="M852.144032 937.162236 285.2368 937.162236c-62.614579 0-113.380832-50.764174-113.380832-113.37721L171.855968 710.408839l56.690416 0 0 113.376187c0 31.306007 25.38415 56.688093 56.690416 56.688093l566.907232 0c31.307289 0 56.690416-25.38311 56.690416-56.688093l0-623.572098c0-31.306007-25.38415-56.688093-56.690416-56.688093L285.2368 143.524834c-31.307289 0-56.690416 25.382087-56.690416 56.688093l0 113.376187-56.690416 0L171.855968 200.212928c0-62.612013 50.766254-113.37721 113.380832-113.37721l566.907232 0c62.615602 0 113.381856 50.765197 113.381856 113.37721l0 623.572098C965.525888 886.398062 914.759634 937.162236 852.144032 937.162236zM606.752315 335.069335c-11.044996-11.072173-11.044996-29.036313 0-40.079834 11.071603-11.072173 29.03648-11.072173 40.109106 0l195.565921 195.557908c5.896532 5.89629 8.414992 13.729699 8.028166 21.451568 0.386826 7.721869-2.131634 15.556301-8.028166 21.48022L646.862445 729.038128c-11.072627 11.07115-29.037503 11.07115-40.109106 0-11.044996-11.072173-11.044996-29.036313 0-40.080857l148.619825-148.613736L86.818808 540.343535c-15.639829 0-28.34572-12.67774-28.34572-28.344558 0-15.639189 12.70589-28.344558 28.34572-28.344558l668.552308 0L606.752315 335.069335z"
          p-id="2798" fill="#ffffff"></path>
      </svg>
      <span class="userstatus">{{ statusmsg }}</span>
    </div>
    <div id="headtitle" style="height: max-content;">SummerBBS</div>
    <el-menu :default-active="$route.path" class="headbox" mode="horizontal" style="padding-left: 25%;"
      @select="handleSelect" router>
      <el-menu-item index="/">首页</el-menu-item>
      <el-submenu index="/A">
        <template slot="title">版块</template>
        <el-menu-item index="/A-1">版块1</el-menu-item>
        <el-submenu index="/A-2">
          <template slot="title">版块2</template>
          <el-menu-item index="/A-3-1">发表新贴</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-submenu index="/B">
        <template slot="title">版块</template>
        <el-menu-item index="/B-1">版块1</el-menu-item>
        <el-submenu index="/B-2">
          <template slot="title">版块2</template>
          <el-menu-item index="/B-3-1">发表新贴</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="/yours" @click="check_islogin">{{yours}}</el-menu-item>
    </el-menu>
    <loginbox :key="wantto"></loginbox>
    <router-view></router-view>
  </div>
</template>

<script>
  import loginbox from "./components/login.vue"
  export default {
    name: "app",
    components: {
      loginbox,
    },
    props: {
      loginstatus: Boolean
    },
    data() {
      return {
        activeIndex: '1',
        activeIndex2: '1',
        yours: "个人中心",
        statusmsg: "未登录",
        wantto:true
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        // console.log(key, keyPath);
      },
      check_islogin(islogin) { //个人中心页
        // console.log("check");
        var islogin = sessionStorage.getItem('status');
        if (islogin == "false") {
          this.yours = "尚未登录";
          this.statusmsg = sessionStorage.getItem('you');
          this.wantto=!this.wantto;
        } else {
          this.statusmsg = "已登录";
          this.yours = "个人中心"
        }
      }
    }
  }
</script>

<style>
  body {
    background-color: #e5f0f3;
  }

  body,
  #app,
  .el-container {
    margin: 0;
    padding: 0%;
  }

  #headtitle {
    background-color: #385d9f;
    font-size: 6rem;
    color: white;
    text-align: center;
    padding-top: 60px;
    padding-bottom: 60px;
  }

  ul.headbox.el-menu--horizontal.el-menu {
    height: max-content !important;
  }

  ul.headbox.el-menu--horizontal.el-menu>li,
  ul.headbox.el-menu--horizontal.el-menu>li .el-submenu__title {
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

  /*userstatus*/
  .user_icon,
  .userstatus {
    position: absolute;
    right: 0px;
    top: 0px;
    /* padding: 10px; */
    padding-right: 10px;
    width: 25px;
    height: 40px;
  }

  .userstatus {
    width: max-content;
    right: 10px;
    padding: 0;
    color: white;
    height: max-content;
    top: 35px;
    font-size: 10px;
    float: right;
  }

  .user_icon:hover,
  .user_icon:active {
    opacity: 0.4;
  }
</style>