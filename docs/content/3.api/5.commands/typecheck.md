# `nuxi typecheck`

```{bash}
npx nuxi typecheck [rootDir]
```
`typecheck` 命令会执行 [`vue-tsc`](https://github.com/johnsoncodehk/volar/tree/master/packages/vue-tsc) 来检查整个应用的类型.

Option        | Default          | 描述
-------------------------|-----------------|------------------
`rootDir` | `.` | 目标应用的目录

此命令会把 `process.env.NODE_ENV` 设置为 `production`.可以`.env`在文件或命令行参数修改`NODE_ENV` 

::alert
你也可以在构建或开发阶段使用[the `typescript.typeCheck` option in your `nuxt.config` file](/api/configuration/nuxt.config#typescript)检查类型.
::
