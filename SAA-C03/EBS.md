1) Flag for Delete on Termination:
   It is by default TRUE on the default EBS volume when it is created through EBS backed EMI
   When added additional EBS volumes, it is by default false.

2) Recycle bin
   Archive Tier
   Fast snapshot restore (FSR)

3) EBS volumme types lecture
4) Multi-Attach is same EBS connected with multiple instances in same AZ

5) 
Key Exam Tips:
16,000 IOPS = gp3 limit (remember this!)
64,000 IOPS = io1/io2 limit
256,000 IOPS = io2 Block Express limit
>100K IOPS = Consider Instance Store or FSx Lustre
gp2 formula: 3 × GB size = IOPS (capped at 16K)
Focus on the 16K and 64K thresholds - these are the most commonly tested decision points.
