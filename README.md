Q: How does the storage auto scaling in rds happens or how does the size of the rds increases?

<details>
  <summary>Click to view Answer</summary>

- You can't reduce the amount of storage for a DB instance after storage has been allocated. When you increase the allocated storage, it must be by at least 10 percent. If you try to increase the value by less than 10 percent, you get an error. Scaling storage for RDS for SQL Server DB instances is supported only for the General Purpose SSD and Provisioned IOPS SSD storage types. [Increasing DB instance storage capacity](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIOPS.ModifyingExisting.html)
- You must set the maximum storage threshold to at least 10% more than the current allocated storage. We recommend setting it to at least 26% more to avoid receiving an event notification that the storage size is approaching the maximum storage threshold.
- For example, if you have DB instance with 1000 GiB of allocated storage, then set the maximum storage threshold to at least 1100 GiB. If you don't, you get an error such as Invalid max storage size for engine_name. However, we recommend that you set the maximum storage threshold to at least 1260 GiB to avoid the event notification. [Managing capacity automatically with Amazon RDS storage autoscaling](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIOPS.Autoscaling.html)
- Storage optimization can take several hours. You can't make further storage modifications for either six (6) hours or until storage optimization has completed on the instance, whichever is longer. 

</details>

---

Q: How does RDS changes to Secondary Instance when Primiary instance fails, if it fails does RDS changes the endpoint which changed to Secondary DB?

<details>
  <summary>Click to view Answer</summary>

- Implementing disaster recovery. You can promote a read replica to a standalone instance as a disaster recovery solution if the primary DB instance fails.[Working with DB instance read replicas](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html)
- Yes, in an Amazon RDS Multi-AZ setup, the endpoint will remain the same after a failover to the secondary DB instance. This ensures a seamless transition for applications without requiring any manual intervention or changes to the application's database connection settings.
- During a failover:
  - RDS updates the DNS record to point to the secondary instance (now promoted to primary).
  - The failover typically completes in 1–2 minutes, and applications can reconnect using the same endpoint without any changes to their configuration.
  - This ensures seamless failover for applications, as they don’t need to know which instance is primary or update connection strings.
- Why This Works:
  - RDS uses a CNAME DNS record for the endpoint, which can be updated to point to the new primary’s IP address during failover.
  - Applications experience a brief interruption (usually 60–120 seconds), but no manual intervention or code changes are needed.

</details>

---

Q: EC2 instance DB vs RDS DB Instance, Why do we preffer RDS DB Instance?

<details>
  <summary>Click to view Answer</summary>

| **Feature**               | **Amazon RDS**                                                                                         | **Amazon EC2**                                                                                             |
|---------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| **Definition**            | Managed Database-as-a-Service (DBaaS) for relational databases.                                        | Virtual server where you manually install and manage your database engine.                                 |
| **Supported Engines**     | MySQL, MariaDB, PostgreSQL, Oracle, SQL Server                                                        | Any database engine/version you want.                                                                      |
| **Administration**        | Fully managed by AWS: provisioning, patching, backups, recovery.                                       | Full control, but you manage all tasks including setup, patching, backups, and failover.                   |
| **High Availability**     | Built-in multi-AZ deployments with automatic failover.                                                 | Must be configured manually (e.g., clustering, replication).                                               |
| **Backups**               | Automated daily backups, point-in-time recovery, and snapshots supported.                             | Manual setup required. CloudWatch can't monitor backup status natively.                                    |
| **Scalability**           | Click-based vertical scaling and automatic read replicas.                                              | Manual architecture design needed (load balancing, sharding, clustering).                                  |
| **Performance**           | Provisioned IOPS for consistent high performance; integrated with CloudWatch.                         | Depends on EBS and instance type; external tools needed for monitoring.                                    |
| **Storage Options**       | General Purpose SSD, Provisioned IOPS SSD, Magnetic.                                                   | Up to 16,000 IOPS and 2,000 Mbps using EBS-optimized instances.                                             |
| **Support & Control**     | Limited to AWS-supported engines/versions; limited OS/database control.                               | Full control over OS, software stack, and database configuration.                                          |
| **Security**              | Encryption at rest & in transit managed by AWS.                                                       | Must configure EBS-level or database-level encryption manually.                                             |
| **Licensing**             | Offers License Included & BYOL (depends on DB engine). SQL Server supports only License Included.     | BYOL supported for all engines.                                                                            |
| **Cost**                  | Higher, as AWS handles most maintenance and management tasks.                                          | Lower, but requires time and effort for manual setup and management.                                       |
| **Ease of Use**           | Simple API calls and console usage for deployment, management, and scaling.                           | Complex setup and management process, but maximum flexibility.                                             |
| **Monitoring**            | Integrated with Amazon CloudWatch.                                                                    | Requires third-party tools or custom scripts.                                                              |
| **Disaster Recovery**     | PITR (Point-In-Time Recovery) supported for last 7 days; automated backups.                           | You must manually implement and test your DR plan.                                                         |
| **Read Replicas**         | Native support for read replicas, which can be regionally distributed.                                | Requires manual setup of replication and query routing.                                                    |
| **When to Choose**        | Preferable when reducing management overhead and ensuring automation.                                 | Suitable when you need full control, unsupported DB versions, or have a tight budget.                      |
| **KuebOps Recommendation**| RDS is recommended due to time and cost savings from reduced maintenance overhead.                     | Use EC2 if specific database requirements are not met by RDS or for cost-saving with in-house expertise.   |

</details>
