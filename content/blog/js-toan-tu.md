---
title: "Toán tử trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-co-ban"]
---

## 1. Toán tử là gì?

**Toán tử (Operator)** là các ký hiệu dùng để:
- Thực hiện phép tính
- So sánh
- Gán giá trị
- Kết hợp điều kiện

👉 Ví dụ:
```js
let a = 10 + 5;
| Toán tử | Ý nghĩa     |
| ------- | ----------- |
| `+`     | Cộng        |
| `-`     | Trừ         |
| `*`     | Nhân        |
| `/`     | Chia        |
| `%`     | Chia lấy dư |
| `**`    | Lũy thừa    |
let a = 10;
let b = 3;

a + b; // 13
a - b; // 7
a * b; // 30
a / b; // 3.333...
a % b; // 1
a ** b; // 1000
📌 Lưu ý:

"10" + 5 // "105"


Dấu + vừa là cộng, vừa là nối chuỗi.

3. Toán tử gán (Assignment Operators)
| Toán tử | Ví dụ    | Tương đương |
| ------- | -------- | ----------- |
| `=`     | `x = 10` |             |
| `+=`    | `x += 5` | `x = x + 5` |
| `-=`    | `x -= 2` | `x = x - 2` |
| `*=`    | `x *= 3` | `x = x * 3` |
| `/=`    | `x /= 2` | `x = x / 2` |
4. Toán tử tăng / giảm
let x = 5;

x++; // 6
x--; // 5

Phân biệt:
let a = 5;
console.log(a++); // 5
console.log(++a); // 7


👉 ++a: tăng trước
👉 a++: tăng sau

5. Toán tử so sánh (Comparison Operators)
| Toán tử | Ý nghĩa                |
| ------- | ---------------------- |
| `==`    | So sánh giá trị        |
| `===`   | So sánh giá trị + kiểu |
| `!=`    | Khác giá trị           |
| `!==`   | Khác giá trị hoặc kiểu |
| `>`     | Lớn hơn                |
| `<`     | Nhỏ hơn                |
| `>=`    | ≥                      |
| `<=`    | ≤                      |
Ví dụ:
5 == "5";   // true
5 === "5";  // false


📌 Luôn ưu tiên dùng ===
6. Toán tử logic (Logical Operators)

| Toán tử | Ý nghĩa |   |    |
| ------- | ------- | - | -- |
| `&&`    | AND     |   |    |
| `       |         | ` | OR |
| `!`     | NOT     |   |    |

Ví dụ:
let age = 20;
let isStudent = true;

age >= 18 && isStudent; // true

!true; // false

7. Toán tử điều kiện (Ternary Operator)
condition ? value1 : value2;

Ví dụ:
let age = 16;

let result = age >= 18 ? "Đủ tuổi" : "Chưa đủ tuổi";


👉 Viết gọn hơn if...else

8. Toán tử typeof

Dùng để kiểm tra kiểu dữ liệu.

typeof 10;        // "number"
typeof "Hello";   // "string"
typeof true;      // "boolean"

9. Thứ tự ưu tiên toán tử
let result = 10 + 5 * 2; // 20


👉 Nhân chia trước, cộng trừ sau
👉 Dùng ngoặc để rõ ràng:

(10 + 5) * 2; // 30