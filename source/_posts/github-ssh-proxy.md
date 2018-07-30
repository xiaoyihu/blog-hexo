---
title: github ssh代理的使用方法
date: 2018-07-30 12:37:03
tags:
---


今天碰到ssh 代理的问题，找了一些，总结如下：

## 环境
win10




## 生成ssh
需要有github的ssh，具体生成可以参考github帮助文档，可以直接搜索关键词`github ssh`，或者点击https://help.github.com/articles/connecting-to-github-with-ssh/。


## 增加ssh的配置
在用户目录的.ssh的文件夹下，新建一个文件，config，不带扩展名，内容如下：

```
ProxyCommand "/c/Program Files/Git/mingw64/bin/connect.exe" -H http://{proxyServerNameOrIp}:{port} %h %p

Host github.com
  User git
  Port 22
  Hostname github.com
  IdentityFile "/c/Users/{你的名字}/.ssh/id_rsa"
  TCPKeepAlive yes
  IdentitiesOnly yes

Host ssh.github.com
  User git
  Port 443
  Hostname ssh.github.com
  IdentityFile "/c/Users/{你的名字}/.ssh/id_rsa"
  TCPKeepAlive yes
  IdentitiesOnly yes
```

## 相关连接
- https://communary.net/2017/01/12/getting-git-to-work-through-a-proxy-server-in-windows/
- https://stackoverflow.com/questions/5103083/ssh-in-git-behind-proxy-on-windows-7
- http://www.returnbooleantrue.com/2009/06/using-github-through-draconian-proxies.html