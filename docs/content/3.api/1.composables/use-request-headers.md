# `useRequestHeaders`

Nuxt 为了一流的服务器渲染提供了组合项和工具函数。

在页面，组件，插件中，可以通过`useRequestEvent`来访问进行中的请求头。

```js
// 获取所有头信息
const headers = useRequestHeaders()

// 只获取头部cookie
const headers = useRequestHeaders(['cookie'])
```

::alert{icon=👉}
在浏览器端, `useRequestHeaders` 回返回空独喜.
::
