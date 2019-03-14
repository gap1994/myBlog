---
title: '使用Gridsome搭建个人博客（一）'
date: 2019-03-13
slug: girdsome-create
published: true
tags: ['Markdown','gridsome']
canonical_url: false
description: "快速开始gridsome."
---
### 1\. 安装 Gridsome CLI tool

使用 yarn:
`yarn global add @gridsome/cli`

 使用 npm:
`npm install --global @gridsome/cli`

### 2\. 创建 Gridsome 项目

1.  `gridsome create my-gridsome-site` 创建一个新的项目
2.  `cd my-gridsome-site` 打开文件
3.  `gridsome develop` 服务器跑起来后打开 `http://localhost:8080`
4.  可以开始快乐的码字了 🎉🙌

### 3\. 最后一步

1.  在`/pages`目录下创建的vue文件都会生成单独的页面.
2.  使用`gridsome build`打包文件到`/dist`文件

