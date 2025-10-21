## Purchasing Options: Flexibility for Different Needs

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
