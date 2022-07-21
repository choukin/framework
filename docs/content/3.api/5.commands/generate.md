# `nuxi generate`

```{bash}
npx nuxi generate [rootDir]
```

`generate` 命令会把应用程序的路由与渲染到纯净的HTML文件。你可以部署到任何静态托管服务中。该命令会触发 `nuxi build` 并设置 `prerender` 参数为`true`.

Option        | Default          | 描述
-------------------------|-----------------|------------------
`rootDir` | `.` | 要操作生产的项目目录
