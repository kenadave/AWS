1) managed NFS. Many EC2 instances across AZs also at a time

2) High availability, 3*gp2 cost, pay per use

Performance mode
Throughput mode

3) EFS storage classes &  lifecycle management
a) standard 
b) infrequent access 
c) archive

Provisioned:- provide a figure for the throughput
Elastic:- no need to provide
Bursting:- Baseline, credits, and Bursts in a limit

4) while assigning EFS to EC2, subnet needs to be selected.
EFS has SG-EFS & ec2 has SG-EC2 then sg-ec2 should have outbound rules & sg-efs should have inbound rules to connect from ec2 to efs

5) so efs created one/VPC. mount target created one/AZ

