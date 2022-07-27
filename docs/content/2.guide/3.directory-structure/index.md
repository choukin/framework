---
title: '目录结构'
layout.aside: true
layout.asideClass: ''
navigation.redirect: /guide/directory-structure/nuxt
# navigation.collapse: true
---

## 项目目录结构

一个完整的Nuxt 3项目默认包含下列目录和文件
```bash
root
| .nuxt/ # 开发模式默认存放运行打包目录文件夹
| .output/ # 生产模式打包文件夹
| assets/ # 资源文件
| composables/ # 辅助方法目录
| components/ # 组件目录
| content/ #内容目录
| layouts/  # 布局目录
| middleware/ # 中间件目录
| node_modules/ # 依赖库
| pages/ # 页面目录
| plugins/ # 插件目录
| public/ # 公共文件
| server/ # 服务器端文件
| .gitignore # git忽略文件
| app.vue # 入口文件
| .nuxtignore # nuxt忽略配置
| nuxt.config.js # nuxt 配置文件
| package.json 
| tsconfig.ts

```

## `.nuxt/`

Nuxt 在开发阶段时使用 `.nuxt/` 目录，来生成你的Vue应用。

## `.output/`
当你打包生产代码时，Nuxt 会创建 `.output/` 目录。

## `assets/`
`assets/` 目录存放所有网站需要的资源，这些资源会被打包工具处理。


## `components/` 

目录用来存放自定义的Vue组件，这些组件可以被自动引入到你的页面或其他组件中


`components/` 目录用来存放自定义的Vue组件，这些组件可以被自动引入到你的页面或其他组件中([了解更多](https://vuejs.org/guide/essentials/component-basics.html#components-basics))

Nuxt 自动导入`components/`目录中的任何组件(以及你通过模块注册的任何会使用的组件)。

```bash
| components/
--| TheHeader.vue
--| TheFooter.vue
```

```html{}[layouts/default.vue]
<template>
  <div>
    <TheHeader />
    <slot />
    <TheFooter />
  </div>
</template>
```

### 组件名称

如果你有一个在嵌套目录的组件例如：


```bash
| components/
--| base/
----| foo/
------| Button.vue
```

... 然后，组件名称将基于路径和文件夹名，并且删除重复部分，因此这个组件名称为:

```html
<BaseFooButton />
```

::alert
为了更清晰，我们建议用组件名称作为文件名，（所以在这个例子中，你可以把`Button.vue`重命名为`BaseFooButtton.vue`）
::

### 动态组件 components

如果你想使用Vue的`<component :is=“someComputedComponent”>`语法，你需要使用Vue 提供的`resolveComponent`辅助函数。


实例:

```vue
<template>
  <component :is="clickable ? MyButton : 'div'" />
</template>

<script setup>
const MyButton = resolveComponent('MyButton')
</script>
```

::alert{type=warning}
如果你正在使用`resolveComponent` 来处理动态组件，请确保你只传组件名称，该名称只能是字符串，不能是变量。
::

或者，尽管不推荐，但你可以在全局注册你的组件，者将为你的组件创建异步块，并在整个应用程序中可用。

```diff
  import { defineNuxtConfig } from 'nuxt'

  export default defineNuxtConfig({
    components: {
+     global: true,
+     dirs: ['~/components']
    },
  })
```

::alert{type=info}
`global` 选项也可以按组件目录进行设置。
::

### 动态导入

要想动态加载组件（也称为延迟加载组件），你只需要在组件名称中添加`Lazy`前缀.

```html{}[layouts/default.vue]
<template>
  <div>
    <TheHeader />
    <slot />
    <LazyTheFooter />
  </div>
</template>
```

当组件不经常使用，这样设置很必要，通过使用`Lazy`前缀，你可以在合适的时机加载组件，这有助于优化JavaScript包的大小。

```html{}[pages/index.vue]
<template>
  <div>
    <h1>Mountains</h1>
    <LazyMountainsList v-if="show" />
    <button v-if="!show" @click="show = true">Show List</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false
    }
  }
}
</script>
```

### 显式导入

如果希望或想要绕过Nuxt的自动导入，可以显式的从`#components`导入组件。

```html{}[pages/index.vue]
<template>
  <div>
    <h1>Mountains</h1>
    <LazyMountainsList v-if="show" />
    <button v-if="!show" @click="show = true">Show List</button>
    <NuxtLink to="/">Home</NuxtLink>
  </div>
</template>

<script setup>
  import { NuxtLink, LazyMountainsList } from '#components'
  const show = ref(false)
</script>
```

## #`<ClientOnly>` 组件用于有目的的在客户端渲染组件，要仅在客户端导入组件，请在仅客户端插件中注册组件。


```html{}[pages/example.vue]
<template>
  <div>
    <Sidebar />
    <ClientOnly>
      <!-- this component will only be rendered on client-side -->
      <Comments />
    </ClientOnly>
  </div>
</template>
```

使用插槽 faback 作为默认展示，直到 `<ClientOnly>`在客户端挂载后。

```html{}[pages/example.vue]
<template>
  <div>
    <Sidebar />
    <ClientOnly>
      <!-- this component will only be rendered on client side -->
      <Comments />
      <template #fallback>
        <!-- this will be rendered on server side -->
        <p>Loading comments...</p>
      </template>
    </ClientOnly>
  </div>
</template>
```

### 库作者


制作具有自动tree-shaking 和组件注册的Vue组件库特别简单 ✨

你可以使用`components:dirs` 钩子扩展目录列表，不用在 Nuxt 模块中进行自定义配置。

想象一个下列结构的目录：

```bash
| node_modules/
---| awesome-ui/
------| components/
---------| Alert.vue
---------| Button.vue
------| nuxt.js
| pages/
---| index.vue
| nuxt.config.js
```
在 `awesome-ui/nuxt.js`  你可以使用 `components:dirs`钩子：

```js
import { defineNuxtModule } from '@nuxt/kit'
import { fileURLToPath } from 'node:url'

export default defineNuxtModule({
  hooks: {
    'components:dirs'(dirs) {
      // Add ./components dir to the list
      dirs.push({
        path: fileURLToPath(new URL('./components', import.meta.url)),
        prefix: 'awesome'
      })
    }
  }
})
```

就这样，在你的项目中，你可以在`nuxt.config`文件中用Nuxt模块的方式导入你的UI库:

```js
export default {
  modules: ['awesome-ui/nuxt']
}
```

... 然后直接在 `pages/index.vue` 中直接使用模块组件(`awesome-`作为前缀)

```vue
<template>
  <div>
    My <AwesomeButton>UI button</AwesomeButton>!
    <awesome-alert>Here's an alert!</awesome-alert>
  </div>
</template>
```

只有在使用时对应的组件才会自动导入，并且`node_moduels/awesome-ui/components/` 中的组件支持热更新。

## `composables/`
Nuxt 3支持 `composables/`目录通过[`aauto-imports`](/guide/concepts/auto-imports)来自动将Vue的组合项导入到Nuxt应用程序中。


### 文件是如何被扫描的

Nuxt 只对`composables/`目录顶级文件（或目录结果中的index文件）进行扫描。


实力:

```bash
composables
 | - useFoo.ts // 扫描
 | - useBar
 | --- supportingFile.ts // 不扫描
 | --- index.ts // 扫描
```

只有 `useFoo.ts` 和 `useBar/index.ts` 会被扫描成导入文件，并且如果后者是默认导出，他会被注册成 `useBar` 而不是 `index`.


想要导出`useBar/supportingFile.ts`,你必须从 `useBar/index.ts`文件中重新导出。

```js [composables/useBar/index.ts]
export const useBar = () => {
}

// Enables auto import for this export
export { useBaz } from './supportingFile'
```

::alert{type=warning}
自动生成导入，不适用于 `export * from './supportingFile.ts'`，你必须使用具名导出或者默认导出。
::


在后台，Nuxt 自动生成 `.nuxt/auto-imports.d.ts` 来声明类型。

请注意，为了让Nuxt 生成类型文件，你必须执行`nuxi prepare`  `nuxi dev` 或者`nuxi build`.如果你在没有运行dev服务的情况下创建组合项，typescript 会抛出一个错误`Cannot find name 'useBar'`.

### 例: (使用具名导出)

```js [composables/useFoo.ts]
export const useFoo = () => {
  return useState('foo', () => 'bar')
}
```

### 例: (使用默认导出)

```js [composables/use-foo.ts or composables/useFoo.ts]
// It will be available as useFoo() (camelCase of file name without extension)
export default function () {
  return useState('foo', () => 'bar')
}
```

现在可以自动导入这个组合项：

```vue [app.vue]
<template>
  <div>
    {{ foo }}
  </div>
</template>

<script setup>
const foo = useFoo()
</script>
```






