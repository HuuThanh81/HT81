---
weight: 4
title: "Math-Time - Thao tác với math và time"
date: 2020-11-12T21:57:40+08:00
lastmod: 2020-01-01T16:45:40+08:00
draft: false
author: "Hữu Thành"
authorLink: "https://www.facebook.com/OGCN01"
description: "This article shows the basic Markdown syntax and format."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Question", "PHP", "Math-Time"]
categories: ["PHP Programming - Basics"]

lightgallery: true
---

Biết cách thao tác với một số hàm toán học, thời gian.

<!--more-->

### 1. Viết chương trình cho phép người dùng nhập vào một phân số, thực hiện tối giản phân số và xuất ra kết quả.

>Source app Repl.it: https://repl.it/@HuuThanh81/Ex1-Math-Time#index.php

{{< iframe src="https://Ex1-Math-Time.huuthanh81.repl.co/?lite=true" >}}

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
            $fraction = '';
            if(isset($_POST["PS"])){
                $fraction = $_POST["PS"];
           }
            
            $arrFraction = explode('/', $fraction);
            $ts = $arrFraction[0];
            $ms = $arrFraction[1];
            $x ='';
            
            function UCLN($n1, $n2) {
                        for($i = 1; $i <= $n1; $i++) {
                                    if($n1 % $i == 0) { $uclnN1[] = $i; }
                        }
                        for($i = 1; $i <= $n2; $i++) {
                                    if($n2 % $i == 0) { $uclnN2[] = $i; }
                        }
                        $temp = array_intersect($uclnN1, $uclnN2);
                        $result = max($temp);
                        return $result;
            
                    }

            $ucln = UCLN($ts, $ms);
            $ts = $ts/$ucln;
            $ms = $ms/$ucln;
?>

    <form method="POST">
    <input type="Text" name="PS" placeholder="Nhập phân số" value="<?php echo $fraction;?>">
    <button type="submit">Ok</button>
    </form>
    <?php
        echo '<p>'.$ts.'/'.$ms.'</p>';
    ?>
</body>
</html>
```