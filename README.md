# git-hook
####1:创建一个新的git库 (只有git索引文件,不含工作目录!注意,空目录相当于git 服务器)

```
    git init --bare test-bare.git
    或
    mkdir xxx-bare.git
    cd xxx-bare.git
    git init --bare
```

####2:复制post-update.sample 文件 添加如下
```

#!/bin/sh
unset GIT_DIR
DIR_ONE=/home/wwwroot/gph.yndth.cn/  #此目录为服务器页面展示目录
cd $DIR_ONE
git init
git remote add origin /home/wwwroot/test-bare.git
git clean -df
git pull origin master
```


####3:本地添加远程仓库
```$xslt
git remote add origin ssh://root@182.92.165.86/home/wwwroot/test-bare.git
```


####4:本地推送指定仓库
````

git push origin master
````


