# `useRequestEvent`

Nuxt 为了一流的服务器渲染提供了组合项和工具函数。

在页面，组件，插件中，可以通过`useRequestEvent`来访问进行中的请求。

```js
// Get underlying request event
const event = useRequestEvent()

// Get the URL
const url = event.req.url
```

::alert{icon=👉}
在浏览器端, `useRequestEvent` 返回 `undefined`.
::
