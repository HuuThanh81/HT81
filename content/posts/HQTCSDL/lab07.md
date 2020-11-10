---
weight: 4
title: "Lab 7. Sử dụng DDL định nghĩa dữ liệu cho đối tượng Sinh Viên"
date: 2020-11-06T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Hữu Thành"
authorLink: "https://www.facebook.com/OGCN01"
description: "This article shows the basic Markdown syntax and format."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Lab07", "HQTCSDL", "DDL"]
categories: ["Hệ quản trị CSDL"]

lightgallery: true
---
Sử dụng DDL Định nghĩa dữ liệu cho đối tượng Sinh Viên trong SQL server, My SQL và MongoDB.

<!--more-->
### Định nghĩa dữ liệu cho đối tượng Sinh Viên trong SQL server, My SQL và MongoDB.
- Ví dụ: đối tượng Sinh Viên gồm các thông tin sau: MSSV, Họ Tên, Năm Sinh, Điểm môn 1, Điểm môn 2, Điểm môn 3, Email, Điện thoại.

#### 1. SQLServer

```sql
create table SinhVien (
  MSSV char(8) primary key,
  Hoten nvarchar(30) not null,
  Namsinh int,
  DiemMon1 float,
  DiemMon2 float,
  DiemMon3 float,
  Email char(30),
  Dienthoai char(11)
)
```
![DDL SQLServer](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2FDDL%20SQLServer.png?alt=media&token=f178cde3-0399-4347-a398-8fae6fbef58f)



#### 2. MongoDB
- Ta chỉ có thể định nghĩa đối tượng Sinh viên cho mongodb thông qua schema của mongoose (thư viện npm trong nodejs)
```ts
import mongoose from 'mongoose';
const { Schema } = mongoose;

const SinhVienSchema = new Schema({
  MSSV: String,
  Hoten: String,
  Namsinh: Number,
  DiemMon1: Number,
  DiemMon2: Number,
  DiemMon3: Number,
  Email: String,
  Dienthoat: String
});
```

```js
use quanlysinhvien;
db.createCollection("SinhVien");
```



#### 3. Mysql
```sql
create table SinhVien (
  MSSV char(8) primary key,
  Hoten varchar(30) not null,
  Namsinh int,
  DiemMon1 float,
  DiemMon2 float,
  DiemMon3 float,
  Email char(30),
  Dienthoai char(11)
)
```
![DDL MySQL](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fphpmyadmin.png?alt=media&token=c7e97b40-af24-4862-9b42-e625624ab1bd)