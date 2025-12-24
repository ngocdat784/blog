---

title: "Biến và Kiểu dữ liệu trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-co-ban"]
-------------------

## 1. Biến trong JavaScript là gì?

**Biến (Variable)** là nơi dùng để **lưu trữ dữ liệu tạm thời** trong chương trình.
Dữ liệu này có thể là số, chuỗi, đúng/sai, danh sách, đối tượng,…

### Ví dụ

```js
let name = "Ngọc Đạt";
let age = 20;
```

**Giải thích:**

* `name` là biến lưu **chuỗi** "Ngọc Đạt"
* `age` là biến lưu **số** 20

---

## 2. Cách khai báo biến trong JavaScript

JavaScript có **3 từ khóa** để khai báo biến.

### 2.1. `var` (ít dùng – không khuyến khích)

```js
var x = 10;
```

**Nhược điểm:**

* Dễ gây lỗi
* Không kiểm soát tốt phạm vi (scope)

👉 **Không nên dùng trong code JavaScript hiện đại**

---

### 2.2. `let` (nên dùng)

```js
let score = 100;
score = 120;
```

**Ưu điểm:**

* ✔ Có thể thay đổi giá trị
* ✔ Phạm vi rõ ràng (block scope)
* ✔ Phổ biến nhất hiện nay

---

### 2.3. `const` (hằng số)

```js
const PI = 3.14;
```

* ✔ Không thể gán lại giá trị
* ❌ Gán lại sẽ gây lỗi

```js
PI = 3.15; // ❌ Error
```

👉 Dùng `const` khi **không muốn dữ liệu bị thay đổi**

---

## 3. Quy tắc đặt tên biến

### Hợp lệ

```js
let userName;
let totalPrice;
let _count;
```

### Không hợp lệ

```js
let 1name;
let user-name;
let let;
```

📌 **Quy ước phổ biến:** dùng **camelCase**

```js
let studentName;
let totalScore;
```

---

## 4. Kiểu dữ liệu trong JavaScript

JavaScript là ngôn ngữ **dynamic typing**
👉 Không cần khai báo kiểu dữ liệu trước

---

### 4.1. Number – Kiểu số

```js
let a = 10;
let b = 3.14;
let c = -5;
```

👉 JavaScript **không phân biệt số nguyên và số thực**

---

### 4.2. String – Chuỗi

```js
let name = "JavaScript";
let msg = 'Xin chào';
```

Có thể dùng:

* `" "` (double quotes)
* `' '` (single quotes)
* `` ` ` `` (template string)

```js
let age = 20;
let text = `Tôi ${age} tuổi`;
```

---

### 4.3. Boolean – Đúng / Sai

```js
let isLogin = true;
let isAdmin = false;
```

👉 Thường dùng trong:

* Câu điều kiện
* Kiểm tra trạng thái

---

### 4.4. Undefined

```js
let x;
console.log(x); // undefined
```

👉 Biến đã khai báo nhưng **chưa gán giá trị**

---

### 4.5. Null

```js
let data = null;
```

👉 Chủ động gán giá trị **rỗng**

**Phân biệt:**

* `undefined`: chưa gán
* `null`: cố ý gán rỗng

---

### 4.6. Object – Đối tượng

```js
let student = {
  name: "Đạt",
  age: 20,
  isMale: true
};
```

👉 Object dùng để **gom nhiều dữ liệu liên quan**

---

### 4.7. Array – Mảng

```js
let numbers = [1, 2, 3, 4];
let fruits = ["Táo", "Cam", "Chuối"];
```

👉 Mảng là **một dạng Object đặc biệt**

---

## 5. Kiểm tra kiểu dữ liệu với `typeof`

```js
typeof 10;        // "number"
typeof "Hello"; // "string"
typeof true;     // "boolean"
typeof undefined;// "undefined"
typeof null;     // "object" ❗ (lỗi lịch sử của JS)
```

📌 **Lưu ý quan trọng:**

```js
typeof null === "object" // true (dễ gây nhầm lẫn)
```
