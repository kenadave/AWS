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

15) Make use of an IPAM, such as the Amazon VPC IP Address Manager, to monitor and manage your CIDR use. 
You can use IPAM to do the following:
Organize IP address space into routing and security domains
Monitor IP address space that's in use and monitor resources that are using space against business rules
View the history of IP address assignments in your organization
Automatically allocate CIDRs to VPCs using specific business rules
Troubleshoot network connectivity issues
Enable cross-region and cross-account sharing of your Bring Your Own IP (BYOIP) addresses
Provision Amazon-provided contiguous IPv6 CIDR blocks to pools for VPC creation

16) Identify overlapping IP ranges. You can either migrate to a new range of addresses or consider using techniques like private NAT Gateway or AWS PrivateLink if you need to connect the overlapping ranges.
End of support notice: On September 30, 2026, AWS will discontinue support for AWS App Mesh. After September 30, 2026, you will no longer be able to access the AWS App Mesh console or AWS App Mesh resources.
AWS Cloud Map is a cloud resource discovery service. With Cloud Map, you can define custom names for your application resources, and it maintains the updated location of these dynamically changing resources. This increases your application availability because your web service always discovers the most up-to-date locations of its resources.



=========================================================================

What problem?
What architecture pattern fixes it?
which AWS Service implements it?

=========================================================================

Idempotency is also an important behavior of event-driven architectures. These architectures are typically backed by a message queue such as Amazon SQS, Amazon MQ, Amazon Kinesis Streams, or Amazon Managed Streaming for Apache Kafka (MSK).

If your workload leverages AWS Lambda functions, consider Powertools for AWS Lambda. Powertools for AWS Lambda is a developer toolkit that helps implement serverless best practices and increase developer velocity when you work with AWS Lambda functions. In particular, it provides a utility to convert your Lambda functions into idempotent operations which are safe to retry.

If a dependency fails: Don't crash; show "Stale" or "Partial" data.
If the DB is slow: Use Read Replicas for reads and SQS for writes.
If an update fails halfway: Use Step Functions (Saga Pattern) to roll back.
If the network is flaky: Use Retries with Exponential Backoff and Jitter.

You will see this algorithm mentioned specifically with Amazon API Gateway.
Standard Limit: The steady refill rate.
Burst Limit: The maximum bucket size.
Exam Tip: If a question asks how to handle a sudden, short-lived spike in traffic without failing, ensure your Burst Limit (Bucket Size) is high enough to handle that initial wave.

Amazon API Gateway implements the token bucket algorithm according to account and region limits and can be configured per-client with usage plans. Additionally, Amazon Simple Queue Service (Amazon SQS) and Amazon Kinesis can buffer requests to smooth out the request rate, and allow higher throttling rates for requests that can be addressed. Finally, you can implement rate limiting with AWS WAF to throttle specific API consumers that generate unusually high load.

You can configure API Gateway with throttling limits for your APIs and return 429 Too Many Requests errors when limits are exceeded. You can use AWS WAF with your AWS AppSync and API Gateway endpoints to enable rate limiting on a per IP address basis.

=========================================================================

API Gateway => Throttling limits
WAF on API Gateway & AppSync => rate limiting rules
More throttling control => API Gateway+AppSync
SQS+Lambda => maximum concurrency
API Gateway+SQS/Kinesis => Buffer requests

=========================================================================


If your Lambda consistently takes longer than 29 seconds, AWS generally recommends these alternatives rather than just increasing the timeout: 
Asynchronous Pattern: Have the first Lambda function receive the request, trigger a second "worker" Lambda asynchronously, and immediately return a "202 Accepted" response to the client.
Step Functions: Use AWS Step Functions to manage long-running workflows, allowing the client to poll for a status or receive a notification via Amazon SNS when finished.
WebSockets: For real-time updates without polling, consider using API Gateway WebSockets.


Configuring first in first out (FIFO) queues when last in first out (LIFO) queues would better serve client needs, for example when strict ordering is not required and backlog processing is delaying all new and time sensitive requests resulting in all clients experiencing breached service levels.

=========================================================================

SAA-C03 Exam Tips:
Scenario A: "You need to troubleshoot a specific application error that happened 10 minutes ago." → Choose CloudWatch Logs Insights.
Scenario B: "You need to analyze 2 years of VPC Flow Logs for security auditing with the lowest cost." → Choose S3 + Athena.
Scenario C: "A business analyst wants to create a QuickSight dashboard from log data." → Choose Athena (it integrates natively as a data source for BI tools).


=========================================================================


1. Native Alarm Actions
These are built-in options you select when creating the alarm in the CloudWatch Console. They trigger immediately upon a state change (e.g., OK to ALARM). 

SNS Notifications: The most common action; sends messages to people (email/SMS) or downstream services.
EC2 Actions: Automatically stop, terminate, reboot, or recover an instance.
Auto Scaling Actions: Triggers scaling policies to add or remove capacity.
Systems Manager (SSM) Actions: Creates OpsItems or Incidents to track operational issues. 

2. EventBridge: The "Perform Anything Else" Lever 
While native actions are powerful, they are limited to the list above. For anything else—like running a Lambda function directly or updating a database—you use Amazon EventBridge. 

How it works: Every time an alarm changes state, CloudWatch automatically sends a "State Change" event to the EventBridge default bus.
Custom Rules: You create an EventBridge Rule that matches those alarm events and sends them to a target, such as:
AWS Lambda: To execute custom remediation code.
SSM Automation: To run complex runbooks.
Step Functions: To orchestrate a multi-step recovery workflow. 

Exam Scenario Summary
Scenario: "Notify the team via email if CPU is high." → Use SNS.
Scenario: "Automatically fix a crashed instance." → Use EC2 Reboot/Recover.
Scenario: "Run a custom Python script to clear disk space." → Use EventBridge to trigger Lambda.

=========================================================================

Amazon EventBridge is recommended when you want to build an application that reacts to events from your own applications, SaaS applications, and AWS services. EventBridge is the only event-based service that integrates directly with third-party SaaS partners. EventBridge also automatically ingests events from over 200 AWS services without requiring developers to create any resources in their account.

=========================================================================

Amazon SNS is recommended for applications that need high fan out (thousands or millions of endpoints). A common pattern we see is that customers use Amazon SNS as a target for their rule to filter the events that they need, and fan out to multiple endpoints.

=========================================================================

Use X-Ray tracing for Amazon CloudWatch Synthetic Canaries and Amazon CloudWatch RUM to analyze the request path from your end user client through your downstream AWS infrastructure.

=========================================================================

Select the appropriate automatic scaling mechanism for the component. For Amazon EC2 instances, use Amazon EC2 Auto Scaling. For other AWS services, use Application Auto Scaling. For Kubernetes pods (such as those running in an Amazon EKS cluster), consider Horizontal Pod Autoscaler (HPA) or Kubernetes Event-driven Autoscaling (KEDA). For Kubernetes or EKS nodes, consider Karpenter and Cluster Auto Scaler (CAS).

=========================================================================

Define your applications in AWS Resilience Hub. Resilience assessments generate code snippets that help you create recovery procedures as AWS Systems Manager documents for your applications and provide a list of recommended Amazon CloudWatch monitors and alarms.

