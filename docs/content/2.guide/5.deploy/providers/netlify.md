---
icon: LogoNetlify
---

# Netlify

如何将Nuxt 部署到 [Netlify](https://www.netlify.com/).

::list

- 使用Netlify Functions 和 Edge 支持无服务SSR
- 部署时自动检测
- 无需配置

::

## 设置


通常，部署到Netlify 不需要任何配置，Nuxt 还会自动检测你是否在[Nuxtilfy](https://www.netlify.com) 环境并构建正确版本的Nuxt服务，对于新站点，Netlify会检测你正在使用Nuxt 并且这个公共目录为`dist` 并执行 `npm run build`, 如果你正在升级现有站点，应该检查这些并对其进行更新。

要触发部署服务，只需要[像通常操作](https://docs.netlify.com/configure-builds/get-started/)一样把代码推送到git仓库.

默认情况下，Nuxt将使用[Netlify Functions]() 在服务器中的每个页面进行服务器渲染，你可以选择将部署设置为[Netlify Edge Functions](https://docs.netlify.com/netlify-labs/experimental-features/edge-functions/) 或者[Netlify On-demand Builders](https://docs.netlify.com/configure-builds/on-demand-builders/)



## Netlify 边缘函数功能

[Netlify Edge Functions](https://docs.netlify.com/netlify-labs/experimental-features/edge-functions/) 将使用 [Deno](https://deno.land) 和强大的V8 Javascript 运行时，让你运行全球分布式函数,以获得更快的响应时间，Nuxt输出直接运行子啊边缘服务器，更靠近您的用户。

在 [Netlify Edge Functions announcement](https://www.netlify.com/blog/announcing-serverless-compute-with-edge-functions).中了解更多

## 按需构建

[Netlify 按需构建](https://docs.netlify.com/configure-builds/on-demand-builders/) 是无服务功能，御用根据需要的web内容，自动缓存在Netlify的边缘CDN上，它们能够在您用户第一次访问站点是构建页面,然后将它们缓存供后续访问(也称作增量静态再生成)



## 自定义重定向

如果要添加自定义重定向，可以在[`public`](/guide/directory-structure/public)目录中添加[`_redirects_`](https://docs.netlify.com/routing/redirects/#syntax-for-the-redirects-file)文件来实现。

## 了解更多

:ReadMore{link="https://nitro.unjs.io/deploy/providers/netlify.html" title="the Nitro documentation for Netlify deployment"}
