1) Yes. WebSockets and Secure WebSockets support is available natively and ready for use on an Application Load Balancer.

2) Yes. Request tracing is enabled by default on your Application Load Balancer.

3) No, only encryption is supported to the back-ends with an Application Load Balancer - Not Authentication

4) Cross-zone load balancing is already enabled by default in Application Load Balancer.

5) 1. Amazon Cognito Scenario: "The Identity Hub"
In this scenario, Cognito acts as a bridge and a database. 
Who owns the data? You do. Even if a user logs in via Google, Cognito creates a "shadow profile" in its own directory.
Why use it? You need to enrich that user data. You can add custom fields (like subscription_status: 'paid'), put users into groups (like Admin or Premium), and manage their lifecycle (resetting passwords, disabling accounts) regardless of which provider they used to sign in.
Best for: Applications with a mix of login types (Facebook + Google + email/password) where you want a single, standardized way to manage all those users in one place. 

2. Direct OIDC Scenario: "The Simple Pass-Through"
In this scenario, the ALB talks directly to an existing, external Identity Provider (IdP). 
Who owns the data? The external IdP (like Okta, Ping Identity, or your own custom system).
Why use it? You already have a mature identity system and don't want to create another user directory in AWS. The ALB simply checks the "passport" provided by that system and, if valid, lets the user through. It does not store a local copy of the user's profile.
Best for: Internal corporate apps where you only want employees to log in using the company's existing SSO provider (like Okta or Azure AD) and you don't need to manage extra "AWS-only" data about them. 

6) LambdaTargetProcessedBytes and StandardProcessedBytes

7)  Network Load Balancer automatically provides a static IP per Availability Zone (AZ) to the load balancer

8)  Yes, you can use Amazon Route 53 health checking and DNS failover features to enhance the availability of the applications running behind Network Load Balancers.

9)  For each associated subnet a Network Load Balancer is in, the Network Load Balancer can only support a single public/internet facing IP address.

10)  Correct. Cross-zone load balancing is always enabled by default for ALBs, but it is disabled by default for NLBs

11) The Health Check Requirement: If your LB cannot "hear" the response from the target because a rule is blocking it, the LB will mark the target as Unhealthy, even if the application is running perfectly.
11)  
