Lab 6 - Refactoring a Legacy Application for Cloud-Native Deployment on Azure
# **Scenario**
An online bookstore is currently running a monolithic web application hosted on a Windows Server 2019 virtual machine (VM) in Azure. The company aims to modernize the application by refactoring it into a cloud-native microservices architecture that leverages Azure Cloud services. This transformation will improve scalability, performance, and security while enhancing maintainability and overall operational efficiency.

# **Monolithic Architecture**
A monolithic architecture is a conventional model where all components of an application are tightly coupled and deployed as a single unit.

Components of the Monolithic Application

**1. Frontend**
  -  A single web application or mobile app for customers to interact with the bookstore.
  - Communicates directly with the monolithic backend.

 **2. Single Backend Server**
- The backend is a monolithic system containing all business logic for the bookstore.Handles all functionalities.

 **3. Database**
- A single relational database stores all data.

 **4. Backend Logic**
- All business logic is tightly coupled in the same codebase and executed within the same application instance.

 **5. Payment Gateway Integration**
- The monolithic application interacts with external payment services.
- Payment processing is managed directly by the backend via synchronous API calls.

 **6. Traditional Web Server**
- A single web server  hosts the application.
- Handles incoming HTTP requests and forwards them to the monolithic backend.

 **7. Reporting and Analytics**
- Reports related to sales, inventory, and user activity are generated using custom SQL queries against the monolithic database.
- No need for specialized analytics services since all data is stored in the same database.

![BookStore_MonoliticArchitecture1](https://github.com/user-attachments/assets/8bf60398-c82d-431a-a1f2-d31b7deeff33)
 
# Refactoring Strategy for Cloud Migration

 **1. Frontend Refactoring**  
   - Decouple frontend from the backend and host separately on Azure App Service for scalability and performance.

**2. Backend Refactoring (Monolithic to Microservices)**  
   - Break the monolithic backend into independent microservices running in containers, orchestrated by Azure Kubernetes Service (AKS).

**3. Database Refactoring**  
   - Migrate to a distributed database architecture using Cosmos DB for non-relational data and SQL Database for transactional data.

**4. Payment Gateway Refactoring**  
   - Isolate payment processing into a dedicated Payment Service with secure credentials managed in Azure Key Vault

**5. Service Communication Refactoring**  
   - Implement an API Gateway using Azure API Management for routing requests and ensuring secure service-to-service communication.

**6. Web Server and Load Balancer Refactoring**  
   - Transition to Azure App Service for frontend hosting and use Azure Load Balancer to distribute traffic across microservices.

**7. Cloud Storage and Data Management**  
   - Leverage Azure Blob Storage for file storage; use Cosmos DB and SQL Database for data storage.

**8. Reporting and Analytics Refactoring**  
   - Implement cloud-native analytics with Azure Monitor and Application Insights for advanced reporting.

**9. Authentication & Authorization Refactoring**  
   - Implement Azure Active Directory (Azure AD for user authentication and secure API access.

**10. Serverless Functions**  
   - Use Azure Functions for event-driven operations like email confirmations and processing discount coupons.

**11. Security & Compliance Refactoring**  
   - Secure sensitive data using Azure Key Vault enable encryption for data at rest and in transit, and monitor security with Azure Security Center

 **12. Deployment Strategy**  
   - Set up CI/CD pipelines with Azure DevOps for automated, secure deployments.

**13. Monitoring and Observability**  
   - Use Azure Monitor for infrastructure health and Application Insights for real-time application monitoring and troubleshooting.

# **Implement Refactoring Changes**:
The bookstore’s architecture consists of containerized microservices hosted in the cloud, connected to cloud storage and analytics tools for efficient management of books, customer data, and inventory.

 **1. Frontend**
-A web application or mobile app for customers to interact with the bookstore. It is Hosted on Azure App Service for scalable and managed hosting.

 **2. Azure API Management**
- Acts as the API Gateway for the system.
- Handles all customer requests and routes them to the appropriate microservices.
- Ensures secure and efficient communication between the client and backend services.

 **3. Azure Load Balancer**
- Distributes incoming traffic evenly across multiple instances of microservices.
- Prevents overloading by routing requests efficiently to Kubernetes clusters managing microservices.
- Ensures high availability and reliability.

 **4. Azure Kubernetes Service (AKS)**
- Manages and orchestrates containers for each microservice.
- Each microservice runs independently and communicates with others via APIs.

### **Microservices in AKS:**
#### **I. Search Service**
- Handles search functionality within the bookstore.
- Database: Uses Cosmos DB to index and retrieve books.

#### **II. Shop Service**
- Manages the user interface for browsing and adding books to the cart.
- Handles promotions, categories, and shopping experience.
- Database: Uses Cosmos DB for storing user cart data and preferences.

#### **III. Inventory Service**
- Manages the available stock of books.
- Ensures stock availability and updates inventory after each purchase.
- Database: Uses SQL Database to store book inventory details (e.g., stock quantity, location).

#### **IV. Payment Service**
- Handles all payment processing and transactions.
- Database: Interacts with Azure Key Vault to securely manage payment credentials and API keys for third-party payment processors.

#### **V. Order Management Service**
- Manages customer orders, updates order statuses, and tracks order history.
- Database: Uses SQL Database to store order history, shipping details, and customer information.

#### **VI. Sales Service**
- Tracks sales data and generates reports on book sales, discounts, and performance analytics.
- Database: Uses SQL Database or Cosmos DB for high-performance storage of sales data.

#### **VII. Accounting Service**
- Handles financial calculations, invoice generation, and reporting.
- Manages payments and financial reconciliations.
- Database: Uses SQL Database to store financial data securely.

 **5. Azure Functions (Serverless)**
- Handles serverless operations such as:
  - Sending email confirmations after a successful purchase.
  - Processing one-time discount coupons.

 **6. Azure Key Vault**
- Stores sensitive credentials such as:
  - API keys
  - Payment gateway credentials
- Ensures secure access to sensitive data.

 **7. Azure Active Directory (Azure AD)**
- Manages user authentication (e.g., logging in, managing personal order history).
- Authenticates API requests to ensure secure access to services.

 **8. Azure Monitor & Application Insights**
- Provides real-time monitoring of:
  - Infrastructure: Using Azure Monitor.
  - Application-level performance: Using Application Insights.
- Helps identify and resolve issues quickly, ensuring optimal performance.


![BookStore_CloudArchitecture](https://github.com/user-attachments/assets/7b38cc76-5dab-4699-8874-623cfbf2c603)

# Justifications for Chosen Azure Services

**1. Azure App Service:**
- Scalable and managed hosting for the frontend, simplifying deployment and maintenance without worrying about infrastructure management.

**2. Azure Kubernetes Service (AKS):**
- Container orchestration for microservices, providing efficient resource management, scaling, and isolation of services.

**3. Azure Cosmos DB & SQL Database:**
- Cosmos DB offers global distribution and scalability for non-relational data (e.g., search, cart), while SQL Database handles transactional data (e.g., inventory, orders).

**4. Azure API Management:**
- Centralized API gateway for managing and securing communication between frontend and microservices, ensuring scalable and reliable access to backend services.

**5. Azure Functions:**
- Serverless execution for event-driven operations like sending email confirmations and processing discounts, reducing overhead and cost.

**6. Azure Key Vault:**
- Securely stores sensitive credentials (e.g., API keys, payment credentials), improving security compliance.

**7. Azure Active Directory (Azure AD):**
- Centralized identity management for secure user authentication and API access control.

**8. Azure Monitor & Application Insights:**
- Provides real-time monitoring, enabling quick issue resolution and performance optimization for both infrastructure and application-level performance.

# Migration and Deployment Steps

**1. Frontend Deployment:**
- Deploy the frontend on Azure App Service, configuring it with automated CI/CD pipelines for deployment.

**2. Microservice Decomposition:**
- Break down the monolithic backend into individual microservices, each containerized and managed by Azure Kubernetes Service (AKS).

**3. Database Migration:**
- Migrate the relational database to Azure SQL Database and non-relational data to Azure Cosmos DB.

**4. API Gateway Setup:**
- Set up Azure API Management to route and secure traffic to the appropriate microservices.

**5. Serverless Functions:**
- Implement Azure Functions for event-driven operations and integrate them with the rest of the system.

**6. Security Integration:**
- Configure Azure Key Vault for secure storage of credentials and Azure AD for user authentication.

**7. Monitoring Setup:**
- Implement Azure Monitor and Application Insights for continuous monitoring and performance tracking.

# Lessons Learned and Challenges Faced

**1. Complexity in Microservice Design:**
- Breaking down the monolithic app into independent services requires careful planning of service boundaries and data management, while ensuring seamless communication and data consistency between microservices.

**2. Database Refactoring:**
- Migrating data to distributed databases like Cosmos DB and SQL Database required addressing data consistency challenges, while ensuring smooth migration without data loss or downtime.

**3. Deployment and Scaling:**
- Utilizing Azure DevOps for CI/CD pipelines streamlined deployments, but fine-tuning auto-scaling policies in AKS was a key step to meet changing traffic demands, and ensuring efficient resource allocation and load balancing across AKS containers was a challenge.

  
