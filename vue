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
  
