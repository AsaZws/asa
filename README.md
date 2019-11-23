## 本博客系统采用vuepress，[原文作者](https://github.com/zhhlwd/vuepress-theme-indigo-material)

### 开始写作  

由于没有自动生成 md 文件的命令,需要手动创建 Markdown 文件,而且要放在 **./docs/posts/** 下, 然后还需要文件顶部像原主题那样写上信息 

```
---
title: 【读书笔记】《JavaScript权威指南》第7章数组
date: 2018-11-08 04:10:03
tags: [读书笔记, 《JavaScript权威指南》]
---
```

### 部署  

写完文章, 在本地预览无误后, 可以直接双击 deploy,sh 文件, 然后脚本运行编译打包 push 到远程仓库   

如果不用 deploy.sh 文件,而是手打命令,要注意的是,**一定要在 dist 目录下运行这三步**

```
git init
git add -A
git commit -m 'deploy'
```

### 目录结构

```sh
|-- template
    |-- .babelrc                   // 主题的babel配置, 按需加载element ui所需
    |-- .gitignore                 // 让git忽略跟踪dist文件夹等等, 不要把docs文件夹加进去
    |-- deploy.sh                  // 部署到git 远程仓库的shell文件, 要部署时双击即可, 前提是配置的构建目录位置没变
    |-- init.sh                    // (只要执行一次)克隆template分支到本地后, 双击它, 一步完成所有操作, 等他完成下载, 开启测试服务器, 打开http://localhost:8080/看到效果
    |-- package-lock.json
    |-- package.json
    |-- 目录说明.md
    |-- docs                       // 存放所有开发环境的目录
        |-- index.md               // 首页,不用改
        |-- .vuepress
        |   |-- config.js          // 主题的配置
        |   |-- public             // 存放静态文件的目录, 例如img, ico ...
        |       |-- avatar.jpg
        |       |-- brand.jpg
        |       |-- favicon.ico
        |-- about                  // 展示在自我介绍页面的内容
        |   |-- index.md           // 不能删除, 可以添加内容
        |-- tags                   // 不能删除, 不能动
        |   |-- index.md           // 不能删除, 不能动
        |-- all                    // 不能删除, 不能动
        |   |-- index.md           // 不能删除, 不能动
        |-- posts                  // 存放所有文章的目录
```