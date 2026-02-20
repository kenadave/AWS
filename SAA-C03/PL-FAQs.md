1) Amazon VPC offers five different types of VPC endpoints: gateway endpoint, interface endpoint, Gateway Load Balancer endpoint,
   resource endpoint, and service network endpoint.

2) All VPC endpoint types except gateway endpoint are powered by PrivateLink.

3) While VPC peering is limited to 125 VPC connections, AWS PrivateLink has virtually unlimited scale

4) You can create up to 100 VPC endpoints per VPC

5) PrivateLink does not provide any encryption by default for data in transit. The service consumer always initiates the service (it is a one-way service), and that the service provider only provides service to allowlisted customers.

6) Yes. You can associate security groups with VPC endpoints.

7)  You cannot associate security groups with Gateway Endpoints (S3 and DynamoDB). Those are managed via Route Tables and Endpoint Policies instead.
