1) CLB - supports http, https, tcp, ssl (secure tcp)
2) ALB - supports http, https, websocket (only layer 7)
3) NLB - supports tcp, tls (secure tcp), udp
4) GWLB - operates at layer 3, IP protocol
          GENEVE protocol on port 6081

6) GWLB : Network Layer (3) - IP Packets

7) Sticky sessions:
   Used cookie for this and NLB works without cookies
   Application based cookies:-
     1) Custom cookie
     2) Application cookie
   Duration based cookies:-

8) Cross-Zone load balancing
   Enabled by default for ALB and no charges for inter AZ data
   NLB & GWLB by default disabled and if enabled then charges
   CLB by default disabled and if enabled then no charges

9) SSL ( Secure Socket Layer ) used for encryption during transit
   TLS ( Transport Layer Security )
   SNI ( server name indication ) solves multiple certificates on web server

10) ASG can terminate instances which ALB mark as unhealthy
    ASG based on cloudwatch alarms
    Usecases of desired capacity and minimum capacity

11) Dynamic scaling:
              a) Target
              b) Simple / Step
    Scheduled scaling
    Predictive scaling: based on forecast


Questions:
  1) Is websocket at layer 7?
     Yes

  2) How to manage notes on git, on udemy, and the questions?


  3) How will the ALB differ if multiple applications on same machine ( how it is like containers ) and multiple http
     applications across machines?
  4) How to save time by these questions?
  5) How ELB supports redirect? from http to https?
     2 listeners. One for http & another for https. User don't need to specify https in the browser.
  6) How one ALB can support 2 independent routes?
  7) What about load balancer for SSH?
  8) What is the usecase of having ELB in all the AZs while creating? 
  9) How health is identified within target groups while attaching them to the ELB?
  10) Why NLB with private ip addresses only?
  11) How NLB supports health checks of HTTP, HTTPS?
  12) Why listeners on the load balancers need port and protocol, but not the ip address?
  13) How Lambda can give TCP/UDP which can be connected with NLB? There should be multiple lambdas to redirect?
  14) How ALB can give TCP/UDP which can be connected with NLB? There should be multiple ALBs to redirect?
Elastic IP or PrivateLink scenario. NLB receives connection on one IP. It routes to ALB. ALB then does layer 7 routing. So benefits of both static IP + ALB routing rules

  15) Steps to enable the load balancers and security group configurations
  16) Why NLB does not need cookie for sticky session?
  17) Does duration factor impact in Application based cookies?
  18) Scheduled scaling also has forcast?
  19) Difference between simple and step scaling? Both are based on cloudwatch metrics?
  20) When I configure scaling policies, cloudwatch alarms are automatically shown in cloudwatch?

Notes:
  1) Revise ALB & NLB videos, hands on for the steps
