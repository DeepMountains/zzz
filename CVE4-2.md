# Vendor

Chengdu Guangda Network Technology

# Product

BeikeShop

# version

<=v1.5.5

# Download 

https://beikeshop.cn/download

# Vulnerability

FileUpload

# Description

In the FileManagerController.php controller, the rename method can modify the name of the file, but due to improper filtering, attackers can directly modify the file suffix to php file.

# Analysis

1. Upload a jpeg file in the normal file upload interface. Since the interface has file type detection, it is necessary to add the GIF89a logo to the file header of the image Trojan.
<img width="946" alt="image" src="https://github.com/user-attachments/assets/29b52b31-fd03-4e6c-838b-61e8f76c34d2">

2. Through routing, you can find that the controller corresponding to the /admin/file_manager/rename interface is beike/Admin/Http/Controllers/FileManagerController.php.
<img width="634" alt="image" src="https://github.com/user-attachments/assets/f0f5bd86-7677-4c0c-9601-a1fba1c8449b">

3. The fileManagerService object is set to "\Beike\Admin\Services\FileManagerService::class" in the __construct() method

4. 
