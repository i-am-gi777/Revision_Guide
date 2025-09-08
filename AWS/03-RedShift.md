# Short Note on Amazon Redshift
-Amazon Redshift is a fully managed, petabyte-scale data warehouse service in AWS.
-It enables fast querying and analysis of large datasets using SQL.
-Redshift is based on a columnar storage architecture and massively parallel processing (MPP) for speed.
-You can load data from S3, run complex analytical queries, and integrate with BI tools.
# Redshift Architecture Overview
- Leader Node:	
Manages client connections, parses queries, creates execution plans, and coordinates the processing across 
- compute nodes:
Compute Nodes	Store data and perform queries in parallel. Each node runs its own slice of the data and executes query fragments.
- Node Slices:
Each compute node is divided into slices; each slice 
manages a portion of the node’s memory and disk space.
- Columnar Storage:
Data is stored column-wise (not row-wise), which improves compression and query performance.
- Massively Parallel Processing (MPP)	:
Distributes queries across nodes for faster performance.
# Step-by-Step Guide: Create Amazon Redshift Cluster & Run Sample SQL
# Prerequisites:
AWS account
Proper IAM permissions for Redshift
Basic knowledge of SQL
# Steps to Create Redshift Cluster
1. Open AWS Redshift Console
Go to https://console.aws.amazon.com/redshift/
2. Click “Create cluster”
Click the “Create cluster” button.
3. Configure Cluster Basics
Cluster identifier: Give a unique name (e.g., sample-redshift-cluster)
Database name: e.g., dev
Master username: e.g., awsuser
Master user password: Enter and confirm a secure password
4. Node Configuration
Choose node type (e.g., dc2.large for testing)
Number of nodes: 1 (for demo/small workload)
5. Advanced Settings
Set VPC and subnet (default is usually fine)
Configure public access if you want to connect externally (for demo, 
enable it)
Set IAM roles if you want to load data from S3 (optional)
6. Create Cluster
Review and click Create cluster
7. Wait for Cluster to be Available
It takes several minutes for the cluster status to show Available
# Connect and Run SQL Queries
-Option 1: Using Query Editor in AWS Console
- 1.Go to Redshift Console
- 2.Click Query editor v2 (or Query editor)
- 3.Choose your cluster and connect using the master username and password

Run SQL commands like:
```sql
CREATE TABLE sample_table (
    id INT,
    name VARCHAR(50),
    age INT
);

INSERT INTO sample_table VALUES (1, 'Alice', 30), (2, 'Bob', 25);
SELECT * FROM sample_table;
--Option 2: Use SQL Client (e.g., SQL Workbench/J)
-- 1.Download SQL client
-- 2.Use cluster endpoint, port (default 5439), username, and password to connect
