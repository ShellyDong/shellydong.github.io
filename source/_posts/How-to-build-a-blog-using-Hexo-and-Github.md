title: 如何使用Hexo+Github构建博客
date: 2015-06-23 22:24:58
categories: 
- Inbox
tags: 
- Hexo
- Git
- Blog 
---
终于有自己的博客了，记录一下小窝诞生的过程吧~

<!--more--> 

## 建站流程
####1. 安装git
####2. 安装[node.js](https://nodejs.org/download/)
####3. 安装hexo
```bash
$ npm install -g hexo
```
####4. 创建Repository
######以下方式二选一
  - 建立一个 username.github.com 的repo，username为你的github用户名，每个用户只能有一个这样的repo，则直接发布到master分支即可。
  - 建立一个项目repo，发布的branch是gh-pages.
######自定义域名
  - 如果你用自定义域名的话，github pages需要你建立一个名称为CNAME的文件，里面放入你的域名地址。如我的CNAME文件.
  - 因为每次deploy的时候hexo都会重新生成文件，所以直接加在github是不好使的，这个文件需要放在 hexo folder/source文件夹根目录下。

####5. Hexo初始化及操作  
修改站点的_config.yml文件
```yml
deploy:#修改_config.yml中关于deploy的配置
  type: git
  repository: https://github.com/ShellyDong/shellydong.github.io.git
  branch: master
```
```bash
$ hexo init #初始化Hexo
$ npm install 
$ hexo server #默认端口为4000
$ hexo new "My New Post" #新建博客
$ hexo generate #产生静态页面
$ npm install hexo-deployer-git --save  #安装deployer
$ hexo deploy -g  #重新为变化项产生静态页面后再deploy
```
####6. 主题设置
我使用的是[Next](https://github.com/iissnan/hexo-theme-next)
![Next预览](https://camo.githubusercontent.com/0180dd24aad9b84b3ac176f7df44a53da068bac7/687474703a2f2f696973736e616e2e636f6d2f6e657875732f6e6578742f6465736b746f702d707265766965772e706e67)
######安装

从 GitHub 下载
```bash
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

更改站点 `_config.yml` 中的 `theme` 字段设置为 `next`
```bash
theme: next
```

######更新
```bash
cd themes/next
git pull
```