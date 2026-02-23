1) Geo DNS provides three levels of geographic granularity: continent, country, and state, and Geo DNS also provides a global record which is served in cases where an end user’s location doesn’t match any of the specific Geo DNS records you have created. You can also combine Geo DNS with other routing types, such as Latency Based Routing and DNS Failover, to enable a variety of low-latency and fault-tolerant architectures.

2) Amazon Route 53 Traffic Flow is an easy-to-use and cost-effective global traffic management service.

3) When you create a traffic flow policy, you can specify either an AWS region (if you're using AWS resources) or the latitude and longitude for each endpoint.

4) To take advantage of Route 53 Private DNS, you must configure a VPC and migrate your resources into it.

5) Yes, you can block domains and specific DNS names by creating these names in one or more Private DNS hosted zones and pointing these names to your own server

6) You can configure DNS Failover for Elastic Load Balancers and Amazon S3 website buckets via the Amazon Route 53 Console without needing to create a health check of your own. For these endpoint types, Route 53 automatically creates and manages health checks on your behalf which are used when you create an Alias record pointing to the ELB or S3 website bucket and enable the "Evaluate Target Health" parameter on the Alias record.

For all other endpoints, you can specify either the DNS name (e.g. www.example.com) or the IP address of the endpoint when you create a health check for that endpoint.

7) Route 53 does not make routing decisions based on the load or available traffic capacity of your endpoints.

8) No. Route 53 health checks consider an HTTP 3xx code to be a successful response, so they don’t follow the redirect.

9) Route 53 can only fail over to an endpoint that is healthy. If there are no healthy endpoints remaining in a resource record set, Route 53 will behave as if all health checks are passing.

10) If the exam question asks for the fastest possible failover (minimizing the "TTL window" we discussed earlier), the answer is almost always Global Accelerator or CloudFront Origin Groups, because they don't rely on the user's browser to update its DNS cache.

11) R53 do not validate the SSL certificate returned by the endpoint.

12) You can use Route 53 health checks to check for the presence of a designated string in a server response by selecting the “Enable String Matching” option

13) Yes. You can enable DNSSEC signing for existing and new public hosted zones.

14) Route 53 Resolver is integrated with AWS Resource Access Manager (RAM) which provides customers with a simple way to share their resources across AWS accounts or within their AWS Organization. Rules can be created in one primary account and then shared across multiple accounts using RAM. Once shared, the rules still need to be applied to VPCs in those accounts before they can take effect

15) Amazon Route 53 Resolver DNS Firewall works together with AWS Firewall Manager so you can build policies based on DNS Firewall rules, and then centrally apply those policies across your VPCs and accounts.

16) 
