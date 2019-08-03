# BBSwithVue

## 登录

前端发包：

```
[{
    "function":"login",
    "username":"you",
    "password":"8numwithtext",
    "time":"timestamp"
}]
```

取回：

```
[{
    "function":"login",
    "username":"you",
    "loginstatus":0,
    "errmsg":"普通用户 0/超级用户 3",
    "time":"timestamp"
}]
```

loginstatus 0时显示已登录  超级用户显示"Super" 

## 注册

前端发包：

```
[{
    "function":"sign",
    "username":"you",
    "password":"8numwithtext",
    "checkpwd":"8numwithtext",
    "someinfo_name":"someinfo(Obeject)",
    "time":"timestamp"
}]
```

取回：

```
[{
    "function":"sign",
    "username":"you",
    "loginstatus":0,
    "errmsg":"注册成功 0/密码不一致 1/信息填写错误 2",
    "someinfo_name":"someinfo(Obeject)",
    "time":"timestamp"
}]
```

## 基础功能：主页展示/版块展示/个人空间

前端发包：

```
[{
    "section":"home/mine/section…",
    "method":"get",
    "time":"timestamp"
}]
```

取回：

```
[{
[{
    "total":2
},{
    "passageid":"for home passage id",
    "author":"Dr.Stanly",
    "icon":"src",
    "info":"I'm Bad guy",
    "title":"Shengdiyago",
    "text":"passage-content",
    "time":"posttime"
},{
    "passageid":"someone+num",
    "author":"Dr.Stanly",
    "icon":"src",
    "info":"I'm Bad guy",
    "title":"Shengdiyago",
    "text":"passage-content",
    "time":"posttime"
}]
}]
```

## 基础功能：个人信息

前端发包：

```
[{
    "section":"info",
    "method":"get"
}]
```

取回：

```
[{
    "name":"Stanly",
    "gender":"male",
    "age":"99",
    "intro":"还是另请高明吧",
    "department":"tech",
    "grade":"second"
}]
```

## 基础功能：评论（回帖）

前端发包：

```
[{
    "function":"reply",
    "from":"you",
    "to":"someonelse",
    "passageid":"someonelsen#29",
    "text":"你说的都对",
    "relytime":"timestamp"
}]
```

取回：

```
    "errmsg":"评论成功！",
    "errcode":0
```



## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
