1、清华大学提供的镜像链
#### 清华大学提供的镜像链
`https://mirrors.tuna.tsinghua.edu.cn/help/AOSP/`

#### 需要工具如下：git、python
##### 1、创建一个目录，打开Git Bash，执行命令
`git clone https://aosp.tuna.tsinghua.edu.cn/platform/manifest.git`
##### 2、切换到manifest目录
`cd manifest`
##### 3、列出android各个分支版本
`git  tag`
##### 4、checkout git tag列出的版本号4、checkout git tag列出的版本号
`git checkout android-7.0.0_r6`

##### Python下载脚本(执行此脚本的前提是已经执行了git checkout)

```python
    import xml.dom.minidom
    import os
    import subprocess

    #downloaded source path
    rootdir = "F:\Android源码"

    dom = xml.dom.minidom.parse(rootdir+"\\manifest\\default.xml")
    root = dom.documentElement

    prefix =  "git clone https://aosp.tuna.tsinghua.edu.cn/"
    suffix = ".git"

    if not os.path.exists(rootdir):
        os.mkdir(rootdir)

    for node in root.getElementsByTagName("project"):
        os.chdir(rootdir)
        d = node.getAttribute("path")
        last = d.rfind("/")
        if last != -1:
            d = rootdir + "/" + d[:last]
            if not os.path.exists(d):
                os.makedirs(d)
            os.chdir(d)
        cmd = prefix + node.getAttribute("name") + suffix
        subprocess.call(cmd,shell=True)
```