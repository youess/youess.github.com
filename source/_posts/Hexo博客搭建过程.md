---
title: Hexo博客搭建过程
date: 2017-09-20 16:11:49
tags: note
---


## 具体过程

1. 安装npm: `yum install npm`
2. 安装hexo: `npm install hexo-cli -g`
3. 初始博客目录：`hexo init blog && cd blog`
4. 按照主题开发安装并更换主题：`git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia`并更改`_config.yml`中`theme: yilia`
5. 创建博文: `hexo new 'Hexo博客搭建过程'`
6. 在github上创建仓库`${name}.github.com`并在`_config.yml`中`deploy`更改。 `deploy: \n type: git \n repo: <git地址> \n branch: master`
7. 解决不能提交到github上问题. `npm install hexo-deployer-git --save`
8. 写好博文
9. 清理本地数据库。`hexo clean`
9. 生成静态页面, `hexo generate`
10. 部署到github上. `hexo deploy`
11. 本地调试启动服务器. `hexo server`
12. 修改配置文件
13. 将仓库地址设置到`blog`目录并切换到`dev`分支，保存到远端仓库

## 参考

1. [主题litten][1]
2. [Hexo项目][2]


[1]: https://github.com/litten/hexo-theme-yilia
[2]: https://github.com/hexojs/hexo
