---
title: '使用Gridsome搭建个人博客（二）'
date: 2019-03-13
slug: girdsome-director
published: true
tags: ['Markdown','gridsome']
canonical_url: false
description: "大概说说gridsome的目录结构和部分文件的作用."
---

### 目录结构
```
.
├── package.json
├── gridsome.config.js
├── gridsome.server.js
├── static/
└── src/
    ├── main.js
    ├── layouts/
    │   └── Default.vue
    ├── pages/
    │   ├── Index.vue
    │   └── Blog.vue
    └── templates/
        └── BlogPost.vue
```
### 先来说说gridsome.config.js
```
//这个文件是放配置参数和插件的，基本配置如下
module.exports = {
  siteName: 'Gridsome',
  siteUrl: 'https://www.gridsome.org',
  plugins: []
}
```
详细配置参考官方文档https://gridsome.org/docs/config
```
//我的配置
module.exports = {
  siteUrl: '',
  port: '80',
  pathPrefix: '',
  titleTemplate: '',
  siteName: '个人技术日志',
  siteDescription: '',
  transformers: {
    //Add markdown support to all file-system sources
    remark: {
      externalLinksTarget: '_blank',
      externalLinksRel: ['nofollow', 'noopener', 'noreferrer'],
      anchorClassName: 'icon icon-link',
      plugins: [
        '@gridsome/remark-prismjs'
      ]
    }
  },
  plugins: [
    {
      use: '@gridsome/source-filesystem',
      options: {
        path: 'blog/**/*.md',
        typeName: 'Post',
        route: '/blog/:slug',
        refs: {
          // Creates a GraphQL collection from 'tags' in front-matter and adds a reference.
          tags: {
            typeName: 'Tag',
            route: '/tag/:id',
            create: true
          }
        },
        remark: {
          plugins: [
            '@gridsome/remark-prismjs'
          ]
        }
      }
    }
  ]
}
```
### gridsome.server.js
这个文件主要用来请求各种数据的

### main.js
这个文件和原来vue的很相似
举个例子
```
import Bootstrap from 'bootstrap-vue'

import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default function (Vue) {
  Vue.use(Bootstrap)
}
```
> 使用vuex

```
import Vuex from 'vuex'

export default function (Vue, { appOptions }) {
  Vue.use(Vuex)
  
  appOptions.store = new Vuex.Store({
    state: {
      count: 0
    },
    mutations: {
      increment (state) {
        state.count++
      }
    }
  })
}
```
> 使用router

```
export default function (Vue, { router }) {
  router.beforeEach((to, from, next) => {
    // Do stuff before next page load
    next()
  })
}
```
### `/static`是静态资源目录
> 举个例子
> **/static/robots.txt** 访问的地址是 [https://yoursite.com/robots.txt](https://yoursite.com/robots.txt)

### `/template`目录是能够使用GraphQL schema数据的
> GraphQL可以自己学习一下https://gridsome.org/docs/querying-data#query-data-in-templates