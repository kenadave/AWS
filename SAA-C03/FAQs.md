1) No. When using public IP addresses, all communication between instances and services hosted in AWS use AWS's private network. Packets that originate from the AWS network with a destination on the AWS network stay on the AWS global network, except traffic to or from AWS China Regions.

* 2) Interface type endpoints provide private connectivity to services powered by PrivateLink, being AWS services, your own services or SaaS solutions, and supports connectivity over Direct Connect.
 
3) Default VPCs are assigned a CIDR range of 172.31.0.0/16. Default subnets within a default VPC are assigned /20 netblocks within the VPC CIDR range. 

4) Amazon VPC IP Address Manager (IPAM) is a managed service that makes it easier for you to plan, track, and monitor IP addresses for your AWS workloads.

5) VPC Flow Logs vs Traffic Mirroring
    Amazon VPC flow logs allow customers to collect, store, and analyze network flow logs. The information captured in flow logs includes information about allowed and denied traffic, source and destination IP addresses, ports, protocol number, packet and byte counts, and an action (accept or reject). You can use this feature to troubleshoot connectivity and security issues and to make sure that the network access rules are working as expected.

    Amazon VPC traffic mirroring, provides deeper insight into network traffic by allowing you to analyze actual traffic content, including payload, and is targeted for use-cases when you need to analyze the actual packets to determine the root cause a performance issue, reverse-engineer a sophisticated network attack, or detect and stop insider abuse or compromised workloads.

5b) VPC Flow Logs provide lightweight metadata (5-tuple: source/dest IP, port, protocol, action, bytes) for network auditing and monitoring, capturing "who talked to whom" without impacting performance. Network Mirroring (Traffic Mirroring) provides deep, full-packet capture, including payload, for forensics, security inspection, and troubleshooting

6) Yes. DescribeInstances() will return all running Amazon EC2 instances. You can differentiate EC2-Classic instances from EC2-VPC instances by an entry in the subnet field. If there is a subnet ID listed, the instance is within a VPC. 
Yes. DescribeVolumes() will return all your EBS volumes.

7) Yes. To launch an instance into nondefault VPCs you must specify a subnet-ID during instance launch.

8) Yes, however, an instance launched in a VPC using an Amazon EBS-backed AMI maintains the same IP address when stopped and restarted. This is in contrast to similar instances launched outside a VPC, which get a new IP address. The IP addresses for any stopped instances in a subnet are considered unavailable.

9) Network interfaces can only be attached to instances residing in the same Availability Zone.

10) Can I attach a network interface in one VPC to an instance in another VPC?
Network interfaces can only be attached to instances in VPCs in the same account.

11) You can attach and detach secondary interfaces (eth1-ethn) on an EC2 instance, but you can’t detach the eth0 interface.

12) Is VPC peering traffic within the region encrypted?
No. Traffic between instances in peered VPCs remains private and isolated – similar to how traffic between two instances in the same VPC is private and isolated.

13) Inter-Region VPC Peering is encrypted using modern AEAD algorithms

14) VPC peering connections do not require an Internet Gateway.

15) Security groups cannot be referenced across an Inter-Region VPC Peering connection.

16) Monitor mode (for visibility, assessment and initiate migration) and Enforce mode (for preventing unencrypted traffic).

17) Track in monitor mode:
VPC flow logs with the encryption-status field
Console dashboard
GetVpcResourcesBlockingEncryptionEnforcement command


18)Amazon VPC Lattice automatically manages network connectivity and application layer routing between services across different VPCs and AWS accounts

19) 
VPC → TGW	Propagation	 === Automatic (via AWS internal APIs)
TGW → VPC	Static Routing	===	Manual (You must add the entry)
