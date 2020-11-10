---
weight: 4
title: "Lab 3. Tải và cài đặt Mongo trên máy cục bộ"
date: 2020-11-05T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Hữu Thành"
authorLink: "https://www.facebook.com/OGCN01"
description: "This article shows the basic Markdown syntax and format."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Lab03", "HQTCSDL", "MongoDB"]
categories: ["Hệ quản trị CSDL"]

lightgallery: true
---
Tìm hiểu và cài đặt MonoDB trên máy tính cục bộ.

<!--more-->


### 1. Giới thiệu 
- MongoDB là một hệ quản trị cơ sở dữ liệu mã nguồn mở, là CSDL thuộc NoSql và được hàng triệu người sử dụng.
- MongoDB là một database hướng tài liệu (document), các dữ liệu được lưu trữ trong document kiểu JSON thay vì dạng bảng như CSDL quan hệ nên truy vấn sẽ rất nhanh.


### 2. Cài đặt Mongo
- link documentation install mongodb: https://docs.mongodb.com/manual/installation/

>Step by step install mongodb in docker

# Pull mongo image 
docker pull mongo 

# Run container from image mongo in background, publish 50001 host port to 27017 container port 
docker run --name mongoserver --restart=always -d -p 50001:27017 mongo


#------------------------- Refrence Commands ----------------------
# Show docker images 
docker images 

# Remove docker image 
docker rmi image_id

# Pull docker image 
docker pull image_name

# Display system-wide information
docker info	

#List constainers 
docker ps 

# List all containers 
docker ps -a 

# List container with filters - exited 
docker ps -a --filter 'exited=0'

# List container with filter name 
docker ps --filter "name=nostalgic"

# List container which are running 
docker ps --filter status=running

# list all running containers with their labels in a table format
docker ps --format "table {{.ID}}\t{{.Labels}}"

# Remove container 
docker rm container_name/container_id


# Run a command in a new container
docker run [OPTIONS]