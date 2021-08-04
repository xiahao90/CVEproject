# Availability Calendar<=1.2 - Authenticated SQL Injection
## Description
    When the plug-in uses short code, Unfiltered parameters, resulting in SQL Injection issue.  
## Affects Plugins
    Availability Calendar<=1.2 (the latest version at this time)
    https://cn.wordpress.org/plugins/availability-calendar/
## Author
    xiahao@webray.com.cn inc 
## Detail
    The issue is occured at file availability-calendar/public/includes/frontend.php. line 59.Unfiltered parameters $category_short
```
 public function OWAC_calendar_front_shortcode($atts = array())
{	
	$atts = shortcode_atts(array('category' => ''), $atts);
	$category_short = $atts['category'];

   /**
	* Get Event and Category value
	*/
	global $wpdb;
	$contactus_table = $wpdb->prefix."OWAC_event";
	$total_pages_sql = $wpdb->get_results("SELECT * FROM $contactus_table WHERE 1 AND `flag`='0'");
	$ec_category_table = $wpdb->prefix."OWAC_category";
	if($category_short != ""){
		$ec_category_sql = $wpdb->get_results("SELECT * FROM $ec_category_table WHERE 1 AND `cat_id` IN (".$category_short.") AND `flag`='0' ORDER BY `cat_ord_num` ASC");
	}else{
		$ec_category_sql = $wpdb->get_results("SELECT * FROM $ec_category_table WHERE 1 AND `flag`='0' ORDER BY `cat_ord_num` ASC");
	}
	$settings_options = get_option( 'OWAC_settings_option' );
	$display_calendar_month = preg_replace("/[^0-9\.]/", '', $settings_options['display_calendar_month']);
	$language_display = $settings_options['language_display'];
	$language = owac_language();
	foreach($language as $key => $va){
		if($language_display == $key){
			setlocale(LC_TIME, array(''.$va['code'].'.UTF-8',''.$va['code'].'@euro',''.$va['code'].'',$key));
		}
	}

```
## Proof of Concept
1,add the "Availability Calendar"->"Category"->"Add New"
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210804105242.png "Wordpress plugin sqli")
2,Add the shortcode [availabilitycalendar category="5) UNION select user(),user(),user(),user(),user(),user(),user() -- "] on the content of a page/post/etc. to add the plugin into a page
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210804105249.png "Wordpress plugin sqli")
3,Visit the content of a page/post/etc. We can see the alert page.
![blockchain](https://github.com/xiahao90/CVEproject/blob/main/imgs/20210804105255.png "Wordpress plugin sqli")
