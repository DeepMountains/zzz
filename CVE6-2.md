# Vendor

零起飞

# Product

07FlyCms

# version

1.3.8

# Download 

https://gitee.com/07fly/cms-php.git

# Vulnerability

XSS

# Description

In the background of 07flycms, In the "System Settings" page, all input boxes have XSS vulnerabilities. Inserting special POCs can lead to XSS vulnerabilities in the front-end and back-end.
<img width="1227" alt="image" src="https://github.com/user-attachments/assets/e6604365-5cba-4c37-bc7e-e1e89256cd04">


# POC
```
"><script>alert("mirage")</script>
```
