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

