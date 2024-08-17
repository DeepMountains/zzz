# Vendor

itsourcecode

# Product

Laravel Property Management System

# version

V1.0

# Download 

https://itsourcecode.com/wp-content/uploads/2021/10/Property-Management-System-Laravel.zip

# Vulnerability

FileUpload

# Description

In the DocumentsController.php controller, documents can be uploaded, and there are no filtering rules, which allows attackers to register a normal user and directly upload PHP files.

# Analysis

Register a common user and log in. Visit the /admin/documents/create page and upload a PHP file directly. In the app/Http/Controllers/Admin/DocumentsController.php controller, the UpdateDocumentsRequest class object passed to the upload() method does not filter for file types.
<img width="1123" alt="image" src="https://github.com/user-attachments/assets/ca03f7b1-f731-4c7a-a6f5-9fa6dda73607">
<img width="628" alt="image" src="https://github.com/user-attachments/assets/9565c1f9-0b49-43b7-9ca8-8d506521d871">
