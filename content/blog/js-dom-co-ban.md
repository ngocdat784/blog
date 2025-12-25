---
title: "DOM cơ bản trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-dom"]
---

## 1. DOM là gì?

**DOM (Document Object Model)** là mô hình đối tượng biểu diễn **toàn bộ trang HTML** dưới dạng cây (tree).

👉 Nhờ DOM, JavaScript có thể:
- Truy cập HTML
- Thay đổi nội dung
- Thay đổi style
- Bắt sự kiện người dùng

📌 **Không có DOM → JS không làm được web động**

---

## 2. Cấu trúc DOM dạng cây

```js
<html>
  <body>
    <h1>Tiêu đề</h1>
    <p>Nội dung</p>
  </body>
</html>
```
👉 Trình duyệt hiểu như:
```js
document
 └── html
     └── body
         ├── h1
         └── p
         
```
3. Truy cập phần tử HTML
🔹 3.1. getElementById
```js
<h1 id="title">Hello DOM</h1>

let title = document.getElementById("title");
console.log(title);
```
🔹 3.2. getElementsByClassName
```js
<p class="text">Đoạn 1</p>
<p class="text">Đoạn 2</p>

let texts = document.getElementsByClassName("text");

```
👉 Trả về HTMLCollection

🔹 3.3. getElementsByTagName
```js
let paragraphs = document.getElementsByTagName("p");
```
🔹 3.4. querySelector (rất nên dùng)
```js
let title = document.querySelector("#title");
```

👉 Dùng CSS selector

🔹 3.5. querySelectorAll
```js
let items = document.querySelectorAll(".text");

```
👉 Trả về NodeList

4. Thay đổi nội dung HTML
🔹 innerText
```js
title.innerText = "Nội dung mới";
```
🔹 innerHTML
```js
title.innerHTML = "<span>DOM</span>";
```

⚠️ Cẩn thận XSS khi dùng innerHTML

5. Thay đổi thuộc tính
```js
let img = document.querySelector("img");

img.src = "image.png";
img.alt = "Ảnh minh hoạ";

```
Hoặc:
```js
img.setAttribute("src", "image.png");
```
6. Thay đổi CSS bằng JavaScript
🔹 Inline style
```js
title.style.color = "red";
title.style.fontSize = "32px";
```
🔹 ClassList (khuyên dùng)
```js
title.classList.add("active");
title.classList.remove("active");
title.classList.toggle("active");

```
✔ Sạch
✔ Dễ quản lý

7. Tạo và xoá phần tử
🔹 Tạo phần tử
```js
let p = document.createElement("p");
p.innerText = "Đoạn mới";
document.body.appendChild(p);
```
🔹 Xoá phần tử
```js
p.remove();
```
8. DOM và thời điểm chạy JS

❌ Lỗi thường gặp:
```js
document.getElementById("title"); // null
```

👉 Do JS chạy trước khi HTML load

✔ Cách xử lý:
```js
document.addEventListener("DOMContentLoaded", function() {
  // code DOM ở đây
});
```
9. Ví dụ thực tế
Đổi tiêu đề khi click:
```js
let btn = document.querySelector("button");

btn.onclick = function() {
  title.innerText = "Bạn vừa click";
};
```
10. So sánh nhanh
| Cách           | Ghi chú   |
| -------------- | --------- |
| getElementById | Nhanh     |
| querySelector  | Linh hoạt |
| innerText      | An toàn   |
| innerHTML      | Cẩn thận  |
| classList      | Nên dùng  |
11. Lỗi thường gặp

❌ Sai selector
❌ DOM chưa load
❌ Lạm dụng innerHTML
