---
title: "Cấu trúc điều kiện trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-co-ban"]
---

## 1. Cấu trúc điều kiện là gì?

**Cấu trúc điều kiện** cho phép chương trình:
- **Ra quyết định**
- Thực hiện các đoạn code khác nhau
- Dựa trên điều kiện đúng hoặc sai (`true / false`)

👉 Ví dụ:
```js
if (age >= 18) {
  console.log("Đủ tuổi");
}
```
2. Câu lệnh if
Cú pháp:
```js
if (điều_kiện) {
  // code chạy nếu điều kiện đúng
}
```
Ví dụ:
```js
let age = 20;

if (age >= 18) {
  console.log("Bạn đủ tuổi");
}
```
3. if...else
```js
let age = 16;

if (age >= 18) {
  console.log("Đủ tuổi");
} else {
  console.log("Chưa đủ tuổi");
}
```
4. if...else if...else
```js
let score = 8;

if (score >= 9) {
  console.log("Xuất sắc");
} else if (score >= 7) {
  console.log("Khá");
} else if (score >= 5) {
  console.log("Trung bình");
} else {
  console.log("Yếu");
}

```
📌 Điều kiện được kiểm tra từ trên xuống

5. Điều kiện lồng nhau
```js
let age = 20;
let hasID = true;

if (age >= 18) {
  if (hasID) {
    console.log("Được vào");
  } else {
    console.log("Thiếu giấy tờ");
  }
}
```

❌ Dễ rối nếu lồng quá nhiều
✔ Nên viết gọn hơn khi có thể

6. Kết hợp với toán tử logic
```js
if (age >= 18 && hasID) {
  console.log("Được vào");
}

```
👉 Gọn hơn ví dụ trên

7. Câu lệnh switch...case
Cú pháp:
```js
switch (value) {
  case x:
    // code
    break;
  case y:
    // code
    break;
  default:
    // code
}
```
Ví dụ:
```js
let day = 2;

switch (day) {
  case 1:
    console.log("Thứ hai");
    break;
  case 2:
    console.log("Thứ ba");
    break;
  case 3:
    console.log("Thứ tư");
    break;
  default:
    console.log("Không hợp lệ");
}

```
📌 Quên break sẽ chạy xuyên case

8. Toán tử điều kiện (? :)
```js
let age = 20;

let message = age >= 18 ? "Đủ tuổi" : "Chưa đủ tuổi";

```
👉 Dùng cho điều kiện đơn giản

9. Giá trị truthy & falsy

❌ Falsy:
```js
false

0

""

null

undefined

NaN
```
✔ Truthy:

Mọi giá trị còn lại
```js

if ("hello") {
  console.log("Chạy");
}
```
10. Ví dụ thực tế
Kiểm tra đăng nhập:
```js
let isLogin = true;

if (isLogin) {
  console.log("Đã đăng nhập");
} else {
  console.log("Chưa đăng nhập");
}
```
11. Lỗi thường gặp

❌ Dùng == thay vì ===
❌ Quên break trong switch
❌ Viết điều kiện quá phức tạp
12. So sánh nhanh
| Cách        | Khi nào dùng           |
| ----------- | ---------------------- |
| `if`        | Điều kiện đơn          |
| `if...else` | 2 nhánh                |
| `else if`   | Nhiều nhánh            |
| `switch`    | So sánh giá trị cụ thể |
| `? :`       | Viết gọn               |
