# Highlight<=0.9.2 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The plugin doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Affects Plugins
    Highlight<=0.9.2
    https://cn.wordpress.org/plugins/highlight/
## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,Edit the "Highlight"->"Settings" select "Enable Highlight"
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730140927.png "Wordpress plugin Splash header XSS")
2,Edit the "Highlight"->"Custom css"  text area to "</style><script>setTimeout("alert('1')", 3000 )</script>"
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730140948.png "Wordpress plugin Splash header XSS")
3,Add the shortcode "[highlight-scroll] your expected text here [/highlight-scroll]" on the content of a page/post/etc. to add the plugin into a page
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730141007.png "Wordpress plugin Splash header XSS")
4,Visit the admin home page. We can see the alert page.
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730141015.png "Wordpress plugin Splash header XSS")
