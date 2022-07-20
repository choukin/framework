# `useRoute`

`useRoute` 返回当前路由对象，只能在`setup`函数，插件，或路由中间件中使用。

在Vue组件模版中，你可以使用 `$route`

## 示例

在下面的例子中我们通过 `useFetch` 来获取动态路由参数，- `slug`作为URL的一部分.

```html [~/pages/[slug].vue]
<script setup>
const route = useRoute()
const { data: mountain } = await useFetch(`https://api.nuxtjs.dev/mountains/${route.params.slug}`)
</script>

<template>
  <div>
    <h1>{{ mountain.title }}</h1>
    <p>{{ mountain.description }}</p>
  </div>
</template>
```

如果要获取query参数，（例如：路径 `/tets?example=true` 中的 `example`）你可以用 `useRoute().query`.

除了动态路由参数和query参数，`useRoute()`还提供了下列于当前路由相关的计算引用：

* **fullPath**: 编码过的当前路由URL，包括 path,query,hash
* **hash**: 解码后的hash，URL中#开始的内容
* **matched**: 与当前路由位置，匹配的标准化匹配路由数组
* **meta**: 附加的自定义数据
* **name**: 记录路由唯一的名称
* **path**: 编码后的URL的pathname 部分
* **redirectedFrom**: 在到达当前路由时,访问过的路由位置

::ReadMore{link="https://router.vuejs.org/api/#routelocationnormalized"}
::

::ReadMore{link="/guide/features/routing"}
::
