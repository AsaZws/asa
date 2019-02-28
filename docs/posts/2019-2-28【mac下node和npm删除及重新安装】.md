---
title: 2019-2-28【mac下node和npm删除及重新安装】
date: 2019-02-28 08:47:08
tags: [mac》]
categories: [mac]
---

mac由于平时不太了解，导致后面npm出错，现在想删除重装
### 删除
#### 如果是用 brew 安装的node，用下面的命令卸载
    brew uninstall node
#### 进入 /usr/local/bin 删除 node 执行文件
    cd /usr/local/bin  
    sudo rm -rf /usr/local/bin/npm  
    sudo rm -rf /usr/local/bin/node
#### 仔细检查，全局安装的npm包一般会在这个目录下创建软连接，发现就删除
    ls
#### 其他清理工作
    sudo rm -rf /usr/local/share/man/man1/node.1  
    sudo rm -rf /usr/local/lib/dtrace/node.d  
    sudo rm -rf ~/.npm
### 卸载
#### 安装cnpm
    sudo npm install -g cnpm –registry=https://registry.npm.taobao.org/
#### 如果报错执行如下命令
    npm set registry https://registry.npm.taobao.org # 注册模块镜像  
    npm set disturl https://npm.taobao.org/dist # node-gyp 编译依赖的 node 源码镜像  
    npm cache clean # 清空缓存  
    sudo npm install -g cnpm –registry=https://registry.npm.taobao.org/ #重新安装
#### npm升级到最新版本
    npm install npm@latest -g