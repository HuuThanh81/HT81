---
weight: 4
title: "Lab 4. Tải và cài đặt SQL server trên Docker"
date: 2020-11-05T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Hữu Thành"
authorLink: "https://www.facebook.com/OGCN01"
description: "This article shows the basic Markdown syntax and format."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Lab04", "HQTCSDL", "SQLServer"]
categories: ["Hệ quản trị CSDL"]

lightgallery: true
---
Tìm hiểu và cài đặt MonoDB trên máy tính cục bộ.

<!--more-->
### Tải và cài đặt SQL server trên docker.
cài SQLServer khi sử dụng image
> docker pull mcr.microsoft.com/mssql/server:2017-latest

Để dữ liệu MSSQLServer không bị mất khi xóa Container cần tạo ra một ổ đĩa để ánh xạ vào container, ta tạo ổ đĩa đặt tên là vmssql.
- Đầu tiên ta phải tạo volume để chứa ánh xạ
```cmd
docker volume create device=path_in_host vmssql
```

-Giờ sẽ tạo/chạy container với thông số sau:
  *Đặt password cho tài khoản sa là Password789
  *Public xạ cổng 1433 vào container
  *Ánh xạ ổ đĩa vmssql vào thư mục /var/opt/mssql (nơi lưu DB)
  *Đặt tên container là c-mssql

- Tiếp theo tạo/chạy container với lệnh sau:
```cmd
docker run -e 'ACCEPT_EULA=Y' --name sqlserver -e 'SA_PASSWORD=Password789' -p 1433:1433 -v vmssql:/var/opt/mssql -d mcr.microsoft.com/mssql/server:2019-latest
```

- Để sử dụng mysql trên terminal
```cmd
docker exec -it -sqlserver bash
```

- Thực hiện kết nối SQL Server
```cmd
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P 'Password789'
```

![SqlServer in docker](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fsqlserver-docker.png?alt=media&token=a4b4218c-0320-4fb6-ba67-2509a411eda7)


Sử dụng Azure Data Studio để quản lý SQL Server trên docker dễ dàng

Tải về và cài đặt tại: [Azure Data Studio.](https://docs.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-2017)


Kết nối với MS SQL Server
![Setup](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fazure.png?alt=media&token=43873564-0098-441c-998a-a775d771ab32)


Tương tác với SQL Server trực quan
![connection success full](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fconnection-success.png?alt=media&token=fab0dce9-e743-4c79-b421-509b6ad6ef71)
