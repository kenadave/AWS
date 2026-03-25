### Reliability Problems Summary Table

| Problem                   | Architecture Pattern        | AWS Service                  |
|---------------------------|-----------------------------|-------------------------------|
| Dependency Failures       | Circuit Breaker             | Amazon API Gateway, AWS Lambda|
| Database Bottlenecks      | Read Replicas               | Amazon RDS, Amazon DynamoDB   |
| Partial Update Failures   | Eventual Consistency        | Amazon S3, Amazon DynamoDB    |
| Network Instability       | Resilient Network Design    | AWS Global Accelerator         |
| Traffic Spikes            | Auto-Scaling                | Amazon EC2, AWS Lambda         |
| Long-Running Operations   | Step Functions              | AWS Step Functions             |
| Queue Configuration       | Message Queuing             | Amazon SQS, Amazon SNS        |
| Monitoring & Troubleshooting| Monitoring Dashboards      | Amazon CloudWatch              |

