# `useRouter`

`useRouter` 返回路由实例，只能在`setup` 函数，插件，路由中间件中调用，在Vue模版中可以使用 `$router`

如果你有 `pages/`文件夹，`userRoute` 和 `vue-router`提供的方法用法一样，请阅读vue-router文档了解每种方法的用法。

::ReadMore{link="https://router.vuejs.org/api/#currentroute"}
::

## 基本操作

- **addRoute:** 在router实例中添加一个新路由，设置`parentName`可以把新加的路由添加为已有路由的自路由。
- **removeRoute:** 通过名字删除一个已有路由.
- **getRoutes:** 获取完整的路由列表.
- **hasRoute:** 检查指定名称的路由是否存在。

## 基于 history API

- **back:** 如果可以返回历史路由和 `router.go(-1)`一样.
- **forward:** 和 `router.go(1)`一样如果可以前进一个路由.
- **go:** 在历史中向前或向后移动，没有`router.back()` 和 `router.forward()`中的限制。 
- **push:** 通过先历史栈中添加新的URL，以编程方式导航到新的路由。 **推荐使用[`navigateTo`](http://v3.nuxtjs.org/api/utils/navigate-to#navigateto) .**
- **replace:** 以编程导航的方式打开一个新的路由，它回替换历史栈中的当前条目. **推荐使用[`navigateTo`](http://v3.nuxtjs.org/api/utils/navigate-to#navigateto) .**

> 提示: `router.addRoute()`把路由的详细信息添加到路由数组中，在构建Nuxt组件时很有用.而`router.push()`回立即触发新的导航，在页面组件和组合项中很有用。

```js [js]
const router = useRouter();
router.back();
router.forward();
router.go();
router.push({ path: "/home" });
router.replace({ hash: "#bio" });
````

::ReadMore{link="https://developer.mozilla.org/en-US/docs/Web/API/History"}
::

## 导航守卫

`useRouter` 组合项提供`afterEach`, `beforeEach` 和 `beforeResolve` 来充当导航守卫方法。

然而，Nuxt有一个 **中间件** 的概念，它简化了导航守卫的实现，并提供了更好的开发者体验。


::ReadMore{link="/guide/directory-structure/middleware"}
::

## Promise 和 错误处理

- **isReady:** 返回当前路由返程初始化导航的Promise.
- **onError:** 添加一个错误处理程序，每次在导航间发生未捕获的错误时被调用。
- **resolve:**  返回标准化的路由location,除了现有属性还包含一个`href`.

::ReadMore{link="https://router.vuejs.org/api/#router-methods"}
::

## 通用路由实例

如果你没有`pages/`文件夹，`useRouter`会返回一个类似辅助函数的通用路由实例，但请注意，并非所有的功能都与`vue-router`一致。

::ReadMore{link="/guide/features/routing"}
::
