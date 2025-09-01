Placement Groups:
  1) Cluster : Same AZ (Lowest latency)
  2) Spread : Multiple AZ, one instance/rack 7 instances/AZ/group
  3) Partition : 7 partitions/AZ, each partitions can have 100s of EC2 (Big Data)
  If Big Data + lowest latency : Cluster

ENI :
  Kind of Ethernet card attached to instance for internet connectivity within the VPC.
  
