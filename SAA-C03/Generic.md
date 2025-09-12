1) Load balancer videos revise
2) RDS-Aurora quiz go through
aws cloudformation list-stacks --region us-east-1 --stack-status-filter CREATE_COMPLETE


aws cloudformation create-stack \
  --stack-name region-pmry \
  --template-body file://cloudformation-multi-region-setup.yaml \
  --parameters ParameterKey=DomainName,ParameterValue=kd.com \
  --region us-east-1
  
  
aws cloudformation create-stack \
  --stack-name region-scdry \
  --template-body file://cloudformation-secondary-region.yaml \
  --parameters ParameterKey=DomainName,ParameterValue=kd.com \
               ParameterKey=PrimaryHostedZoneId,ParameterValue=Z04628732D55A9UE5RRSF \
  --region us-west-2  
  
aws cloudformation describe-stacks   --stack-name region-pmry   --query 'Stacks[0].StackStatus'   --output text   --region us-east-1
aws cloudformation describe-stacks   --stack-name region-pmry   --query 'Stacks[0].Capabilities'   --output text   --region us-east-1
aws cloudformation describe-stacks   --stack-name region-scdry   --query 'Stacks[0].StackStatus'   --output text   --region us-west-2

aws cloudformation describe-stacks --stack-name region-pmry --query 'Stacks[0].Outputs[?OutputKey==`HostedZoneId`].OutputValue' --output text

https://github.com/kenadave/AWS.git

echo $AWS_DEFAULT_REGION


Internet Request → Route53 → ALB → Target Group → EC2
                     ↓         ↓        ↓         ↓
                 Hosted Zone  Subnets  Subnets  Subnets
                              ↓        ↓         ↓
                             VPC ← Route Table ← IGW


                    One ALB
                       |
        ┌──────────────┼──────────────┐
        │              │              │
    AZ-1a          AZ-1b          AZ-1c
 (us-east-1a)   (us-east-1b)   (us-east-1c)
        │              │              │
   Subnet-1       Subnet-2       Subnet-3
 (10.0.1.0/24)  (10.0.2.0/24)  (10.0.3.0/24)
        │              │              │
   ┌────┴────┐    ┌────┴────┐    ┌────┴────┐
   │         │    │         │    │         │
 EC2-1a   EC2-1b EC2-2a   EC2-2b EC2-3a   EC2-3b

ALB
├── HTTPListener (port 80) → HTTPTargetGroup
└── HTTPSListener (port 443) → HTTPSTargetGroup


