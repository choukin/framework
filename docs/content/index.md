---
navigation: false
template: Page
title: Vue 混合框架
description: 'Build your next application with Vue 3 and experience hybrid rendering, with an improved directory structure and new features Nuxt 3 is an open source framework making web development simple and powerful.'
---

::HomeHero
---
primary:
  text: 在 GitHub 加星
  url: https://github.com/nuxt/framework
  icon: IconGitHub
---

#title
 [Vue]{.text-primary} 混合开发框架

#description
使用 Vue 3 构建下一个 
Nuxt 3 是一个开源的框架，使网站开发体验更简单、强大

#secondary-button
:button-link[现在开始]{ href="/getting-started/quick-start" size="medium" aria-label="Get started" }
::

::home-features{.dark:bg-secondary-darkest .bg-gray-50}
---
category: 发现
---
#title
新特性

#description
Nuxt 3 进行了重新设计的内核体积更小，性能更快，并且有了更好的开发体验。

#default
  ::section-content-item
  ---
  title: 更轻便
  description: 达到75倍轻便，服务端部署和针对现代浏览器的客户端包文件都缩小了
  image: IconFeather
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  title: 更快
  description: 'nitro 提供了动态服务器代码拆分来优化冷启动'
  image: IconRabbit
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  soon: true
  title: 混合
  description: '现在使用增量静态生成，和其他高级模式成为可能'
  image: IconHybrid
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  title: 悬念
  description: '在导航之前或之后，获取任何组件的数据'
  image: IconSuspense
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  title: 组合API
  description: "使用CompositionAPI和Nuxt3的可组合项来实现正真的代码可重用"
  image: IconCAPI
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  title: Nuxt CLI
  description: '全新的零依赖体验，轻松搭建和集成模块。'
  image: IconCLI
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  soon: true
  title: Nuxt 开发工具
  description: '在浏览器中快速使用信息和快速修复.'
  image: IconDevtools
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  title: Nuxt 套件
  description: '使用TypeScript和跨版本兼容带来的全新的开发模块'
  image: IconKit
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  title: Webpack 5
  description: '打包时间短，体积小，无需配置F'
  image: IconWebpack
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  title: Vite
  description: '使用Vite作为捆绑器，体验闪电般的热更新.'
  image: IconVite
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  title: Vue 3
  description: 'Vue 3 为您的下一个web应用程序提供鉴定的基石.'
  image: IconVue
  imageClass: w-10 h-10
  ---
  ::
  ::section-content-item
  ---
  title: TypeScript
  description: '使用原生TypeScript 和 ESM 无需额外操作'
  image: IconTypeScript
  imageClass: w-10 h-10
  ---
  ::
#bottom
  :button-link[开始使用]{ href="/getting-started" size="medium" aria-label="开始上手" }
::

::section{.py-20 .text-lg}
  ::nuxt-container{.text-justify}
    :icon-nuxt-nitro{.h-32}
    :headline[Nitro 引擎]
    我们花费了9个月的时间开发了Nuxt 的新的服务端引擎[**Nitro**](/guide/concepts/server-engine)，它为Nuxt 服务器和其他服务器解锁了新的 **全栈技能额**

    在开发中，它使用  [Rollup](https://rollupjs.org/guide/en/) 和 [Node.js workers](https://nodejs.org/api/worker_threads.html) 来隔离服务器代码和上下文,它还通过读取 [`server/api/`](/guide/directory-structure/server#api-routes) 的文件 **生成服务端API** ，读取 [`server/middleware`](/guide/directory-structure/server#server-middleware) 中的文件 **生成服务端中间件**
  
    在生产环境，它将您的应用和服务器构建到一个通用 [`.output`](/guide/directory-structure/output) 文件夹中，这个 `output 很轻量` 是压缩过的，并且除 polyfills 外删除了Nodejs 的模块。
    你可以把这个 output 文件部署到任何支持JavaScript 的系统中，包括 Node.js ServerLess,workders, 边缘渲染，或纯静态。

    output 文件包括了运行时的代码 在任何环境中运行你的 运行 Nuxt 服务（包括实验下的浏览器service Workers）以及为你提供镜头文件服务，使它成为了一个 **真正的JAMStack混合框架** 。此外还实现了本机存储层，支持多源，驱动程序和本地资源。

    Nitro 服务的基础是 Rollup 和 [h3](https://github.com/unjs/h3): 一个高性能可移植的最小http架构
    :button-link[了解更多 Nitro 相关知识]{ href="/guide/concepts/server-engine" size="medium" aria-label="了解更多 Nitro 相关知识" }
  ::
::

::section{.dark:bg-secondary-darkest .bg-gray-50 .py-20 .text-justify}
  ::nuxt-container{.text-justify}
    :icon-nuxt-bridge{.h-32}
    :headline[升级桥梁]

    四年后我们转移到[Vue 3] () 并重新开发了 Nuxt，使其成为未来的坚实基础


    ### 平滑升级到Nuxt3

    我们努力使 Nuxt 2 和 Nuxt3 之间的升级尽可能容易

    ::list
    - 遗留的插件和模块将继续工作
    - 兼容 Nuxt2 的配置
    - 部分页面 options 可用
    ::

    ### 为您现有的Nuxt 2项目带来Nuxt 3的体验

    由于我们一直在为Nuxt 3开发功能，我们会把其中的一些功能向后兼容Nuxt2

    ::list{.mb-8}
    - 在 Nuxt2中 使用 [Nitro server](/guide/concepts/server-engine)
    - 在Nuxt 2 中使用 Composition API (和Nuxt 3一样)
    - 在 Nuxt2 中使用心得 CLI 和 DevTools
    - 逐步升级到 Nuxt 3
    - 兼容Nuxt 2的模块生态系统
    - 逐步升级 (Nitro, Composition API, Nuxt Kit)
    ::

    :button-link[开始使用 Nuxt Bridge]{ href="/bridge" size="medium" aria-label="开始使用" }
  ::
::
