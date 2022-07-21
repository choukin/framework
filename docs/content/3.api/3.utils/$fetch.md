# `$fetch`

::ReadMore{link="/guide/features/data-fetching"}
::

Nuxt 使用[ohmyfetch](https://github.com/unjs/ohmyfetch)实现了一个全局的`$fetch`函数来在客户端和API路由中发送HTTP请求。

服务端渲染时，调用`$fetch`来请求内部 [API routes](/guide/directory-structure/server) 回直接调用对应的函数（模拟请求），**节省API调用**。

注意 `$fetch` 是Nuxt 3中首选的HTTP调用方式。而不是Nuxt 2 中的 [@nuxt/http](https://github.com/nuxt/http) 和 [@nuxtjs/axios](https://github.com/nuxt-community/axios-module) 

::NeedContribution
::
