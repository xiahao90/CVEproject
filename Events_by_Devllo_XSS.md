# Events by Devllo<=1.0.4.2 Authenticated Stored Cross-Site Scripting(XSS)
## Description
    The plugin doesn't properly sanitise POST parameter, which result into a Stored Cross-Site Scripting(XSS).
## Affects Plugins
    Events by Devllo<=1.0.4.2
    https://cn.wordpress.org/plugins/devllo-events/
## Author
    xiahao@webray.com.cn inc  
## Proof of Concept
1,add the "Events"->"Add Event"->"Add New"->"添加标题" text area to "events2021-9-24<script>setTimeout("alert('1')",3000)</script>" ，Then publish
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210924174011.png "Events by Devllo<=1.0.4.2 Authenticated Stored Cross-Site Scripting(XSS)")

2,Get the link and open it.
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210924174031.png "Events by Devllo<=1.0.4.2 Authenticated Stored Cross-Site Scripting(XSS)")
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210924174116.png "Events by Devllo<=1.0.4.2 Authenticated Stored Cross-Site Scripting(XSS)")
