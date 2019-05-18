---
title: 2019-03-02【vscde-git报错】
date: 2019-03-02 23:50:08
tags: [vscode》]
categories: [vscode]
---

#### 更新版本-1.19.3
报如下错误
![](https://user-gold-cdn.xitu.io/2018/2/1/1614f0384a6c3daa?w=997&h=74&f=png&s=10671)
原因可能是 git.path 设置成了null, 按照如下更改后重启Vs就好了
![](https://user-gold-cdn.xitu.io/2018/2/1/1614f082d62a9ac5?w=1304&h=284&f=png&s=55850)
<h3 style="color: #f34e33;">注意：</h3>
不要使用这样的路径风格，例如&nbsp;&nbsp;D:\ruanjian\git\Git\bin\bash.exe <br/>
一定要使用这样的路径风格，例如&nbsp;&nbsp;D:/ruanjian/git/Git/bin/bash.exe