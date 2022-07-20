# `useState`

```ts
useState<T>(init?: () => T | Ref<T>): Ref<T>
useState<T>(key: string, init?: () => T | Ref<T>): Ref<T>
```

* **key**: 确保跨请求（没懂？）时删除重复数据的唯一键值，如果你不提供key，`useState`会根据文件和行号为你生成唯一的key。

* **init**: 在未启动时，为状态提供初始值的函数，这个函数还可以返回一个R`Ref`.
* **T**: (typescript only) Specify the type of state

::ReadMore{link="/guide/features/state-management"}
::
