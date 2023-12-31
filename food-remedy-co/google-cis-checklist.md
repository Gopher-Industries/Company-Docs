# **Food Remedy API**

## **CIS Google Cloud Platform Benchmark Checklist**

| # | CIS Benchmark Recommendation | Set Correctly - Yes | Set Correctly - No | N/A |
|----------|--------------------|-----------------------|------------------------| ------------------------|
| **1** | **Identity and Access Management** |
| 1.1 | Ensure that Corporate Login Credentials are Used (Manual) |  |  |  |
| 1.2 | Ensure that Multi-Factor Authentication is 'Enabled' for All Non-Service Accounts (Manual) |  |  |  |
| 1.3 | Ensure that Security Key Enforcement is Enabled for All Admin Accounts (Manual) |  |  |  |
| 1.4 | Ensure That There Are Only GCP-Managed Service Account Keys for Each Service Account (Automated) |  |  |  |
| 1.5 | Ensure That Service Account Has No Admin Privileges (Automated) |  |  |  |
| 1.6 | Ensure That IAM Users Are Not Assigned the Service Account User or Service Account Token Creator Roles at Project Level (Automated) |  |  |  |
| 1.7 | Ensure User-Managed/External Keys for Service Accounts Are Rotated Every 90 Days or Fewer (Automated) |  |  |  |
| 1.8 | Ensure That Separation of Duties Is Enforced While Assigning Service Account Related Roles to Users (Automated) |  |  |  |
| 1.9 | Ensure That Cloud KMS Cryptokeys Are Not Anonymously or Publicly Accessible (Automated) |  |  |  |
| 1.10 | Ensure KMS Encryption Keys Are Rotated Within a Period of 90 Days (Automated) |  |  |  |
| 1.11 | Ensure That Separation of Duties Is Enforced While Assigning KMS Related Roles to Users (Automated) |  |  |  |
| 1.12 | Ensure API Keys Only Exist for Active Services (Automated) |  |  |  |
| 1.13 | Ensure API Keys Are Restricted To Use by Only Specified Hosts and Apps (Manual) |  |  |  |
| 1.14 | Ensure API Keys Are Restricted to Only APIs That Application Needs Access (Automated) |  |  |  |
| 1.15 | Ensure API Keys Are Rotated Every 90 Days (Automated) |  |  |  |
| 1.16 | Ensure Essential Contacts is Configured for Organization (Automated) |  |  |  |
| 1.17 | Ensure that Dataproc Cluster is encrypted using Customer-Managed Encryption Key (Automated) |  |  |  |
| 1.18 | Ensure Secrets are Not Stored in Cloud Functions Environment Variables by Using Secret Manager (Manual) |  |  |  |
| **2** |**Logging and Monitoring** |
| 2.1 | Ensure That Cloud Audit Logging Is Configured Properly (Automated) |  |  |  |
| 2.2 | Ensure That Sinks Are Configured for All Log Entries (Automated) |  |  |  |
| 2.3 | Ensure That Retention Policies on Cloud Storage Buckets Used for Exporting Logs Are Configured Using Bucket Lock (Automated) |  |  |  |
| 2.4 | Ensure Log Metric Filter and Alerts Exist for Project Ownership Assignments/Changes (Automated) |  |  |  |
| 2.5 | Ensure That the Log Metric Filter and Alerts Exist for Audit Configuration Changes (Automated) |  |  |  |
| 2.6 | Ensure That the Log Metric Filter and Alerts Exist for Custom Role Changes (Automated) |  |  |  |
| 2.7 | Ensure That the Log Metric Filter and Alerts Exist for VPC Network Firewall Rule Changes (Automated) |  |  |  |
| 2.8 | Ensure That the Log Metric Filter and Alerts Exist for VPC Network Route Changes (Automated) |  |  |  |
| 2.9 | Ensure That the Log Metric Filter and Alerts Exist for VPC Network Changes (Automated) |  |  |  |
| 2.10 | Ensure That the Log Metric Filter and Alerts Exist for Cloud Storage IAM Permission Changes (Automated) |  |  |  |
| 2.11 | Ensure That the Log Metric Filter and Alerts Exist for SQL Instance Configuration Changes (Automated) |  |  |  |
| 2.12 | Ensure That Cloud DNS Logging Is Enabled for All VPC Networks (Automated) |  |  |  |
| 2.13 | Ensure Cloud Asset Inventory Is Enabled (Automated) |  |  |  |
| 2.14 | Ensure 'Access Transparency' is 'Enabled' (Manual) |  |  |  |
| 2.15 | Ensure 'Access Approval' is 'Enabled' (Automated) |  |  |  |
| 2.16 | Ensure Logging is enabled for HTTP(S) Load Balancer (Automated) |  |  |  |
| **3**| **Networking** |
| 3.1 | Ensure That the Default Network Does Not Exist in a Project (Automated) |  |  |  |
| 3.2 | Ensure Legacy Networks Do Not Exist for Older Projects (Automated) |  |  |  |
| 3.3 | Ensure That DNSSEC Is Enabled for Cloud DNS (Automated) |  |  |  |
| 3.4 | Ensure That RSASHA1 Is Not Used for the Key-Signing Key in Cloud DNS DNSSEC (Automated) |  |  |  |
| 3.5 | Ensure That RSASHA1 Is Not Used for the Zone-Signing Key in Cloud DNS DNSSEC (Automated) |  |  |  |
| 3.6 | Ensure That SSH Access Is Restricted From the Internet (Automated) |  |  |  |
| 3.7 | Ensure That RDP Access Is Restricted From the Internet (Automated) |  |  |  |
| 3.8 | Ensure that VPC Flow Logs is Enabled for Every Subnet in a VPC Network (Automated) |  |  |  |
| 3.9 | Ensure No HTTPS or SSL Proxy Load Balancers Permit SSL Policies With Weak Cipher Suites (Manual) |  |  |  |
| 3.10 | Use Identity Aware Proxy (IAP) to Ensure Only Traffic From Google IP Addresses are 'Allowed' (Manual) |  |  |  |
| **4**| **Virtual Machines** |
| 4.1 | Ensure That Instances Are Not Configured To Use the Default Service Account (Automated) |  |  |  |
| 4.2 | Ensure That Instances Are Not Configured To Use the Default Service Account With Full Access to All Cloud APIs (Automated) |  |  |  |
| 4.3 | Ensure “Block Project-Wide SSH Keys” Is Enabled for VM Instances (Automated) |  |  |  |
| 4.4 | Ensure Oslogin Is Enabled for a Project (Automated) |  |  |  |
| 4.5 | Ensure ‘Enable Connecting to Serial Ports’ Is Not Enabled for VM Instance (Automated) |  |  |  |
| 4.6 | Ensure That IP Forwarding Is Not Enabled on Instances (Automated) |  |  |  |
| 4.7 | Ensure VM Disks for Critical VMs Are Encrypted With Customer-Supplied Encryption Keys (CSEK) (Automated) |  |  |  |
| 4.8 | Ensure Compute Instances Are Launched With Shielded VM Enabled (Automated) |  |  |  |
| 4.9 | Ensure That Compute Instances Do Not Have Public IP Addresses (Automated) |  |  |  |
| 4.10 | Ensure That App Engine Applications Enforce HTTPS Connections (Manual) |  |  |  |
| 4.11 | Ensure That Compute Instances Have Confidential Computing Enabled (Automated) |  |  |  |
| 4.12 | Ensure the Latest Operating System Updates Are Installed On Your Virtual Machines in All Projects (Manual) |  |  |  |
| **5**| **Storage** |
| 5.1 | Ensure That Cloud Storage Bucket Is Not Anonymously or Publicly Accessible (Automated) |  |  |  |
| 5.2 | Ensure That Cloud Storage Buckets Have Uniform Bucket-Level Access Enabled (Automated) |  |  |  |
| **6**| **Cloud SQL Database Services** |
| **6.1**| **MySQL Database** |
| 6.1.1 | Ensure That a MySQL Database Instance Does Not Allow Anyone To Connect With Administrative Privileges (Manual) |  |  |  |
| 6.1.2 | Ensure ‘Skip_show_database’ Database Flag for Cloud SQL MySQL Instance Is Set to ‘On’ (Automated) |  |  |  |
| 6.1.3 | Ensure That the ‘Local_infile’ Database Flag for a Cloud SQL MySQL Instance Is Set to ‘Off’ (Automated) |  |  |  |
| **6.2**| **PostgreSQL Database** |
| 6.2.1 | Ensure ‘Log_error_verbosity’ Database Flag for Cloud SQL PostgreSQL Instance Is Set to ‘DEFAULT’ or Stricter (Automated) |  |  |  |
| 6.2.2 | Ensure That the ‘Log_connections’ Database Flag for Cloud SQL PostgreSQL Instance Is Set to ‘On’ (Automated) |  |  |  |
| 6.2.3 | Ensure That the ‘Log_disconnections’ Database Flag for Cloud SQL PostgreSQL Instance Is Set to ‘On’ (Automated) |  |  |  |
| 6.2.4 | Ensure ‘Log_statement’ Database Flag for Cloud SQL PostgreSQL Instance Is Set Appropriately (Automated) |  |  |  |
| 6.2.5 | Ensure that the ‘Log_min_messages’ Flag for a Cloud SQL PostgreSQL Instance is set at minimum to 'Warning' (Automated) |  |  |  |
| 6.2.6 | Ensure ‘Log_min_error_statement’ Database Flag for Cloud SQL PostgreSQL Instance Is Set to ‘Error’ or Stricter (Automated) |  |  |  |
| 6.2.7 | Ensure That the ‘Log_min_duration_statement’ Database Flag for Cloud SQL PostgreSQL Instance Is Set to ‘-1′ (Disabled) (Automated) |  |  |  |
| 6.2.8 | Ensure That 'cloudsql.enable_pgaudit' Database Flag for each Cloud SQL Postgresql Instance Is Set to 'on' For Centralized Logging (Automated) |  |  |  |
| 6.2.9 | Ensure Instance IP assignment is set to private (Automated) |  |  |  |
| **6.3**| **SQL Server** |
| 6.3.1 | Ensure 'external scripts enabled' database flag for Cloud SQL SQL Server instance is set to 'off' (Automated) |  |  |  |
| 6.3.2 | Ensure that the 'cross db ownership chaining' database flag for Cloud SQL SQL Server instance is set to 'off' (Automated) |  |  |  |
| 6.3.3 | Ensure 'user Connections' Database Flag for Cloud Sql Sql Server Instance Is Set to a Non-limiting Value (Automated) |  |  |  |
| 6.3.4 | Ensure 'user options' database flag for Cloud SQL SQL Server instance is not configured (Automated) |  |  |  |
| 6.3.5 | Ensure 'remote access' database flag for Cloud SQL SQL Server instance is set to 'off' (Automated) |  |  |  |
| 6.3.6 | Ensure '3625 (trace flag)' database flag for all Cloud SQL Server instances is set to 'on' (Automated) |  |  |  |
| 6.3.7 | Ensure that the 'contained database authentication' database flag for Cloud SQL on the SQL Server instance is set to 'off' (Automated) |  |  |  |
| 6.4 | Ensure That the Cloud SQL Database Instance Requires All Incoming Connections To Use SSL (Automated) |  |  |  |
| 6.5 | Ensure That Cloud SQL Database Instances Do Not Implicitly Whitelist All Public IP Addresses (Automated) |  |  |  |
| 6.6 | Ensure That Cloud SQL Database Instances Do Not Have Public IPs (Automated) |  |  |  |
| 6.7 | Ensure That Cloud SQL Database Instances Are Configured With Automated Backups (Automated) |  |  |  |
| **7**| **BigQuery** |
| 7.1 | Ensure That BigQuery Datasets Are Not Anonymously or Publicly Accessible (Automated) |  |  |  |
| 7.2 | Ensure That All BigQuery Tables Are Encrypted With Customer-Managed Encryption Key (CMEK) (Automated) |  |  |  |
| 7.3 | Ensure That a Default Customer-Managed Encryption Key (CMEK) Is Specified for All BigQuery Data Sets (Automated) |  |  |  |

___
## References
[1] Center for Internet Security, “CIS Google Cloud Platform Foundation Benchmark,” Center for Internet Security, 2022.
___
###### _Emily Merchant, 15th September, 2023_