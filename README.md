# Amazon Relational Database Service (Amazon RDS)
Amazon Relational Database Service (Amazon RDS) is a web service that makes it easier to set up, operate, and scale a relational database in the AWS Cloud. It provides cost-efficient, resizable capacity for an industry-standard relational database and manages common database administration tasks.
- Amazon RDS is a managed database service. It's responsible for most management tasks. By eliminating tedious manual processes, Amazon RDS frees you to focus on your application and your users.
- Amazon RDS provides the following principal advantages over database deployments that aren't fully managed:
  - You can use database engines that you are already familiar with: IBM Db2, MariaDB, Microsoft SQL Server, MySQL, Oracle Database, and PostgreSQL.
  - Amazon RDS manages backups, software patching, automatic failure detection, and recovery.
  - You can turn on automated backups, or manually create your own backup snapshots. You can use these backups to restore a database. The Amazon RDS restore process works reliably and efficiently.
  - You can get high availability with a primary DB instance and a synchronous secondary DB instance that you can fail over to when problems occur. You can also use read replicas to increase read scaling.
  - In addition to the security in your database package, you can control access by using AWS Identity and Access Management (IAM) to define users and permissions. You can also help protect your databases by putting them in a virtual private cloud (VPC).

## Features of RDS

| **Feature**                  | **On-Premises Management** | **Amazon EC2 Management** | **Amazon RDS Management** | **Notes**                                                                 |
|------------------------------|----------------------------|---------------------------|---------------------------|---------------------------------------------------------------------------|
| **Application Optimization** | Customer                   | Customer                  | Customer                  | Application tuning and optimization remain the customer's responsibility across all models. |
| **Scaling**                  | Customer                   | Customer                  | AWS                       | AWS manages scaling for RDS, while the customer handles it for on-premises and EC2. |
| **High Availability**        | Customer                   | Customer                  | AWS                       | AWS ensures high availability for RDS; customer manages it for others.     |
| **Database Backups**         | Customer                   | Customer                  | AWS                       | AWS automates backups for RDS; customer manages backups elsewhere.         |
| **Database Software Patching** | Customer                 | Customer                  | AWS                       | AWS handles database patching for RDS; customer manages it otherwise.      |
| **Database Software Install**| Customer                   | Customer                  | AWS                       | AWS performs database software installation for RDS; customer for others.  |
| **Operating System (OS) Patching** | Customer             | Customer                  | AWS                       | AWS manages OS patching for RDS; customer handles it for on-premises and EC2. |
| **OS Installation**          | Customer                   | Customer                  | AWS                       | AWS installs the OS for RDS; customer manages it for on-premises and EC2.  |
| **Server Maintenance**       | Customer                   | AWS                       | AWS                       | AWS takes over server maintenance for EC2 and RDS; customer for on-premises. |
| **Hardware Lifecycle**       | Customer                   | AWS                       | AWS                       | AWS manages hardware lifecycle for EC2 and RDS; customer for on-premises.  |
| **Power, Network, and Cooling** | Customer                | AWS                       | AWS                       | AWS provides infrastructure support for EC2 and RDS; customer for on-premises. |

## RDS Instance Families
A DB instance class determines the computation and memory capacity of a DB instance. A DB instance class consists of both the DB instance class type and the size. Amazon RDS supports the following instance class types, where the asterisk (*) represents the generation, optional attribute, and size:
- **General-purpose (db.m*):** Balanced for most applications.
- **Memory-optimized (db.r*, db.x*, db.z*):** High memory for memory-intensive tasks.
- **Compute-optimized (db.c*):** High compute for intensive applications.
- **Burstable-performance (db.t*):** Cost-effective for workloads with occasional spikes.
