# youForms free for CopeCart<=1.0.5 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The plugin doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Affects Plugins
    youForms free for CopeCart<=1.0.5
    https://cn.wordpress.org/plugins/youforms-free-for-copecart/
## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,Edit the "youForms free"->"Add new"->"Button text:" text area to "</style><script>setTimeout("alert('17')", 3000 )</script>"
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730175748.png "Wordpress plugin Splash header XSS")
2,Visit the admin home page. We can see the alert page.
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730175756.png "Wordpress plugin Splash header XSS")
