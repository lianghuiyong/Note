macOS 10.12.6 (16G29)

在线教程：http://www.runoob.com/w3cnote/vue2-start-coding.html

1. 安装Node

   ```
   brew install nodejs
   ```
   获取nodejs模块安装目录访问权限

   ```
   sudo chmod -R 777 /usr/local/lib/node_modules/
   ```

2. 安装淘宝镜像

   大家都知道国内直接使用 npm 的官方镜像是非常慢的，这里推荐使用淘宝 NPM 镜像。

   ```
   npm install -g cnpm --registry=https://registry.npm.taobao.org
   ```

   这样就可以使用 cnpm 命令来安装模块了：

   ```
   cnpm install [name]
   ```

3. 安装webpack
   ```
   npm install -g webpack
   ```

4. 安装vue脚手架
   ```
   npm install vue-cli -g
   ```
5. 安装 vue 路由模块`vue-router`和网络请求模块`vue-resource`

   ```
   cnpm install vue-router vue-resource --save
   ```

6. 在硬盘上找一个文件夹放工程用的，在终端中进入该目录

   ```
   cd 目录路径
   ```

7. 根据模板创建项目

   ```
   vue init webpack-simple 工程名字<工程名字不能用中文>
   ```

8. 进入工程目录，载入node_modules库

   ```
   cnpm install
   ```

9. 启动项目

   ```
   npm run dev
   ```