1) Use AWS Budgets to get alerts for unacceptable costs.

Use AWS Compute Optimizer or AWS Trusted Advisor to get cost optimization recommendations.

Use AWS Cost Anomaly Detection to get automated cost anomaly detection and root cause analysis.

2) AWS Batch	Efficiently and dynamically provisions and scales Amazon Elastic Container Service (Amazon ECS), Amazon Elastic Kubernetes Service (Amazon EKS), and AWS Fargate compute resources, with an option to use On-Demand or Spot Instances based on your job requirements	HPC, train ML models

3) Amazon Lightsail	Preconfigured Linux and Windows application for running small workloads	Simple web applications, custom website

4) Storage-optimized instances are designed for workloads that require high, sequential read and write access (IOPS) to local storage.

5) AWS provides tools such as AWS Compute Optimizer and AWS Trusted Advisor that use historical data to provide recommendations to right-size your compute resources.

6) For ephemeral workloads, evaluate instance Amazon CloudWatch metrics such as CPUUtilization to identify if the instance is under-utilized or over-utilized.

For stable workloads, check AWS rightsizing tools such as AWS Compute Optimizer and AWS Trusted Advisor at regular intervals to identify opportunities to optimize and right-size the compute resource.

7) Kubernetes Cluster Autoscaler/Karpenter	To automatically scale Kubernetes clusters.

8) Document database	Amazon DocumentDB	Designed to store semi-structured data as JSON-like documents. These databases help developers build and update applications such as content management, catalogs, and user profiles quickly.

9) Time Series database	Amazon Timestream	Used to efficiently collect, synthesize, and derive insights from data that changes over time. IoT applications, DevOps, and industrial telemetry can utilize time-series databases.

10) Wide column	Amazon Keyspaces (for Apache Cassandra)	Uses tables, rows, and columns, but unlike a relational database, the names and format of the columns can vary from row to row in the same table. You typically see a wide column store in high scale industrial apps for equipment maintenance, fleet management, and route optimization.

11) For high-throughput read as-is transactional processing, consider a NoSQL database such as DynamoDB.

For high-throughput and complex read patterns (like join) with consistency use Amazon RDS.

For analytical queries, consider a columnar database such as Amazon Redshift or exporting the data to Amazon S3 and performing analytics using Athena or Amazon Quick.

12) Aurora automatically replicates your data across three Availability Zones within a Region, meaning your data is highly durable with less chance of data loss.

DynamoDB is automatically replicated across multiple Availability Zones, providing high availability and data durability.

13) 
