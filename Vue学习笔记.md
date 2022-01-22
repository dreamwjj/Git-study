# Vue学习笔记

### 1.环境搭建

官方文档下载vue：https://cn.vuejs.org/v2/guide/installation.html

开发时候调用vue

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vue</title>
    <script type="text/javascript" src="./JS/vue.js"></script>
</head>
<body>
    <script type="text/javascript">
        Vue.config.productionTip = false;//取消提示
    </script>
</body>
</html>
```

Vue之HelloWorld案例

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Vue</title>
    <script type="text/javascript" src="./JS/vue.js"></script>
</head>
<body>
    <div id="vue">
        <h1>hello,{{name}}</h1>
    </div>
    <script type="text/javascript">
        Vue.config.productionTip = false;//取消提示
        new Vue({
            el:'#vue',
            data:{
                name:'wjj'
            }
        })
    </script>
</body>
</html>
```

