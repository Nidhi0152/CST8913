                     High-Level Design Document: Lift-and-Shift Migration to Cloud

Introduction:
The goal of this lift-and-shift migration is to migrate an existing application to a multi-region cloud setup. It ensures high availability and automatic failover in case of regional downtime, with minimum downtime.

Architecture:
![1](https://github.com/user-attachments/assets/8cc71b77-c762-4f8d-b37d-36edad0d2a88)

1)WebServerVM: These virtual machines serve static content and are deployed across multiple regions in at least two availability zones (AZs) for redundancy. Each region has its own set of WebServerVMs that are balanced by regional load balancers. If a region experiences failure, a global load balancer ensures that traffic is redirected to healthy regions where WebServerVMs are still operational. Active Geo-Replication helps ensure that the frontend is accessible from other regions even if one region goes down.

2)SQLVM (Database Backend): The SQL virtual machine hosts the backend database and is replicated across multiple regions using Active Geo-Replication. The primary database in Region A continuously synchronizes with secondary databases in other regions (e.g., Region B). In case of regional failure, geo-failover automatically promotes a secondary database to the primary role, maintaining database availability with minimal downtime. Auto-Failover Groups manage the failover process for all databases, ensuring traffic is redirected to the new primary database.

3)Loadbalancer: The application uses regional load balancers to distribute traffic among WebServerVMs within each region. A global load balancer routes traffic between regions. If a regional failure occurs, the global load balancer reroutes traffic to a healthy region. The auto-failover group ensures that when the database fails over, traffic is directed to the newly promoted database without disruption.

4)Auto Scaling: Auto-scaling for WebServerVMs ensures the infrastructure can handle fluctuating traffic loads. It automatically scales up or down the number of VMs based on demand. During regional failures, the auto-scaling feature ensures sufficient capacity in the fallback region to handle the incoming traffic, while the failover process ensures the application continues operating smoothly.

5)Replication:
-->WebServerVMs: These virtual machines are replicated across multiple regions to ensure the frontend remains available. Each region has its own set of WebServerVMs, and the global load balancer ensures traffic is directed to the healthiest region.
-->SQLVMs: The database is replicated using Active Geo-Replication across regions. The primary database in one region (e.g., Region A) continuously syncs with secondary databases in other regions (e.g., Region B), ensuring data consistency and availability.

6)In case of Failoure:
-->WebServerVMs: In case of a regional failure, the global load balancer automatically detects the issue and redirects traffic to the healthy region where WebServerVMs are still operational, ensuring minimal disruption to the application.
-->SQLVMs: If a regional failure occurs, Auto-Failover Groups handle the failover process. A secondary database is automatically promoted to the primary role, and traffic is rerouted to the new primary database, ensuring continuous database availability and no data loss.
