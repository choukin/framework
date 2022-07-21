# `navigateTo`

`navigateTo` 是一个在应用内部使用编程式导航的工具函数。 

`navigateTo` 在服务端和客户端都可以使用。可以在插件、中间件、页面、组件中使用，可以直接调用来执行页面导航。

## 用法

```ts
navigateTo (route: string | Route, { redirectCode = 302, replace = false })
```

`route` 可以是一个纯字符串，也可以是一个要重定向到的路由对象。

::alert{type="warning"}
确保调用它时使用 `await` / `return`来获得navigateTo()的返回值。
Make sure to use always `await` or `retun` on result of `navigateTo()` when calling it.
::

## 示例

### 在组件中使用

```vue
<script setup>
// string
return navigateTo('/search')

// route object
return navigateTo({ path: '/search' })

// route object with query parameters
return navigateTo({
    path: '/search',
    query: {
        name: name.value,
        type: type.value
    }
})
</script>
```

### 在路由中间件中使用

```js
export default defineNuxtRouteMiddleware((to, from) => {
  // set the redirect code to 301 Moved Permanently
  return navigateTo('/search', { redirectCode: 301 })
})
```

```js
<script setup>
    await navigateTo('/', { replace: true })
</script>
```

::ReadMore{link="/guide/directory-structure/middleware"}
::

### 可选项

#### `redirectCode`

- Type: Number

`navigateTo` 当重定向发生子啊服务器端时，重定向给定的路径并默认设置redirectCode 为 [`302` Found](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/302)。

可以设置`redirectCode`的值来修改默认行为，`redirectCode`时可选参数。可以使用过 [`301` Moved Permanently](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/301) 来设置永久重定向。

#### `replace`

- Type: Boolean

默认情况下,在客户端`navigateTo` 会把给定的路由推送到Vue router 实例中。

可以通过设置`replace:true`来修改默认行为，表示替换实例中的路由。

