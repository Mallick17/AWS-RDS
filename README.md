## Pricing Components and Options

| **Component**                  | **Description**                                                                 | **Billing Details**                                                                 |
|--------------------------------|---------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| DB Instance Hours              | Time your database runs, based on instance class                                | Billed per second, minimum 10 minutes                                               |
| Storage                        | Provisioned storage capacity, prorated if scaled                                | Per GiB per month, General Purpose SSD (20 GiB-64 TiB), Provisioned IOPS SSD (100 GiB-64 TiB) |
| I/O Requests                   | Total storage I/O requests for magnetic storage only                            | Per 1 million requests                                                              |
| Provisioned IOPS               | Rate for Provisioned IOPS (SSD) and General Purpose (SSD) gp3 storage           | Billed per second, minimum 10 minutes                                               |
| Backup Storage                 | Storage for automated backups and snapshots                                     | Metered in GB-month, per second billing does not apply                              |
| Data Transfer                  | Data in/out of DB instance to/from internet and other AWS Regions               | Free within same AZ, $0.01/GB cross-AZ/Region, 100 GB/month free out to internet (new customers, excluding China/GovCloud) |
| Public IPv4 Addresses          | Standard charges for public IPv4 in VPC                                         | Refer to VPC pricing                                                                |

| **Purchasing Option**          | **Description**                                                                 | **Details**                                                                 |
|--------------------------------|---------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| On-Demand Instances            | Pay by the hour, no long-term commitments                                       | Billed per second, minimum 10 minutes, ideal for short-term needs           |
| Reserved Instances             | Commit to 1-3 years for up to 69% discount                                      | No, Partial, or All Upfront options, suitable for steady workloads          |
| Free Tier                      | 12 months free for new customers                                                | 750 hours/month on select Single-AZ, 20 GB SSD, 20 GB backup, then standard rates |

<details>
  <summary>Amazon RDS Pricing Model Explained in Detail</summary>

### Amazon RDS Pricing Model

Amazon Relational Database Service (Amazon RDS) is a fully managed cloud database service provided by AWS, designed to simplify the setup, operation, and scaling of relational databases. As of April 9, 2025, its pricing model is structured to accommodate various usage patterns, offering flexibility through on-demand and reserved instances, with additional costs for storage, I/O, backups, and data transfer. This section provides a comprehensive analysis, including all relevant details from the official AWS documentation and pricing pages.

#### Pricing Components: Breakdown of Costs

The Amazon RDS pricing model includes several key components, each billed based on usage and configuration. Below is a detailed breakdown:

- **DB Instance Hours**:
  - **Description**: You are charged for the time your database instance is running, based on the instance class (e.g., db.t2.small, db.m4.large).
  - **Billing Details**: Billed per second with a minimum of 10 minutes. This reflects the compute capacity used, starting when the instance is available and ending on deletion or failure.
  - **Use Case**: Ideal for short-term or variable workloads where flexibility is key.
  - **Stopped Instances**: Note that stopped instances are not charged for instance hours but are still charged for storage, ensuring cost efficiency for paused workloads.

- **Storage**:
  - **Description**: Charged per GiB of provisioned storage capacity per month.
  - **Billing Details**: Costs are prorated if storage is scaled within the month. RDS offers two primary storage options:
    - **General Purpose (SSD)**: Ranges from 20 GiB to 64 TiB, cost-effective for medium-sized databases, suitable for development, testing, and non-latency-sensitive workloads.
    - **Provisioned IOPS (SSD)**: Ranges from 100 GiB to 64 TiB, with 1000-256,000 IOPS, charged for both storage and provisioned IOPS. Ideal for I/O-intensive, low-latency workloads.
  - **Use Case**: General Purpose SSD is recommended for cost savings on standard applications, while Provisioned IOPS is for performance-critical databases.

- **I/O Requests**:
  - **Description**: Applies to Amazon RDS magnetic storage only, charged per 1 million I/O requests.
  - **Billing Details**: Less relevant for modern workloads, as SSD storage (General Purpose and Provisioned IOPS) is more commonly used and does not incur I/O request charges.
  - **Use Case**: Primarily for legacy setups using magnetic storage, which is being phased out for performance reasons.

- **Provisioned IOPS**:
  - **Description**: For Provisioned IOPS (SSD) and General Purpose (SSD) gp3 storage, you are charged per IOPS per month.
  - **Billing Details**: Billed per second with a minimum of 10 minutes, ensuring flexibility for scaling IOPS as needed.
  - **Use Case**: Critical for databases requiring consistent, low-latency I/O performance, such as large transactional systems.

- **Backup Storage**:
  - **Description**: Charged for the storage used by automated backups and manual snapshots.
  - **Billing Details**: Metered in GB-month, with costs increasing based on retention period or additional snapshots. Per-second billing does not apply, making it a fixed cost component.
  - **Use Case**: Essential for disaster recovery and compliance, with costs scaling with backup retention policies.

- **Data Transfer**:
  - **Description**: Charges apply for data transferred in and out of your DB instance to/from the internet or other AWS Regions.
  - **Billing Details**:
    - Free within the same Availability Zone and for Multi-AZ replication.
    - Cross-AZ or cross-Region transfers incur charges, typically $0.01/GB for EC2 regional data transfer.
    - New AWS customers get 100 GB/month of free data transfer out to the internet under the Free Tier (excluding China and GovCloud).
    - Additional charges for DB snapshot copies across Regions and cross-Region automated backups.
  - **Use Case**: Important for applications with global distribution, with free intra-zone transfers reducing costs for localized setups.

- **Public IPv4 Addresses**:
  - **Description**: Standard public IPv4 address charges apply if your RDS instance is in a VPC and uses public IPv4 addresses.
  - **Billing Details**: Refer to VPC pricing for details, typically a small additional cost for public-facing databases.
  - **Use Case**: Relevant for databases accessible over the public internet, such as web applications.

#### Purchasing Options: Flexibility for Different Needs

Amazon RDS offers two primary purchasing models for DB instances, each catering to different workload patterns:

- **On-Demand Instances**:
  - **Description**: Pay for compute capacity by the hour with no long-term commitments.
  - **Billing Details**: Billed in one-second increments with a 10-minute minimum, ensuring granular cost tracking.
  - **Discounts and Features**: No upfront payment required, recommended for short-term, spiky, or unpredictable workloads.
  - **Use Case**: Ideal for development, testing, or applications with variable demand, offering flexibility without long-term contracts.

- **Reserved Instances**:
  - **Description**: Reserve a DB instance for a 1-year or 3-year term to receive significant discounts (up to 69% compared to On-Demand).
  - **Billing Details**: Payment options include No Upfront (pay monthly over the term), Partial Upfront (portion upfront, rest monthly), or All Upfront (full payment at start).
  - **Discounts and Features**: Allows launching, deleting, starting, and stopping multiple instances within an hour without additional charges, ensuring operational flexibility.
  - **Use Case**: Suitable for long-term, steady-state workloads or mission-critical applications, offering cost savings for predictable usage.

- **Free Tier**:
  - **Description**: Available to new AWS customers for 12 months, providing a cost-effective entry point.
  - **Billing Details**: Includes 750 hours per month on select Single-AZ Instance databases (MySQL, MariaDB, PostgreSQL, or SQL Server Express Edition), 20 GB General Purpose SSD storage, and 20 GB backup storage.
  - **Discounts and Features**: Billed at standard rates after exceeding free tier limits or after 12 months.
  - **Use Case**: Ideal for startups, small projects, or testing, reducing initial costs for new users.

#### Extended Support: An Unexpected Detail

An unexpected detail in the pricing model is the option for **Extended Support**, available for MySQL, PostgreSQL, and Aurora. This feature provides critical security fixes and bug fixes for up to 3 years post-community end-of-life, ensuring continued support for legacy versions. It is priced per vCPU/hour for provisioned instances and per Aurora Capacity Unit (ACU)/hour for Aurora Serverless v2, with costs varying by calendar date. This is particularly useful for organizations needing to maintain older database versions for compliance or legacy application support, adding a layer of flexibility not commonly found in other cloud database services.

#### Cost Reduction Strategies and Tools

To optimize costs, AWS recommends several strategies:

- **Rightsizing**: Choose an instance class and storage type that match your workload needs, avoiding overprovisioning.
- **Aurora Serverless v2**: Automatically scales capacity based on demand, reducing costs for variable workloads.
- **Auto-Scaling**: Dynamically adjust resources to optimize performance and cost.
- **Reserved Instances**: Commit to long-term usage for significant discounts, with the ability to purchase up to 40 Reserved Instances (contact AWS for more via [contact form](https://aws.amazon.com/contact-us/request-to-increase-the-amazon-rds-db-instance-limit/)).
- **Tools**: Use the **AWS Pricing Calculator** ([AWS Pricing Calculator](https://calculator.aws/)) to estimate costs based on specific usage scenarios. For pricing assistance, contact AWS sales support ([Get pricing assistance](https://aws.amazon.com/contact-us/sales-support-pricing/)).

#### Billing and Tax Considerations

- **Billing Start/End**: Billing starts when your DB instance is available and ends on deletion or failure. Stopped instances are charged for storage but not instance hours, ensuring cost efficiency.
- **Taxes**: Excluded unless noted, with Japanese customers subject to Consumption Tax. This ensures transparency in cost calculations.
  
</details>

---

## Comparison and Prices of the RDS Instances as of October,2025
### MySQL instance specifications
#### Common Specifications
- Nodes: 1
- Utilization (On-Demand only) --> Value = 100, Unit = %Utilised/Month
- Deployment option: Single AZ
- Pricing model: On-Demand
  
#### Instance Type: db.r6g.4xlarge
- vCPU: 16
- Memory: 128 GiB
- 1 instance(s) x 1.933 USD hourly x (100 / 100 Utilized/Month) x 730 hours in a month = 1411.0900 USD
- RDS MySQL cost (monthly): 1,411.09 USD

#### Instance Type: db.r6g.2xlarge
- vCPU: 8
- Memory: 64 GiB
- 1 instance(s) x 0.967 USD hourly x (100 / 100 Utilized/Month) x 730 hours in a month = 705.9100 USD
- RDS MySQL cost (monthly): 705.91 USD

#### Instance Type: db.t4g.small
- vCPU: 2
- Memory: 2 GiB
- 1 instance(s) x 0.042 USD hourly x (100 / 100 Utilized/Month) x 730 hours in a month = 30.6600 USD
- RDS MySQL cost (monthly): 30.66 USD

| Attribute                   | **db.r8g.large (Graviton4, DDR5)** | **db.r6g.large (Graviton2, DDR4)** | Notes                                                                              |
| --------------------------- | ---------------------------------- | ---------------------------------- | ---------------------------------------------------------------------------------- |
| **vCPU**                    | 2                                  | 2                                  | Same number of vCPUs                                                               |
| **Memory (GiB)**            | 16                                 | 16                                 | Same memory capacity                                                               |
| **Memory Type**             | DDR5                               | DDR4                               | DDR5 offers higher memory bandwidth                                                |
| **Memory Bandwidth**        | 12.5 Gbps                          | 10 Gbps                            | ~25% higher in R8g                                                                 |
| **EBS Throughput**          | 10 Gbps                            | 4.7 Gbps                           | ~112% higher in R8g                                                                |
| **Throughput**              | 41% higher                         | Baseline                           | “Throughput” here refers to overall data transfer rate performance (I/O + network) |
| **Latency**                 | 29% lower                          | Baseline                           | Latency is improved (lower is better)                                              |
| **Cost per Hour (approx.)** | $0.2720                            | $0.2420                            | R8g is ~12% more expensive                                                         |
| **Processor Type**          | Graviton4                          | Graviton2                          | Graviton4 = latest generation, better efficiency                                   |
| **On-Memory Encryption**    | ✅ Yes                              | ✅ Yes                              | Both support it, but Graviton4 has improved memory bandwidth                       |

<details>
    <summary>Click to view Related articles and Documentation</summary>

RDS Instance Types with db.r8g.
https://aws.amazon.com/rds/instance-types/
 
EC2 Instance Types with r8g
https://aws.amazon.com/ec2/instance-types/r8g/
 
EC2 Instance with r6g
https://aws.amazon.com/ec2/instance-types/r6g/
  
</details>

---
