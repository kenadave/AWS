1) Yes, you can package any code (frameworks, SDKs, libraries, and more) as a Lambda Layer and manage and share them easily across multiple functions.

2) Q: Can I store sensitive information in environment variables?
For sensitive information, such as database passwords, we recommend you use client-side encryption using AWS Key Management Service and store the resulting values as ciphertext in your environment variable. You will need to include logic in your AWS Lambda function code to decrypt these values.

3) 
Lambda SnapStart (Best-Effort Optimization)
Guaranteed Elimination (Provisioned Concurrency)
No. Lambda SnapStart and PC cannot be enabled at the same time, on the same function.

4) On exceeding the maximum concurrent executions limit, AWS Lambda functions being invoked synchronously will return a throttling error (429 error code). Lambda functions being invoked asynchronously can absorb reasonable bursts of traffic for approximately 15-30 minutes, after which incoming events will be rejected as throttled. In case the Lambda function is being invoked in response to Amazon S3 events, events rejected by AWS Lambda may be retained and retried by S3 for 24 hours. Events from Amazon Kinesis streams and Amazon DynamoDB streams are retried until the Lambda function succeeds or the data expires. Amazon Kinesis and Amazon DynamoDB Streams retain data for 24 hours.

5) Q: What happens if my Lambda function fails while processing an event?
On failure, Lambda functions being invoked synchronously will respond with an exception. Lambda functions being invoked asynchronously are retried at least 3 times. Events from Amazon Kinesis streams and Amazon DynamoDB streams are retried until the Lambda function succeeds or the data expires. Kinesis and DynamoDB Streams retain data for a minimum of 24 hours.

6) Each synchronously invoked Lambda function can scale at a rate of up to 1000 concurrent executions every 10 seconds.

7) Q: What happens if my Lambda function invocations exhaust the available policy?
On exceeding the retry policy for asynchronous invocations, you can configure a “dead letter queue” (DLQ) into which the event will be placed; in the absence of a configured DLQ the event may be rejected. On exceeding the retry policy for stream-based invocations, the data would have already expired and therefore rejected.

You can configure an Amazon SQS queue or an Amazon SNS topic as your dead letter queue.

8) You can enable Lambda functions to access resources in your VPC by specifying the subnet and security group as part of your function configuration. Lambda functions configured to access resources in a particular VPC will not have access to the internet as a default configuration. To grant internet to these functions, use internet gateways.

9) Code Signing for AWS Lambda offers trust and integrity controls that enable you to verify that only unaltered code from approved developers is deployed in your Lambda functions. You can use AWS Signer, a fully-managed code signing service, to digitally sign code artifacts and configure your Lambda functions to verify the signatures at deployment. Code Signing for AWS Lambda is currently only available for functions packaged as ZIP archives.

10) CloudWatch Application Signals is an application performance monitoring (APM) solution which enables developers and operators to easily monitor the health and performance of serverless applications built with Lambda

11) 
