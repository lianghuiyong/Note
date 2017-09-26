macOS 10.12.6 (16G29)



1. 安装Node

   ```
   brew install node
   ```

2. 安装webpack

   ```
   npm install -g webpack
   ```

3. 安装gulp

   ```
   npm install -g gulp
   ```

4. 创建项目目录，在项目目录下执行命令，初始化package.json文件

   ```
   npm init
   ```






5. 出错提示

今天在安装npm包时遇到了这个错误，出现如下提示：

```
npm WARN package.json xxx@0.0.0 No repository field.
npm WARN package.json xxx@0.0.0 No README data

```

看字面意思大概是缺少README文件和repository字段，也就是说缺少项目的基本描述文件和仓库字段。此时，我们只需在项目的根目录下创建一个README文件，并且在package.json里面添加如下配置即可:

```
{
    ...
    "repository": {
        "type": "git",
        "url": "http://github.com/yourname/repositoryname.git"
    },
    ...
}

```

但作为测试项目或者练习用，没有仓库地址怎么办？其实也很简单，只需在package.json里面做如下配置即可:

```
{
    ...
    "private": true,
    ...
}

```

以这种方式把项目声明为私有，这样npm就不会再提示配置repository及readme了。