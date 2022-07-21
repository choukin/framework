# `nuxi build`

```{bash}
npx nuxi build [rootDir]
```
`build` 命令会把所有的应用程序，服务器和依赖打包到 `.output` ,可用于生产环。

Option        | 默认值          | 描述
-------------------------|-----------------|------------------
`rootDir` | `.` | 要打包的应用程序目录.
`prerender` | `false` | 预渲染应用程序的每条路径. (**注意:** 还在实验阶段.)

此命令会把`process.env.NODE_ENV` 设置为 `production`.
