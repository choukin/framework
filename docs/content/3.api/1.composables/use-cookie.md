# `useCookie`

Nuxt 提供一个对SSR 友好的组合项，来读写cookie。

可以在页面，组件和插件中，使用 `useCookie`来创建一个具有响应式的cookie.


```js
const cookie = useCookie(name, options)
```

::alert{icon=👉}
**`useCookie` 只能在 `setup` 或 `Lifecycle Hooks`** 中使用.
::

::alert{icon=😌}
`useCookie` ref 会自动把cookie 序列化/反序列化为JSON。

## 实例

下面的例子创建一个名字叫 `counter`的cookie，如果这个cookie不存在，会初始化设置一个随机值。当更新`couter`值时，cookie里的值也会更新。

```vue
<template>
  <div>
    <h1> Counter: {{ counter || '-' }}</h1>
    <button @click="counter = null">
      reset
    </button>
    <button @click="counter--">
      -
    </button>
    <button @click="counter++">
      +
    </button>
  </div>
</template>

<script setup>
const counter = useCookie('counter')
counter.value = counter.value || Math.round(Math.random() * 1000)
</script>
```

:button-link[在 StackBlitz 中打开]{href="https://stackblitz.com/github/nuxt/framework/tree/main/examples/composables/use-cookie?terminal=dev&file=app.vue" blank}

## 选项

Cookie组合项接收多个选项，可以让你修改cookie的行为。

大部分选择会之间传给[cookie](https://github.com/jshttp/cookie)包

### `maxAge` / `expires`

**`maxAge`** 制定 `number` (以秒为单位) 作为 [`Max-Age` `Set-Cookie` attribute](https://tools.ietf.org/html/rfc6265#section-5.2.2)属性值.
给定的值会通过四舍五入转换成整数，默认不设置maxage。

**`expires`**: 指定`Date` 对象作为[`Expires` `Set-Cookie` attribute](https://tools.ietf.org/html/rfc6265#section-5.2.1)的值.
默认情况下，不设置过期日期。大部分浏览器会把他当作`非持久的cookie`，在关闭浏览器后自动删除。

::alert{icon=💡}
**注意:**  [cookie 存储模型规范规定](https://tools.ietf.org/html/rfc6265#section-5.3) 如果同时设置了 `expires`和
`maxAge` 则`maxAge` 优先起作用,但是不是所有的客户端都遵守这个规范，如果两个都设置，你应该使用相同的data和时间。
::

::alert
如果`expires` 和 `maxAge`都没有设置，cookie属于仅会话类型，会在用户关闭浏览器后被删除。
::

### `httpOnly`

指定 `boolean` 作为[`HttpOnly` `Set-Cookie` attribute](https://tools.ietf.org/html/rfc6265#section-5.2.6)的值.如果设置为真值时就是设置了`HttpOnly`属性，否则未设置，默认情况不设置这个值。


::alert{icon=💡}
**注意:** 把这个值设置成true时要小心，因为有些兼容客户端，不允许JavaScript读取`document.cookie`中的cookieB.
::

### `secure`
指定 `boolean` 作为 [`Secure` `Set-Cookie` attribute](https://tools.ietf.org/html/rfc6265#section-5.2.5)的值. 当时真值时,
 `Secure` 属性被设置，否则没有设置.默认情况下不设置 `Secure`.

::alert{icon=💡}
**注意:** 设置成 `true` 是要小心, 如果没有使用HTTPS协议兼容客户端，不回把cookie发送给服务器端。着会导致融合错误。a
::

### `domain`

设置[`Domain` `Set-Cookie` attribute](https://tools.ietf.org/html/rfc6265#section-5.2.3)的值.默认情况不设置domain，大多数客户端回把cookie 设置成只在当前域名可用。 

### `path`

设置[`Path` `Set-Cookie` attribute](https://tools.ietf.org/html/rfc6265#section-5.2.4)的值.默认情况下，path 回被设置为["defalut path"](https://tools.ietf.org/html/rfc6265#section-5.1.4).

### `sameSite`

设置一个[`SameSite` `Set-Cookie` attribute](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1.2.7)`boolean` 或 `string` 值.

- `true` 会设置 `SameSite` 属性为  `Strict` 严格执行同源策略.
- `false` 不会设置 `SameSite` 属性.
- `'lax'` 设置 `SameSite` 属性为`Lax` 执行宽松的同源策略.
- `'none'` 设置 `SameSite` 属性为 `None` 允许跨站点cookie.
- `'strict'` 设置 `SameSite`属性为`Strict` 执行严格的同源策略

要了解更多策等级，请参阅[规范](https://tools.ietf.org/html/draft-ietf-httpbis-rfc6265bis-03#section-4.1.2.7).

### `encode`

设置一个用来给cookie值编码的函数。由于cookie的值只能是简单的字符串，因此这个函数可以把cookie的值编码。
默认编码函数是 `JSON.stringify` + `encodeURIComponent`.

### `decode`

设置一个函数来解码cookie的值，由于cookie的值只能是简单的字符串，这个函数用来把cookie值解码成一个对象或javascript字符串。

默认的解码器是 `decodeURIComponent` + [destr](https://github.com/unjs/destr).

::alert{icon=💡}
**注意:** 当这个函数报错时，cookie的原值会被返回。
::

### `default`

设置cookie的默认返回值，这个函数也可以返回一个 `ref`.

## 处理API路由中的cookie

可以使用 `useCookie` [`h3`](https://github.com/unjs/h3) 中的`setCookie`在服务器路由中设置cookie。

**实例:**

```js
export default defineEventHandler(event => {
  // Read counter cookie
  let counter = useCookie(event, 'counter') || 0

  // Increase counter cookie by 1
  setCookie(event, 'counter', ++counter)

  // Send JSON response
  return { counter }
})
```

:LinkExample{link="/examples/composables/use-cookie"}
