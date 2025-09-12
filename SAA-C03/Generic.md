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

