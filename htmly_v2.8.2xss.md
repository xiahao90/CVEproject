# htmly<=v2.8.2 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The system Client doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Vendor Homepage
    https://www.htmly.com/
    https://github.com/danpros/htmly

## Author
    webraybtl@webray.com.cn inc  
## Proof of Concept
1,After logging in to the background, add an article and enter the XSS code 
```
<script>alert(1);</script>
```
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220315111618.png "htmly<=v2.8.2 Authenticated Stored Cross-Site Scripting(XSS)")

2,Visit the article after adding
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220315111636.png "htmly<=v2.8.2 Authenticated Stored Cross-Site Scripting(XSS)")
