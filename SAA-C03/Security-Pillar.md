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
