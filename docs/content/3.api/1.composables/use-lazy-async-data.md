# `useLazyAsyncData`

## 描述

默认情况下, [useAsyncData](/api/composables/use-async-data)回阻塞导航，直到异步处理完成。

`useLazyAsyncData` 对`useAsyncData`的封装，把 `lazy`选择设置成了`true` 先导航路由在处理异步函数。

> `useLazyAsyncData` 和 `useAsyncData`的签名相同.

:ReadMore{link="/api/composables/use-async-data"}

## 实例

```vue
<template>
  <div>
    {{ pending ? 'Loading' : count }}
  </div>
</template>

<script setup>
/* Navigation will occur before fetching is complete.
  Handle pending and error states directly within your component's template
*/
const { pending, data: count } = useLazyAsyncData('count', () => $fetch('/api/count'))

watch(count, (newCount) => {
  // Because count starts out null, you won't have access
  // to its contents immediately, but you can watch it.
})
</script>
```

:ReadMore{link="/guide/features/data-fetching#uselazyasyncdata"}
