# youForms free for CopeCart<=1.0.5 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The plugin doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Affects Plugins
    youForms free for CopeCart<=1.0.5
    https://cn.wordpress.org/plugins/youforms-free-for-copecart/
## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,Edit the "youForms free"->"Add new"->"Button text:" text area to "<script>setTimeout("alert('17')", 3000 )</script>"
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730175748.png "Wordpress plugin Splash header XSS")
2,Visit the plugin in details page. We can see the alert page.
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730175756.png "Wordpress plugin Splash header XSS")
3,Add the shortcode [form_copecart id="90"] on the content of a page/post/etc. to add the plugin into a page
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730180816.png "Wordpress plugin Splash header XSS")
4,Visit the content of a page/post/etc. We can see the alert page.
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210730180946.png "Wordpress plugin Splash header XSS")
