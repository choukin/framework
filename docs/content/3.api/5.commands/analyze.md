# `nuxi analyze`

分析生产环境的打包文件或者你的Nxut应用。

```{bash}
npx nuxi analyze [rootDir]
```

The `analyze` command builds Nuxt and analyzes the production bundle (experimental).

Option        | 默认值          | 描述
-------------------------|-----------------|------------------
`rootDir` | `.` | 目标应用程序的目录.

此命令设置 `process.env.NODE_ENV` 为 `production`.
