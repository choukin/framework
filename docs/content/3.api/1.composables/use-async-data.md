# `useAsyncData`

在页面，组件和插件中，可以使用`useAysncData` 来异步获取数据。

## Type

```ts [Signature]
function useAsyncData(
  handler: (nuxtApp?: NuxtApp) => Promise<DataT>,
  options?: AsyncDataOptions<DataT>
): AsyncData<DataT>
function useAsyncData(
  key: string,
  handler: (nuxtApp?: NuxtApp) => Promise<DataT>,
  options?: AsyncDataOptions<DataT>
): Promise<AsyncData<DataT>>

type AsyncDataOptions<DataT> = {
  server?: boolean
  lazy?: boolean
  default?: () => DataT | Ref<DataT>
  transform?: (input: DataT) => DataT
  pick?: string[]
  watch?: WatchSource[]
  initialCache?: boolean
}

type AsyncData<DataT> = {
  data: Ref<DataT>
  pending: Ref<boolean>
  refresh: () => Promise<void>
  error: Ref<any>
}
```

## 参数

* **key**: 一个唯一的健，用于确保在夸请求是能正确的删除重复数据。如果你没有设置 key ,`useAsyncData` 实例会更具文件名和行号生成唯一的key。
* **handler**: 一个带返回值的异步函数
* **options**:
  * _lazy_: 是否在家中路由后解析异步函数，而不是阻塞导航(默认 false)
  * _default_: 在异步函数解析前设置data默认值的工具函数，特别适用于设置了`lazy:true`的情况。
  * _server_: 是否获取服务器上的数据（默认是 true）
  * _transform_: 一个可以在 `handler` 函数解析后更改返回结果的函数。
  * _pick_: 用于从`handle`函数的结果中筛选这个数组中指定key。
  * _watch_: 监听响应数据自动更新
  * _initialCache_: 但设置为`false`时，不会对 有效负载进行缓存。默认true

在底层，`lazy:false` 在数据加载完成前使用 `<Suspense>`来阻塞路由加载。推荐使用`lazy:true` 加载数据，以获得更好的用户体验。

## 返回值
* **data**: 传入的异步函数的返回结果
* **pending**: 一个布尔值，表示数据是否仍在加载中。
* **refresh**: 一个函数，用来属性`handler`函数的返回结果。
* **error**: 一个错误对象，包含请求数据错误时的内容功能

默认情况下，Nuxt 回等到 `refresh`执行后才能再次执行。可以传递`true`来跳过等待。


## 实例

```ts
const { data, pending, error, refresh } = await useAsyncData(
  'mountains',
  () => $fetch('https://api.nuxtjs.dev/mountains')
)
```

::ReadMore{link="/guide/features/data-fetching"}
::
