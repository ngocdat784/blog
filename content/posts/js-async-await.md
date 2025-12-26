---
title: "Async / Await trong JavaScript"
date: 2025-12-24
draft: false
tags: ["js-nang-cao"]
---

## Async / Await là gì?

**Async / Await** là cú pháp giúp viết **code bất đồng bộ** trong JavaScript **giống như đồng bộ**, giúp:

- Dễ đọc
- Dễ debug
- Tránh callback hell
- Code sạch hơn Promise thuần

👉 Thực chất, `async / await` **được xây dựng trên Promise**.

---

## Vấn đề của JavaScript bất đồng bộ

JavaScript **không chờ** các tác vụ tốn thời gian:

```js
console.log("A");

setTimeout(() => {
  console.log("B");
}, 1000);

console.log("C");
```
📌 Kết quả:
```js
A
C
B
```
Promise – tiền đề của Async / Await
```js
function getData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Dữ liệu đã tải");
    }, 1000);
  });
}

getData().then(data => console.log(data));
```

❌ Khó đọc khi chain nhiều then().

Cú pháp cơ bản của Async / Await
```js
async function loadData() {
  const data = await getData();
  console.log(data);
}

loadData();

```
📌 Quy tắc:

Hàm dùng await phải có async

await chỉ dùng với Promise

Ví dụ 1: Gọi API bằng Async / Await
```js
async function loadPosts() {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts");
  const data = await res.json();
  console.log(data);
}

loadPosts();
```

✔ Gọn hơn then()
✔ Dễ hiểu hơn

Xử lý lỗi với try / catch
```js
async function loadData() {
  try {
    const res = await fetch(url);

    if (!res.ok) {
      throw new Error("Lỗi server");
    }

    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error(err.message);
  }
}


👉 try / catch = then().catch()
```

Ví dụ 2: Gọi nhiều API liên tiếp
```js
async function loadUserData() {
  const user = await fetch("/api/user").then(res => res.json());
  const orders = await fetch(`/api/orders/${user.id}`).then(res => res.json());

  console.log(user, orders);
}
```

📌 API sau phụ thuộc API trước → dùng await rất hợp.

Ví dụ 3: Gọi nhiều API song song
```js
async function loadAll() {
  const [users, products] = await Promise.all([
    fetch("/api/users").then(r => r.json()),
    fetch("/api/products").then(r => r.json())
  ]);

  console.log(users, products);
}
```

✔ Nhanh hơn
✔ Thực tế hơn

Async / Await với LocalStorage
```js
async function login() {
  const res = await fetch("/api/login");
  const data = await res.json();

  localStorage.setItem("token", data.token);
}
```
Lỗi thường gặp khi dùng Async / Await

❌ Quên await → dữ liệu là Promise
❌ Dùng await ngoài hàm async
❌ Không bắt lỗi
❌ Chờ tuần tự không cần thiết

Khi nào nên dùng Async / Await?

✔ Gọi API
✔ Đọc / ghi file
✔ Xử lý dữ liệu bất đồng bộ
✔ Code nghiệp vụ phức tạp

❌ Không cần cho logic đơn giản, đồng bộ

Async / Await vs Promise thuần
| Tiêu chí  | Async / Await | Promise |
| --------- | ------------- | ------- |
| Dễ đọc    | ⭐⭐⭐⭐⭐         | ⭐⭐⭐     |
| Debug     | Dễ            | Khó     |
| Phổ biến  | Rất cao       | Cao     |
| Dự án lớn | Khuyến nghị   | Ít dùng |
