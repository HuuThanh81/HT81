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

tags: ["Question", "PHP", "String"]
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


### 2. Chuẩn hóa một chuỗi.
Viết hàm để chuẩn hóa một chuỗi bất kỳ.


Một chuỗi gọi là chuẩn khi:
– Không có khoảng trắng ở đầu và cuối chuỗi
– Giữa các từ chỉ có một khoảng trắng
– Viết hoa kí tự đầu tiên của chuỗi, của danh từ riêng
– Các kí tự còn lại ở dạng chữ thường


Ví dụ:
Chuỗi nhập vào là : ' nGuyeN VAn tEo '
Kết quả sau khi chuẩn hóa sẽ là 'Nguyen Van Teo'


### Demo
>App source Repl.it: https://repl.it/@HuuThanh81/Ex2-String#index.php


{{< iframe src="https://ex2-string.huuthanh81.repl.co/?lite=true" >}}


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
    $LastName = '';
    $FirstName = '';
    $result = '';
    if(isset($_POST["first"]) && isset($_POST["last"])){
        $LastName = $_POST["last"];
        $FirstName = $_POST["first"];
        $F = chop(trim(ucfirst(strtolower($LastName))));
        $L = chop(trim(ucfirst(strtolower($FirstName))));
        $result = "$L $F";
   }

    ?>
    <form method="POST">
    <input type="text" placeholder="First Name" name="first"></input>
    <input type="text" placeholder="Last Name" name="last"></input>
    <button type="submit">submit</button>
    </form>

    <?php
    echo '<p>'.$result.'</p>';
    ?>
    
</body>
</html>
```


### 3. Viết chương trình đọc số gồm ba chữ số.
Ví dụ:
100 > một trăm
101 > một trăm linh một
111 > một trăm mười một
121 > một trăm hai mươi mốt
105 > một trăm linh năm
115 > một trăm mười lăm
145 > một trăm bốn mươi lăm


### 4. Viết chương trình đọc số gồm mười hai chữ số.
Ví dụ:
123 456 789 000 > một trăm hai mươi ba tỉ bốn trăm năm mươi sáu triệu bảy trăm tám mươi chín ngàn.


### Demo

>App source repl.it: https://repl.it/@HuuThanh81/Ex3-String#index.php


{{< iframe src="https://Ex3-String.huuthanh81.repl.co/?lite=true" >}}


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
    $number = '';
if(isset($_POST["Nb"])){
    $number = $_POST["Nb"];
}

    function convert_number_to_words($number) {
        $hyphen      = ' ';
        $conjunction = '  ';
        $separator   = ' ';
        $negative    = 'âm ';
        $decimal     = ' phẩy ';
        $dictionary  = array(
        0                   => 'Không',
        1                   => 'Một',
        2                   => 'Hai',
        3                   => 'Ba',
        4                   => 'Bốn',
        5                   => 'Năm',
        6                   => 'Sáu',
        7                   => 'Bảy',
        8                   => 'Tám',
        9                   => 'Chín',
        10                  => 'Mười',
        11                  => 'Mười một',
        12                  => 'Mười hai',
        13                  => 'Mười ba',
        14                  => 'Mười bốn',
        15                  => 'Mười năm',
        16                  => 'Mười sáu',
        17                  => 'Mười bảy',
        18                  => 'Mười tám',
        19                  => 'Mười chín',
        20                  => 'Hai mươi',
        30                  => 'Ba mươi',
        40                  => 'Bốn mươi',
        50                  => 'Năm mươi',
        60                  => 'Sáu mươi',
        70                  => 'Bảy mươi',
        80                  => 'Tám mươi',
        90                  => 'Chín mươi',
        100                 => 'trăm',
        1000                => 'ngàn',
        1000000             => 'triệu',
        1000000000          => 'tỷ',
        1000000000000       => 'nghìn tỷ',
        1000000000000000    => 'ngàn triệu triệu',
        1000000000000000000 => 'tỷ tỷ'
    );

    if (!is_numeric($number)) { //kiểm tra biến $number có phải là số.
        return false;
    }
    
    if (($number >= 0 && (int) $number < 0) || (int) $number < 0 - PHP_INT_MAX) {
    // overflow
        trigger_error(
        '   convert_number_to_words only accepts numbers between -' . PHP_INT_MAX . ' and ' . PHP_INT_MAX,
            E_USER_WARNING
            );
    return false;
    }
    
    if ($number < 0) {
        return $negative . convert_number_to_words(abs($number));
        }
    
        $string = $fraction = null;
        
        if (strpos($number, '.') !== false) {
        list($number, $fraction) = explode('.', $number);
    }
    
    switch (true) {
        case $number < 21:
            $string = $dictionary[$number];
            break;
        case $number < 100:
            $tens   = ((int) ($number / 10)) * 10;
            $units  = $number % 10;
            $string = $dictionary[$tens];
            if ($units) {
                $string .= $hyphen . $dictionary[$units];
            }
            break;
        case $number < 1000:
            $hundreds  = $number / 100;
            $remainder = $number % 100;
            $string = $dictionary[$hundreds] . ' ' . $dictionary[100];
            if ($remainder) {
                $string .= $conjunction . convert_number_to_words($remainder);
            }
            break;
        default:
            $baseUnit = pow(1000, floor(log($number, 1000)));
            $numBaseUnits = (int) ($number / $baseUnit);
            $remainder = $number % $baseUnit;
            $string = convert_number_to_words($numBaseUnits) . ' ' . $dictionary[$baseUnit];
            if ($remainder) {
                $string .= $remainder < 100 ? $conjunction : $separator;
                $string .= convert_number_to_words($remainder);
        }
        break;
        }
    
    if (null !== $fraction && is_numeric($fraction)) {
        $string .= $decimal;
        $words = array();
        foreach (str_split((string) $fraction) as $number) {
        $words[] = $dictionary[$number];
        }
        $string .= implode(' ', $words);
    }
    
    return $string;
    }
    ?>

    <form method="POST">
        <input type="number" name="Nb" placeholder="Typing your number" value="<?php echo $number;?>">
        <button type="submit">Submit</button>
    </form>

    <?php
        $word = convert_number_to_words($number);
        echo '<p>'.$word.'</p>';
    ?>
</body>
</html>

```