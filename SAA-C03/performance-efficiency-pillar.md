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

13) Consider using AWS Cloud WAN to build, manage and monitor your organization's network when building a unified global network.

14) View aggregate network latency between AWS Regions and Availability Zones, as well as within each Availability Zone, using AWS Network Manager to gain insight into how your application performance relates to the performance of the underlying AWS network.Use Network Access Analyzer to identify paths or routes.

15) Share your AWS Transit Gateway between multiple accounts using AWS Resource Access Manager

16) Amazon S3 Transfer Acceleration is a feature that lets external users benefit from the networking optimizations of CloudFront to upload data to Amazon S3.

17) Amazon S3 Multi-Region Access Points replicates content to multiple Regions and simplifies the workload by providing one access point. When a Multi-Region Access Point is used, you can request or write data to Amazon S3 with the service identifying the lowest latency bucket.

18) Elastic Network Interfaces (ENI) used by Amazon EC2 instances, containers, and Lambda functions are limited on a per-flow basis. Review your placement groups to optimize your EC2 networking throughput. To avoid a bottleneck on a per flow-basis, design your application to use multiple flows. To monitor and get visibility into your compute related networking metrics, use CloudWatch Metrics and ethtool. The ethtool command is included in the ENA driver and exposes additional network-related metrics that can be published as a custom metric to CloudWatch.

19) Amazon Elastic Network Adapters (ENA) provide further optimization by delivering better throughput for your instances within a cluster placement group.

20) Elastic Fabric Adapter (EFA) is a network interface for Amazon EC2 instances that allows you to run workloads requiring high levels of internode communications at scale on AWS.

21) Amazon EBS-optimized instances use an optimized configuration stack and provide additional, dedicated capacity to increase the Amazon EBS I/O.

22) If your bandwidth requirements are high, you might consider multiple Direct Connect or VPN services. Traffic can be load balanced across services, although we don't recommend load balancing between Direct Connect and VPN because of the latency and bandwidth differences.

23) The Genius Rule: If the exam asks for the least operational overhead at high speed, pick Native 100 Gbps. If it asks for maximum resiliency and high throughput across different locations, pick BGP ECMP

24) On-Prem Side: You have 2 CGWs (Router A and Router B).
The Cross-Connect:
Router A connects to DX Location 1 and DX Location 2.
Router B connects to DX Location 1 and DX Location 2.
Result: 4 independent physical fiber links.
The AWS Entrance: Those 4 links hit 2 different AWS devices (one in each DX Location).
The Logical Hub (DX Gateway): All 4 Virtual Interfaces (VIFs) terminate at a single Direct Connect Gateway. This is a global resource, so it doesn't live in a single AZ or Region—it’s inherently highly available.
The Router (Transit Gateway): The DX Gateway attaches to your Transit Gateway (TGW). The TGW then routes that traffic to all your VPCs across different Regions.

25) Use LAG if: The requirement is "Scale bandwidth quickly and protect against a single fiber/cable failure."
Use BGP ECMP (the 2 CGW / 2 DX model we discussed) if: The requirement is "Maximum Resiliency" or "Protect against device/location failure."

26) AWS offers scaling direct connect connection bandwidth using either native 100 Gbps, link aggregation group (LAG), or BGP equal-cost multipath (ECMP).

27) If you decide to use Direct Connect, select the appropriate bandwidth for your connectivity.

If you are using an AWS Site-to-Site VPN across multiple locations to connect to an AWS Region, use an accelerated Site-to-Site VPN connection for the opportunity to improve network performance.

If your network design consists of IPSec VPN connection over AWS Direct Connect, consider using Private IP VPN to improve security and achieve segmentation. AWS Site-to-Site Private IP VPN is deployed on top of transit virtual interface (VIF).

AWS Direct Connect SiteLink allows creating low-latency and redundant connections between your data centers worldwide by sending data over the fastest path between AWS Direct Connect locations, bypassing AWS Regions.

<img width="906" height="508" alt="image" src="https://github.com/user-attachments/assets/38415a60-ff28-4ce4-9a75-c11b462a14fd" />

28) For example, using both Application Load Balancer (ALB) and Network Load Balancer (NLB), you
can perform SSL/TLS encryption offloading, which is an opportunity to avoid the CPU-intensive
TLS handshake from being completed by your targets and also to improve certificate management.

When you configure SSL/TLS offloading in your load balancer, it becomes responsible for the
encryption of the traffic from and to clients while delivering the traffic unencrypted to your
backends, freeing up your backend resources and improving the response time for the clients.

29) Your workload latency requirements should be considered when defining the architecture. As an
example, if you have a latency-sensitive application, you may decide to use Network Load Balancer,
which offers extremely low latencies. Alternatively, you may decide to bring your workload closer
to your customers by leveraging Application Load Balancer in AWS Local Zones or even AWS
Outposts.

30) Another consideration for latency-sensitive workloads is cross-zone load balancing. With crosszone load balancing, each load balancer node distributes traffic across the registered targets in all
allowed Availability Zones.

31) Use a combination of both (ALB as a target of NLB) if you want to leverage features of both
products. For example, you can do this if you want to use the static IPs of NLB together with
HTTP header based routing from ALB, or if you want to expose your HTTP workload to an AWS
PrivateLink.
• For a full comparison of load balancers, see ELB product comparison.

32) Use SSL/TLS offloading if possible.
• Configure HTTPS/TLS listeners with both Application Load Balancer and Network Load
Balancer integrated with AWS Certificate Manager.

33) Select the right routing algorithm (only ALB).
• The routing algorithm can make a difference in how well-used your backend targets are and
therefore how they impact performance. For example, ALB provides two options for routing
algorithms:
• Least outstanding requests: Use to achieve a better load distribution to your backend targets
for cases when the requests for your application vary in complexity or your targets vary in
processing capability.
Implementation guidance 79
Performance Efficiency Pillar AWS Well-Architected Framework
• Round robin: Use when the requests and targets are similar, or if you need to distribute
requests equally among targets.

34) Consider cross-zone or zonal isolation.
• Use cross-zone turned off (zonal isolation) for latency improvements and zonal failure
domains. It is turned off by default in NLB and in ALB you can turn it off per target group.
• Use cross-zone turned on for increased availability and flexibility. By default, cross-zone is
turned on for ALB and in NLB you can turn it on per target group.

35) Turn on HTTP keep-alives for your HTTP workloads (only ALB). With this feature, the load
balancer can reuse backend connections until the keep-alive timeout expires, improving your
HTTP request and response time and also reducing resource utilization on your backend targets.

36) • Turn on monitoring for your load balancer.
• Turn on access logs for your Application Load Balancer and Network Load Balancer.
• The main fields to consider for ALB
are request_processing_time, request_processing_time,
and response_processing_time.
• The main fields to consider for NLB are connection_time and tls_handshake_time.
• Be ready to query the logs when you need them. You can use Amazon Athena to query
both ALB logs and NLB logs.
• Create alarms for performance related metrics such as TargetResponseTime for ALB.

37) Use the AWS Global Accelerator and AWS Transfer Family services to improve the throughput
of your online file transfer applications. The AWS Global Accelerator service helps you achieve
lower latency between your client devices and your workload on AWS. With AWS Transfer
Family, you can use TCP-based protocols such as Secure Shell File Transfer Protocol (SFTP) and
File Transfer Protocol over SSL (FTPS) to securely scale and manage your file transfers to AWS
storage services

38) Use network latency to determine if TCP is appropriate for communication between workload
components. If the network latency between your client application and server is high, then
the TCP three-way handshake can take some time, thereby impacting on the responsiveness
of your application. Metrics such as time to first byte (TTFB) and round-trip time (RTT) can be
used to measure network latency. If your workload serves dynamic content to users, consider
using Amazon CloudFront, which establishes a persistent connection to each origin for dynamic
content to remove the connection setup time that would otherwise slow down each client
request.

39) Use the Network Load Balancer (NLB) to deploy services that rely on the UDP protocol, such
as authentication and authorization, logging, DNS, IoT, and streaming media, to improve the
performance and reliability of your workload. The NLB distributes incoming UDP traffic across
multiple targets, allowing you to scale your workload horizontally, increase capacity, and reduce
the overhead of a single target.

40) For your High Performance Computing (HPC) workloads, consider using the Elastic Network
Adapter (ENA) Express functionality that uses the SRD protocol to improve network performance
by providing a higher single flow bandwidth (25 Gbps) and lower tail latency (99.9 percentile) for
network traffic between EC2 instances.

41) Use the Application Load Balancer (ALB) to route and load balance your gRPC (Remote Procedure
Calls) traffic between workload components or between gRPC clients and services. gRPC uses the
TCP-based HTTP/2 protocol for transport and it provides performance benefits such as lighter
network footprint, compression, efficient binary serialization, support for numerous languages,
and bi-directional streaming.

42) 
AWS X-Ray To trace traffic through the application layers
and identify latency between components
and dependencies. Use X-Ray service maps
to see relationships and latency between
workload components.
Amazon Relational Database Service
Performance Insights
To view database performance metrics and
identify performance improvements.
Amazon RDS Enhanced Monitoring To view database OS performance metrics.

43) Set up CloudWatch Synthetic Canaries to mimic browser-based user activities
programmatically using Linux cron jobs or rate expressions to generate consistent metrics over
time.
• Use the AWS Distributed Load Testing solution to generate peak traffic or test the workload at
the expected growth rate.

44) You can use tools such as AWS Systems Manager Patch Manager to automate the process of
system updates, and schedule the activity using AWS Systems Manager Maintenance Windows

45) Use AWS Local Zones to run workloads like video rendering. Local Zones allow you to benefit
from having compute and storage resources closer to end users.

46) Applications like high-resolution live video streaming, high-fidelity audio, and augmented
reality or virtual reality (AR/VR) require ultra-low-latency for 5G devices. For such applications,
consider AWS Wavelength. AWS Wavelength embeds AWS compute and storage services within
5G networks, providing mobile edge computing infrastructure for developing, deploying, and
scaling ultra-low-latency applications.

47) AWS IoT Greengrass => Use to run local compute, messaging, and
data caching for connected devices.

48) Use VPC Flow Logs to capture detailed
information about traffic to and from
network interfaces in your VPCs. With VPC
Flow Logs, you can diagnose overly restricti
ve or permissive security group rules and
determine the direction of the traffic to and
from the network interfaces.

49) Reachability Analyzer helps you analyze and
debug network reachability. Reachability
Analyzer is a configuration analysis tool that
allows you to perform connectivity testing
between a source resource and a destinati
on resource in your VPCs. This tool helps
you verify that your network configuration
matches your intended connectivity.

50) Use Amazon CloudWatch RUM to collect the
metrics that give you the insights that help
you identify, understand, and improve user
experience.

51)  Assess the routing paths in your network to verify that the shortest path between destinations is
always used. Network Access Analyzer can help you do this


