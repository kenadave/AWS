1) AWS Trusted Advisor offers a service quota check that displays your usage and quotas for some aspects of some services. It can aid in identifying services that are near quota.

2) AWS Management Console provides methods to display services quota values, manage, request new quotas, monitor status of quota requests, and display history of quotas.

3) AWS CLI and CDKs offer programmatic methods to automatically manage and monitor service quota levels and usage.

4) Choosing a design that cannot scale or be modified if fixed service quotas are to be exceeded. For example, an SQS payload size of 256KB.

5) Hard limits are shown in the Service Quotas console. If the columns shows ADJUSTABLE = No, the service has a hard limit. Hard limits are also shown in some resources configuration pages. For example, Lambda has specific hard limits that cannot be adjusted.

6) For example, Quota Monitor for AWS can provide automated monitoring of service quotas. This tool integrates with AWS Organizations and deploys using Cloudformation StackSets so that new accounts are automatically monitored on creation.

7) Use features such as Service Quotas request templates or AWS Control Tower to simplify Service Quotas setup for new accounts.

8) When a usage quota continues to account for a resource after you have finished using it, it creates a lack of a "sufficient gap" or buffer between your current usage and your maximum limits. 

This situation can lead to failing or inaccessible resources in the following ways:
Blocking Replacements: If a resource fails and needs to be replaced, the quota system may still "see" the old, failed resource as active. If you are already at or near your limit, the system will reject the creation of the new replacement resource because it would technically exceed the quota.
Failed Failover: During a network or Regional failure, you may need to spin up resources in a different zone or account. If previous resources in that area were not properly cleared from the quota accounting, the failover process will fail due to "Quota Exceeded" errors.
Inconsistent State Errors: In environments like Kubernetes, there can be a misalignment where pods that are no longer consuming actual cluster resources are still counted against the namespace's ResourceQuota. This leads to unnecessary admission rejections for new workloads.
Immutable Dependency Chains: Some resources cannot be fully cleared until their dependent objects are deleted (e.g., an S3 bucket must be empty). If these dependencies linger, the parent resource continues to count against your quota, preventing you from allocating that "space" to new tasks. 

Common Error Codes:
AWS/Azure: OperationNotAllowed or ResourceQuotaExceeded.


9) Because Route 53 health checks monitor CloudWatch data streams instead of the state of CloudWatch alarms, you can't force the status of a health check to change by using the CloudWatch SetAlarmState API operation.

10) When using AWS Direct Connect to connect your on-premises network to AWS, you can achieve maximum network resiliency (SLA of 99.99%) by using separate connections that end on distinct devices in more than one on-premises location and more than one AWS Direct Connect location.

11) lternatively, you can achieve high resiliency (SLA of 99.9%) by using two individual connections to multiple locations (each on-premises location connected to a single Direct Connect location).

12) maximum network resiliency (SLA of 99.99%) by using separate connections that end on distinct devices in more than one on-premises location and more than one AWS Direct Connect location.

13) Alternatively, you can achieve high resiliency (SLA of 99.9%) by using two individual connections to multiple locations (each on-premises location connected to a single Direct Connect location).

14) ECMP (Equal-Cost Multi-Path) routing allows you to achieve an aggregate throughput of up to 50 Gbps by logically bonding multiple individual VPN tunnels and distributing traffic across them. 

While a standard AWS Site-to-Site VPN tunnel is capped at 1.25 Gbps, ECMP enables the following: 
-  Horizontal Scaling: By establishing multiple VPN connections to an AWS Transit Gateway and enabling ECMP, the gateway can use up to 50 parallel paths simultaneously.
-  Traffic Distribution: The Transit Gateway uses a 5-tuple hash (source/destination IP, source/destination port, and protocol) to decide which tunnel to use for a specific packet.
-  Aggregate Capacity: While no single network flow can exceed the 1.25 Gbps limit of a single tunnel, the sum of many different flows across multiple tunnels can scale up to the 50 Gbps aggregate limit.
-  Dynamic Routing Requirement: To use ECMP, your VPN must be configured with dynamic routing (BGP); static routing does not support this feature.

