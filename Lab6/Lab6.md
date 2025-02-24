Lab 6 - Refactoring a Legacy Application for Cloud-Native Deployment on Azure

Monolithic Architecture: A monolithic architecture is a conventional model where all components of an application are tightly coupled and deployed as a single unit.
Components of the Monolithic Application
1)Frontend:A single web server hosting the user interface and handles user requests and serves static content.

2)Backend: Business logic and APIs are tightly integrated into the same codebase as the frontend. I handles data processing, authentication, and other server-side operations.

3)Database: A single SQL Server database hosted on the same VM or a separate VM. it stores all application data, including user information, transactions, and logs.

4)Background Tasks: Long-running processes or scheduled jobs are part of the same application.These tasks run synchronously or as separate threads within the monolithic application.

5)Static Content: Static files are stored on the web server's file system.

6)Logs and Monitoring: Logs are written to local files on the VM. Monitoring is done manually or using basic tools.

Plan the Refactoring Strategy: To refactor existing system, components needs to be replaced with cloud services.
1)Frontend: Migrate to Azure App Service for hosting the web UI.

2)Backend APIs: Refactor into microservices and deploy to Azure App Service or Azure Functions.

3)Database: Migrate from VM-hosted SQL Server to Azure SQL Database.

4)Background Tasks: Convert to Azure Functions for serverless execution.

5)Static Content: Move to Azure Blob Storage.

6)Logs: Store logs in Azure Blob Storage and use Azure Monitor for centralized logging.


