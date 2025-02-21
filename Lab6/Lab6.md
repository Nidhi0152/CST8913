Lab 6 - Refactoring a Legacy Application for Cloud-Native Deployment on Azure

Monolithic Architecture: A monolithic architecture is a conventional model where all components of an application are tightly coupled and deployed as a single unit.
Components of the Monolithic Application
1)Frontend:
-->A single web server (e.g., IIS or Apache) hosting the user interface (HTML, CSS, JavaScript).
-->Handles user requests and serves static content (images, stylesheets, etc.).

2)Backend:
-->Business logic and APIs are tightly integrated into the same codebase as the frontend.
-->Handles data processing, authentication, and other server-side operations.

3)Database:
-->A single SQL Server database hosted on the same VM or a separate VM.
-->Stores all application data, including user information, transactions, and logs.

4)Background Tasks:
-->Long-running processes or scheduled jobs (e.g., batch processing, report generation) are part of the same application.
-->These tasks run synchronously or as separate threads within the monolithic application.

5)Static Content:
-->Static files (e.g., images, CSS, JavaScript) are stored on the web server's file system.

6)Logs and Monitoring:
-->Logs are written to local files on the VM.
-->Monitoring is done manually or using basic tools.

