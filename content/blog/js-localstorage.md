---
title: "LocalStorage trong JavaScript"
date: 2025-12-24
draft: false
tags: ["js-api"]
---

## 📦 LocalStorage là gì?

**LocalStorage** là một **Web API** cho phép JavaScript **lưu trữ dữ liệu trực tiếp trên trình duyệt** của người dùng.

### 🔍 Đặc điểm chính

- Lưu dữ liệu theo dạng **key – value**
- Dữ liệu **không mất** khi reload hoặc đóng trình duyệt
- Dung lượng khoảng **5–10MB**
- Chỉ lưu được **chuỗi (string)**

👉 Thường dùng để:
- Lưu token đăng nhập
- Lưu giỏ hàng
- Lưu theme (Dark / Light)
- Lưu trạng thái người dùng

---

## 🧩 Cách sử dụng LocalStorage

LocalStorage cung cấp các phương thức cơ bản như:
- `setItem()` – lưu dữ liệu
- `getItem()` – lấy dữ liệu
- `removeItem()` – xoá một key
- `clear()` – xoá toàn bộ

Ngoài ra, khi làm việc với **object / array**, ta cần kết hợp với **JSON**.

---

## 🧪 Ví dụ tổng hợp sử dụng LocalStorage

```js
// ===============================
// LƯU & LẤY DỮ LIỆU CƠ BẢN
// ===============================

// Lưu dữ liệu
localStorage.setItem("username", "admin");

// Lấy dữ liệu
const username = localStorage.getItem("username");
console.log(username);

// Xoá một key
localStorage.removeItem("username");

// Xoá toàn bộ LocalStorage
localStorage.clear();


// ===============================
// LƯU OBJECT / ARRAY
// ===============================

const user = {
  name: "Ngọc Đạt",
  role: "admin"
};

// Lưu object (phải stringify)
localStorage.setItem("user", JSON.stringify(user));

// Lấy object
const savedUser = JSON.parse(localStorage.getItem("user"));
console.log(savedUser.name);
```
```js
// ===============================
// VÍ DỤ: LƯU TRẠNG THÁI ĐĂNG NHẬP
// ===============================

// Sau khi đăng nhập thành công
localStorage.setItem("token", "abc123");
localStorage.setItem("fullName", "Ngọc Đạt Trần");

// Khi load trang
const token = localStorage.getItem("token");

if (token) {
  console.log("Đã đăng nhập");
} else {
  console.log("Chưa đăng nhập");
}
```
```js
// ===============================
// VÍ DỤ: ĐĂNG XUẤT (LOGOUT)
// ===============================

function logout() {
  localStorage.removeItem("token");
  localStorage.removeItem("fullName");
  window.location.href = "/login.html";
}
```
```js
// ===============================
// VÍ DỤ: LƯU GIỎ HÀNG
// ===============================

function addToCart(product) {
  let cart = JSON.parse(localStorage.getItem("cart")) || [];

  cart.push(product);

  localStorage.setItem("cart", JSON.stringify(cart));
}

function getCart() {
  return JSON.parse(localStorage.getItem("cart")) || [];
}
```
```js
// ===============================
// VÍ DỤ: LƯU THEME DARK / LIGHT
// ===============================

function setTheme(theme) {
  localStorage.setItem("theme", theme);
  document.body.className = theme;
}

function loadTheme() {
  const theme = localStorage.getItem("theme") || "light";
  document.body.className = theme;
}

loadTheme();
```
## ⚖️ LocalStorage vs SessionStorage

| Tiêu chí         | LocalStorage | SessionStorage |
|------------------|--------------|----------------|
| Lưu lâu dài      | ✅ Có        | ❌ Không       |
| Mất khi đóng tab | ❌ Không     | ✅ Có          |
| Dung lượng       | ~5MB         | ~5MB           |
| Mức độ phổ biến  | Rất cao      | Trung bình     |

**Nên dùng khi nào?**

- 👉 **Token đăng nhập** → LocalStorage  
- 👉 **Form tạm thời** → SessionStorage  

---

## 🔐 Lưu ý bảo mật khi dùng LocalStorage

### ⚠ Không nên lưu

- Mật khẩu
- Thông tin nhạy cảm (CMND, số thẻ, OTP, …)

### ⚠ Token trong LocalStorage

- Có thể bị đánh cắp thông qua **tấn công XSS**

### ✅ Giải pháp an toàn hơn

- Sử dụng **HttpOnly Cookie**
- Kết hợp **CSRF Token** để chống giả mạo request

---

## ❌ Các lỗi thường gặp khi dùng LocalStorage

- Quên `JSON.stringify()` khi lưu object
- Gọi `JSON.parse(null)` gây lỗi
- Dùng trùng key giữa các chức năng
- Lưu quá nhiều dữ liệu không cần thiết
