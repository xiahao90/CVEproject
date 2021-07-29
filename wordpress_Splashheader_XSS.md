# Splash header<=1.20.1 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The plugin doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Affects Plugins
    Splash header<=1.8.8
    https://cn.wordpress.org/plugins/splash-header/
## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
Edit the "Splash Header"->"Plugin Settings"->"Welcome note" text area to "<script>alert(12)</script>1212121212121212"
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210729152014.png "Wordpress plugin Splash header XSS")
Visit the admin home page. We can see the alert page.
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210729152024.png "Wordpress plugin Splash header XSS")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210729152032.png "Wordpress plugin Splash header XSS")
