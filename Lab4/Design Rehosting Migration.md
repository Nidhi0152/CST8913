
                    High-Level Design Document: Lift-and-Shift Migration to Cloud

Introduction:
The goal of this lift-and-shift migration is to migrate an existing application to a multi-region cloud setup. It ensures high availability and automatic failover in case of regional downtime, with minimum downtime.

Architecture:
![1](https://github.com/user-attachments/assets/8cc71b77-c762-4f8d-b37d-36edad0d2a88)

1)WebServerVM: The WebServerVMs are responsible for serving the static content of the application. Each region will have its own set of WebServerVMs deployed in at least two Availability Zones (AZs) to provide redundancy and mitigate the risk of service disruption due to localized failures. This multi-Avalibilty deployment ensures that the application remains accessible even if one Availability Zone experiences issues.

2)SQLVM (Database Backend): The SQL virtual machine (SQLVM) hosts the backend database that powers the application. To provide high availability and fault tolerance, the SQLVM will be replicated across multiple regions. This replication ensures that in the event of a regional failure, the database will continue to function in another region without downtime, preserving data integrity and availability.

3)Loadbalancer: To optimize traffic distribution and ensure that the application remains operational during regional failures, the system will deploy multiple levels of load balancing:

  i)Regional Load Balancers: These load balancers will distribute incoming traffic evenly across the WebServerVMs within each region. This prevents any individual WebServerVM from becoming overloaded and ensures 
    efficient resource utilization.

 ii)Global Load Balancer: A global load balancer will direct traffic between regions. In the case of a regional failure, the global load balancer will reroute traffic to another regions, ensuring that the 
   application continues to operate seamlessly. This global failover mechanism helps maintain business continuity in the event of regional downtime.

4)Replication and failover:
-->WebServerVMs: Replication of the WebServerVMs will occur across regions, ensuring that the application’s frontend is available in multiple locations. This replication ensures that if one region goes down, the load balancer will redirect traffic to the healthy region with minimal delay. The global load balancer will monitor the health of the WebServerVMs across regions and seamlessly direct traffic to a functioning region, ensuring continuous access to the application.

-->SQLVMs: The SQL database will be replicated across regions using Active Geo-Replication, ensuring data availability and consistency. In the event of a regional failure, the auto-failover group will handle the failover automatically, promoting a secondary database to the primary role. This ensures that the backend database remains functional with no data loss, even during unplanned outages. By leveraging Active Geo-Replication with Auto-Failover Groups, the database can failover with minimal downtime, and the system will maintain high availability for both the database and frontend components.

Migration Process: To ensure high availability and little downtime throughout the shift, the migration process requires a number of important steps for setting up and synchronizing the infrastructure.

1)Replication WebseverVM: To replicate WebServerVMs, Azure Migrate can be used to deploy VMs across regions, ensuring they are distributed across at least two Availability Zones (AZs) for redundancy. After deployment, the VMs should be validated to ensure they function correctly and handle the expected traffic load.

2)Configuring Load Balancers:  Azure Load Balancer can be used to distribute traffic evenly across WebServerVMs within each region. To manage traffic between regions and handle failover, Azure Front Door or Azure Traffic Manager can be implemented to provide global load balancing and ensure availability during regional failures.

3)Databe replication and failover: Azure SQL Database or Azure SQL Managed Instance can be used to replicate databases across regions, ensuring data consistency. Azure SQL Always On Availability Groups or Geo-Replication provide automatic failover, ensuring continuous database availability with minimal data loss.



