# emlog<=pro-1.2.2 Stored Cross-Site Scripting(XSS)
## Description
    The system Client doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Vendor Homepage
    https://www.emlog.net/
    https://github.com/emlog/emlog

## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,Register your account on the website and sign in
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/16512144725611.png "emlog<=pro-1.2.2 Stored Cross-Site Scripting(XSS)")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/16512145593882.png "emlog<=pro-1.2.2 Stored Cross-Site Scripting(XSS)")
2,Add articles and write attack code, and then submit
```
<script>alert(123);</script>
```
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/16512147091558.png "emlog<=pro-1.2.2 Stored Cross-Site Scripting(XSS)")
3,The super administrator will trigger the attack code when auditing the article
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/16512149073952.png "emlog<=pro-1.2.2 Stored Cross-Site Scripting(XSS)")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/1651214938416.png "emlog<=pro-1.2.2 Stored Cross-Site Scripting(XSS)")
