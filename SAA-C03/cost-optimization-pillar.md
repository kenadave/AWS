1) You can use AWS Cost Explorer for trend-based forecasting in a defined future time range based on your past spend. AWS Cost Explorer's forecasting engine segments your historical data based on charge types (for example, Reserved Instances) and uses a combination of machine learning and rule-based models to predict spend across all charge types individually.

2) Once you've established your forecast process and built models, you can use AWS Budgets to set custom budgets at a granular level by specifying the time period, recurrence, or amount (fixed or variable) and add filters such as service, AWS Region, and tags. The budget is usually prepared for a single year and remains fixed, which requires strict adherence from everyone involved. In contrast, forecasts are more flexible, which allows for readjustments throughout the year and provides dynamic projections over a period of one, two, or three years. Both budgets and forecasts play a crucial role when you establish financial expectations among various technology and business stakeholders. Accurate forecasts and implementation also provides accountability to stakeholders who are directly responsible for provisioning cost in the first place, and it can also raise their overall cost awareness.

3) The budget is usually prepared for a single year and remains fixed, which requires strict adherence from everyone involved. In contrast, forecasts are more flexible, which allows for readjustments throughout the year and provides dynamic projections over a period of one, two, or three years.

4) Once you've determined your trend-based forecast using Cost Explorer or any other tools, use the AWS Pricing Calculator to estimate your AWS use case and future costs based on the expected usage (traffic, requests-per-second, or required Amazon EC2 instances).

5) View your cost and usage with multiple filters and granularity by using AWS Cost Explorer, which provides dashboards and reports such as costs by service or by account, daily costs, or marketplace costs. Track your progress of cost and usage against configured budgets with AWS Budgets Reports

6) AWS Cost Anomaly Detection allows you to reduce cost surprises and enhance control without slowing innovation. AWS Cost Anomaly Detection identifies anomalous spend and root causes, which helps to reduce the risk of billing surprises. With three simple steps, you can create your own contextualized monitor and receive alerts when any anomalous spend is detected.

7) You can also use Quick with AWS Cost and Usage Report (CUR) data, to provide highly customized reporting with more granular data. Quick allows you to schedule reports and receive periodic Cost Report emails for historical cost and usage or cost-saving opportunities. Check our Cost Intelligence Dashboard (CID) solution built on Quick, which gives you advanced visibility.

8) Use AWS Trusted Advisor, which provides guidance to verify whether provisioned resources are aligned with AWS best practices for cost optimization.

9) You can use AWS Cost Optimization Hub to understand potential cost-saving opportunities
consolidated from a centralized location and create data exports for integration with Amazon
Athena. You can also use the AWS Cost Optimization Hub to deploy the Cost and Usage Dashboard,
which utilizes Quick for interactive cost analysis and secure cost insight sharing.

10) If you don't have essential skills or bandwidth in your organization, you can work with AWS
ProServ, AWS Managed Services (AMS), or AWS Partners. You can also use third-party tools but
ensure you validate the value proposition.

11) Amazon RDS, Amazon Redshift, and Amazon ElastiCache provide a managed database service.
Amazon Athena, Amazon EMR, and Amazon OpenSearch Service provide a managed analytics
service.

12) If desired, you can still export CUR in legacy mode, where you can integrate other processing services such as AWS Glue to prepare the data for analysis and perform data analysis with Amazon Athena using SQL to query the data.

13) Use services such as AWS CloudFormation to verify that resources are tagged when created.

14) You can use AWS Cost Optimization Hub to understand potential cost-saving opportunities consolidated from a centralized location and create data exports for integration with Amazon Athena. You can also use the AWS Cost Optimization Hub to deploy the Cost and Usage Dashboard, which utilizes Quick for interactive cost analysis and secure cost insight sharing.

15) AWS Cost Optimization Hub tells you how to save money in the future, while the Cost and Usage Report (CUR) records exactly how you spent it in the past

16) You can use Amazon EC2 Auto Scaling or Application Auto Scaling to perform the decommissioning process. You can also implement custom code using the API or SDKto decommission workload resources automatically.

17) Modern applications are built serverless-first, a strategy that prioritizes the adoption of serverless services. AWS developed serverless services for all three layers of your stack: compute, integration, and data stores. Using serverless architecture will allow you to save costs during low-traffic periods with scaling up and down automatically.

18) Use Amazon Data Lifecycle Manager: Use lifecycle policies on Amazon Data Lifecycle Manager to automate deletion of Amazon EBS snapshots and Amazon EBS-backed AMIs.

19) For storage resources such as Amazon S3, you can use Amazon S3 Storage Lens, which allows you to see 28 metrics across various categories at the bucket level, and 14 days of historical data in the dashboard by default. You can filter your Amazon S3 Storage Lens dashboard by summary and cost optimization or events to analyze specific metrics.

20) Actionable Recommendations: It provides contextual recommendations directly in the dashboard to help you reduce costs and improve data protection (e.g., suggesting you enable default encryption or delete incomplete multipart uploads).
Organization-Wide Visibility: You can create a single view that aggregates storage data across hundreds or thousands of accounts, regions, and buckets within your AWS Organization.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Identify "Cold" Buckets: By analyzing activity metrics like retrieval rates, you can find buckets that are no longer being accessed and are prime candidates for archiving or deletion.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Granular Prefix-Level Insights: With advanced settings, you can drill down into specific prefixes (up to billions per bucket) to see which datasets are growing the fastest or are most/least active.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Performance Bottleneck Detection: It includes performance metrics (like 503 error counts and request sizes) to help identify throttling or inefficient request patterns that slow down your applications.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Custom Filtering with Groups: You can use Storage Lens groups to aggregate metrics based on custom filters like object tags, suffixes, or object age to better understand specific datasets.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Daily Data Exports: You can automatically export your metrics in CSV or Parquet format to an S3 bucket or S3 Tables for deeper analysis in Amazon Athena or Amazon QuickSight.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
CloudWatch Integration: Advanced metrics can be published to Amazon CloudWatch, allowing you to set alarms when specific thresholds (like a spike in object count or 403 errors) are met.

21) Spot Instances are ideal when there is a queue or buffer in place, or where there are multiple resources working independently to process the requests (for example, Hadoop data processing).
 Means use spot instances when need to use data sent by queue or buffer.

22) At the end of the two minutes, you have the option to hibernate, stop, or terminate the Spot Instance.

23) Commitment discounts – Savings Plans: AWS provides a number of ways for you to reduce your costs by reserving or committing to use a certain amount of resources, and receiving a discounted rate for your resources. A Savings Plan allows you to make an hourly spend commitment for one or three years, and receive discounted pricing across your resources. Savings Plans provide discounts for AWS Compute services such as Amazon EC2, AWS Fargate, and AWS Lambda. When you make the commitment, you pay that commitment amount every hour, and it is subtracted from your On-Demand usage at the discount rate. For example, you commit to $50 an hour, and have $150 an hour of On-Demand usage. Considering the Savings Plans pricing, your specific usage has a discount rate of 50%. So, your $50 commitment covers $100 of On-Demand usage. You will pay $50 (commitment) and $50 of remaining On-Demand usage.
Compute Savings Plans are the most flexible and provide a discount of up to 66%. They automatically apply across Availability Zones, instance size, instance family, operating system, tenancy, Region, and compute service.
Instance Savings Plans have less flexibility but provide a higher discount rate (up to 72%). They automatically apply across Availability Zones, instance size, operating system, and tenancy.

24) Savings plans apply first to the usage in the account they are purchased in, from the highest discount percentage to the lowest, then they apply to the consolidated usage across all other accounts, from the highest discount percentage to the lowest. 
It is recommended to purchase all Savings Plans in an account with no usage or resources, such as the management account. This ensures that the Savings Plan applies to the highest discount rates across all of your usage, maximizing the discount amount.

25) Commitment discounts – Reserved Instances/Commitment: Similar to Savings Plans, Reserved Instances (RI) offer discounts up to 72% for a commitment to running a minimum amount of resources. Reserved Instances are available for Amazon RDS, Amazon OpenSearch Service, Amazon ElastiCache, Amazon Redshift, and DynamoDB. Amazon CloudFront and AWS Elemental MediaConvert also provide discounts when you make minimum usage commitments. Reserved Instances are currently available for Amazon EC2, however Savings Plans offer the same discount levels with increased flexibility and no management overhead.

26) Reserved Instances can be purchased in a Region or a specific Availability Zone. They provide a capacity reservation when purchased in an Availability Zone.

27) 
| Feature | Zonal RI (Specific AZ) | Regional RI (Region-wide) |
| :--- | :--- | :--- |
| **Discount** | Yes | Yes |
| **Capacity Reservation** | Yes (guaranteed availability) | No |
| **AZ Flexibility** | No (locked to one AZ) | Yes (any AZ in region) |
| **Size Flexibility** | No | Yes (within family) |

28) Amazon EC2 features convertible RIs, however, Savings Plans should be used for all EC2 instances due to increased flexibility and reduced operational costs.

29) The same process and metrics should be used to track and make purchases of Reserved Instances. It is recommended to not track coverage of RIs across your accounts. It is also recommended that utilization percentage is not monitored or tracked, instead view the utilization report in Cost Explorer, and use net savings column in the table. If the net savings is a significantly large negative amount, you must take action to remediate the unused RI.

30) Workloads and usage typically change over time. It is recommended to continually purchase small amounts of Savings Plans commitment over time. This ensures that you maintain high levels of coverage to maximize your discounts, and your plans closely match your workload and organization requirements at all times.

31) Monitor the utilization and coverage, but only to detect changes. Do not aim for a specific utilization percent, or coverage percent, as this does not necessarily scale with savings. Ensure that a purchase of Savings Plans results in an increase in coverage, and if there are decreases in coverage or utilization ensure they are quantified and known. For example, you migrate a workload resource to a newer instance type, which reduces utilization of an existing plan, but the performance benefit outweighs the saving reduction.

32) Note that On-Demand Capacity reservations (ODCR) are not a pricing discount. Capacity Reservations are charged at the equivalent On-Demand rate, whether you run instances in reserved capacity or not. They should be considered when you need to provide enough capacity for the resources you plan to run. ODCRs don't have to be tied to long-term commitments, as they can be cancelled when you no longer need them, but they can also benefit from the discounts that Savings Plans or Reserved Instances provide.

33) Reserved Instances (RIs) apply first to matching usage.
Savings Plans apply second to any remaining eligible usage.
EC2 Instance Savings Plans are applied before Compute Savings Plans because they have a narrower, more specific scope.

34) 

| Commitment Type | Eligible Services |
| :--- | :--- |
| **Compute Savings Plans** | Amazon EC2, AWS Lambda, AWS Fargate |
| **EC2 Instance Savings Plans** | Amazon EC2 (specific family and region) |
| **SageMaker Savings Plans** | Amazon SageMaker |
| **Database Savings Plans** | Amazon Aurora, RDS, DynamoDB, ElastiCache, Redshift (Gen 7+ instances) |
| **Reserved Instances** | Amazon EC2, RDS, ElastiCache, OpenSearch, Redshift |

35) If your account owns both RI and SP commitments, they will be applied in this order:
COST07-BP05 Perform pricing model analysis at the management account level
112
Cost Optimization Pillar AWS Well-Architected Framework
1.
Zonal RI
2.
Standard RI
3.
Convertible RI
4.
Instance Savings Plan
5.
Compute Savings Plan

36) It is "Use it or Lose it": If you have a $10/hour commitment but only use $5 of compute between 2:00 PM and 3:00 PM, you still pay $10, and you cannot "roll over" the extra $5 to 4:00 PM [1, 5].

37) If you purchase an SP at the management account level, the savings will be applied based on highest to lowest discount percentage.

Imagine your Management Account has a Compute Savings Plan for $10/hour. Across your linked accounts, you have two different types of instances running:
Instance A (Linux in US-East-1):
On-Demand Price: $1.00/hr
Savings Plan Discount: 50% (SP Price: $0.50/hr)
Instance B (Windows in US-West-2):
On-Demand Price: $1.00/hr
Savings Plan Discount: 25% (SP Price: $0.75/hr)

38) Today, we are announcing the Amazon CloudFront Security Savings Bundle, a flexible self-service pricing plan that helps you save up to 30% on your CloudFront bill in exchange for a monthly spend commitment for a 1-year term. The savings bundle also includes free AWS WAF (Web Application Firewall) usage up to 10% of your committed amount. Any additional Standard CloudFront or WAF charges not covered by the CloudFront Security Savings Bundle still apply.

39) VPC Endpoints allow connectivity between AWS services over private networking and can be used to reduce public data transfer and NAT gateway costs. Gateway VPC endpoints have no hourly charges, and support Amazon S3 and Amazon DynamoDB. Interface VPC endpoints are provided by AWS PrivateLink and have an hourly fee and per-GB usage cost.
•
NAT gateways provide built-in scaling and management for reducing costs as opposed to a standalone NAT instance. Place NAT gateways in the same Availability Zones as high traffic instances and consider using VPC endpoints for the instances that need to access Amazon DynamoDB or Amazon S3 to reduce the data transfer and processing costs.

40) With AWS Trusted Advisor, you can provision your resources following best practices to improve system performance and reliability, increase security, and look for opportunities to save money.

41) AWS Instance Scheduler allows you to configure the stop and start of your Amazon EC2 and Amazon RDS instances at defined times so that you can meet the demand for the same resources within a consistent time pattern such as every day user access Amazon EC2 instances at eight in the morning that they don’t need after six at night.

42) You can also easily configure schedules for your Amazon EC2 instances across your accounts and Regions with a simple user interface (UI) using AWS Systems Manager Quick Setup. You can schedule Amazon EC2 or Amazon RDS instances with AWS Instance Scheduler and you can stop and start existing instances. However, you cannot stop and start instances which are part of your Auto Scaling group (ASG) or that manage services such as Amazon Redshift or Amazon OpenSearch Service. Auto Scaling groups have their own scheduling for the instances in the group and these instances are created.

43) Not all Auto Scaling features are available when you use launch configurations. For example, you cannot create an Auto Scaling group that launches both Spot and On-Demand Instances or that specifies multiple instance types. You must use a launch template to configure these features.

44) Demand-based dynamic scaling policies
•
Simple/Step Scaling: Monitors metrics and adds/removes instances as per steps defined by the customers manually.
•
Target Tracking: Thermostat-like control mechanism that automatically adds or removes instances to maintain metrics at a customer defined target.

45) You can also use attribute-based instance type selection (ABS) strategy in Auto Scaling groups, which lets you express your instance requirements as a set of attributes, such as vCPU, memory, and storage. This also allows you to automatically use newer generation instance types when they are released and access a broader range of capacity with Amazon EC2 Spot Instances.

46) Amazon EC2 Fleet and Amazon EC2 Auto Scaling select and launch instances that fit the specified attributes, removing the need to manually pick instance types.

47) 

| Feature | Systems Manager Quick Setup | AWS Instance Scheduler |
| :--- | :--- | :--- |
| **Primary Goal** | Simple, "one-click" UI setup for basic schedules. | Advanced, highly customizable automation. |
| **Supported Services** | EC2 only. | EC2, RDS, Aurora, Neptune, and more. |
| **Setup Method** | Simple UI within the Systems Manager console. | CloudFormation template that deploys Lambda, DynamoDB, and CloudWatch. |
| **Complexity** | Low: No code or manual templates needed. | High: Requires managing infrastructure and using a CLI or tagging system. |
| **Schedules** | Simple daily start/stop (e.g., 9-to-5). | Complex "spanning" schedules (e.g., run 48 hours straight). |
| **Cost** | Free (standard AWS service usage only). | Paid (costs for Lambda executions and DynamoDB storage). |

48) Instead of manually choosing instance types for your mixed instances group, you can specify a set of instance attributes that describe your compute requirements. As Amazon EC2 Auto Scaling launches instances, any instance types used by the Auto Scaling group must match your required instance attributes. This is known as attribute-based instance type selection.

This approach is ideal for workloads and frameworks that can be flexible about which instance types they use, such as containers, big data, and CI/CD.

49) Demand-based dynamic scaling policies
•
Simple/Step Scaling: Monitors metrics and adds/removes instances as per steps defined by the customers manually.
•
Target Tracking: Thermostat-like control mechanism that automatically adds or removes instances to maintain metrics at a customer defined target.

50) Time based scaling policies:
Configure scheduled scaling: For predictable changes in demand, time-based scaling can provide the correct number of resources in a timely manner. It is also useful if resource creation and configuration is not fast enough to respond to changes on demand.

51) If you have regular traffic spikes and applications that take a long time to start, you should consider using predictive scaling. For example, if users start using your workload with the start of the business hours and don’t use after hours, then predictive scaling can add capacity before the business hours which eliminates delay of dynamic scaling to react to changing traffic.

52) Use Scheduled Scaling for 100% predictable events (e.g., "We have a massive sale every Friday at 10 AM").
Use Predictive Scaling for recurring patterns that might vary in intensity (e.g., "Daily business traffic that fluctuates day-to-day").

53) The Winning Strategy:
Enable Predictive Scaling to proactively set your "Minimum Capacity" based on historical patterns.
Add a Dynamic (Target Tracking) Policy to handle any surprises and to scale the group back down to save costs at night.

54) 
| Feature | Predictive Scaling | Dynamic Scaling |
| :--- | :--- | :--- |
| **Nature** | **Proactive**: It acts before the load arrives based on the past. | **Reactive**: It acts after it sees a real-time metric spike. |
| **Mechanism** | Uses Machine Learning to analyze 14 days of history. | Uses CloudWatch Alarms triggered by real-time thresholds. |
| **Direction** | **Only Scales Out**: It increases capacity but rarely scales in on its own. | **Scales Out and In**: Excellent at removing instances once the rush is over. |
| **Ideal For** | Repeatable, cyclical patterns (daily/weekly business hours). | Unexpected spikes or "Scale-In" (saving money when quiet). |


55) Implement throttling when your clients perform retries. Implement buffering to store the request and defer processing until a later time.

56) Throttling: If the source of the demand has retry capability, then you can implement throttling. Throttling tells the source that if it cannot service the request at the current time, it should try again later. The source waits for a period of time, and then retries the request. Implementing throttling has the advantage of limiting the maximum amount of resources and costs of the workload. In AWS, you can use Amazon API Gateway to implement throttling.

57) Throttling: If the source of the demand has retry capability, then you can implement throttling. Throttling tells the source that if it cannot service the request at the current time, it should try again later. The source waits for a period of time, and then retries the request. Implementing throttling has the advantage of limiting the maximum amount of resources and costs of the workload. In AWS, you can use Amazon API Gateway to implement throttling.
Buffer based: A buffer-based approach uses producers (components that send messages to the queue), consumers (components that receive messages from the queue), and a queue (which holds messages) to store the messages. Messages are read by consumers and processed, allowing the messages to run at the rate that meets the consumers’ business requirements. By using a buffer-centric methodology, messages from producers are housed in queues or streams, ready to be accessed by consumers at a pace that aligns with their operational demands.
In AWS, you can choose from multiple services to implement a buffering approach. Amazon Simple Queue Service(Amazon SQS) is a managed service that provides queues that allow a single consumer to read individual messages. Amazon Kinesis provides a stream that allows many consumers to read the same messages.

58) 
