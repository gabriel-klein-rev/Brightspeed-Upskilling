## Unit

# Data Warehousing

## Links

- [Data Warehousing](#data-warehousing)
  - [Links](#links)
  - [IMPORTANCE: Required](#importance-required)
  - [IMPORTANCE: Preferred](#importance-preferred)
  - [Importance: Stretch](#importance-stretch)

## IMPORTANCE: Required

[Back to top](#unit)

* **What are the key components of the Databricks UI?**
    * The key components of the Databricks UI include:
        * Workspace: Central place to manage notebooks, folders, libraries, dashboards, and other workspace assets.
        * Data: Allows users to browse and manage datasets in Databricks File System (DBFS), external data sources, and catalogs (Unity Catalog if enabled).
        * Workflows (or Jobs): Used for orchestrating tasks, job scheduling, and running data pipelines.
        * Compute: Section to create and manage clusters and SQL warehouses.
        * persona-based navigation
            * SQL: Focused on data analysts; enables working with SQL warehouses, dashboards, and visualizations.
            * Data Engineering: Ideal for notebook-based workflows, managing clusters, repos, and running Spark jobs.
            * Machine Learning: Adds MLflow integration for experiment tracking, model registry, and managing features.

* **What are the different types of compute available in Databricks, and how do they differ in terms of use cases?**
    * All-Purpose Compute (Standard Clusters) – For interactive development using notebooks across various languages. Ideal for exploratory data analysis, prototyping, and ad hoc jobs.
    * Job Compute (Job Clusters) – Ephemeral clusters automatically created and terminated for scheduled jobs. Optimized for cost and automation.
    * Serverless Compute for Notebooks: On-demand, scalable compute to run SQL and Python code interactively in notebooks. No infrastructure management needed.
    * Serverless Compute for Jobs: On-demand compute for running Databricks jobs automatically, without manual infrastructure configuration.
    * Instance Pools: Compute that pre-allocates idle, ready-to-use instances to reduce start times for clusters and autoscaling.
    * Serverless SQL Warehouses: On-demand, elastic compute designed for running SQL queries in the SQL editor or notebooks with high concurrency.
    * Classic SQL Warehouses: Provisioned SQL compute for running SQL commands on data, similar to serverless SQL warehouses but with fixed resources.

* **How do you configure cluster resources (memory, cores, autoscaling) based on your workload requirements?**
    * To configure cluster resources in Databricks:
    * Memory and Cores: When setting up the cluster, you can choose the instance type (e.g., Standard_DS3_v2, r5.xlarge), which defines the memory and core count. You can adjust the number of worker nodes based on the expected workload size.
    * Autoscaling: Enabling autoscaling ensures that the cluster scales up or down based on the workload's resource demands, which helps reduce costs when the workload is lighter. Autoscaling helps balance performance and resource utilization.
    * Custom Configurations: You can further customize Spark settings (e.g., spark.executor.memory, spark.executor.cores, etc.) in the advanced cluster settings, tailoring them to specific workloads like heavy transformations or ML jobs.

* **How would you monitor and troubleshoot Spark job execution in Databricks?**
    * Spark UI: Use the Spark UI to visualize job stages, tasks, and their execution times. It provides insights into bottlenecks and stages where failures or delays occur.
    * Job Logs: Check the driver and executor logs in the Databricks UI to diagnose any errors or exceptions that occur during the job.
    * Job Dashboard: Use the Databricks Job UI to monitor the status of automated jobs and check for retries or failures.
    * Cluster Metrics: Monitor resource usage metrics (memory, CPU) from the cluster details page to ensure that resource allocation is adequate.

* **How do you optimize Spark performance in Databricks?**
  *  Partition data appropriately based on query patterns
  * Use caching strategically for frequently accessed data
  * Configure the right cluster size and instance types for your workload
  * Use Delta Lake's `OPTIMIZE` command for file compaction
  * Enable Photon engine for compatible workloads

* **Explain the high-level architecture of Databricks.**
    * Control Plane: Managed by Databricks. It hosts services such as the web application, job scheduler, notebooks, cluster manager, and APIs. It is responsible for orchestration, management, and user interfaces.
    * Compute Plane: This is where user data is processed.
        * In classic compute, resources run in the customer's cloud environment (like AWS or Azure).
        * In serverless compute, Databricks manages the compute resources in its own account.

* **Explain the key differences between a data warehouse, a data lake, and a lakehouse.**
    * A Data Warehouse stores structured data optimized for fast SQL-based analytics, often with predefined schema and strict governance.
    * A Data Lake stores raw, unstructured, or semi-structured data at scale, typically in formats like JSON, Parquet, or CSV, with minimal governance upfront.
    * A Lakehouse combines the best of both — it supports the raw data storage flexibility of a lake with the transactional, governance, and performance capabilities of a warehouse, using formats like Delta Lake.
  
* **What is Delta Lake and what advantages does it provide over traditional file formats?**
  * Delta Lake is an open-source storage layer that brings ACID transactions to Apache Spark and big data workloads.
  * Advantages include: Time travel (data versioning), schema enforcement, ACID transactions, audit history, optimized data layout, and unified batch/streaming processing.
  * Delta Lake solves common data lake challenges like handling schema evolution and ensuring data quality and consistency.

* **What is the medallion architecture?**
    * The medallion architecture is a layered data design pattern used in lakehouses to improve data quality and optimize processing. It typically consists of three layers:
        * Bronze layer: Raw, ingested data — often in its original format (e.g., JSON, CSV). Minimal transformation is applied.
        * Silver layer: Cleaned and enriched data — involves deduplication, type casting, filtering, and joins.
        * Gold layer: Business-level data — highly curated data used for analytics and reporting; often aggregates or key metrics.

* **What does ETL stand for, and what happens in each stage?**
    * ETL stands for Extract, Transform, Load:
        * Extract: Data is collected from source systems (e.g., databases, APIs, files).
        * Transform: Data is cleaned, filtered, joined, aggregated, and enriched to match business needs.
        * Load: Transformed data is loaded into the destination system (like a data warehouse or lakehouse).

* **What is the difference between managed and external tables in Databricks?**
  * Managed tables: Both metadata and data are controlled by Databricks. Dropping a managed table deletes both the metadata and the underlying data.
  * External tables: Only metadata is managed by Databricks; data resides in external locations. Dropping an external table only removes the metadata while preserving the underlying data.

* **What are the common ways to authenticate Databricks clusters to access external AWS or Azure resources, and how do these methods differ?**
    * AWS: Databricks uses IAM roles for cluster access to AWS resources (like S3, Redshift, etc.), which can be assigned directly to the cluster. This method ensures secure, seamless access without requiring access keys.
    * Azure: Databricks uses Service Principal authentication or Azure Managed Identity for accessing Azure resources such as Azure Data Lake or Azure Blob Storage. Managed Identity is a more secure option as it doesn't require storing secrets.

* **A data engineer has a job with multiple tasks that runs nightly. Each task runs slowly because the clusters take a long time to start. Which cluster type should the data engineer choose to improve the startup time for clusters used by the job?**
    * Instance Pools would be the best choice to improve cluster startup times.
    * Instance pools provide pre-warmed, idle instances that are ready for use, which significantly reduces the time it takes to start clusters compared to provisioning new clusters from scratch.
    * They reduce the startup time for each task in the job, improving overall job performance.

## IMPORTANCE: Preferred

[Back to top](#unit)

* **What is Delta Live Tables (DLT), and how does it improve the ETL pipeline process?**
    * Delta Live Tables (DLT) is a framework provided by Databricks that simplifies the creation and management of ETL pipelines. It automates the ingestion, transformation, and validation of data in Delta Lake, while ensuring data quality. DLT helps with:
        * Data pipeline automation: It allows for easy orchestration and management of ETL workflows.
        * Data quality and validation: DLT automatically validates data against predefined rules.
        * Performance optimization: DLT manages data processing efficiently using Delta Lake’s capabilities like ACID transactions and incremental processing.

* **What is Unity Catalog in Databricks and how does it differ from legacy access controls?**
   *  Unity Catalog provides a unified governance solution for all data and AI assets in Databricks.
   *  Unlike traditional ACLs, it offers fine-grained access control at the catalog, schema, table, column, and even row levels, and supports centralized management across workspaces.
  
*  **What is a UDF in Spark and when would you use it?**
   *  A UDF (User-Defined Function) allows you to apply custom logic not available in built-in functions. 
   *  It's used when transformations involve logic too complex for SQL or PySpark functions.
   *  example: Clean and Mask Email Addresses

* **How do you pass parameters to a Databricks job?**
  * You can pass parameters to a Databricks job through multiple methods:
  * Jobs UI: 
    * When creating or editing a job in the UI, there's a section called "Parameters" where you can pass key-value pairs.
    * These are available in the notebook using `dbutils.widgets.get("parameter_name")`.
  * Databricks CLI:
    * You can submit a job run with parameters using the databricks jobs run-now command with the --notebook-params flag
  * REST API:
    * You can trigger jobs and pass parameters via a JSON payload to the Jobs Run Now API.
  * Notebook Access:
    * As mentioned, you can use `dbutils.widgets` to retrieve parameters
    
* **Explain how you would schedule a notebook job to run daily at 2 AM.**
  * Go to the Jobs tab in the Databricks workspace.
  * Click “Create Job”.
  * Attach the desired notebook to the job.
  * Under the “Schedule” section:
  * Choose “Recurring”.
  * Enter the schedule using a CRON expression.
    * For running at 2 AM every day: `0 2 * * * `
    * This follows standard UNIX CRON syntax: “minute hour day month day-of-week”.
  * Optionally, set timezone, retry policies, and email alerts.

* **Your company needs to implement a solution where data scientists can query sales data but should not see customer PII (Personally Identifiable Information). How would you implement this in Databricks?**
  *  Implement Unity Catalog with column-level access controls
  * Create table views that exclude PII columns for general access
  * Set up row-level security if certain data scientists should only see specific regions
  * Use dynamic masking on sensitive columns like email, phone numbers
  * Create specific roles with limited permissions and assign data scientists to these roles
  * Implement audit logging to track access patterns
  * Consider using UDFs to mask sensitive data during query execution

## Importance: Stretch

[Back to top](#unit)

* **How do you authenticate to Databricks using the CLI?**
  * There are multiple methods to authenticate to Databricks using the CLI:
  * Databricks Personal Access Token (PAT) Authentication:
    * The most common method where you generate a personal access token from your Databricks account and configure it with the CLI. You can authenticate using the following command:
    * `databricks configure --token`
    * You will be prompted for your Databricks workspace URL and personal access token.
  * OAuth Machine-to-Machine (M2M) Authentication:
    * Used for machine-to-machine communication where you authenticate using an OAuth token issued for a service principal. This method is useful when integrating Databricks with other applications in a secure and automated manner.
  * OAuth User-to-Machine (U2M) Authentication:
    * Involves authenticating using OAuth credentials associated with a user identity. This is often used for scenarios where human interaction is needed but with automated tools.