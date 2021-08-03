# Availability Calendar<=1.2 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The plugin doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Affects Plugins
    Availability Calendar<=1.2
    https://cn.wordpress.org/plugins/availability-calendar/
## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,add the "Availability Calendar"->"Category"->"Add New"->"Category Name" text area to "<script>setTimeout("alert(1)", 3000 )</script>1"
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210803175426.png "Wordpress plugin Splash header XSS")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210803175437.png "Wordpress plugin Splash header XSS")
2,Add the shortcode [availabilitycalendar category="2"] on the content of a page/post/etc. to add the plugin into a page
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210803175443.png "Wordpress plugin Splash header XSS")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210803175448.png "Wordpress plugin Splash header XSS")
3,Visit the content of a page/post/etc. We can see the alert page.
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210803175453.png "Wordpress plugin Splash header XSS")

