# automad<=1.10.9 Stored Cross-Site Scripting(XSS)
## Description
    The system Client doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Vendor Homepage
    https://github.com/marcantondahmen/automad
    https://automad.org/

## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,After installing the program, log in to the background system, modify the website title and inject attack code, and then submit
```
Home</title><script>alert("home")</script><title>
```
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/16512246203215.png "automad<=1.10.9 Stored Cross-Site Scripting(XSS)")

2,Visiting the home page of the website will trigger the code
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/16512246561844.png "automad<=1.10.9 Stored Cross-Site Scripting(XSS)")
