---
weight: 4
title: "String - Tách chuỗi, chuẩn hóa, đọc chữ"
date: 2020-10-20T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Hữu Thành"
authorLink: "https://www.facebook.com/OGCN01"
description: "This article shows the basic Markdown syntax and format."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Question", "PHP", "Array"]
categories: ["PHP Programming - Basics"]

lightgallery: true
---

Thực hành với String.

<!--more-->

### 1. Tách chuỗi.
Cho chuỗi URL ='http://210.245.126.171/Music/NhacTre/TinhYeu_LyMaiTrang/wma32/06_BienTham_TinhYeu_LyMaiTrang.wma'


Hãy viết chương trình để lấy ra được các thông tin: mã bài hát (ID), tên bài hát (Name), tên album
(Album), tên ca sỹ trình bày (Singer), và loại tập tin (Type).


Ví dụ:
– ID: 06
– Name: Bien Tham
– Album: Tinh Yeu
– Singer: Ly Mai Trang
– Type: wma


### Demo
>App source Repl.it: https://repl.it/@HuuThanh81/Ex-String#index.php


{{< iframe src="https://ex-string.huuthanh81.repl.co/?lite=true" >}}



```php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
<?php
	$url 	= "http://210.245.126.171/Music/NhacTre/TinhYeu_LyMaiTrang/wma32/06_BienTham_TinhYeu_LyMaiTrang.wma";
	
	function format($str){ //chuyển thành viết hoa
		$result = $str[0];
		for($i = 1; $i < strlen($str); $i++){
			if(ctype_upper($str[$i])==true){
				$result .= " " . $str[$i];
			}else{
				$result .= $str[$i];
			}
		}
		return $result;
	}

	function getInfo($url){ 
		$index 	= strripos($url, "/"); //tìm vị trí xuất hiện / trong chuỗi
		$result = substr($url, $index+1); // hiển thị từ ở vị trí phía sau lần xuất hiện dấu /
		return $result;
	}
	
	$info 	= getInfo($url);
	
	$result = array();
	
	$arrayInfo	= explode("_", $info); // Chia chuỗi thành mảng
	
	// ID
	$result["id"]	= $arrayInfo[0];

	// TYPE
	$arrType		= explode(".", $arrayInfo[3]);
	$result["type"]	= $arrType[1];
	
	// NAME, AUDIO, SINGER
	$arrayInfo[3]	= $arrType[0];
	
	$result["singer"]	=	format($arrayInfo[3]);
	$result["name"]		=	format($arrayInfo[1]);
	$result["album"]	=	format($arrayInfo[2]);
	echo '<p>URL = '.$url.'</p>';
    echo '<p>ID: '.$result["id"].'</p>';
    echo '<p>Name: '.$result["name"].'</p>';
    echo '<p>Singer: '.$result["singer"].'</p>';
    echo '<p>Album: '.$result["album"].'</p>';
    echo '<p>Type: '.$result["type"].'</p>';
 ?>   
</body>
</html>
```