Placement Groups:
  1) Cluster : Same AZ (Lowest latency)
  2) Spread : Multiple AZ, one instance/rack 7 instances/AZ/group
  3) Partition : 7 partitions/AZ, each partitions can have 100s of EC2 (Big Data)
  If Big Data + lowest latency : Cluster

ENI :
  Kind of Ethernet card attached to instance for internet connectivity within the VPC.
  
EC2-Hibernate :
  The RAM is stored into EBS root volume when the instance is stopped. When the instance is started, the RAM is taken from EBS root volume. That decreases the boot time.
  When you see the uptime, it will not start from 0 once it is started from the hibernation.

4) ec2 instance connect uses port 22 because it uses SSH behind the scenes.
SSM doesn't need any port and most secure way of connecting 

5) one SG can contain another. While writing IP, select custom and add SG. 
When one app needs to connect to another which is on another instance, update inbound rules of the target SG

6) if one instance fails, DNS doesn't resolve automatically to new instance. Use load balancer or Elastic IPs in this cases to keep the client url constant
7) Fleet of EC2 means not a single instance but a group of instances of different types and configurations.
