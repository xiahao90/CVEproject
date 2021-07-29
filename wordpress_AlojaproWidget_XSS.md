# Alojapro Widget<=1.1.15 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The plugin doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Affects Plugins
    Alojapro Widget<=1.1.15
    https://cn.wordpress.org/plugins/alojapro-widget/
## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,Use the Alojapro Widget option on the sidebar menu to configure the widget parameters,Edit the "Custom CSS" text area to 
```
</style>
<script>
setTimeout("alert('1')",3000)
</script>
<style>
```
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210729181407.png "Wordpress plugin Alojapro Widget XSS")

2,Add the shortcode [alojapro-widget-block] on the content of a page/post/etc. to add the plugin into a page
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210729181416.png "Wordpress plugin Alojapro Widget XSS")

3,Preview article
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210729181423.png "Wordpress plugin Alojapro Widget XSS")
