                                                                                   Traditioanl Design

![1](https://github.com/user-attachments/assets/cfbbabbe-9e46-4378-aef7-b58556732712)

1 Company-Operated Network:
This is where the networking infrastructure (routers, firewalls) is managed. It handles the communication between all components in the system (web application, database, email services, and file storage).
2 Web Application (Monolithic): 
A monolithic web application hosted on physical servers. This application depends on the database and file storage for serving content and interacting with customers. It is tightly coupled with the other components and manages everything within one codebase.
3 Backend Database (SQL Server): 
An SQL server running on-premises, which stores all of the critical business data. This database is accessed by the monolithic web application to manage data such as customer information, inventory, and sales.
4  File Storage (Local File System): 
A local file storage system where static files (images, documents, backups) are stored and accessed by the web application. This file system is physically hosted on servers managed by the company.
5  Email Services (Client Notification): 
The email services are hosted internally and integrated with the web application. These services are responsible for sending notifications to clients (e.g., order confirmations, marketing emails).


