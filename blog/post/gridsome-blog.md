---
title: '使用Gridsome搭建个人博客（三）'
date: 2019-03-14
slug: girdsome-blog
published: true
tags: ['Markdown','gridsome']
canonical_url: false
description: "大概说说这里用markdown书写博客时的技术点."
---

### 用Markdown写文章
markdown文件里面可以写元数据
Front Matter格式(参考https://vuepress.vuejs.org/zh/guide/markdown.html#front-matter)
```
---
title: Blogging Like a Hacker
lang: en-US
date: 2019-03-13
slug: girdsome-create
---
```

### 我的文章路由格式

```
plugins: [
    {
      use: '@gridsome/source-filesystem',
      options: {
        path: 'blog/**/*.md',
        typeName: 'Post',
        route: '/blog/:year/:month/:day/:slug',
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
```

> `/blog/:year/:month/:day/:slug`中的`:year/:month/:day`来自`date: 2019-03-13`
> `slug` 来自`slug: girdsome-create`
> 所以这个路由就是`/blog/2019/03/13/girdsome-create`

