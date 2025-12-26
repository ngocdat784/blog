---
title: "Xử lý Form & Validation trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-dom"]
---

## 1. Form và Validation là gì?

- **Form** dùng để thu thập dữ liệu người dùng
- **Validation** dùng để **kiểm tra dữ liệu trước khi gửi**

👉 Validation giúp:
- Tránh dữ liệu sai
- Tăng trải nghiệm người dùng
- Giảm lỗi phía server

---

## 2. Cấu trúc form cơ bản

```js
<form id="registerForm">
  <input type="text" id="username" placeholder="Tên đăng nhập">
  <input type="email" id="email" placeholder="Email">
  <input type="password" id="password" placeholder="Mật khẩu">
  <button type="submit">Đăng ký</button>
</form>

<p id="error"></p>
```
3. Bắt sự kiện submit
```js
const form = document.getElementById("registerForm");

form.addEventListener("submit", function(e) {
  e.preventDefault(); // ngăn reload trang
  console.log("Submit form");
});
```

📌 Bắt buộc dùng preventDefault()

4. Lấy dữ liệu từ input
```js
const username = document.getElementById("username").value;
const email = document.getElementById("email").value;
const password = document.getElementById("password").value;
```
5. Kiểm tra dữ liệu rỗng
```js
if (username === "" || email === "" || password === "") {
  error.innerText = "Vui lòng nhập đầy đủ thông tin";
  return;
}
```
6. Kiểm tra email hợp lệ
```js
function isValidEmail(email) {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
}

if (!isValidEmail(email)) {
  error.innerText = "Email không hợp lệ";
  return;
}
```
7. Kiểm tra độ dài mật khẩu
```js
if (password.length < 6) {
  error.innerText = "Mật khẩu phải ít nhất 6 ký tự";
  return;
}
```
8. Hiển thị lỗi thân thiện
```js
error.style.color = "red";
error.innerText = "Lỗi nhập liệu";

```
Hoặc dùng class:
```js
error.classList.add("error");
```
9. Validation khi nhập (Realtime)
```js
password.addEventListener("input", function() {
  if (password.value.length < 6) {
    error.innerText = "Mật khẩu yếu";
  } else {
    error.innerText = "";
  }
});
```
10. Ví dụ hoàn chỉnh
```js
form.addEventListener("submit", function(e) {
  e.preventDefault();

  if (!username.value || !email.value || !password.value) {
    error.innerText = "Không được để trống";
    return;
  }

  if (!isValidEmail(email.value)) {
    error.innerText = "Email không hợp lệ";
    return;
  }

  if (password.value.length < 6) {
    error.innerText = "Mật khẩu quá ngắn";
    return;
  }

  error.style.color = "green";
  error.innerText = "Dữ liệu hợp lệ!";
});
```
11. Validation HTML5 vs JavaScript
| HTML5                 | JavaScript    |
| --------------------- | ------------- |
| Dễ dùng               | Linh hoạt     |
| Ít tuỳ chỉnh          | Tuỳ chỉnh cao |
| Phụ thuộc trình duyệt | Chủ động      |
👉 Thực tế: kết hợp cả hai

12. Lỗi thường gặp

❌ Quên preventDefault()
❌ Kiểm tra không đầy đủ
❌ Chỉ validate frontend (cần backend nữa)