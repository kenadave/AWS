1) Easily move endpoints between Availability Zones or AWS Regions without needing to update your DNS configuration or change client-facing applications.
2) Dial traffic up or down for a specific AWS Region by configuring a traffic dial percentage for your endpoint groups. This is especially useful for testing performance and releasing updates.
3) Control the proportion of traffic directed to each endpoint within an endpoint group by assigning weights across the endpoints.
4) However, while ELB provides load balancing within one Region, AWS Global Accelerator provides traffic management across multiple Regions.
5) AWS Global Accelerator relies on ELB to provide the traditional load balancing features such as support for internal and non-AWS endpoints, pre-warming, and Layer 7 routing
6) If you have workloads that cater to a global client base, we recommend that you use AWS Global Accelerator. If you have workloads hosted in a single AWS Region and used by clients in and around the same Region, you can use an Application Load Balancer or Network Load Balancer to manage your resources.

7) AWS Global Accelerator and Amazon CloudFront are separate services that use the AWS global network and its edge locations around the world. CloudFront improves performance for both cacheable content (such as images and videos) and dynamic content (such as API acceleration and dynamic site delivery). Global Accelerator improves performance for a wide range of applications over TCP or UDP by proxying packets at the edge to applications running in one or more AWS Regions. Global Accelerator is a good fit for non-HTTP use cases, such as gaming (UDP), IoT (MQTT), or Voice over IP, as well as for HTTP use cases that specifically require static IP addresses or deterministic, fast regional failover. Both services integrate with AWS Shield for DDoS protection.

8) You can’t directly configure on-premises resources as endpoints for your static IP addresses, but you can configure a Network Load Balancer (NLB) in each AWS Region to address your on-premises endpoints. Then you can register the NLBs as endpoints in your AWS Global Accelerator configuration.
9) Yes. By using a custom routing accelerator, you can use your own application logic to route user traffic to a specific Amazon EC2 IP and port in a single or multiple AWS Regions. An example use case is a multi-player game where you want to assign multiple players to a single session on a game server, based on factors such as geographic location, player skill, and gaming configuration. Other examples are VoIP, EdTech, and social media applications that assign multiple users to a specific media server to initiate voice, video, and messaging sessions.

10) You can use Amazon S3 Multi-Region Access Points to get the benefits of Global Accelerator for object storage. S3 Multi-Region Access Points use Global Accelerator transparently to provide a single global endpoint to access a data set that spans multiple S3 buckets in different AWS Regions. This allows you to build multi-region applications with the same simple architecture used in a single region, and then to run those applications anywhere in the world. Application requests made to an S3 Multi-Region Access Point’s global endpoint automatically route over the AWS global network to the S3 bucket with the lowest network latency. This allows applications to automatically avoid congested network segments on the public internet, improving application performance and reliability.

11) AWS Global Accelerator includes the following benefits:
a) Instant regional failover
b) High availability
c) No variability around clients that cache IP addresses
d) Improved performance
e) Easy manageability
f) Fine-grained control

12) No, you can only advertise an IPv4 pool from either one of the services.

13) While Global Accelerator’s IP addresses and EC2 Elastic IP addresses are both static addresses, there are some differences between the two. 
First, Global Accelerator’s IP addresses can be associated with one or more endpoints - Application Load Balancers, Network Load Balancers or EC2 instances, in any number of AWS Regions. This allows you to easily scale out your applications to multiple AZ’s or AWS Regions. Elastic IPs on the other hand are tied to a single AWS resource, such as a load balancer or an EC2 instance, in a single AWS Region. 
Second, Global Accelerator’s IP addresses can only support client-generated connections, unlike Elastic IPs which support both, client and server -generated connections. 
Third, Global Accelerator’s IP addresses are advertised from the AWS’s expansive network of edge locations. Traffic ingresses onto the highly performant and available AWS network as close as possible to your users. Elastic IPs are advertised from a single AWS Region at a time.

14) Custom routing accelerators support only VPC subnet endpoints, each containing one or more EC2 instances that are running your application.

15) Correct. Custom routing accelerators do not support Application Load Balancers (ALB) or Network Load Balancers (NLB). They only support VPC subnet endpoints

16) Custom routing accelerators support only VPC subnet endpoints, each containing one or more EC2 instances that are running your application.

17) In above, there will be multiple subnets, mapping will be done based on subnet ID, and these subnets can be in different regions.
