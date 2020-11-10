---
weight: 4
title: "Lab 8. Tạo 10 mẫu tin (nhập dữ liệu) cho 10 sinh viên. Sau đó thực hiện các thao tác CRUD (Create, Read, Update, Delete) trên dữ liệu mẫu"
date: 2020-11-06T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Hữu Thành"
authorLink: "https://www.facebook.com/OGCN01"
description: "This article shows the basic Markdown syntax and format."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Lab08", "HQTCSDL", "CRUD"]
categories: ["Hệ quản trị CSDL"]

lightgallery: true
---
thực hiện các thao tác CRUD (Create, Read, Update, Delete) trên dữ liệu mẫu.

<!--more-->

### 1. SQLServer, MySQL
- C (Create): tạo 10 mẫu tin cho 10 sinh viên:
```sql
insert into sinhvien (MaSV, TenSV, NamSinh, Diem1, Diem2, Diem3, Email, Dienthoai) values
('m01', N'Huỳnh Lê Hữu Thành', '1999', 7, 8, 9, 'huuthanh@gmail.com','0789000xxxx'),
('m02', N'Nguyễn Văn Tèo A', '1999', 7, 8, 9,'huuthanh@gmail.com','0789000xxxx'),
('m03', N'Nguyễn Văn Tèo B', '1999', 7, 8, 9,'huuthanh@gmail.com','0789000xxxx'),
('m04', N'Nguyễn Văn Tèo C', '1999', 7, 8, 9,'huuthanh@gmail.com','0789000xxxx'),
('m05', N'Nguyễn Văn Tèo D', '1999', 7, 8, 9,'huuthanh@gmail.com','0789000xxxx'),
('m06', N'Nguyễn Văn Tèo E', '1999', 7, 8, 9,'huuthanh@gmail.com','0789000xxxx'),
('m07', N'Nguyễn Văn Tèo F', '1999', 7, 8, 9,'huuthanh@gmail.com','0789000xxxx'),
('m08', N'Nguyễn Văn Tèo G', '1999', 7, 8, 9,'huuthanh@gmail.com','0789000xxxx'),
('m09', N'Nguyễn Văn Tèo H', '1999', 7, 8, 9,'huuthanh@gmail.com','0789000xxxx'),
('m10', N'Nguyễn Văn Tèo I', '1999', 7, 8, 9,'huuthanh@gmail.com','0789000xxxx'); 
go
```

- R (Read): đọc dữ liệu sinh viên
```sql
select * from sinhvien
```
![read](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fread.png?alt=media&token=58116bda-2607-4c80-be68-9665f9bfa9aa)


- U (Update): cập nhật điểm sinh viên
```sql
update sinhvien set TenSV= N'Dang Tran Huu Nhan', Diem1 = 8 , Diem2 = 8, Diem3 = 8 where MaSV = 'm02'; 
```
![Update](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fupdate.png?alt=media&token=abbb54cf-c556-444d-b819-48995a19e1e4)


- D (Delete): xoá 1 sinh viên nào đó
```sql
delete from sinhvien where(MaSV = 'm01');
```
![delete](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fdelete.png?alt=media&token=7ecb2972-328b-4326-bb99-8f2e8ca4163d)


### 2. MongoDB
- C (Create): tạo 10 mẫu tin cho 10 sinh viên:
```json
db.getCollection('SinhVien').insertMany([{ 
  MSSV: '1710289', Hoten: 'Phan Quốc Trung', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1710289@dlu.edu.vn', DienThoai: '0349981228'
}, {
  MSSV: '1710233', Hoten: 'Đặng Trần Hữu Nhân', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1710233@dlu.edu.vn', DienThoai: '0349981228'
}, {
  MSSV: '1710196', Hoten: 'Nguyễn Đăng Khoa', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1710196@dlu.edu.vn', DienThoai: '0349981228'
}, {
  MSSV: '1714234', Hoten: 'Hứa Đình Doanh', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1714234@dlu.edu.vn', DienThoai: '0349981228'
}, {
  MSSV: '1710264', Hoten: 'Huỳnh Lê Hữu Thành', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1710264@dlu.edu.vn', DienThoai: '0349981228'
}, {
  MSSV: '1710144', Hoten: 'Nguyễn Đức Đề', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1710144@dlu.edu.vn', DienThoai: '0349981228'
}, {
  MSSV: '1710156', Hoten: 'Phạm Bá Xuân Duy', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1710156@dlu.edu.vn', DienThoai: '0349981228'
}, {
  MSSV: '1710204', Hoten: 'Bùi Đức Hoàng Lâm', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1710204@dlu.edu.vn', DienThoai: '0349981228'
}, {
  MSSV: '1710303', Hoten: 'Phạm Hoàng Việt', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1710303@dlu.edu.vn', DienThoai: '0349981228'
}, {
  MSSV: '1710285', Hoten: 'Lê Anh Trí', Namsinh: 1999, DiemMon1: 8, DiemMon2: 7, DiemMon3: 10, Email: '1710289@dlu.edu.vn', DienThoai: '0349981228'
}])
```


- R (Read): đọc dữ liệu sinh viên
```js
use quanlysinhvien;
db.getCollection('SinhVien').find({});
```



- U(Update): cập nhật điểm sinh viên
```ts
use quanlysinhvien;
db.getCollection('SinhVien').updateOne(
  { MSSV: '1710289' }, // query parameter
  $set: {
    DiemMon1: 10,
    DiemMon2: 9,
    DiemMon3: 10
  }
)
```



- D (Delete): xoá 1 sinh viên nào đó
```ts
db.getCollection('SinhVien').remove({
  MSSV: '1710289'
})
```
