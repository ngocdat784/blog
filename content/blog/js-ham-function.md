---
title: "Hàm (Function) trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-co-ban"]
---

## 1. Hàm là gì?

**Hàm (Function)** là một khối code dùng để:
- Thực hiện một công việc cụ thể
- Có thể **tái sử dụng nhiều lần**
- Giúp code gọn gàng, dễ bảo trì

👉 Ví dụ:
```js
function sayHello() {
  console.log("Xin chào JavaScript");
}

sayHello();
2. Vì sao phải dùng hàm?

❌ Không dùng hàm:

console.log("Xin chào");
console.log("Xin chào");
console.log("Xin chào");


✔ Dùng hàm:

function greet() {
  console.log("Xin chào");
}

greet();

3. Cách khai báo hàm
🔹 3.1. Function Declaration (phổ biến)
function sum(a, b) {
  return a + b;
}

sum(3, 5); // 8


📌 Có thể gọi hàm trước khi khai báo

🔹 3.2. Function Expression
const multiply = function(a, b) {
  return a * b;
};

multiply(2, 4); // 8


❌ Không gọi được trước khi khai báo

🔹 3.3. Arrow Function (ES6 – rất phổ biến)
const add = (a, b) => {
  return a + b;
};


Viết gọn:

const add = (a, b) => a + b;

4. Tham số và đối số
function greet(name) {
  console.log("Xin chào " + name);
}

greet("Đạt");


name → tham số

"Đạt" → đối số

5. Giá trị trả về (return)
function square(x) {
  return x * x;
}

let result = square(5); // 25


📌 Sau return, code không chạy tiếp

6. Hàm không có return
function showMessage() {
  console.log("Hello");
}

let x = showMessage();
console.log(x); // undefined

7. Tham số mặc định (Default Parameter)
function greet(name = "bạn") {
  console.log("Xin chào " + name);
}

greet();
greet("Đạt");

8. Hàm và phạm vi biến (Scope)
let x = 10;

function test() {
  let y = 20;
  console.log(x); // OK
}

console.log(y); // ❌ Error


👉 Biến trong hàm chỉ dùng trong hàm

9. Hàm lồng nhau
function outer() {
  function inner() {
    console.log("Hàm bên trong");
  }
  inner();
}

outer();


📌 Đây là nền tảng của Closure (học sau)

10. Callback Function (khái niệm rất quan trọng)
function process(callback) {
  callback();
}

process(function() {
  console.log("Đây là callback");
});


👉 Hàm được truyền vào hàm khác

11. Ví dụ thực tế
Tính tổng các số trong mảng:
function sumArray(arr) {
  let total = 0;

  for (let num of arr) {
    total += num;
  }

  return total;
}

sumArray([1, 2, 3, 4]); // 10

12. Lỗi thường gặp

❌ Quên return
❌ Nhầm tham số & đối số
❌ Gọi hàm trước khi khai báo (với expression)