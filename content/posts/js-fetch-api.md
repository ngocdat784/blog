---
title: "Fetch API trong JavaScript"
date: 2025-12-24
draft: false
tags: ["js-api"]
---

## Fetch API là gì?

**Fetch API** là một API hiện đại trong JavaScript dùng để **gửi và nhận dữ liệu từ server** thông qua giao thức HTTP.  
Fetch thường được dùng để:

- Lấy dữ liệu từ API (JSON)
- Gửi dữ liệu lên server
- Thay thế cho `XMLHttpRequest` cũ

👉 Fetch hoạt động dựa trên **Promise**, giúp code gọn gàng và dễ đọc hơn.

---

## Cú pháp cơ bản của Fetch API

```js
fetch(url)
  .then(response => response.json())
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error(error);
  });
  ```
📌 Giải thích:

fetch(url) → gửi request

response.json() → chuyển dữ liệu trả về thành JSON

then() → xử lý dữ liệu

catch() → bắt lỗi

Ví dụ: Lấy dữ liệu từ API
```js
fetch("https://jsonplaceholder.typicode.com/posts")
  .then(res => res.json())
  .then(posts => {
    console.log(posts);
  });
```

📌 API trên trả về danh sách bài viết giả để test.

Sử dụng Fetch với async / await (khuyến nghị)
```js
async function getPosts() {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

getPosts();

```
✅ Code dễ đọc hơn
✅ Gần giống code đồng bộ

Gửi dữ liệu bằng Fetch (POST)
```js
fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({
    title: "Hello JS",
    body: "Fetch API rất dễ dùng",
    userId: 1
  })
})
.then(res => res.json())
.then(data => console.log(data));

```
📌 Các thành phần quan trọng:

method: HTTP method (GET, POST, PUT, DELETE)

headers: kiểu dữ liệu gửi đi

body: dữ liệu gửi (phải dùng JSON.stringify)

Kiểm tra lỗi khi gọi API
```js
fetch(url)
  .then(res => {
    if (!res.ok) {
      throw new Error("Lỗi HTTP: " + res.status);
    }
    return res.json();
  })
  .then(data => console.log(data))
  .catch(err => console.error(err.message));

```
📌 res.ok = false khi:
```js

404 Not Found

500 Server Error
```

Ví dụ thực tế: Hiển thị dữ liệu ra HTML
```js
<ul id="post-list"></ul>

async function loadPosts() {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts");
  const posts = await res.json();

  const ul = document.getElementById("post-list");
  posts.slice(0, 5).forEach(post => {
    const li = document.createElement("li");
    li.textContent = post.title;
    ul.appendChild(li);
  });
}

loadPosts();
```

👉 Rất hay dùng trong:

Trang blog

Trang sản phẩm

Dashboard
So sánh Fetch API và XMLHttpRequest
| Tiêu chí          | Fetch API   | XMLHttpRequest |
| ----------------- | ----------- | -------------- |
| Cú pháp           | Gọn, dễ đọc | Dài, khó nhớ   |
| Promise           | Có          | Không          |
| Hiện đại          | ✅           | ❌              |
| Phổ biến hiện nay | ✅           | Ít dùng        |
Lỗi thường gặp khi dùng Fetch

❌ Quên return response.json()
❌ Quên await
❌ Gửi body nhưng không set Content-Type
❌ Không xử lý lỗi HTTP