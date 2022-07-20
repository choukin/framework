# `useHead`

::ReadMore{link="/guide/features/head-management"}

Nuxt 提供了一个用来在页面中更新head属性的组合项，它使用[`MetaObject`](/api/composables/use-head/#metaobject) 的属性来对应元数据标记:

`title`, `base`, `script`, `style`, `meta`  `link`, 以及 `htmlAttrs` 和 `bodyAttrs`. 或者你可以传一个函数，这个函数的返回值是一个响应式的元数据对象。


```js
useHead(options: MetaObject)
```

::alert{icon=👉}
**`useHead` 只能在 `setup`**中使用.
::

## 实例

下面的例子使用`meta`标记来修改网站title，并且使用`link`来插入google字体。

```js
export default {
  setup () {
    useHead({
      meta: [
        { name: 'title' content: 'Nuxt 3 - The Hybrid Vue Framework' }
      ],
      link: [
        { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
        { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: '' },
        { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css2?family=Roboto&display=swap', crossorigin: '' },
      ]
    })
  }
}
```

## `MetaObject`

* **charset**: 文档的字符编码格式。=> `<meta charset="<value>" />` (默认: `'utf-8'`)
* **viewport**: 配置视口(窗口可以看到的web内容的可视区域) => `<meta name="viewport" content="<value>" />` (default: `'width=device-width, initial-scale=1'`)
* **meta**: 数组类型，每个元素都可以创建一个`<meta>`标签，对象属性对应标签的属性。
* **link**: 数组类型，每个元素都会创建一个`<link>`元素 对象属性对应标签的属性.
* **style**: 数组类型n每个元素都会创建一个`<style>`元素 对象属性对应标签的属性.
* **script**: 数组类型n每个元素都会创建一个`<script>`元素 对象属性对应标签的属性.

meta对象中的元素都是可选的，你也可以只穿一个值。

