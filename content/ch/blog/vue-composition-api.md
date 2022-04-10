---
author: "Eddie Liu"
title: "Composition API: setup()"
date: 2022-04-11
description: "vue3入門導讀-Composition API"
tags: ["vue", "Composition API"]
thumbnail: /vue.png
---

此篇將紀錄 vue3 LifeCycle 一個比較大的改動，也就是 Composition API。
由於工作上還是使用 vue2，因此本篇會順便介紹 vue2 與 vue3 這部分的差異性。

## vue2 LifeCycle

vue2 總共有 8 個 hook,網上有非常多講解 LifeCycle 的文章,這裡就不再貼測試每個 hook 的程式碼，直接快速帶過。
正常情況下會經歷四個 hook(beforeCreate、created、beforeMount 及 mounted),分別是以下的狀況:

1. beforeCreate：el 和 data 並未初始化,還是 undefind 的狀態
2. created:此時完成了 data 的初始化，el 還沒有建立
3. beforeMount：完成了 el 和 data 的初始化
4. mounted:el 掛載完成

若 data 有被更新,則會觸發 beforeUpdate 與 updated。
最後 beforeDestroy 及 destroyed 作者比較少用，但若有 el 需要此功能，可使用`destroy()`,此 el 被銷毀後這時 el 中的任何定義( data 、 methods...等)都已被解除綁定，代表在此做的任何操作都會失效，而整個 LifeCycle 最後能對 el 做事情的 hook 就是 beforeDestroy。

## vue3 LifeCycle

進入到 vue3 後,LifeCycle hook function 的寫法有所改變，下面就直接來看一下新做法吧。

### 定義 setup 函式

首先要定義 setup 函式，這個函式包含 data、methods、computed、lifecycle 等方法。

## 參考資料

1. [Vue.js - Lifecycle Hooks](https://vuejs.org/guide/essentials/lifecycle.html)
2. [Vue.js Core 30 天屠龍記(第 4 天): Vue 實體的生命週期](https://ithelp.ithome.com.tw/articles/10202949)
3. [重構倒數第 29 天 - Vue2 Option API 轉換 Vue3 Composition API](https://ithelp.ithome.com.tw/articles/10259305)
