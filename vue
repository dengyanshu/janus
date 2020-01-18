1  安装node  下载node.exe 安装完成  会自动怕命令加入path  使用node -v npm -v查看相关版本信息
2、配置node全局安装的路径和缓存安装的路径
npm config set cache "c:\nodejs\node_cache"
npm config set prefix "c:\nodejs\node_global"

3、安装cnpm 加快下载
npm install cnpm -g --registry=https://registry.npm.taobao.org

4、C:\nodejs\node_global加入path  不然 global全局安装的模块命令无法使用

----------------------------------------------------------

1、安装vue-cli 
cnpm i vue-cli -g
2、进入目录
  cd  e:/vue_ws/vue-mycli
  然后运行命令 vue init  webpack 开始构建vue项目
  
  
3、cnpm i 安装工程所有依赖


4、npm run dev 开启工程
  
-------------------vue项目
1、index.html   <body style="background-color:white">  整个app会是白色主基调
2、app.vue  padding-top:40px 留出title位置   overflow-X:hidden;//动画的时候不会飘    mint-ui的header组件 z-index:99 在上面
3、v-enter  与v-leave-to 分开写  
   transform:translateX（100%或者-100%）进入的时候100%横向 v-leave-to 离开的时候-100%从页面最左边离开效果
   position:absloute;可以解决页面上下跳动
4、v-enter-active  v-leave-active
    router对象中使用 linkActiveClass:'mui-active'

5、使用axios跨域请求数据(注意有可能与vue-resources冲突)
  import axios  from 'axios'
  import VueAxios from 'vue-axios'
  Vue.use(VueAxios, axios)
  第2步 
  config/index.js中配置代理
   proxyTable: {
      '/api': {
        target:'http://127.0.0.1:8888/',
        // secure: false, // 如果是https接口，需要配置这个参数
        changeOrigin: true,
        ws: true,
        pathRewrite:{
          '^/api': ''
        }
      }
    },
    第3步请求
     this.axios.get("/api/user/list.action?page=1&rows=10").then(result=>{
                    //成功回调
                    if(result.data.status==="ok"){
                          Toast("ok!!")
                    }
                    //失败回调
                    else{
                        Toast("fail!!")
                    }
        }) 
 6、css3flex 新特性   里面的标签浮动 内容2端对齐
    p{
       display:flex;
       justify-content:space-between;
    }
    
    
 7、mainjs中全局过滤器和moment的使用
   安装moment
   mainjs中 
       1\全局引入  import moment from 'moment'
       //pattern如果为空就以默认的初始化值传入
       2\Vue.filter('dateFormat',function(str,pattern="YYYY-MM-DD HH:mm:ss"){
                  此moment已经相当于 var moment=require('moment')生成 可以直接使用  不需要new
                  return  moment(str).format(pattern)  
       }) 
   
8、路由路径获取
    <router-link  :to="'/home/newsinfo/'+item.id">
    然后下一个页面路由路径会是/home/newsinfo/1 这样子    $route.params.id获取
    新闻详情页面会有图片不全bug  去掉style里面的 scope可以解决
    
9、评论子组件
   在组件中         import comment from './comment.vue'
   在组件属性中注册  components:{'comment':comment}
   在<template>  <comment :id="newsid"></comment>  子组件中 用props:['id']来接收
   点击更多  this.page++; this.getNewsComment();   
   getNewsComment(){
      this.comments=this.comments.concat(res.data);//不清空列表  原列表基础上添加
   }
   

10、
