---
weight: 4
title: "Lab 5. Tải và cài đặt Mongo trên Docker"
date: 2020-11-06T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Hữu Thành"
authorLink: "https://www.facebook.com/OGCN01"
description: "This article shows the basic Markdown syntax and format."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Lab05", "HQTCSDL", "MongoDB"]
categories: ["Hệ quản trị CSDL"]

lightgallery: true
---
Tìm hiểu và cài đặt MonoDB trên Docker.

<!--more-->

>Step by step intstall MongoDB in Docker 

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

# Run container with name mongoserver from image mongo intractive shell 
docker run -it --name mongoserver mongo bash

# Run container in background and print container ID
docker run -it --name mongoserver -d mongo bash

# Publish a container’s port(s) to the host -p host_port:container_port
docker run --name mongoserver --restart=always -d -p 27017:27017 mongo

# bash into the container
sudo docker exec -i -t mongoserver bash

# stop container
docker stop mongoserver

# start container
docker start mongoserver

# Cài đặt thành công: 
![setup](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fmongodb-in-docker.png?alt=media&token=a0e4e740-11ae-43c6-9672-f14fd920dc42)

# kết nối mongodb
![connect](https://firebasestorage.googleapis.com/v0/b/blog-7d3a3.appspot.com/o/HQTCSDL%2Fconnect-mogo.png?alt=media&token=04899075-df1e-4528-a893-67a505eefee2)