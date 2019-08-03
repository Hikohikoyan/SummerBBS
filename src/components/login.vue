<template>
    <div id="loginbox">
        <svg t="1563727609706" class="cha" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
            p-id="5433" width="200" height="200">
            <path
                d="M886.528 908.032c-28.096 28.096-73.856 28.096-102.016 0L138.304 261.824c-28.096-28.16-28.16-73.856 0-102.016 28.032-28.16 73.792-28.16 102.08 0l646.144 646.144C914.624 834.24 914.752 879.872 886.528 908.032L886.528 908.032zM885.76 261.504 239.616 907.648c-28.224 28.224-73.92 28.224-102.08 0-28.16-28.096-28.16-73.728 0.064-102.016L783.744 159.552c28.224-28.16 73.984-28.16 102.016-0.064C913.984 187.648 913.856 233.344 885.76 261.504L885.76 261.504z"
                p-id="5434" fill="#6495ED"></path>
        </svg>
        <el-tabs v-model="activeName" @tab-click="handleClick" id="switchbox">
            <el-tab-pane label="LOGIN" name="first">
                <el-form :model="ruleForm2" status-icon :rules="rules2" ref="ruleForm1" label-width="100px"
                    class="demo-ruleForm">
                    <el-form-item prop="username">
                        <span class="label">用户名</span>
                        <el-input v-model.number="ruleForm1.username"></el-input>
                    </el-form-item>
                    <el-form-item prop="pass">
                        <span class="label">密码</span>
                        <el-input type="password" v-model="ruleForm1.pass" autocomplete="off">
                        </el-input>
                    </el-form-item>
                    <el-form-item>
                        <el-button id="loginin" type="primary" @click="submitForm('ruleForm1')">提交</el-button>
                    </el-form-item>
                </el-form>
            </el-tab-pane>
            <el-tab-pane label="SIGN" name="second">
                <el-form :model="ruleForm2" status-icon :rules="rules2" ref="ruleForm2" label-width="100px"
                    class="demo-ruleForm">
                    <el-form-item prop="username">
                        <span class="label">用户名</span>
                        <el-input v-model.number="ruleForm2.username"></el-input>
                    </el-form-item>
                    <el-form-item prop="pass">
                        <span class="label">密码</span>
                        <el-input type="password" v-model="ruleForm2.pass" autocomplete="off">
                        </el-input>
                    </el-form-item>
                    <el-form-item prop="checkPass">
                        <span class="label">确认密码</span>
                        <el-input type="password" v-model="ruleForm2.checkPass" autocomplete="off"></el-input>
                    </el-form-item>
                    <el-form-item>
                        <el-button id="signin" type="primary" @click="submitForm('ruleForm2')">提交</el-button>
                    </el-form-item>
                </el-form>
            </el-tab-pane>

        </el-tabs>
    </div>
</template>
<style>
    #switchbox {
        position: relative;
        top: -30px;
        left: -10px;
    }

    #loginin,
    #signin {
        float: right;
        font-size: 1.7rem !important;
    }

    .el-form-item__content,
    .el-form-item .el-form-item--feedback,
    .el-form-item.el-form-item--feedback {
        margin-left: 0px !important;
        margin-bottom: 0px;
        margin-top: 3%;
    }

    #loginbox {
        visibility: visible;
        background-color: white;
        z-index: 90;
        border: solid;
        border-color: cornflowerblue;
        border-width: 4px;
        border-radius: 1.4em;
        padding: 50px;
        position: absolute;
        left: 25%;
        right: 25%;
        top: 40%;
    }

    #tab-first,
    #tab-second {
        font-size: 200% !important;
    }

    .label {
        font-size: 1.8rem;
        float: left;
        margin-bottom: 10px;
    }

    .cha {
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

    .cha:hover {
        opacity: 0.3;
    }
</style>
<script>
    export default {
        name: 'loginbox',
        props: {
            username: String,
            islogin: Boolean,
        },
        data() {
            var checkAge = (rule, value, callback) => {
                if (!value) {
                    return callback(new Error('用户名不能为空'));
                }
            };
            var validatePass = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请输入密码'));
                } else {
                    if (this.ruleForm2.checkPass !== '') {
                        this.$refs.ruleForm2.validateField('checkPass');
                    }
                    callback();
                }
            };
            var validatePass2 = (rule, value, callback) => {
                if (value === '') {
                    callback(new Error('请再次输入密码'));
                } else if (value !== this.ruleForm2.pass) {
                    callback(new Error('两次输入密码不一致!'));
                } else {
                    callback();
                }
            };
            return {
                activeName: 'first',
                ruleForm2: {
                    pass: '',
                    checkPass: '',
                    username: ''
                },
                ruleForm1: {
                    pass: '',
                    username: ''
                },
                rules1: {
                    pass: [{
                        validator: validatePass,
                        trigger: 'blur'
                    }],
                    username: [{
                        validator: checkAge,
                        trigger: 'blur'
                    }]
                },
                rules2: {
                    pass: [{
                        validator: validatePass,
                        trigger: 'blur'
                    }],
                    checkPass: [{
                        validator: validatePass2,
                        trigger: 'blur'
                    }],
                    username: [{
                        validator: checkAge,
                        trigger: 'blur'
                    }]
                }
            };
        },
        methods: {
            handleClick(tab, event) {
                console.log(tab, event);
            },
            submitForm(formName) {
                this.$refs[formName].validate((valid) => {
                    if (valid) {
                        alert('submit!');
                    } else {
                        console.log('error submit!!');
                        return false;
                    }
                });
            },
            resetForm(formName) {
                this.$refs[formName].resetFields();
            }
        }

    };
</script>