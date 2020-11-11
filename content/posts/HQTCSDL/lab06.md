---
weight: 4
title: "Lab 6. Tải và cài đặt MySQL trên Docker"
date: 2020-11-07T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Hữu Thành"
authorLink: "https://www.facebook.com/OGCN01"
description: "This article shows the basic Markdown syntax and format."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Lab05", "HQTCSDL", "MySQL"]
categories: ["Hệ quản trị CSDL"]

lightgallery: true
---
Tìm hiểu và cài đặt MySQL trên Docker.

<!--more-->

### 1. Cài đặt MySQL Image:
Chạy câu lệnh sau trên cmd hay windowpowershell.
```
docker run -it -d --name mysql01 -v /data/mysql/mysql01:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 mysql:latest
```


Hướng dẫn các tham số:



– “docker run“: câu lệnh để chạy 1 image và bắt đầu 1 container. Container là một process sử dụng 1 image là nội dung bên trong.
– “-it“: tham số để cho phép thao tác về sau như can thiệp vào container để thực thi các câu lệnh hệ thống.
– “-d“: tham số để nói sau khi thực hiện câu lệnh trên thì cho nó chạy background và con trỏ vẫn ở host hiện tại.
– “–name mysql01“: đặt tên cho cái container này. Bởi vì có thể tạo nhiều container từ chung 1 image (đây chính là điểm ưu điểm của Docker), mỗi container cần có cái tên để dễ làm việc, không thì docker sẽ tự tạo 1 cái tên ngẫu nhiên. Và lưu ý, không được phép có 2 container cùng 1 tên.
– “-v /data/mysql/mysql01:/var/lib/mysql“: cho phép mount volume (link thư mục) từ bên trong container ra một thư mục bên ngoài máy đang chạy. Thử tưởng tượng, nếu không sử dụng volume để mapping thư mục, khi container này stop và bị xóa thì toàn bộ dữ liệu trong container cũng bị mất. Do đó, phải mapping ra thư mục bên ngoài để khi container bị xóa thì dữ liệu vẫn còn. Và khi start 1 container mới thì sẽ có dữ liệu trước đó. tham số “-v” là một tham số rất quan trọng Trong ví dụ này thì thư mục “/data/mysql/mysql01” là thư mục trên máy và “/var/lib/mysql” là chuỗi cố định được cài đặt sẵn trong image.
– “-e MYSQL_ROOT_PASSWORD=123456“: Tham số “-e” sẽ set một biến môi trường. Ở đây, set biến môi trường làm password root cho mysql server. Thường mỗi image đều có ghi chú về các biến môi trường và công dụng của nó khi chạy một image.
– “mysql:latest“: tên image và tag phiên bản của image sẽ chạy.



Truy cập vào MySQL container:

```
docker exec -it mysql01 mysql -uroot -p
```



### 2. Kết nối với MySQL Workbench:
![MySQL conect](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fmysql-connect.png?alt=media&token=5be96d82-94db-4325-bb5b-37ec88c6a9e6)

