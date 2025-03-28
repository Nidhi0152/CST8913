# 1.Discovery and Tooling Setup for Migration to Azure

## Tools for Discovery

- **Azure Migrate**: A comprehensive tool for assessing, planning, and migrating on-premises workloads to Azure.
- **Azure Migrate: Server Assessment**: Used to assess on-premises infrastructure for migration readiness and provide sizing recommendations for Azure.
- **Azure Migrate: Server Migration**: Facilitates the migration of workloads from on-premises servers to Azure, ensuring a smooth transition.
- **Azure Migrate Appliance**: A lightweight, agentless appliance that collects data from the on-premises environment to assist in migration planning.

## Data to be Collected

- **Operating System Details**: Information about the OS version, configuration, and patch level on existing servers.
- **Software Inventory**: A list of all software components and dependencies, such as NGINX, Node.js, PostgreSQL, and Redis.
- **Dependencies**: Details of inter-service communication, network configurations, and firewall rules between components.
- **Resource Utilization**: Metrics on CPU, memory, storage, and network usage for optimal Azure resource sizing.
- **Backup Strategy**: Information on the current backup system, including backup frequency and retention policies.

## Credential and Permission Management

- **Azure Active Directory (AAD)**: Used to manage user identities and control access to Azure resources and migration tools.
- **Managed Identity**: Azure service feature that enables secure authentication without storing credentials in plaintext.
- **Azure Key Vault**: Securely stores sensitive data, such as passwords and API keys, with encrypted access control.
