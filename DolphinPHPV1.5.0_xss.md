# DolphinPHP<=1.5.0 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The system Client doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Vendor Homepage
    https://dolphinphp.com/
    https://github.com/caiweiming/DolphinPHP

## Author
    webraybtl@webray.com.cn inc  
## Proof of Concept
1,After the system installation is completed, log in to the background
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220317154815.png "DolphinPHP<=1.5.0 Authenticated Stored Cross-Site Scripting(XSS)")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220317154848.png "DolphinPHP<=1.5.0 Authenticated Stored Cross-Site Scripting(XSS)")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220317154902.png "DolphinPHP<=1.5.0 Authenticated Stored Cross-Site Scripting(XSS)")

2,Insert a danger code where the nickname is modified in the personal settings
```
<script>alert(1);</script>超级管理员
```
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220317155039.png "DolphinPHP<=1.5.0 Authenticated Stored Cross-Site Scripting(XSS)")

3,Click "user" - > "permission management" - > "user management" to execute the code
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220317155317.png "DolphinPHP<=1.5.0 Authenticated Stored Cross-Site Scripting(XSS)")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220317155341.png "DolphinPHP<=1.5.0 Authenticated Stored Cross-Site Scripting(XSS)")
