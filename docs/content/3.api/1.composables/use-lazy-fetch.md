# `useLazyFetch`

## 描述

默认情况下, [useFetch](/api/composables/use-fetch) 回阻塞导航，直到异步处理完成。

`useLazyFetch` 是对 `useFetch`的封装，把 `lazy`选择设置成了`true`,先触发导航在处理异步请求。

> `useLazyFetch` 和 `useFetch`的签名相同.

:ReadMore{link="/api/composables/use-fetch"}

## Example

```vue
<template>
  <div v-if="pending">
    Loading ...
  </div>
  <div v-else>
    <div v-for="post in posts">
      <!-- do something -->
    </div>
  </div>
</template>

<script setup>
/* Navigation will occur before fetching is complete.
  Handle pending and error states directly within your component's template
*/
const { pending, data: posts } = useLazyFetch('/api/posts')
watch(posts, (newPosts) => {
  // Because posts starts out null, you won't have access
  // to its contents immediately, but you can watch it.
})
</script>
```

:ReadMore{link="/guide/features/data-fetching#uselazyfetch"}
