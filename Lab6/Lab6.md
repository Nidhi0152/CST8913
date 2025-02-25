Lab 6 - Refactoring a Legacy Application for Cloud-Native Deployment on Azure

**Monolithic Architecture**: A monolithic architecture is a conventional model where all components of an application are tightly coupled and deployed as a single unit.

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

**Implement Refactoring Changes**:
The bookstore’s architecture consists of containerized microservices hosted in the cloud, connected to cloud storage and analytics tools for efficient management of books, customer data, and inventory.

 **1. User/Client Request**
The user can request various services such as:
- Searching for books
- Adding books to the cart
- Processing payments
- Viewing order history

 **2. Azure API Management**
- Acts as the API Gateway for the system.
- Handles all customer requests and routes them to the appropriate microservices (e.g., Search, Cart, Inventory, Payment, etc.).
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
- **Database**: Uses Cosmos DB for storing user cart data and preferences.

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


![BookStore_CloudArchitecture](https://github.com/user-attachments/assets/9e254f2c-ca92-4660-93e5-0ebc97f55089)



