# Vendor

Chengdu Guangda Network Technology

# Product

BeikeShop

# version

<=v1.5.5

# Download 

https://beikeshop.cn/download

# Vulnerability

Arbitrary File Deletion

# Description

When sending a DELETE request action to the admin/file_manager/files interface, an attacker can construct a special POC to implement an arbitrary file deletion attack.

# Analysis

1. The route finds the destroyFiles method of beike/Admin/Http/Controllers/FileManagerController.php corresponding to the admin/file_manager/files interface.
<img width="671" alt="image" src="https://github.com/user-attachments/assets/0af3fd3e-9ca6-4762-8f62-15f436faba6d">

2. The fileManagerService object is set to "\Beike\Admin\Services\FileManagerService::class" in the __construct() method
<img width="1040" alt="image" src="https://github.com/user-attachments/assets/96924cbd-3105-45f5-8f6e-74345171e838">

3. Follow up the FileManagerService class in beike/Admin/Services/FileManagerService.php, and you can find the deleteFiles method, in which you can construct a directory traversal POC to achieve arbitrary file deletion. 
<img width="724" alt="image" src="https://github.com/user-attachments/assets/52195804-7410-4ecb-a0e5-e7888455b5cf">

# POC
<img width="944" alt="image" src="https://github.com/user-attachments/assets/8e46f4b3-fdf1-4336-8533-e3c5e59eeb44">
