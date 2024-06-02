---
title: 關於 JavaScript 的 Iterator Protocol 和 Iterable Protocol
date: 2024-06-02 21:15:05
categories: 前端知識
tags: "JavaScript"
---
在這篇文章中，我將介紹 JavaScript 的 Iterator Protocol 和 Iterable Protocol，並解釋 next() 方法以及 Symbol.iterator 的使用方式。我會使用範例程式碼來幫助說明這些概念。

## Iterable protocol

對象必須實現一個名為 Symbol.iterator 的方法，該方法返回一個符合 Iterator Protocol 的對象。這使得對象可以被 ``for...of`` 循環訪問。這個協議為對象添加了一個可供迭代的屬性，``[Symbol.iterator] `` 屬性的值應該是一個函數，該函數返回一個迭代器物件。這個迭代器物件必須有一個名為 next 的方法。

在 JavaScript 中，Symbol.iterator 是一個內建的 Symbol，它的主要用途是定義一個物件的預設迭代行為。``` [Symbol.iterator] ```會在需要對一個物件進行迭代的時候被呼叫。這通常會在以下情況發生：

1. 當物件被用在 for...of 迴圈中時。例如：
```JavaScript
   for (let value of object) {
        console.log(value);
    }
```

在這個例子中，object 的``` [Symbol.iterator] ```方法會被呼叫，以取得一個迭代器物件。

2. 當使用 ... 展開運算符對物件進行展開時。例如：
```JavaScript
   let array = [...object];
```
在這個例子中，object 的 [Symbol.iterator] 方法也會被呼叫。

3. 當物件被傳遞給期望迭代的內建函數或方法時，如 Array.from()、Map()、Set() 等。例如：
```JavaScript
   let array = Array.from(object);
```
在這個例子中，object 的 [Symbol.iterator] 方法同樣會被呼叫。


## Iterator protocol

Iterator Protocol 定義了一種標準的方式來產生一系列的值。符合這個協議的對象需要實現一個 next() 方法。每次調用 next() 方法時，它都返回一個表示當前值和遍歷狀態的物件。這個物件包含兩個屬性：

- value：當前的值。
- done：一個布爾值，表示遍歷是否完成。如果迭代完成，則返回 true，否則返回 false。

### next() 方法

next() 方法是迭代器協議的核心部分。每次調用 next() 方法時，它返回一個包含兩個屬性的對象：value 和 done。value 表示當前迭代的值，而 done 表示迭代是否完成。

以下是 next() 方法的工作流程：

1. 當調用 next() 方法時，迭代器生成並返回下一個值。
2. 當序列中沒有更多值可以生成時，next() 方法返回一個 { done: true } 的對象。

>  範例程式碼
```JavaScript
const myIterable = {
    [Symbol.iterator]() {
        return {
            i: 0,
            next() {
                if (this.i < 3) {
                    return { value: this.i++, done: false };
                }
                return { value: undefined, done: true };
            }
        }
    }
};

// 使用 for...of 迴圈來遍歷 myIterable
for (const value of myIterable) {
    console.log(value); // 輸出 0, 1, 2
}
```
> 在這段範例程式碼中，我們定義了一個可迭代對象 myIterable。這個對象實現了 Symbol.iterator 方法，該方法返回一個迭代器。迭代器包含一個 next() 方法，每次調用時返回當前的值和遍歷狀態。當 i 小於 3 時，next() 方法返回 { value: this.i++, done: false }，並且增加 i。當 i 等於或大於 3 時，next() 方法返回 { value: undefined, done: true }，表示遍歷完成。


## 使用場景

1. 數據結構遍歷：如陣列、集合、映射等。
2. 自定義迭代行為：當內建迭代器無法滿足需求時，可以創建自定義迭代器。
3. 生成器函數：用於控制生成值的順序和數量。

### 優點

在未使用 Symbol.iterator 的對象通常需要手動管理迭代狀態。這樣的對象無法直接使用 for...of 迴圈進行迭代，因為它們不符合迭代器協議。例如：
```JavaScript
   let array = Array.from(object);

   const myObject = {
        i: 0,
        next() {
            if (this.i < 3) {
                return { value: this.i++, done: false };
            }
            return { value: undefined, done: true };
        }
    };

    const iterator = myObject;
    console.log(iterator.next()); // { value: 0, done: false }
    console.log(iterator.next()); // { value: 1, done: false }
    console.log(iterator.next()); // { value: 2, done: false }
    console.log(iterator.next()); // { value: undefined, done: true }
```
使用 Symbol.iterator 的對象提供了更靈活和標準的方式來管理迭代，適合複雜的迭代需求和與內建迭代工具的兼容。這樣的對象可以使用 for...of 迴圈，並且更容易與其他 JavaScript 迭代工具配合。

1. 靈活性高：可以自定義迭代行為，滿足不同需求。
2. 可與 for...of 循環配合使用：使代碼更簡潔、易讀。
3. 兼容性好：支持所有可迭代對象（如陣列、字符串等）。

### 缺點

1. 複雜度：對於簡單的數據結構，使用迭代器可能增加不必要的複雜度。
2. 性能問題：自定義迭代器在某些情況下可能比內建迭代器慢。

---

希望這篇文章能幫助你更好地理解 JavaScript 的 Iterator 和 Iterable Protocol。如果有任何問題或需要進一步的解釋，歡迎留言討論！
