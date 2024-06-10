---
title: 提升網頁SEO的指南：從基本原則到Schema.org和Open Graph (持續更新)
date: 2024-06-10 20:56:23
categories: 前端知識
tags: "SEO"
---
SEO（Search Engine Optimization，搜尋引擎優化）是提升網站在搜尋引擎結果頁（SERP）中排名的重要策略。這不僅有助於提高網站的可見度，還能吸引更多潛在用戶訪問你的網站。本文將介紹SEO的基本原則，並重點說明Schema.org和Open Graph如何幫助提升網站的SEO表現。

# 一、SEO的基本原則

## 1. 高質量內容

高質量的內容不僅能吸引和留住訪客，還能提高搜尋引擎的排名。撰寫內容時，應注意以下幾點：

1. 有價值的信息：提供對讀者有幫助的信息，解決他們的問題。
2. 定期更新：保持內容的新鮮度和相關性，定期發布新的內容。
3. 自然融入關鍵字：將相關的關鍵字自然地融入內容中，確保不影響閱讀體驗。

## 2. 網站結構

良好的網站結構有助於搜尋引擎爬蟲更高效地索引你的網站。以下是一些網站結構優化的建議：

1. 清晰的導航：確保網站的導航結構清晰易懂，方便用戶和搜尋引擎瀏覽。
2. 使用內部鏈接：適當地使用內部鏈接來連接相關內容，增強網站的內部結構。

## 3. 網頁速度

網頁速度是SEO的一個重要因素。較快的頁面加載速度能提升用戶體驗，並可能提高搜尋引擎的排名。

1. 優化圖片：壓縮圖片大小，使用合適的圖片格式。
2. 使用CDN：使用內容分發網絡（CDN）來加速網站的全球傳輸速度。

## 4. 移動端優化

隨著移動設備的普及，確保網站在移動端的優化同樣至關重要。Google已經將移動端優化作為排名因素之一。

1. 響應式設計：確保網站在不同設備上都能有良好的顯示效果。
2. 移動友好內容：簡化移動端的導航和操作，提高用戶體驗。

## 5. 用戶體驗（UX）

用戶體驗是SEO的核心因素之一。提升用戶體驗有助於降低跳出率，增加停留時間。

1. 易讀性：使用清晰的字體和段落結構，使內容易於閱讀。
2. 互動性：增加圖片、影片、互動內容等，提升用戶的參與度。

# 二、Schema.org

## 核心概念

Schema.org是由Google、Microsoft、Yahoo和Yandex共同發起的結構化數據標記語言。通過在HTML中添加Schema.org標記，可以幫助搜尋引擎更好地理解網頁內容，從而在搜尋結果中提供更豐富的信息展示（如豐富摘要）。

## 範例程式碼

以下是一個使用Schema.org標記的範例，標記一個產品的信息：

```html
<div itemscope itemtype="https://schema.org/Product">
  <span itemprop="name">Amazing Product</span>
  <img itemprop="image" src="amazing-product.jpg" alt="Amazing Product">
  <span itemprop="description">This is an amazing product that you will love.</span>
  <span itemprop="brand">Awesome Brand</span>
  <span itemprop="offers" itemscope itemtype="https://schema.org/Offer">
    <span itemprop="priceCurrency" content="USD">$</span>
    <span itemprop="price" content="29.99">29.99</span>
    <link itemprop="availability" href="https://schema.org/InStock">In stock</link>
  </span>
</div>
```

1. ``<div itemscope itemtype="https://schema.org/Product">``：定義了一個包含產品信息的區塊，使用itemscope表示這是一個獨立的項目，itemtype指定這是類型為Product的Schema.org類型。
2. ``<span itemprop="name">Amazing Product</span>``：標記產品的名稱。
3. ``<img itemprop="image" src="amazing-product.jpg" alt="Amazing Product">``：標記產品的圖片。
4. ``<span itemprop="description">This is an amazing product that you will love.</span>``：標記產品的描述。
5. ``<span itemprop="brand">Awesome Brand</span>``：標記產品的品牌。
6. ``<span itemprop="offers" itemscope itemtype="https://schema.org/Offer">``：標記產品的報價信息，itemscope表示這是一個獨立的報價項目，itemtype指定這是類型為Offer的Schema.org類型。
7. ``<span itemprop="priceCurrency" content="USD">$</span>``：標記價格的貨幣類型。
8. ``<span itemprop="price" content="29.99">29.99</span>``：標記產品的價格。
9. ``<link itemprop="availability" href="https://schema.org/InStock">In stock</link>``：標記產品的庫存狀態。

在google搜尋頁面大概會長這樣:
![img](/images/Shema.png)

## 優點

- 提升搜尋引擎理解：幫助搜尋引擎更好地理解和索引網頁內容。
- 豐富摘要：在搜尋結果中顯示豐富摘要（如評價星級、價格），提高點擊率。

# 三、Open Graph

## 核心觀念

Open Graph是由Facebook推出的協議，旨在讓網頁在社交媒體平台上分享時顯示更豐富的信息。通過在HTML中添加Open Graph標籤，可以自定義分享到社交媒體時顯示的標題、描述、圖片等信息。

## 範例代碼

以下是一個使用Open Graph標記的範例：

```html
<head>
  <meta property="og:title" content="Amazing Product">
  <meta property="og:description" content="This is an amazing product that you will love.">
  <meta property="og:image" content="https://example.com/amazing-product.jpg">
  <meta property="og:url" content="https://example.com/amazing-product">
</head>
```

1. ``<meta property="og:title" content="Amazing Product">``：設置分享時顯示的標題。
2. ``<meta property="og:description" content="This is an amazing product that you will love.">``：設置分享時顯示的描述。
3. ``<meta property="og:image" content="https://example.com/amazing-product.jpg">``：設置分享時顯示的圖片。
4. ``<meta property="og:url" content="https://example.com/amazing-product">``：設置分享時指向的URL。

> Open Graph是控制在社交媒體上分享時的標題、描述和圖片，這裡僅能提供程式碼做參考而無法提供圖片

## 優點
- 自定義分享信息：控制在社交媒體上分享時顯示的標題、描述和圖片。
- 提升點擊率：通過吸引人的分享信息，提高點擊率。


# 結論

提升網頁的SEO需要綜合考慮多個方面，從高質量內容、網站結構、網頁速度到用戶體驗，每個環節都不可忽視。此外，利用Schema.org和Open Graph等技術手段，可以進一步提升搜尋引擎和社交媒體上的表現。希望這篇文章能幫助你理解和應用這些SEO技巧，讓你的網站在搜尋引擎中脫穎而出。