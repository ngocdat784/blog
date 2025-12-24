---
title: "LocalStorage trong JavaScript"
date: 2025-12-24
draft: false
tags: ["js-api"]
---

## LocalStorage là gì?

**LocalStorage** là một Web API cho phép JavaScript **lưu trữ dữ liệu ngay trên trình duyệt** của người dùng.

📌 Đặc điểm:
- Lưu dữ liệu **dạng key – value**
- Dữ liệu **không tự mất** khi reload hay đóng trình duyệt
- Dung lượng khoảng **5–10MB**
- Chỉ lưu được **string**

👉 Rất hay dùng trong:
- Lưu token đăng nhập
- Giỏ hàng
- Theme (dark / light)
- Trạng thái người dùng

---

## Cú pháp cơ bản của LocalStorage

### Lưu dữ liệu

```js
localStorage.setItem("username", "admin");
Lấy dữ liệu
const username = localStorage.getItem("username");
console.log(username);

Xoá 1 key
localStorage.removeItem("username");

Xoá toàn bộ
localStorage.clear();

Lưu Object / Array vào LocalStorage

❌ LocalStorage không lưu trực tiếp object

👉 Phải chuyển sang JSON.

Lưu object
const user = {
  name: "Ngọc Đạt",
  role: "admin"
};

localStorage.setItem("user", JSON.stringify(user));

Lấy object
const user = JSON.parse(localStorage.getItem("user"));
console.log(user.name);

Ví dụ 1: Lưu trạng thái đăng nhập
Sau khi login thành công
localStorage.setItem("token", "abc123");
localStorage.setItem("fullName", "Ngọc Đạt Trần");

Khi load trang
const token = localStorage.getItem("token");

if (token) {
  console.log("Đã đăng nhập");
} else {
  console.log("Chưa đăng nhập");
}

Ví dụ 2: Đăng xuất (Logout)
function logout() {
  localStorage.removeItem("token");
  localStorage.removeItem("fullName");
  window.location.href = "/login.html";
}

Ví dụ 3: Lưu giỏ hàng vào LocalStorage
Thêm sản phẩm vào giỏ
function addToCart(product) {
  let cart = JSON.parse(localStorage.getItem("cart")) || [];

  cart.push(product);

  localStorage.setItem("cart", JSON.stringify(cart));
}

Lấy giỏ hàng
function getCart() {
  return JSON.parse(localStorage.getItem("cart")) || [];
}

Ví dụ 4: Lưu theme Dark / Light
function setTheme(theme) {
  localStorage.setItem("theme", theme);
  document.body.className = theme;
}

function loadTheme() {
  const theme = localStorage.getItem("theme") || "light";
  document.body.className = theme;
}

loadTheme();

LocalStorage vs SessionStorage
| Tiêu chí         | LocalStorage | SessionStorage |
| ---------------- | ------------ | -------------- |
| Lưu lâu dài      | ✅            | ❌              |
| Mất khi đóng tab | ❌            | ✅              |
| Dung lượng       | ~5MB         | ~5MB           |
| Phổ biến         | Rất cao      | Trung bình     |
👉 Token đăng nhập → LocalStorage
👉 Form tạm → SessionStorage

Lưu ý bảo mật khi dùng LocalStorage

⚠ Không nên lưu:

Mật khẩu

Thông tin nhạy cảm

⚠ Token trong LocalStorage:

Dễ bị XSS đánh cắp

Giải pháp nâng cao: HttpOnly Cookie

Các lỗi thường gặp

❌ Quên JSON.stringify
❌ JSON.parse(null) gây lỗi
❌ Dùng key trùng nhau
❌ Lưu quá nhiều dữ liệu