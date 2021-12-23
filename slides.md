---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
---

# Tailwind CSS 分享

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Let's go <carbon:arrow-right class="inline"/>
  </span>
</div>
<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# 什麼是 Utility class
或者可以稱為 Functional CSS、 Atomic CSS

<div v-click>
  Bootstrap 5

  ```css
  .d-flex {
    display: flex !important;
  }

  .opacity-75 {
    opacity: .75 !important;
  }

  .ms-1 {
    margin-left: 4px !important;
  }

  .px-2 {
    padding-left: 8px !important;
    padding-right: 8px !important;
  }
  ```
</div>

<div v-click>
  每一個 class 都負責一小部分的 CSS，沒有任何耦合，可以自由組合
</div>

---
layout: center
---

### 假如都沒有耦合，那我們是不是就能使用這些 utility class 來建構網站呢？

---
layout: center
---
# Tailwind CSS

一個 utility-first 的 CSS 框架

---

# 寫起來是什麼樣子？

<div v-click class="grid grid-cols-2 gap-3 mb-4">

  ```html
  <button class="px-4 py-2 text-base text-white bg-blue-500 dark:bg-orange-500 rounded hover:bg-blue-700 dark:hover:bg-orange-700">
    我是按鈕
  </button>
  ```
  
  <div class="flex items-center justify-center">
    <button class="px-4 py-2 text-base text-white bg-blue-500 dark:bg-orange-500 rounded hover:bg-blue-700 dark:hover:bg-orange-700">
      我是按鈕
    </button>
  </div>

</div>

<div v-click class="grid grid-cols-2 gap-2 mb-4">

  ```html
  <div class="flex justify-center items-center space-x-4 bg-white rounded">
    <div v-for="i in 6" :key="i" class="w-10 h-10 bg-blue-400 dark:bg-orange-400 rounded shadow-md" />
  </div>
  ```
  
  <div class="flex justify-center items-center space-x-4 bg-white rounded">
    <div v-for="i in 6" :key="i" class="w-10 h-10 bg-blue-400 dark:bg-orange-400 rounded shadow-md" />
  </div>

</div>

<div v-click class="grid grid-cols-2 gap-2">

  ```html
  <div class="bg-white dark:bg-gray-900 rounded-lg px-6 py-8 ring-1 ring-gray-900/5 shadow-xl">
    <h3 class="text-gray-900 dark:text-white mt-5 text-base font-medium tracking-tight">Dark Mode</h3>
    <p class="text-gray-500 dark:text-gray-400 mt-2 text-sm">The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.</p>
  </div>
  ```

  <div class="bg-white dark:bg-gray-900 rounded-lg px-6 py-8 ring-1 ring-gray-900/5 shadow-xl">
    <h3 class="text-gray-900 dark:text-white mt-5 text-base font-medium tracking-tight">Dark Mode</h3>
    <p class="text-gray-500 dark:text-gray-400 mt-2 text-sm">The Zero Gravity Pen can be used to write in any orientation, including upside-down. It even works in outer space.</p>
  </div>

</div>

---
layout: center
---

# 有什麼特色？

---

# 響應式設計

Tailwind CSS 預設提供了５個斷點可以使用
| 斷點前綴 | 最小寬度 | CSS |
| --- | --- | --- |
| `sm` | 640px | `@media (min-width: 640px) { ... }` |
| `md` | 768px | `@media (min-width: 768px) { ... }` |
| `lg` | 1024px | `@media (min-width: 1024px) { ... }` |
| `xl` | 1280px | `@media (min-width: 1280px) { ... }` |
| `2xl` | 1536px | `@media (min-width: 1536px) { ... }` |

<div v-click>

  ```html
  <div class="block md:flex md:justify-center p-3 md:p-5 xl:p-10 rounded md:rounded-md 2xl:rounded-xl">
    <img class="w-16 md:w-32 lg:w-48" src="...">
  </div>
  ```

</div>

---

# 黑暗模式

```html
  <div class="bg-white dark:bg-black text-white dark:text-black">
    <!-- ... -->
  </div>
```

<div class="flex justify-center items-center w-15 h-15 mt-5 bg-black dark:bg-white text-white dark:text-black rounded">
  Hi
</div>

---

# 支援 Hover, Focus, Active, Disabled 等狀態

<div class="grid grid-cols-2 gap-3 mb-6">

```html
    <button
      class="hover:bg-indigo-700 focus:ring-4 focus:ring-indigo-500/50 disabled:opacity-50 ...">
        Button text
    </button>
```
  <div class="flex items-center justify-center">
    <button type="button" class="px-4 py-2 border border-transparent rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-4 focus:ring-indigo-500/50 disabled:opacity-50">Button text</button>
  </div>

</div>

<div v-click>

Before 和 After

```html
<div class="after:w-10 after:block after:h-10 after:bg-red-400 after:rounded"></div>
```

</div>

---
layout: center
---

### 這些功能看起來都很不錯，但是都在用 Tailwind CSS 內建的樣式
### 想要客製化怎麼辦？🤔

---

# 自定義樣式
tailwind.config.js

```javascript
module.exports = {
  theme: {
    fontSize: {
      sm: '0.875rem',
      base: '1rem',
    },
    colors: {
      orange: {
        100: '#FFECE8',
        200: '#FFCFC5',
        300: '#F4AA9B',
        400: '#ED7961'
      }
    },
    borderRadius: {
      none: '0px',
      DEFAULT: '0.125rem',
      md: '0.25rem',
    }
  }
}
```

---
layout: center
---

### OK 看起來有點香了，但如果有一些不常用的顏色或數值怎麼辦？🤔

---

# 支援任意值

```html
<div class="w-[20px] h-[31px] bg-[#52bdeb]"></div>
```

<div v-click>

  也可以使用前綴

  ```html
  <div class="w-[20px] lg:w-[43px] h-[31px] bg-[#52bdeb] hover:bg-[#eb5282]"></div>
  ```

</div>

<div v-click>

  還有圖片路徑

  ```html
  <div class="bg-[url('/bg.png')]">...</div>
  ```

</div>

<div v-click>

  要放 CSS 變數也沒問題

  ```html
  <div class="text-[var(--my-var)]">...</div>
  ```

</div>

---
layout: center
---

### 不過看起來有好多 class，這樣產生出來的 CSS 會不會很肥啊？🤔

---

# JIT（Just-In-Time）編譯器
按需編譯，不會產生所有 CSS

<img src="/img/jit-demo.png">

---
layout: center
---

### 使用 utility class 跟以前傳統的寫法比有什麼優點？🤔

---

# 先看一下比對

<div class="grid grid-cols-2 gap-5">

```html
<div class="chat-notification">
  <div class="chat-notification-content">
    <p class="chat-notification-message">You have a new message!</p>
  </div>
</div>
<style>
  .chat-notification {
    display: flex;
    max-width: 24rem;
    padding: 1.5rem;
    background-color: #fff;
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
  }
  .chat-notification-content {
    margin-left: 1.5rem;
    padding-top: 0.25rem;
  }
  .chat-notification-message {
    color: #718096;
    font-size: 1rem;
    line-height: 1.5;
  }
</style>
```

```html
<div class="p-6 max-w-sm bg-white shadow-lg flex items-center space-x-4">
  <div>
    <p class="text-gray-500">You have a new message!</p>
  </div>
</div>
```

</div>

---
layout: center
---

# 優點：

<v-clicks>

1. 你不必再花時間想 class name！
2. CSS 不會再變多
3. co-work 的時候就會先想到用定義好的 CSS，而不會自己寫一個
4. 不怕改 A 壞 B

</v-clicks>

---
layout: center
---

### 這跟直接寫 inline-style 有什麼不一樣？🤔

<img src="/img/meme/spider-man.jpeg" class="mx-auto mt-5">

---

# 為何不直接用 inline-style ？

<v-clicks>

1. 不能寫 media query
2. 不能用 hover, focus, before, after 等狀態
3. 不能用定義好的 Design system 做切版

    舉例來說：假如要加上紅色背景，使用 Utility class 的情況下我們只需要加上 `.bg-red`，就可以用事先定義好的色票，但如果用 inline-style，就需要寫 `background-color: #f00;`

4. 承上不能複用
5. 可讀性差

</v-clicks>

---
layout: center
---

### 但... 這樣寫一整排 class 看起來好醜，維護性好差

---

# 你可以這麼做：

<v-clicks>

1. 使用前端框架時，做成 component

2. 與傳統的 class name 命名方式共用

    ```html
    <div class="chat-notification p-6 max-w-sm bg-white shadow-lg flex items-center space-x-4">
      <div>
        <p class="text-gray-500">You have a new message!</p>
      </div>
    </div>
    ```

3. 使用 `@apply` 抽取 class（不建議）

    ```html
    <div class="chat-notification">
      <div>
        <p class="text-gray-500">You have a new message!</p>
      </div>
    </div>
    <style>
      .chat-notification {
        @apply p-6 max-w-sm bg-white shadow-lg flex items-center space-x-4;
      }
    </style>
    ```

</v-clicks>

---
layout: center
---

### 我好懶，有沒有人幫我切好版？🥺

---
layout: center
---

# 當然有啦！

- [Tailwind UI](https://tailwindui.com/)
- [Tailblocks](https://tailblocks.cc/)
- [Tailwind-kit](https://www.tailwind-kit.com/)

---
layout: center
---

<img src="/img/meme/真香.jpeg">

---
layout: center
---

# 現在就開始嘗試吧！

- [Tailwind CSS 安裝指南](https://tailwindcss.com/docs/installation)
- [Tailwind Play](https://play.tailwindcss.com/)

---
layout: center
---

# Q&A 🧐
