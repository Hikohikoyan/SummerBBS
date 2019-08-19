<template>
    <transition name="el-fade-in-linear">
        <div id="loginbox" v-focus v-if="show">
            <el-button @click="close" id="underbutton">
                <svg t="1563727609706" id="cha" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
                    p-id="5433" width="200" height="200">
                    <path
                        d="M886.528 908.032c-28.096 28.096-73.856 28.096-102.016 0L138.304 261.824c-28.096-28.16-28.16-73.856 0-102.016 28.032-28.16 73.792-28.16 102.08 0l646.144 646.144C914.624 834.24 914.752 879.872 886.528 908.032L886.528 908.032zM885.76 261.504 239.616 907.648c-28.224 28.224-73.92 28.224-102.08 0-28.16-28.096-28.16-73.728 0.064-102.016L783.744 159.552c28.224-28.16 73.984-28.16 102.016-0.064C913.984 187.648 913.856 233.344 885.76 261.504L885.76 261.504z"
                        p-id="5434" fill="#6495ED"></path>
                </svg>
            </el-button>
            <span class="hellomsg">{{hellomsg}}</span>
            <!-- <el-form :model="ruleForm" :rules="rules" ref="form">
            
            </el-form> -->
        </div>
    </transition>
</template>
<style>
    #underbutton {
        border: none !important;
        background-color: unset !important;
        outline: 0px;
        padding: 0;
    }

    #loginbox {
        background-color: white;
        visibility: visible;
        z-index: 90;
        border: solid;
        border-color: cornflowerblue;
        border-width: 4px;
        border-radius: 1.4em;
        padding: 50px;
        position: absolute;
        top: 40%;
        left: 25%;
        right: 25%;
    }

    #cha {
        float: right;
        width: 30px;
        position: absolute;
        display: block;
        top: 10px;
        right: 15px;
        height: 30px;
        padding: 3px;
        border: none;
        border-color: #6495ED;
        border-radius: 4em;
    }

    #cha:hover {
        opacity: 0.3;
    }

    .hellomsg {
        font-size: 3rem;
        font-weight: 700;
        color: #6995b5;
    }
</style>
<script>
    export default {
        name: 'loginbox',
        props: {
            username: String,
            islogin: Boolean,
        },
        directives: {
            focus: {
                // 指令的定义
                inserted: function (el) {
                    // 聚焦元素
                    el.focus();
                    // console.log("focus")
                }
            }
        },
        data() {
            return {
                hellomsg: "这里是SummerBBS",
                show: true
            }
        },
        methods: {
            close: function () {
                var time=new Date();
                var username="游客No."+String(Math.round(Math.random() * 100));
                if(sessionStorage.getItem('you')==undefined){
                sessionStorage.setItem('you',username);
                localStorage.setItem('lastlogintime',time);
                }else{
                    username=sessionStorage.getItem('you');
                }
                this.hellomsg = "欢迎~" + username;
                this.islogin=false;
                sessionStorage.setItem('status',this.islogin);
                var closebox=setTimeout(() => {
                    this.show = !this.show;
                    // console.log(this.show)
                }, 500);
            }
        },
    };
</script>