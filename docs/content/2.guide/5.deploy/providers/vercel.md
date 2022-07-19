---
icon: LogoVercel
---

# Vercel

Vercel 上的Nuxt支持服务端渲染和API路由

::list

- 支持无服务构建
- 部署时自动检测
- 无需配置
::

## Git

1. 把代码推送到git仓库里(GitHub, GitLab, Bitbucket).
2. [导入你的项目](https://vercel.com/new)到 Vercel.
3. Vercel 将监测到你正在使用Nuxt并且为你的部署启用正确的配置。
4. 你的应用部署成功！(e.g. [nuxt.vercel.app](https://nuxt.vercel.app/))

在你的项目加载部署后，后续所有的推送将生成[预览部署](https://vercel.com/docs/concepts/deployments/environments#preview), 所有对主分支的修改都会自动[生产部署](https://vercel.com/docs/concepts/deployments/environments#production)


了解更多关于 Vercel [git 集成](https://vercel.com/docs/concepts/git)信息

## CLI

1. 安装 [Vercel CLI](https://vercel.com/cli).
2. Vercel 将检测到您正在使用 Nuxt，并为您的部署启用正确的设置.
3. 你的应用已部署! (e.g. [nuxt.vercel.app](https://nuxt.vercel.app/))

```bash
npm i -g vercel
npx nuxi init -t v3-vercel
vercel
```

## 了解更多

:ReadMore{link="https://nitro.unjs.io/deploy/providers/vercel.html" title="the Nitro documentation for Vercel deployment"}
