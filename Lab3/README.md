Purpose of the Lab:

This lab focuses on understanding cloud migration and adoption strategies, highlighting the key service models: PaaS, IaaS, and SaaS. Participants will explore how to transition from on-premises systems to the cloud, selecting the right service model for each component. By examining cloud architectures and migration approaches, the lab provides insights into modernizing IT infrastructure and leveraging cloud technologies effectively.

On-Premises Design:

On-premises refers to IT infrastructure and software hosted on-site within a company’s physical premises, offering businesses control over performance, security, and maintenance. While many businesses continue using on-premises solutions, there is a growing shift toward migrating to the cloud for scalability, cost-effectiveness, and flexibility. Some companies also adopt hybrid environments, combining on-premises and cloud services.

For a mid-sized retail company, their current on-premises setup includes a monolithic web application, SQL database, file storage, and email services. While offering control, this traditional infrastructure requires significant maintenance and limits scalability. As the company explores cloud adoption, evaluating which components to migrate to cloud services (PaaS, IaaS, or SaaS) based on performance, security, and business needs will help achieve greater flexibility and scalability while maintaining control over critical infrastructure.

![1](https://github.com/user-attachments/assets/6a8b9742-f3a2-44a4-ba84-f02d5678908f)


1 Company-Operated Network: This is where the networking infrastructure (routers, firewalls) is managed. It handles the communication between all components in the system (web application, database, email services, and file storage).

2 Web Application : A monolithic web application hosted on physical servers. This application depends on the database and file storage for serving content and interacting with customers. It is tightly coupled with the other components and manages everything within one codebase.

3 Backend Database : An SQL server running on-premises, which stores all of the critical business data. This database is accessed by the monolithic web application to manage data such as customer information, inventory, and sales.

4 File Storage : A local file storage system where static files (images, documents, backups) are stored and accessed by the web application. This file system is physically hosted on servers managed by the company.

5 Email Services : The email services are hosted internally and integrated with the web application. These services are responsible for sending notifications to clients (e.g., order confirmations, marketing emails).

Cloud Migration Strategy:

As businesses modernize their IT infrastructure, migrating from on-premises solutions to the cloud is crucial for improved scalability, cost-efficiency, and flexibility. This migration involves transitioning components of existing systems to cloud-based services such as PaaS, IaaS, and SaaS.
For a mid-sized retail company with a monolithic web application, SQL database, local file storage, and email services, a carefully planned migration strategy is essential. The strategy may consider a hybrid approach, moving some components like the web application to PaaS for scalability, while keeping others, like the database, on IaaS for more control.

![3](https://github.com/user-attachments/assets/a29dc193-f88d-48af-b531-8d9d7260e6ff)


1 Web Application: • PaaS:

The recommended service for the web application is Azure App Service, which allows the company to focus on application development while Azure handles infrastructure management, scaling, and updates.

2 Backend Database • IaaS: 

For businesses requiring more control over database configurations, Azure Virtual Machines (VMs) running SQL Server can host the database, providing a lift-and-shift migration approach.

3 File Storage • PaaS:

Azure Blob Storage is ideal for storing unstructured data, including files, images, and backups. It is highly scalable, secure, and offers low-cost storage options. It’s a perfect replacement for the company's on-premises file storage system.

4 Networking:

• Azure Virtual Network (VNet): This service allows the company to create a private network in Azure, securely connecting its resources in the cloud, similar to an on-premises network.

• Azure Firewall: Azure’s cloud-native firewall service provides stateful packet inspection, intrusion detection, and prevention, and helps maintain security for the entire cloud infrastructure.

• Azure VPN Gateway: For secure communication between the on-premises network and Azure, the company can implement a VPN Gateway, ensuring secure data transfer across hybrid environments.

5 Email Services • Saas:

Microsoft 365 (Exchange Online): For client email notifications, Exchange Online is a fully managed SaaS service that provides reliable, secure, and scalable email services. It integrates seamlessly with other Microsoft tools such as Office 365, SharePoint, and Teams, and eliminates the need to manage on-premises email servers.




