1) gp1 & gp2 general purpose SSD
2) io1 & io2 high performance SSD
3) st1 low-cost HDD, frequently Accessed, throughput intensive workloads (st means atandard)
4) sc1 lowest cost HDD, less frequently Accessed ( sc means cold storage)
Due to low latency requirement, for boot purpose only gp & io are used and not HDD
5) linked IOPS :- gp2
independent IOPS :- gp3,io1,io2

independent means IOPS can be increased without increasing the storage

Provisioned IOPS