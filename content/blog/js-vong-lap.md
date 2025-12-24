---
title: "Vòng lặp trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-co-ban"]
---

## 1. Vòng lặp là gì?

**Vòng lặp (Loop)** dùng để **thực hiện một đoạn code nhiều lần** cho đến khi điều kiện không còn đúng.

👉 Ví dụ:
```js
console.log("Xin chào");
console.log("Xin chào");
console.log("Xin chào");
❌ Viết như vậy rất dở
✔ Vòng lặp giúp viết gọn hơn

2. Vòng lặp for
Cú pháp:
for (khởi_tạo; điều_kiện; cập_nhật) {
  // code
}

Ví dụ:
for (let i = 1; i <= 5; i++) {
  console.log(i);
}


👉 Chạy từ 1 đến 5

3. Vòng lặp while
Cú pháp:
while (điều_kiện) {
  // code
}

Ví dụ:
let i = 1;

while (i <= 5) {
  console.log(i);
  i++;
}


📌 Cẩn thận vòng lặp vô hạn nếu quên tăng i

4. Vòng lặp do...while
Cú pháp:
do {
  // code
} while (điều_kiện);

Ví dụ:
let i = 10;

do {
  console.log(i);
  i++;
} while (i < 5);


👉 Chạy ít nhất 1 lần, dù điều kiện sai

5. break và continue
🔹 break – thoát vòng lặp
for (let i = 1; i <= 10; i++) {
  if (i === 5) break;
  console.log(i);
}


👉 Kết quả: 1 2 3 4

🔹 continue – bỏ qua lượt hiện tại
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue;
  console.log(i);
}


👉 Bỏ qua số 3

6. Vòng lặp với mảng
🔹 for truyền thống
let fruits = ["Táo", "Cam", "Chuối"];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}

🔹 for...of (rất nên dùng)
for (let fruit of fruits) {
  console.log(fruit);
}


✔ Gọn
✔ Dễ đọc
✔ Phổ biến

7. for...in (ít dùng)
let student = {
  name: "Đạt",
  age: 20
};

for (let key in student) {
  console.log(key, student[key]);
}


👉 Dùng cho object

❌ Không nên dùng cho mảng

8. forEach – vòng lặp hiện đại
fruits.forEach(function(item, index) {
  console.log(index, item);
});


Hoặc dùng arrow function:

fruits.forEach((item, index) => {
  console.log(index, item);
});


📌 Không dùng được break
9. So sánh nhanh các vòng lặp
| Vòng lặp     | Khi nào dùng               |
| ------------ | -------------------------- |
| `for`        | Khi cần chỉ số             |
| `while`      | Khi chưa biết trước số lần |
| `do...while` | Chạy ít nhất 1 lần         |
| `for...of`   | Lặp mảng                   |
| `for...in`   | Lặp object                 |
| `forEach`    | Code gọn, hiện đại         |
10. Ví dụ thực tế
In các số chẵn từ 1 đến 10:
for (let i = 1; i <= 10; i++) {
  if (i % 2 === 0) {
    console.log(i);
  }
}

11. Lỗi thường gặp

❌ Quên tăng biến lặp → vòng lặp vô hạn
❌ Dùng for...in cho mảng
❌ Không kiểm tra length