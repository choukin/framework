# `nuxi preview`

```{bash}
npx nuxi preview [rootDir]
```

`preview` 命令在执行 `build` 后启动一个服务来预览Nuxt应用。

Option        | Default          | Description
-------------------------|-----------------|------------------
`rootDir` | `.` | 要预览应用程序的根目录

这个命令会把`process.env.NODE_ENV` 设置为 `production`.可以在 `.env` 文件或命令行中设置`NODE_ENV`来覆盖默认值。

::alert{type=info}
为了方便，在预览模式中`.env`文件会加加载到`process.env`.（但是，生成模式时，需要自己设置环境变量）
::
