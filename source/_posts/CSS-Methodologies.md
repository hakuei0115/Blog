---
title: 深入淺出 OOCSS、SMACSS、BEM三種CSS命名規則詳解
date: 2024-06-10 14:22:20
categories: 前端知識
tags: "CSS"
---

CSS（Cascading Style Sheets，層疊樣式表）在網頁開發中扮演著至關重要的角色。隨著網站規模和複雜度的增加，管理和維護CSS代碼變得越來越困難。為了提高代碼的可維護性和重用性，業界提出了多種CSS命名規則，其中包括OOCSS、SMACSS和BEM。本文將詳細介紹這三種命名規則的核心概念，並進行比較，以幫助初學者和有一定經驗的前端開發者選擇適合自己的命名規則。

# 一、OOCSS（Object-Oriented CSS）

## 核心概念

OOCSS，即面向對象的CSS，旨在通過模組化的方式來管理CSS代碼。OOCSS主要有兩個核心概念：

結構與外觀分離：將結構（如佈局）和外觀（如顏色、字體）分開，從而實現樣式的重用。
模組化塊（Objects）：將樣式定義為可重用的模組，這些模組可以在不同的地方組合使用。

### 範例程式碼

```html
<div class="card card--primary">
  <h2 class="card__title">Card Title</h2>
  <p class="card__content">This is a card.</p>
</div>

<div class="card card--secondary">
  <h2 class="card__title">Card Title</h2>
  <p class="card__content">This is another card.</p>
</div>
```
```css
/* 結構 */
.card {
  border: 1px solid #ccc;
  padding: 16px;
  margin: 16px;
}

/* 外觀 */
.card--primary {
  background-color: blue;
  color: white;
}

.card--secondary {
  background-color: grey;
  color: black;
}
```
## 優缺點

### 優點
- 提高樣式的重用性。
- 減少代碼重複，提高可維護性。

### 缺點

- 初學者可能需要時間來理解和掌握這種分離方式。

# 二、SMACSS（Scalable and Modular Architecture for CSS

## 核心觀念

SMACSS，即可擴展和模組化的CSS架構，是一套整理和編寫CSS的指南。SMACSS將CSS分為五種類型：

1. 基礎規則（Base rules）：定義基本元素樣式。
2. 佈局規則（Layout rules）：定義佈局相關的樣式，如頁面主要結構。
3. 模組規則（Module rules）：定義可重用的UI組件，如導航欄、卡片。
4. 狀態規則（State rules）：定義組件在不同狀態下的樣式。
5. 主題規則（Theme rules）：定義主題相關的樣式，如顏色方案。

### 基礎規則（Base rules）

基礎規則主要用於定義頁面中HTML標籤的初始樣式，如html、body、h1、p等。這些樣式通常是通用的，適用於整個網站。CSS reset也算在其中

```css
/* 基礎規則 */
html, body, h1, h2, h3, p {
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
}

a {
  color: blue;
  text-decoration: none;
}
```

### 佈局規則（Layout rules）

Layout rules 主要用於定義頁面佈局的樣式，通常包括頁面的主要結構部分，如頭部（header）、內容區（content）、側邊欄（sidebar）、頁尾（footer）等。這些佈局元素通常不會包含具體的內容樣式，而是負責頁面的佈局和定位。

```html
<!-- HTML -->
<header class="layout-header">
  <h1>Website Title</h1>
</header>

<main class="layout-content">
  <nav class="layout-sidebar">
    <!-- Sidebar content -->
  </nav>
  <section class="layout-main">
    <!-- Main content -->
  </section>
</main>

<footer class="layout-footer">
  <p>&copy; 2024 Website</p>
</footer>
```
```css
/* 佈局規則 */
.layout-header {
  background: #333;
  color: white;
  padding: 16px;
}

.layout-content {
  display: flex;
}

.layout-sidebar {
  width: 250px;
  background: #f4f4f4;
  padding: 16px;
}

.layout-main {
  flex: 1;
  padding: 16px;
}

.layout-footer {
  background: #333;
  color: white;
  text-align: center;
  padding: 16px;
}
```

### 模組規則（Module rules）
Module rules 用於定義頁面中可重用的UI組件，例如導航欄（nav）、卡片（card）、按鈕（button）等。這些組件通常包含具體的樣式和結構，並可以在不同的頁面或佈局中重用。

```html
<!-- HTML -->
<nav class="module-nav">
  <ul>
    <li class="module-nav-item is-active">Home</li>
    <li class="module-nav-item">About</li>
    <li class="module-nav-item">Contact</li>
  </ul>
</nav>

<div class="module-card">
  <h2 class="module-card__title">Card Title</h2>
  <p class="module-card__content">This is a card.</p>
</div>
```
```css
/* 模組規則 */
.module-nav {
  list-style: none;
  padding: 0;
  display: flex;
}

.module-nav-item {
  margin-right: 16px;
}

.module-card {
  border: 1px solid #ccc;
  padding: 16px;
  margin: 16px;
}

.module-card__title {
  margin: 0 0 8px;
  font-size: 1.5em;
}

.module-card__content {
  margin: 0;
}
```

### 狀態規則（State rules）
State rules 定義UI組件在不同狀態下的樣式，例如激活、隱藏、顯示等。這些樣式通常是以is-開頭的類名表示。

```html
<!-- HTML -->
<button class="button is-active">Active Button</button>
<button class="button is-disabled">Disabled Button</button>
```
```css
/* 狀態規則 */
.is-active {
  background-color: green;
  color: white;
}

.is-disabled {
  background-color: grey;
  color: darkgrey;
  cursor: not-allowed;
}
```

### 主題規則（Theme rules）
Theme rules 用於定義網站或應用的主題樣式，例如顏色方案。這些樣式通常用於實現主題的切換。

```html
<div class="theme-light">
  <p>This is light theme</p>
</div>

<div class="theme-dark">
  <p>This is dark theme</p>
</div>
```
```css
/* 主題規則 */
.theme-light {
  background-color: white;
  color: black;
}

.theme-dark {
  background-color: black;
  color: white;
}
```

## 優缺點

### 優點：

- 清晰的結構，易於理解和維護。
- 提供了明確的分類，有助於組織和管理CSS代碼。

### 缺點：

- 需要嚴格遵守規則，否則容易出現混亂。

# 三、BEM（Block Element Modifier）

## 核心觀念

BEM，即Block Element Modifier，是一種基於命名規則的CSS方法，使CSS類名更具語意和組織性。BEM的命名規則如下：

1. Block：表示區塊，是一個獨立的功能體。
2. Element：表示區塊中的元素，是Block的一部分，使用兩個底線__分隔。
3. Modifier：表示區塊或元素的修飾狀態，使用兩個連字符--分隔。

### 範例程式碼

```html
<button class="button button--primary">
  <span class="button__icon">🌟</span>
  Primary Button
</button>

<button class="button button--secondary">
  <span class="button__icon button__icon--large">🔍</span>
  Secondary Button
</button>
```

```css
/* Block */
.button {
  display: inline-block;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}

/* Element */
.button__icon {
  margin-right: 8px;
}

/* Modifier */
.button--primary {
  background-color: blue;
  color: white;
}

.button--secondary {
  background-color: grey;
  color: black;
}

.button__icon--large {
  font-size: 1.5em;
}
```

## 優缺點

### 優點：

1. 命名規則清晰，易於理解和使用。
2. 強大的可維護性和可擴展性。

### 缺點：

1. 類名較長，會增加HTML文件的冗長度。
2. 需要遵守嚴格的命名規則，初學者可能需要時間來適應。

# 四、三種命名規則的比較

| 特點 | oocss | SMACSS | BEM |
| :--: | :--: | :--: |  :--: | 
|   命名規則    |   分離結構和外觀  |   分為五種類型    |   Block__Element--Modifier    |
|   可重用性    |   高  |   高  |   高  |
|   可維護性    |   高  |   高  |   很高    |
|   學習曲線    |   適中    |   適中    |   稍高    |
|   清晰度  |   高  |   很高    |   很高    |
|   類名長度    |   適中    |   適中    |   長  |
|   適用範圍    |   小型到大型專案  |   各類型專案  |   各類型專案  |

# 結論

在選擇CSS命名規則時，需要根據專案的規模和複雜度，以及團隊成員的技術水平來決定。OOCSS適合希望提高樣式重用性的團隊；SMACSS提供了明確的分類，有助於組織和管理CSS代碼；BEM則以其強大的可維護性和可擴展性，成為許多大型專案的首選。希望這篇文章能幫助你理解這三種命名規則，並選擇最適合你的方法。