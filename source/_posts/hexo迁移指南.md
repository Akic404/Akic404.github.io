---

title: hexo迁移/备份指南
comments: false
categories: hexo
reward: false
no_toc: false
date: 2021-03-27 13:47:34
updated: 2021-03-27 13:47:34
tags: hexo迁移
---

- # 博客文件备份指南

1. 博客根目录下打开git bash

   ```
   git init
   ```

2. 添加所有文件到仓库

   ```
   git add -all
   ```

   有报错（仓库里包含了仓库）属于正常现象，git会识别并且不会将这些文件夹放入仓库

   ***创建新文章之类的，有新文件产生后，必须从新添加一次文件***

3. 将所有文件提交到仓库

   ```
   git commit -m "解释下这次提交的改动"
   ```

4. 关联远程仓库

   ```
   git remote add origin git@github.com:akic404/akic404.github.io.git
   ```

   ***注意要先进行ssh，输入用户名，邮箱这些事项***

   代码框里的akic404和akic404.github.io.git要分别改为你自己的GitHub用户名和GitHub创建的仓库地址

   ```
   git remote rm origin
   ```

   ↑取消关联远程仓库（防止你输错了

5. 在推送前先将原文件转到新的仓库，防止hexo推送页面文件时覆盖掉源文件

   ```
   git checkout -b doc
   ```

   ↑创建分支doc

   ```
   git checkout master
   ```

   ↑切换回master分支（不一定用得上）

6. 推送分支

   ```
   git push -u origin doc
   ```

   第一次推送doc分支的所有内容

   此后，每次本地提交后，只要有必要，就可以使用命令`git push origin doc`推送最新修改

7. 克隆（下载文件

   ```
   git clone git@github.com:akic404/akic404.github.io.git
   ```

   代码框里的akic404和akic404.github.io.git要分别改为你自己的GitHub用户名和GitHub创建的仓库地址

---

---

---
- # hexo克隆后重建

## 1. 安装必要软件

- git

  > https://gitforwindows.org/

- nodejs

  > https://nodejs.org/en/download/ 

- (不一定用得上）Notepad++

  > https://notepad-plus.it.softonic.com/

## 2.安装Hexo
打开 git bash运行
   ``` 
npm install -g hexo-cli
   ```
```
hexo init
```
```
npm install hexo-deployer-git --save
```

## 3.复制原来的文件到目录下

## 4.ssh

回到你的git bash中，

    git config --global user.name "yourname"
    git config --global user.email "youremail"

这里的yourname输入你的GitHub用户名，youremail输入你GitHub的邮箱。这样GitHub才能知道你是不是对应它的账户。

可以用以下两条，检查一下你有没有输对

```
git config user.name
git config user.email
```

然后创建SSH,一路回车

    ssh-keygen -t rsa -C "youremail"

这个时候它会告诉你已经生成了.ssh的文件夹。在你的电脑中找到这个文件夹。

ssh，简单来讲，就是一个秘钥，其中，id_rsa是你这台电脑的私人秘钥，不能给别人看的，id_rsa.pub是公共秘钥，可以随便给别人看。把这个公钥放在GitHub上，这样当你链接GitHub自己的账户时，它就会根据公钥匹配你的私钥，当能够相互匹配时，才能够顺利的通过git上传你的文件到GitHub上。

而后在GitHub的setting中，找到SSH keys的设置选项，点击New SSH key
把你的id_rsa.pub里面的信息复制进去。
————————————————

> 版权声明：ssh部分为CSDN博主「zjufangzh」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
> 原文链接：https://blog.csdn.net/sinat_37781304/article/details/82729029 

## 5.正常运行

```
hexo g
```

整合文件

```
hexo s
```

开启本地端口（http://localhost:4000

```
hexo d
```

推送到服务器

------

-----

