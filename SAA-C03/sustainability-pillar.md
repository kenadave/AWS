58) 

| Service | When to use |
| :--- | :--- |
| **Lambda@Edge** | Use for compute-heavy operations that are initiated when objects are not in the cache. |
| **Amazon CloudFront Functions** | Use for simple use cases like HTTP(s) request or response manipulations that can be initiated by short-lived functions. |
| **AWS IoT Greengrass** | Use to run local compute, messaging, and data caching for connected devices. |


59) 
| Queuing mechanism | Description |
| :--- | :--- |
| **AWS Batch job queues** | AWS Batch jobs are submitted to a job queue where they reside until they can be scheduled to run in a compute environment. |
| **Amazon SQS and Amazon EC2 Spot Instances** | Pairing Amazon SQS and Spot Instances to build fault tolerant and efficient architectures. |


60) 

| Scheduling mechanism | Description |
| :--- | :--- |
| **Amazon EventBridge Scheduler** | A capability from Amazon EventBridge that allows you to create, run, and manage scheduled tasks at scale. |
| **AWS Glue time-based schedule** | Define a time-based schedule for your crawlers and jobs in AWS Glue. |
| **Amazon ECS scheduled tasks** | Amazon ECS supports creating scheduled tasks. Scheduled tasks use Amazon EventBridge rules to run tasks either on a schedule or in a response to an EventBridge event. |
| **Instance Scheduler** | Configure start and stop schedules for your Amazon EC2 and Amazon Relational Database Service instances. |
