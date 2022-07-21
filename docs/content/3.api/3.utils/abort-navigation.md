# `abortNavigation`

```ts
abortNavigation(err?: Error | string): false
```

* **err**: `abortNavigation()`中的抛出的错误是可选的.

::alert{type="warning"}
`abortNavigation()` 只能在 [路由中间件处理程序中](/guide/directory-structure/middleware)中使用。
::

在路由中间件内部`abortNavigation()`如果设置了错误参数，导航会被终止。

::ReadMore{link="/guide/features/routing"}
::
