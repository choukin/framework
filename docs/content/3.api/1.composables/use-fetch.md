# `useFetch`

这个组合项是基于[`useAsyncData`](/api/composables/use-async-data) 和 [`$fetch`](/api/utils/$fetch)的封装.它会基于URL和请求参数自动生成唯一的key，并推导响应的类型.

## Type

```ts [Signature]
function useFetch(
  url: string | Request | Ref<string | Request> | () => string | Request,
  options?: UseFetchOptions<DataT>
): Promise<AsyncData<DataT>>

type UseFetchOptions = {
  key?: string,
  method?: string,
  params?: SearchParams,
  body?: RequestInit['body'] | Record<string, any>
  headers?: {key: string, value: string}[],
  baseURL?: string,
  server?: boolean
  lazy?: boolean
  default?: () => DataT
  transform?: (input: DataT) => DataT
  pick?: string[]
  watch?: WatchSource[]
}

type AsyncData<DataT> = {
  data: Ref<DataT>
  pending: Ref<boolean>
  refresh: () => Promise<void>
  error: Ref<Error | boolean>
}
```

## 参数

* **Url**: 要请求的URL
* **Options (扩展了 [unjs/ohmyfetch](https://github.com/unjs/ohmyfetch) 选项 和 [AsyncDataOptions](/api/composables/use-async-data#params))**:
  * `method`: 请求方法
  * `params`: query参数
  * `body`: 请求体，如果传递的是对象，回自动序列化
  * `headers`: 请求头
  * `baseURL`: 请求的BaseURL
* ** 来自 `useAsyncData`的选项**:
  * _lazy_: 是否在家中路由后解析异步函数，而不是阻塞导航(默认 false)
  * _default_: 在异步函数解析前设置data默认值的工具函数，特别适用于设置了`lazy:true`的情况。
  * _server_: 是否获取服务器上的数据（默认是 true）
  * _transform_: 一个可以在 `handler` 函数解析后更改返回结果的函数。
  * _pick_: 用于从`handle`函数的结果中筛选这个数组中指定key。
  * _watch_: 监听响应数据自动更新
  * _initialCache_: 但设置为`false`时，不会对 有效负载进行缓存。默认true

::alert{type=warning}
如果你提供一个函数或者ref作为`url`参数，或者提供一个函数作为`options`参数，即使选项值看起来相同，这个`useFetach`调用也不会匹配代码中其他地方的调用。**没理解啥意思，不匹配会怎样？**如果你想强制匹配，你需要在opetions中自定义`opitons` key.
::


## 返回值
* **data**: 传入的异步函数的返回结果
* **pending**: 一个布尔值，表示数据是否仍在加载中。
* **refresh**: 一个函数，用来属性`handler`函数的返回结果。
* **error**: 一个错误对象，包含请求数据错误时的内容功能

默认情况下，Nuxt 回等到 `refresh`执行后才能再次执行。可以传递`true`来跳过等待。


## 例子

```ts
const { data, pending, error, refresh } = await useFetch(
  'https://api.nuxtjs.dev/mountains',
  {
    pick: ['title']
  }
)
```

:ReadMore{link="/guide/features/data-fetching"}

:LinkExample{link="/examples/composables/use-fetch"}
