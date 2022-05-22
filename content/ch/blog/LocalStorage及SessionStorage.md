---
author: "Eddie Liu"
title: "LocalStorage及SessionStorage"
date: 2022-05-22
description: "有些時候使用者在網站上操作時，我們可能會需要儲存一些資料，這類資料不需要寫入資料庫，這時就可以進入本次文章的主題:
LocalStorage及SessionStorage。"
tags: ["LocalStorage","SessionStorage"]
thumbnail: /pexels.jpg
---

## 基本概念

有些時候使用者在網站上操作時，我們可能會需要儲存一些資料，這類資料不需要寫入資料庫，這時就可以進入本次文章的主題:
LocalStorage 及 SessionStorage。

![](/storage-application.png)

這兩個地方等於是我們將上述資料儲存在用戶端，而非寫入資料庫。使用場景可能會在紀錄當前使用者的購物車行為、列表頁的篩選項目等項目，比較屬於是操作後產生的行為數據，就能儲存在用戶端上，並且根據其特性或需求來操作這些數據。

## SessionStorage

以下為 SessionStorage 的特性:

1. 儲存的資料只能在當前頁面使用
2. 關閉或切換該頁面(Browser Sessions)，則該資料會自動刪除

所以符合上述特性的資料都能儲存在 SessionStorage，那我們來看看資料要如何儲存在 SessionStorage 吧。

```js
// 將資料存到sessionStorage
sessionStorage.setItem("key", "value");

// 從sessionStorage取得之前存的資料
var data = sessionStorage.getItem("key");

// 從sessionStorage移除之前存的資料
sessionStorage.removeItem("key");

// 從sessionStorage移除之前存的所有資料
sessionStorage.clear();
```

**key** 為任意字串，可自行定義，**value** 的部分則只能是 **string**，所以如果要儲存物件或陣列的話可以使用 JSON。

## LocalStorage

以下為 LocalStorage 的特性:

1. 儲存的資料可以在當前網站所有頁面使用
2. 關閉或切換該頁面(Browser Sessions)，則該資料依舊存在，除非手動去刪除

與 SessionStorage 最大的差異在於資料會永久儲存及跨頁面(Browser Sessions)使用，所以有上述需求的就必須要使用 LocalStorage。

```js
// 將資料存到localStorage
localStorage.setItem("key", value);

// 從localStorage取得之前存的資料
var data = localStorage.getItem("key");

// 從localStorage移除之前存的資料
localStorage.removeItem("key");

// 從localStorage移除之前存的所有資料
localStorage.clear();
```

**key** 與 **value** 的規則跟 SessionStorage 一樣。

## 兩者的資訊安全

不論資料放在 sessionStorage 還是 localStorage，都被限制在該網站的規範內，其他網站無法存取。

## 結論

在了解特性與資安後妥善利用 sessionStorage 及 localStorage，其實在前端的互動上會有不錯幫助。

## 參考資料:

[sessionStorage](https://developer.mozilla.org/zh-TW/docs/Web/API/Window/sessionStorage)

[LocalStorage](https://developer.mozilla.org/zh-TW/docs/Web/API/Window/localStorage)
