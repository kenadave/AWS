1) ENA Express is an enhancement on the Elastic Network Adapter that brings the Scalable Reliable Datagram (SRD) protocol to traditional TCP and UDP networking. Transparent to the application, ENA Express improves single flow bandwidths and reduces tail latencies in throughput intensive workloads.

2) If you see a question where a customer has a 25 Gbps or 100 Gbps instance but their application is stuck at 5 Gbps for a single connection (like a large file transfer or a database sync), the answer is almost always Enable ENA Express.

3) Q: What are the differences between an EFA ENI and an ENA ENI?

An ENA ENI provides traditional IP networking features necessary to support VPC networking. An EFA ENI provides all the functionality of an ENA ENI, plus hardware support for applications to communicate directly with the EFA ENI without involving the instance kernel (OS-bypass communication) using an extended programming interface. Due to the advanced capabilities of the EFA ENI, EFA ENIs can only be attached at launch or to stopped instances.

4) In the case of hibernate, your instance gets hibernated and the RAM data persisted. In the case of Stop, your instance gets shut down and RAM is cleared.
   In both the cases, data from your EBS root volume and any attached EBS data volumes is persisted. Your private IP address remains the same, as does your elastic IP address (if applicable). The network layer behavior will be similar to that of EC2 Stop-Start workflow. Stop and hibernate are available for Amazon EBS backed instances only. Local instance storage is not persisted.

5) Exam Tip: If you see "Low Tail Latency" + "Standard Web App/Database," choose ENA Express. If you see "Low Latency" + "HPC/Supercomputing," choose EFA.

6) Summary for your Study Notes
Feature	ENA Express	EFA
Protocol	TCP & UDP	OS-Bypass (SRD)
Effort	Zero (Check a box in AWS)	High (Re-code/Config app)
Target	High-throughput DBs, File transfers	HPC, Weather Sim, ML Training
Max Flow	25 Gbps	100+ Gbps

7) We do not support keeping an instance hibernated for more than 60 days.

8) Exam Trigger: If a scenario says hibernation is failing, check if the Root Volume (EBS) has enough free space to hold the entire contents of the RAM.

9) 3. Stop vs. Hibernate vs. Terminate
State	Root/Attached EBS Data	RAM Content	Billing
Stopped	Persists	Deleted	No instance fee; pay for EBS storage.
Hibernated	Persists	Saved to EBS Root	No instance fee; pay for EBS storage (including RAM file).
Terminated	Deleted (by default)	Deleted	No more charges.

10) No, an RI is associated with a specific region, which is fixed for the duration of the reservation's term.

11) When you exchange one Convertible RI for another, EC2 ensures that the total value of the Convertible RIs is maintained through a conversion. So, if you are converting your RI with a total value of $1000 for another RI, you will receive a quantity of Convertible RIs with a value that’s equal to or greater than $1000. You cannot convert your Convertible RI for Convertible RI(s) of a lesser total value.

12) For example, let’s say you purchased one No Upfront Convertible RI (A) with a $0.10/hr rate, and you decide to exchange Convertible RI A for another RI (B) that costs $0.06/hr. When you convert, you will receive two RIs of B because the amount that you pay on an hourly basis must be greater than or equal to the amount you’re paying for A on an hourly basis.

13) Yes, you can upgrade the payment option associated with your RI. For example, you can exchange your No Upfront RIs for Partial or All Upfront RIs to benefit from better pricing. You cannot change the payment option from All Upfront to No Upfront, and cannot change from Partial Upfront to No Upfront.

14) With a single API call, EC2 Fleet lets you provision compute capacity across different instance types, Availability Zones and across On-Demand, Reserved Instances (RI) and Spot Instances purchase models to help optimize scale, performance and cost.

15) 
