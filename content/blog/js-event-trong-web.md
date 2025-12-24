---
title: "Xử lý sự kiện trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-dom"]
---

## 1. Sự kiện (Event) là gì?

**Sự kiện (Event)** là những hành động xảy ra khi người dùng:
- Click chuột
- Nhập dữ liệu
- Di chuyển chuột
- Gửi form
- Load trang

👉 JavaScript dùng event để **tương tác với người dùng**

---

## 2. Các cách gắn sự kiện

### ❌ Cách 1: Inline HTML (không khuyến khích)

```html
<button onclick="alert('Hello')">Click</button>
Ok 👍 tiếp tục series js-dom nha.
Dưới đây là nội dung hoàn chỉnh cho file js-event-trong-web.md, nối mạch trực tiếp sau bài DOM cơ bản.

---
title: "Xử lý sự kiện trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-dom"]
---

## 1. Sự kiện (Event) là gì?

**Sự kiện (Event)** là những hành động xảy ra khi người dùng:
- Click chuột
- Nhập dữ liệu
- Di chuyển chuột
- Gửi form
- Load trang

👉 JavaScript dùng event để **tương tác với người dùng**

---

## 2. Các cách gắn sự kiện

### ❌ Cách 1: Inline HTML (không khuyến khích)

```html
<button onclick="alert('Hello')">Click</button>


❌ Khó quản lý
❌ Không sạch code

🔹 Cách 2: Gán qua thuộc tính
let btn = document.querySelector("button");

btn.onclick = function() {
  alert("Click");
};


✔ Dễ hiểu
❌ Ghi đè sự kiện cũ

✅ Cách 3: addEventListener (nên dùng)
btn.addEventListener("click", function() {
  alert("Click");
});


✔ Gắn nhiều event
✔ Chuẩn hiện đại

3. Các sự kiện phổ biến
| Sự kiện     | Khi nào      |
| ----------- | ------------ |
| `click`     | Click chuột  |
| `dblclick`  | Click đúp    |
| `mouseover` | Di chuột vào |
| `mouseout`  | Di chuột ra  |
| `keydown`   | Nhấn phím    |
| `keyup`     | Nhả phím     |
| `input`     | Nhập liệu    |
| `change`    | Thay đổi     |
| `submit`    | Gửi form     |
| `load`      | Load trang   |
4. Đối tượng Event (event)
btn.addEventListener("click", function(event) {
  console.log(event);
});


👉 event chứa:

Loại sự kiện

Phần tử gây ra sự kiện

Vị trí chuột, phím bấm…

🔹 event.target
document.addEventListener("click", function(e) {
  console.log(e.target);
});


👉 Phần tử được click

5. Ngăn hành vi mặc định
🔹 preventDefault()
<form id="myForm">
  <button type="submit">Gửi</button>
</form>

document.getElementById("myForm")
  .addEventListener("submit", function(e) {
    e.preventDefault();
    console.log("Không reload trang");
});


👉 Rất quan trọng khi làm form

6. Bắt sự kiện nhập liệu
let input = document.querySelector("input");

input.addEventListener("input", function(e) {
  console.log(e.target.value);
});

7. Event Bubbling & Capturing (hiểu cơ bản)
<div id="parent">
  <button id="child">Click</button>
</div>

parent.addEventListener("click", () => console.log("Parent"));
child.addEventListener("click", () => console.log("Child"));


👉 Click button:

Child
Parent


📌 Đây gọi là bubbling

8. Event Delegation (rất hay dùng)
document.querySelector("ul")
  .addEventListener("click", function(e) {
    if (e.target.tagName === "LI") {
      console.log(e.target.innerText);
    }
});


👉 Dùng khi:

Danh sách động

Nhiều phần tử con

9. Ví dụ thực tế
Click đổi màu nền:
let btn = document.querySelector("button");

btn.addEventListener("click", function() {
  document.body.classList.toggle("dark");
});

10. Lỗi thường gặp

❌ Gắn event khi DOM chưa load
❌ Dùng inline event
❌ Quên preventDefault khi submit form
11. So sánh nhanh
| Cách             | Ghi chú    |
| ---------------- | ---------- |
| Inline           | Không dùng |
| onclick          | Đơn giản   |
| addEventListener | Chuẩn      |
