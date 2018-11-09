---
title: 使用travis-ci帮你自动编译发布 Hexo 博客
date: 2018-11-09 15:20:00
tags: 
    - README 
---

# goldhan.github.io

> 本教程只是提供大概的思路，有可能到最后不会成功，请见谅

## 你需要知道

- git 使用
- 基础的终端使用
- 如果使用 GitHub Pages 服务

![Logo](https://raw.githubusercontent.com/goldhan/GDResource/master/Logo/GoldKingLogo.png)

[![Build Status](https://travis-ci.com/goldhan/goldhan.github.io.svg?branch=Dev)](https://travis-ci.com/goldhan/goldhan.github.io)

## 分支说明

- master 为编译后的文件
- Dev 为 Hexo 源文件

> 每次更改 Dev 分支将会自动触发travis-ci编译，自动更新 master 分支

## 如何实现？

### 准备环境

1. git
2. node.js  npm

> 以上环境安装都比较简单这里不做描述

### 准备工作

#### github创建一个新的项目（其他git平台也可）__GitHub Pages__

    > 具体流程很简单，这里不做说明

#### github申请 token

    1. ![01](/img/GitHubToken/token_01.png)
    2. ![02](/img/GitHubToken/token_02.png)
    3. ![03](/img/GitHubToken/token_03.png)
    4. ![04](/img/GitHubToken/token_04.png)
    5. ![05](/img/GitHubToken/token_05.png)
        > 记住返回的 token 字符串，最好保存起来

    > 其他git服务商也有对应的token申请，这里不做描述

#### 准备好Hexo相关文件

> [Hexo 文档](https://hexo.io/zh-cn/docs/)

    1. npm install -g hexo-cli
    2. hexo init <folder>
    3. cd <folder>
    4. npm install

> 这里使用默认主题，其他主题，有些复杂的主题需要做一些额外的安装

#### 配置travis

> 这里默认你已经申请好[travis-ci](https://travis-ci.com/)

1. 创建 .travis.yml 文件在你博客目录的根目录下

按照以下代码进行对应修改

``` yml
language: node_js
node_js: stable

before_install: # 这里是之前让你申请的git仓库地址
  - git clone https://xxx.git -b Dev
install:
  - npm install
  - npm install hexo-cli -g
script:
  - hexo clean
  - hexo g
after_success:
  - cp README.md public
  - cd ./public
  - git init
  # git 提交的署名
  - git config --global user.name "xxx"
  # git 提交的邮箱
  - git config --global user.email "xxx@xxx.com"
  - git add -A
  - git commit -m "Travis CI Auto Builder"
  # Token 为之前上边让你申请的 token，注意这里并不是明文，是你设置的常量名字
  - git push --force -u https://${Token}@xxx.git master:master
```

    - 关于设置 Token

    1. 打开 [travis-ci](https://travis-ci.com/) 找到你对应关联项目的设置界面，类似这个地址的页面：https://travis-ci.com/goldhan/goldhan.github.io/settings

    2. 设置 Environment Variables
    name可以填Token，或者其他常量名，但是注意要和上边 .travis.yml 里的一致，value 填上边申请的 token即可

### 上传git

此时，还没有上传到git服务商

1. git clone https://xxx.git 上边申请的仓库
2. 把你的整个博客目录里的 __内容__ 移动到此目录下
3. git add -A
4. git commit -m "你的提交日志"
5. git push origin master:dev

## 后续

此时顺利的话，travis-ci 应该已经自动编译。

## 注意事项

1. git仓库是带有 GitHub Pages 服务的，具体请搜索
2. travis-ci 基础使用，请看官网的文档
3. 案例：[github](https://github.com/goldhan/goldhan.github.io)
