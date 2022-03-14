# CLTPHP<=6.0 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The system Client doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Vendor Homepage
    https://show.cltphp.com/
    https://gitee.com/chichu/cltopen
    https://github.com/cltphp/cltphp

## Author
    webraybtl@webray.com.cn inc  
## Proof of Concept
1,The injection point is the user name and location filled in when registering a user 
```
<script>alert(1);</script>
```
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220314144707.png "CLTPHP<=6.0 Authenticated Stored Cross-Site Scripting(XSS)")

2,Log in to the management terminal to view the user list
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20220314144725.png "CLTPHP<=6.0 Authenticated Stored Cross-Site Scripting(XSS)")
