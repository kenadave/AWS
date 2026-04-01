1) A beneficial resource is AWS Artifact, which gives you on-demand access to AWS’ security and compliance reports and select online agreements.

2) AWS CloudFormation StackSets allow you to centrally manage AWS CloudFormation stacks across accounts and OUs in your organization

3) AWS Control Tower offers a simplified way to set up and govern multiple accounts. It automates the setup of accounts in your AWS Organization, automates provisioning, applies guardrails (which include prevention and detection), and provides you with a dashboard for visibility.

4) Service control policies (SCPs) allow the organization administrator to establish granular preventative controls on member accounts, and AWS Config can be used to establish proactive and detective controls on member accounts.

5) Three benefits that provide improved account governance are:
Integrated mandatory security controls that are automatically applied to accounts admitted into the organization.

Optional controls that can be turned on or off for a given set of OUs.

AWS Control Tower Account Factory provides automated deployment of accounts containing pre-approved baselines and configuration options inside your organization.

6) Consider AWS CloudFormation StackSets: StackSets help you deploy resources including IAM policies, roles, and groups into different AWS accounts and Regions from an approved template.

7) Do not create access keys for the root user. If access keys exist, remove them

8) Use preventative controls for member account root users in AWS multi-account environments.

Consider using the Disallow Creation of Root Access Keys for the Root User preventative guard rail for member accounts.

Consider using the Disallow Actions as a Root User preventative guard rail for member accounts.

9) Create alarms to detect use of the root credentials (CIS 1.7). Amazon GuardDuty can monitor and alert on root user API credential usage through the RootCredentialUsage finding.

Evaluate and implement the detective controls included in the AWS Well-Architected Security Pillar conformance pack for AWS Config, or if using AWS Control Tower, the strongly recommended controls available inside Control Tower.

10) Use AWS Artifact to find documentation and reports aligned to your target frameworks that describe the scope of responsibility covered by AWS and guidance for the remaining scope that is your responsibility. For further service-specific guidance as they align to various framework control statements, see AWS Customer Compliance Guides

11) Help prevent non-compliant resource configurations and actions across your AWS Organizations using service control policies (SCP). Implement rules in AWS Config to monitor and report on non-compliant resources, then switch rules to an enforcement model once confident in their behavior

12) To deploy sets of pre-defined and managed rules that align to your cybersecurity frameworks, evaluate the use of AWS Security Hub CSPM standards as your first option

13)  For example, Amazon GuardDuty stays up to date with industry threat intelligence for detecting anomalous behaviors and threat signatures within your accounts.  Amazon Inspector automatically keeps a database of the CVEs it uses for its continuous scanning features up to date.  Both AWS WAF and AWS Shield Advanced provide managed rule groups that are updated automatically as new threats emerge.

14)  Wherever possible, define your security controls in a declarative way, such as in AWS CloudFormation, and store them in a source control system.  Use DevOps practices to automate the deploying your controls for more predictable releases, automated testing using tools like AWS CloudFormation Guard, and detecting drift between your deployed controls and your desired configuration.

15)  One way to achieve this is by using Service Catalog, where you can publish templates as products that workload teams can incorporate into their own pipeline deployments.

16)  To aid and guide you in performing threat modeling, consider using the **Threat Composer tool**, which aims to your reduce time-to-value when threat modeling.

17)  Some security services, such as **Amazon GuardDuty** and **AWS Security Hub CSPM**, provide their own SNS topics to stay informed about new standards, findings, and other updates for those particular services.

18)  imilarly, if you subscribed to **AWS Enterprise Support**, you will receive weekly updates from your **Technical Account Manager (TAM)** and can schedule a regular review meeting with them.

19) For IoT devices, you can use the **AWS IoT Core credential provider** to request temporary credentials.

20) For on-premises systems or systems that run outside of AWS that need access to AWS resources, you can use **IAM Roles Anywhere**.

21) These short-term credentials can be provided through IAM roles for EC2 instances, execution roles for Lambda functions, Cognito IAM roles for mobile user access, and IoT Core policies for IoT devices. When interfacing with third parties, prefer delegating access to an IAM role with the necessary access to your account's resources rather than configuring an IAM user and sending the third party the secret access key for that user.

22) One way to determine the needed permissions is to review AWS
CloudTrail logs. You can use this review to create permissions tailored to the actions that the user
actually performs within AWS. IAM Access Analyzer can automatically generate an IAM policy
based on access activity. You can use IAM Access Advisor at the organization or account level to
track the last accessed information for a particular policy.

23) How the Workflow Works
Request: You select an IAM role or user and a specific time range (up to 90 days).
Analyze: Access Analyzer scans your CloudTrail logs for that period.
Review & Refine: It presents a generated JSON policy. You can then replace any placeholders (like ${Region} or ${Account}) with specific values to further tighten security.
Create: Once refined, you save and attach the new, secure policy.

24) Also
consider using AWS Control Tower, which provides prescriptive managed controls that enrich
AWS Organizations. You can also define your own controls within Control Tower.

25) 
Root (Logical Container)
├── Management Account (Fixed here)
├── Security OU (Sub-OU)
│   ├── Log Archive Account (Member)
│   └── Security Tooling Account (Member)
└── Workloads OU (Sub-OU)
    ├── Production OU (Nested OU)
    │   └── App-Prod Account (Member)
    └── Development OU (Nested OU)
        └── App-Dev Account (Member)

26) If you are using AWS Control Tower, you can leverage its controls and landing zones as the
foundation for your permission guardrails and multi-account environment. The landing zones
provide a pre-configured, secure baseline environment with separate accounts for different
workloads and applications. The guardrails enforce mandatory controls around security,
operations, and compliance through a combination of Service Control Policies (SCPs), AWS Config
rules, and other configurations

27) A more granular step is to implement privileged access management (PAM) and temporary
elevated access management (TEAM) techniques.

28) 
Why use Trust Policies for Multi-Account Access?
In a multi-account setup, the Trust Policy is the "handshake" between accounts.
Account A (Production) has a role called CrossAccountAuditor.
**The Trust Policy** on that role says: "I trust Account B (Security) to assume this role."
**The Identity-based Policy** on that same role says: "Once assumed, this role can s3:Get* on all buckets."

29) **AWS Config** can report resources that are misconfigured, and through AWS Config policy checks,
can detect resources that have public access configured. Services such as **AWS Control Tower**
and **AWS Security Hub CSPM** simplify deploying detective controls and guardrails across AWS
Organizations to identify and remediate publicly exposed resources. For example, AWS Control
Tower has a managed guardrail which can detect if any Amazon EBS snapshots are restorable by
AWS accounts.

30) Use Trusted Advisor if you want a free, "set it and forget it" report on your overall account security health.
Use AWS Config if you need to maintain a specific compliance standard and want to automatically shut down public access as soon as a user enables it

31) Cross-account sharing within AWS Organizations is supported by a number of AWS services, such
as AWS Security Hub CSPM, Amazon GuardDuty, and AWS Backup. These services allow for data to
be shared to a central account, be accessible from a central account, or manage resources and data
from a central account. For example, AWS Security Hub CSPM can transfer findings from individual
accounts to a central account where you can view all the findings. AWS Backup can take a backup
for a resource and share it across accounts. You can use AWS Resource Access Manager (AWS RAM)
to share other common resources, such as VPC subnets and Transit Gateway attachments, AWS
Network Firewall, or Amazon SageMaker AI pipelines.

32) 

| Service | Information Flow | Primary Purpose |
| :--- | :--- | :--- |
| **AWS Security Hub** | Member -> Central | Aggregates security alerts and compliance findings. |
| **AWS Backup** | Central -> Member | Pushes data protection policies down to accounts. |
| **AWS Trusted Advisor** | Member -> Central | Consolidates best-practice recommendations (Cost, Performance, etc.). |

33) 
To restrict your account to only share resources within your organization, use service control
policies (SCPs) to prevent access to external principals. When sharing resources, combine identitybased controls and network controls to create a data perimeter for your organization to help
protect against unintended access. A data perimeter is a set of preventive guardrails to help verify
that only your trusted identities are accessing trusted resources from expected networks. These
controls place appropriate limits on what resources can be shared and prevent sharing or exposing
resources that should not be allowed. For example, as a part of your data perimeter, you can use
VPC endpoint policies and the AWS:PrincipalOrgId condition to ensure the identities accessing
your Amazon S3 buckets belong to your organization. It is important to note that SCPs do not
apply to service-linked roles or AWS service principals.

34) When using Amazon S3, turn off ACLs for your Amazon S3 bucket and use IAM policies to define
access control. For restricting access to an Amazon S3 origin from Amazon CloudFront, migrate
from origin access identity (OAI) to origin access control (OAC) which supports additional features
including server-side encryption with AWS Key Management Service.

35) 
| Feature | S3 ACLs (Legacy) | IAM & Bucket Policies (Modern) |
| :--- | :--- | :--- |
| **Granularity** | Object-level (Hard to audit at scale) | Bucket/Prefix level (Centralized) |
| **Ownership** | Depends on who uploaded the file | Bucket Owner always owns everything |
| **Logic** | Only "Allow" rules | Can "Allow" and "Deny" |
| **Conditions** | None | IP, Date, MFA, VPC, etc. |


36) If you have resources that you shared previously using a resource-based policy, you can use the
PromoteResourceShareCreatedFromPolicy API or an equivalent to promote the resource
share to a full AWS RAM resource share.


37) Using Amazon GuardDuty, you can be alerted when unexpected and potentially unauthorized or malicious activity occurs within your AWS accounts.

38) Alternatively, you can create a CloudTrail Lake, which retains CloudTrail logs for up to seven years and provides a SQL-based querying facility

39) AWS CloudTrail Logs, VPC Flow Logs, and Route 53 resolver query logs are the basic logging sources to support security investigations in AWS. You can also use Amazon Security Lake to collect, normalize, and store this log data in Apache Parquet format and Open Cybersecurity Schema Framework (OCSF), which is ready for querying. Security Lake also supports other AWS logs and logs from third-party sources.

40) For log queries, you can use CloudWatch Logs Insights for data stored in CloudWatch log groups, and Amazon Athena and Amazon OpenSearch Service for data stored in Amazon S3.

41) AWS Security Hub does not ingest raw logs like CloudTrail, DNS, or VPC Flow Logs directly. Instead, it ingests findings—pre-analyzed security alerts—from other AWS services and third-party products.

While GuardDuty acts as a "detective" that scans raw data to find threats, Security Hub acts as a centralized dashboard (like a "city hall") that aggregates those findings into a single view.

Security Hub: Ingests findings (already-detected issues) from:
AWS Services: GuardDuty, Amazon Inspector, Amazon Macie, and AWS IAM Access Analyzer.
Security Standards: It runs its own automated configuration checks against frameworks like CIS or PCI DSS using AWS Config data.
Third-Party Partners: Vulnerability scanners and firewalls from external vendors.

42) To ease capturing and standardizing logs and findings, evaluate Amazon Security Lake in your Log Archive account.

43) Using AWS Organizations, create the Log Archive and Security Tooling accounts under a security organizational unit. If you are using AWS Control Tower to manage your organization, the Log Archive and Security Tooling accounts are created for you automatically.

44) An example of a service that can perform correlation for you is Amazon Detective. Detective performs ongoing ingestion of alerts from various AWS and third-party sources and uses different forms of intelligence to assemble a visual graph of their relationships to aid investigations.

45) 
Detect (GuardDuty): GuardDuty continuously monitors raw logs (VPC Flow Logs, CloudTrail, etc.). It detects a threat, such as an EC2 instance communicating with a malicious IP address, and generates a Finding.

Aggregate & Prioritize (Security Hub): The finding is automatically sent to Security Hub. Security Hub acts as the "central command center," normalizing the finding into a standard format and ranking its severity against other alerts in your environment.

Investigate (Detective): From within the Security Hub console, you can "pivot" to Amazon Detective with a single click. Detective builds a visual behavior graph that correlates the finding with historical log data to show you the root cause and the full extent of the attacker's activity. 

46) When traffic moves between VPCs, it's common to use VPC peering for simple routing or the AWS Transit Gateway for complex routing. With these approaches, you facilitate traffic flows between the range of IP addresses of both the source and destination networks. However, if your workload only requires traffic flows between specific components in different VPCs, consider using a point-to-point connection using AWS PrivateLink. To do this, identify which service should act as the producer and which should act as the consumer. Deploy a compatible load balancer for the producer, turn on PrivateLink accordingly, and then accept a connection request by the consumer. The producer service is then assigned a private IP address from the consumer's VPC that the consumer can use to make subsequent requests. This approach reduces the need to peer the networks.

47) Use firewalls to define fine-grained control over network traffic in, out, and across your VPCs, such as the Route 53 Resolver DNS Firewall, AWS Network Firewall, and AWS WAF. Consider using the AWS Firewall Manager for centrally configuring and managing your firewall rules across your organization.

48) If you are using solutions that perform out-of-band inspections, such as pcap analysis of packet data from network interfaces operating in promiscuous mode, you can configure VPC traffic mirroring.

49) For components that transact over HTTP-based protocols, protect your application from common threats with a web application firewall (WAF). AWS WAF is a web application firewall that lets you monitor and block HTTP(S) requests that match your configurable rules before sending to Amazon API Gateway, Amazon CloudFront, AWS AppSync or an Application Load Balancer.

50) You can centrally manage AWS WAF, AWS Shield Advanced, AWS Network Firewall, and Amazon VPC security groups across your AWS Organization with AWS Firewall Manager.

51) Turn on VPC Traffic Mirroring on interfaces where inbound and outbound traffic should be mirrored. You can use Amazon EventBridge rules to invoke an AWS Lambda function to turn on traffic mirroring on interfaces when new resources are created. Point the traffic mirroring sessions to the Network Load Balancer in front of your appliance that processes traffic.

52) AWS offers a range of services to support vulnerability management programs. Amazon Inspectorcontinuously scans AWS workloads for software vulnerabilities and unintended network access, while AWS Systems Manager Patch Manager helps manage patching across Amazon EC2 instances. These services can be integrated with AWS Security Hub CSPM, a cloud security posture management service that automates AWS security checks, centralizes security alerts, and provides a comprehensive view of an organization's security posture. Furthermore, Amazon CodeGuru Security uses static code analysis to identify potential issues in Java and Python applications during the development phase.

53) For example, you can use tools like Amazon GuardDuty to analyze, detect, and alert of malware in EC2 and EBS volumes. GuardDuty can also scan newly uploaded objects to Amazon S3 for potential malware or viruses and take action to isolate them before they are ingested into downstream processes.

54) If you're using a CI/CD pipeline for your application deployment, integrate vulnerability scanning tools into your pipeline. Tools like Amazon CodeGuru Security and open-source options can scan your source code, dependencies, and artifacts for potential security issues.

55) We recommend you start with an Amazon Machine Image (AMI) published by AWS or an APN partner, and use the AWS EC2 Image Builder to automate configuration according to an appropriate combination of CIS and STIG controls.

56) For containerized workloads, hardened images from Docker are available on the Amazon Elastic Container Registry (ECR) public repository. You can use EC2 Image Builder to harden container images alongside AMIs.

57) When using containers, implement ECR Image Scanning in your build pipeline and on a regular basis against your image repository to look for CVEs in your containers.

58) Configure code signing for Lambda to make sure that only trusted code runs in your Lambda functions.

59) Verify that the IAM Roles associated with your EC2 instance profiles include the AmazonSSMManagedInstanceCore managed IAM policy.

60) You can use AWS Signer to help manage the verification of signatures, as well as your own code-signing lifecycle for your own software and artifacts. Both AWS Lambda and Amazon Elastic Container Registry provide integrations with Signer to verify the signatures of your code and images.

61) [EC2.8] EC2 instances should use Instance Metadata Service Version 2 (IMDSv2). IMDSv2 uses the techniques of session authentication, blocking requests that contain an X-Forwarded-For HTTP header, and a network TTL of 1 to stop traffic originating from external sources to retrieve information about the EC2 instance. This check in Security Hub CSPM can detect when EC2 instances use IMDSv1 and initiate automated remediation

62) AWS Organizations tag policies can be used to enforce tagging standards.

63) Evaluate options to reduce the sensitivity level of data where appropriate, such as using tokenization or anonymization.

64) Within AWS, you can upload data sets into Amazon S3 and scan them using Amazon Macie, Amazon Comprehend, or Amazon Comprehend Medical.

65) Other features such as sensitive data detection in AWS Glue, Amazon SNS, and Amazon CloudWatch can also be used to detect PII and take mitigating action.

66) For data stored in DynamoDB, you can use the Time To Live (TTL) feature to define a per-item expiration timestamp.

67) Another aspect of lifecycle management is recording the history of data as it progresses through your workload, called data provenance tracking

68) For example, you can log metadata about transformations in an Amazon DynamoDB table. Within a data lake, you can keep copies of transformed data in different S3 buckets for each data pipeline stage. Store schema and timestamp information in an AWS Glue Data Catalog.

69) Ensure that you understand and audit the use of encryption keys to validate that the access control mechanisms on the keys are appropriately implemented. For example, any AWS service using an AWS KMS key logs each use in AWS CloudTrail. You can then query AWS CloudTrail, by using a tool such as Amazon CloudWatch Logs Insights, to ensure that all uses of your keys are valid.

70) Key policies are the primary way to control access to an AWS KMS key. Additionally, AWS KMS key grants can provide access to AWS services to encrypt and decrypt data on your behalf.
