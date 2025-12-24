---
title: "Mảng và Object trong JavaScript"
date: 2025-12-22
draft: false
tags: ["js-co-ban"]
---

## 1. Mảng và Object là gì?

Trong JavaScript:
- **Mảng (Array)** dùng để lưu **danh sách dữ liệu**
- **Object** dùng để lưu **dữ liệu có cấu trúc**

👉 Đây là **2 kiểu dữ liệu quan trọng nhất** khi làm web thực tế.

---

## 2. Mảng (Array)

### 2.1. Khai báo mảng

```js
let numbers = [1, 2, 3, 4];
let fruits = ["Táo", "Cam", "Chuối"];
👉 Mảng bắt đầu từ index = 0

fruits[0]; // "Táo"

2.2. Độ dài mảng
fruits.length; // 3

2.3. Thêm / xoá phần tử
fruits.push("Xoài");    // thêm cuối
fruits.pop();           // xoá cuối
fruits.unshift("Nho");  // thêm đầu
fruits.shift();         // xoá đầu

2.4. Duyệt mảng
for (let fruit of fruits) {
  console.log(fruit);
}


Hoặc:

fruits.forEach(item => {
  console.log(item);
});

2.5. Một số hàm mảng rất hay dùng
let numbers = [1, 2, 3, 4, 5];

numbers.map(x => x * 2);        // [2,4,6,8,10]
numbers.filter(x => x > 2);     // [3,4,5]
numbers.find(x => x === 3);     // 3
numbers.includes(4);            // true


📌 Các hàm này không làm thay đổi mảng gốc (trừ vài hàm đặc biệt)

3. Object
3.1. Khai báo Object
let student = {
  name: "Đạt",
  age: 20,
  major: "CNTT"
};

3.2. Truy cập thuộc tính
student.name;        // "Đạt"
student["age"];      // 20

3.3. Thêm / sửa / xoá thuộc tính
student.email = "dat@gmail.com";
student.age = 21;
delete student.major;

3.4. Duyệt Object
for (let key in student) {
  console.log(key, student[key]);
}

4. Mảng chứa Object (cực kỳ phổ biến)
let students = [
  { name: "An", age: 20 },
  { name: "Bình", age: 21 },
  { name: "Đạt", age: 22 }
];

Lọc sinh viên trên 20 tuổi:
let result = students.filter(s => s.age > 20);

5. Destructuring (ES6)
let { name, age } = student;
console.log(name, age);


Với mảng:

let [a, b] = numbers;

6. Spread Operator (...)
let newFruits = [...fruits, "Ổi"];


Với object:

let newStudent = { ...student, age: 23 };


👉 Rất hay dùng khi làm React / API

7. So sánh mảng & object
|          | Mảng      | Object              |
| -------- | --------- | ------------------- |
| Lưu      | Danh sách | Dữ liệu có cấu trúc |
| Truy cập | Index     | Key                 |
| Thứ tự   | Có        | Không bắt buộc      |
8. Ví dụ thực tế
Tính tổng điểm sinh viên:
let scores = [8, 7, 9];

let total = scores.reduce((sum, s) => sum + s, 0);

9. Lỗi thường gặp

❌ Truy cập sai index
❌ Nhầm for...in và for...of
❌ Thay đổi mảng gốc không kiểm soát