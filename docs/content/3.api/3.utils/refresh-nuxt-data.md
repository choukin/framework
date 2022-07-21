# `refreshNuxtData`

::ReadMore{link="/guide/features/data-fetching"}
::

```ts
refreshNuxtData(keys?: string | string[])
```

可选项:

* `keys`: 用字符串或数组表示要重新获取的`useAsyncData`数据中使用的健。如果未指定，会重新获取 `useAsyncData` 和 `useFetch` 中的全部数据.
