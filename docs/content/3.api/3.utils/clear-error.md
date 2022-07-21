# `clearError`

 Nuxt 提供了一个组合项来清楚所有已处理的错误。

在页面、组件、插件中，可以使用 `clearError` 来清除所有错误，并让用户重定向。

**参数:**

- `options?: { redirect?: string }`

你可以提供一个可选的路径用来重定向（例如，你想导航到一个安全的页面）

```js
// Without redirect
clearError()

// With redirect
clearError({ redirect: '/homepage' })
```
使用[`useError()`](/api/composables/use-error)把错误设置到状态中. `clearError` 组合项会重置状态，并用可选参数调用  `app:error:cleared` 钩子。

::ReadMore{link="/guide/features/error-handling"}
::
