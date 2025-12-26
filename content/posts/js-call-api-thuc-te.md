---
title: "Gọi API thực tế bằng JavaScript"
date: 2025-12-24
draft: false
tags: ["js-api"]
---

## Gọi API thực tế là gì?

Trong các website hiện đại, **JavaScript thường xuyên gọi API từ backend** để:

- Lấy danh sách sản phẩm
- Đăng nhập / đăng ký
- Thêm giỏ hàng
- Đặt lịch, thanh toán
- Chatbot, AI, dashboard

👉 Bài này sẽ tập trung **case thực tế**, không chỉ ví dụ minh hoạ.

---

## Mô hình Frontend gọi Backend API

HTML / JS (Browser)
↓ fetch()
REST API
↓
Backend (FastAPI / Node / ASP.NET)
↓
Database


📌 Frontend **không truy cập DB trực tiếp**, chỉ gọi API.

---

## Ví dụ 1: Gọi API lấy danh sách sản phẩm

### API giả định



GET http://localhost:8000/api/products


### JavaScript gọi API

```js
async function loadProducts() {
  try {
    const res = await fetch("http://localhost:8000/api/products");

    if (!res.ok) {
      throw new Error("Không thể lấy dữ liệu sản phẩm");
    }

    const products = await res.json();
    renderProducts(products);
  } catch (err) {
    console.error(err.message);
  }
}
```
Hiển thị ra HTML
```js
<div id="product-list"></div>

function renderProducts(products) {
  const container = document.getElementById("product-list");
  container.innerHTML = "";

  products.forEach(p => {
    container.innerHTML += `
      <div class="product">
        <h3>${p.name}</h3>
        <p>Giá: ${p.price} VND</p>
      </div>
    `;
  });
}

loadProducts();
```


Ví dụ 2: Gửi dữ liệu lên server (POST)
API tạo sản phẩm
POST http://localhost:8000/api/products
```js
JavaScript
async function createProduct() {
  const product = {
    name: "Áo thun nam",
    price: 150000
  };

  const res = await fetch("http://localhost:8000/api/products", {
    method: "POST",
    headers: {
      "Content-Type": "application/json"
    },
    body: JSON.stringify(product)
  });

  const data = await res.json();
  console.log("Đã tạo:", data);
}
```


Ví dụ 3: Gọi API có Token (Authentication)
Lưu token sau khi đăng nhập
```js
localStorage.setItem("token", "abc123xyz");
```
Gọi API có xác thực
```js
async function getProfile() {
  const token = localStorage.getItem("token");

  const res = await fetch("http://localhost:8000/api/profile", {
    headers: {
      "Authorization": "Bearer " + token
    }
  });

  const data = await res.json();
  console.log(data);
}
```


📌 Rất phổ biến trong:

Admin panel

Trang tài khoản

Hệ thống phân quyền


Ví dụ 4: Xử lý lỗi từ API
Backend trả lỗi
```js
{
  "message": "Email hoặc mật khẩu không đúng"
}
```
Frontend xử lý
```js
const res = await fetch(url);

if (!res.ok) {
  const errorData = await res.json();
  alert(errorData.message);
  return;
}
```
Ví dụ 5: Loading khi gọi API
```js
const loading = document.getElementById("loading");

async function loadData() {
  loading.style.display = "block";

  const res = await fetch(url);
  const data = await res.json();

  loading.style.display = "none";
  console.log(data);
}

```
👉 Trải nghiệm người dùng tốt hơn.

Các lỗi thường gặp khi gọi API thực tế

❌ Sai URL / sai cổng
❌ Lỗi CORS
❌ Quên token
❌ Sai method (GET vs POST)
❌ Backend chưa bật JSON

CORS là gì? (rất hay gặp)

Nếu thấy lỗi:
```js

Access to fetch has been blocked by CORS policy
```

👉 Backend cần bật CORS:

FastAPI:
```js

from fastapi.middleware.cors import CORSMiddleware

```
ASP.NET:
```js
builder.Services.AddCors();
```
Fetch API vs Axios (thực tế)
| Tiêu chí      | Fetch | Axios   |
| ------------- | ----- | ------- |
| Cài thêm      | ❌     | ✅       |
| Tự parse JSON | ❌     | ✅       |
| Bắt lỗi HTTP  | ❌     | ✅       |
| Phổ biến      | Cao   | Rất cao |
👉 Dự án lớn thường dùng Axios.