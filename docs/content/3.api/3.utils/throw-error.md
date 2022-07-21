# `throwError`

Nuxt 提供了一个快捷简单的方式来抛出异常

在页面，组件，插件中，可以使用 `throwerror` 来抛出一个错误。

**参数:**

- `error`: `string | Error`

```js
throwError("😱 Oh no, an error has been thrown.")
```

抛出的错误会通过[`useError()`](/api/composables/use-error)设置到状态里，因此这个错误是响应式的，SSR友好的，跨组件的。

`throwError`调用了 `app:error` 钩子。

::ReadMore{link="/guide/features/error-handling"}
::
