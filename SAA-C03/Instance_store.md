1) gp1 & gp2 general purpose SSD
2) io1 & io2 high performance SSD
3) st1 low-cost HDD, frequently Accessed, throughput intensive workloads (st means atandard)
4) sc1 lowest cost HDD, less frequently Accessed ( sc means cold storage)
Due to low latency requirement, for boot purpose only gp & io are used and not HDD
5) linked IOPS :- gp2
independent IOPS :- gp3,io1,io2

independent means IOPS can be increased without increasing the storage

Provisioned IOPS

6) io1 & io2 for high IOPS
st1 & sc1 for high throughput
high iops but small chunk then low throughput 
high throughput but large chunk then low iops possible 

7) encrypted volumes are created by 
   - copying snapshot, encrypt it and create new volume out of it
   - while creating volume from a snapshot,select for encryption 

8) gp3, io1, io2 consistent performance 
   gp2, st1, sc1 has credit & bursts