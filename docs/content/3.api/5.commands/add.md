# `nuxi add`

在Nuxt应用程序中新建一个实体。

```{bash}
npx nuxi add [--cwd] [--force] <TEMPLATE> <NAME>
```

可选项        | 默认值          | 描述
-------------------------|-----------------|------------------
`TEMPLATE` | - | 指定要生成文件的模版。
`NAME` | - | 指定要创建的文件名称。
`--cwd` | `.` | 目标应用程序的目录.
`--force` | `false` | 是否强制覆盖已存在的文件。

**示例:**

```{bash}
npx nuxi add component TheHeader
```
`add` 命令可以生成的模块有:

* **component**: `npx nuxi add component TheHeader`
* **composable**: `npx nuxi add composable foo`
* **layout**: `npx nuxi add layout custom`
* **plugin**: `npx nuxi add plugin analytics`
* **page**: `npx nuxi add page about` 或 `npx nuxi add page "category/[id]"`
* **middleware**: `npx nuxi add middleware auth`
* **api**: `npx nuxi add api hello` (CLI 会在 `/server/api` 下面生成文件)
