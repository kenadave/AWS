1) There are four best practice areas for operational excellence in the cloud:

Organization

Prepare

Operate

Evolve

2) Use services like AWS Config to create governance-as-code and validate that governance requirements are followed.

If you use AWS Organizations, you can leverage Service Control Policies to implement governance requirements.

3) Validate continual compliance of AWS resources with services like AWS Compute Optimizer and AWS Security Hub CSPM.

4) Use services like AWS Audit Manager to validate compliance and generate audit reports.

You can download AWS security and compliance documents with AWS Artifact.

5) To implement application telemetry for your workload, use AWS services like Amazon CloudWatch and AWS X-Ray. In tandem, AWS X-Ray lets you trace, analyze, and debug your applications, giving you a deep understanding of your workload's behavior. With features like service maps, latency distributions, and trace timelines, AWS X-Ray provides insights into your workload's performance and the bottlenecks affecting it.

6) The CloudWatch agent can also be used to collect OpenTelemetry or X-Ray traces and send them to X-Ray. For the SAA-C03, if a question asks about a vendor-agnostic or portable tracing solution, the answer is OpenTelemetry (ADOT). If it asks for the simplest AWS-native setup for a legacy app, it might still refer to the X-Ray SDK.

7) Use CloudWatch Logs anomaly detection and CloudWatch Metrics anomaly detection to automatically identify unusual activities in your application's operations. These tools use machine learning algorithms to detect and alert on anomalies, which enanhces your monitoring capabilities and speeds up response time to potential disruptions or security threats. Set up these features to proactively manage application health and security.

8) To leverage RUM and synthetic transactions for user activity telemetry, AWS offers services like Amazon CloudWatch RUM and Amazon CloudWatch Synthetics

9) Use Amazon DevOps Guru: This machine learning-driven service identifies operational issues, predicts when critical issues might occur, and recommends specific actions to take.

10) 
To implement distributed tracing effectively:

Adopt AWS X-Ray: Integrate X-Ray into your application to gain insights into its behavior, understand its performance, and pinpoint bottlenecks. Utilize X-Ray Insights for automatic trace analysis.

Instrument your services: Verify that every service, from an AWS Lambda function to an EC2 instance, sends trace data. The more services you instrument, the clearer the end-to-end view.

Incorporate CloudWatch Real User Monitoring and synthetic monitoring: Integrate Real User Monitoring (RUM) and synthetic monitoring with X-Ray. This allows for capturing real-world user experiences and simulating user interactions to identify potential issues.

Use the CloudWatch agent: The agent can send traces from either X-Ray or OpenTelemetry, enhancing the depth of insights obtained.

Use Amazon DevOps Guru: DevOps Guru uses data from X-Ray, CloudWatch, AWS Config, and AWS CloudTrail to provide actionable recommendations.

Analyze traces: Regularly review the trace data to discern patterns, anomalies, or bottlenecks that might impact your application's performance.

Set up alerts: Configure alarms in CloudWatch for unusual patterns or extended latencies, allowing proactive issue addressing.

Continuous improvement: Revisit your tracing strategy as services are added or modified to capture all relevant data points.

11) Use Amazon Q Developer, a generative AI tool that can help create unit test cases (including boundary conditions), generate functions using code and comments, and implement well-known algorithms.

Use Amazon CodeGuru Reviewer to test your application code for defects.

You can use AWS CodeBuild to conduct tests on software artifacts.

AWS CodePipeline can orchestrate your software tests into a pipeline.

12) For dynamic configurations in your applications running on Amazon EC2 instances, AWS Lambda, containers, mobile applications, or IoT devices, you can use AWS AppConfig to configure, validate, deploy, and monitor them across your environments.

13)  If the exam question asks about "feature flags" or "dynamic application settings," pick AppConfig. If it asks about "compliance auditing" or "resource history," pick AWS Config.

14)  AppConfig is for your application's code and features; Config is for your AWS infrastructure.

15)  EC2 Image Builder is a fully-managed service that simplifies customization, testing, distribution, and lifecycle management of Amazon Machine Images (AMIs) and container images.

16)  
