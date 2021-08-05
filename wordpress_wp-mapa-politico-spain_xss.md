# WP Mapa Politico España<=3.6.2 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The plugin doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Affects Plugins
    WP Mapa Politico España<=3.6.2
    [https://cn.wordpress.org/plugins/wp-mapa-politico-spain/](https://cn.wordpress.org/plugins/wp-mapa-politico-spain/)
## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,add the "WP Mapa Politico"->"Mapa"->"A Coruña" text area to ""><script>alert(2)</script>" click the "guardian cambios"
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210805143902.png "Wordpress plugin XSS")
2,Visit the content of a page/post/etc. We can see the alert page.
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210805143909.png "Wordpress plugin XSS")
