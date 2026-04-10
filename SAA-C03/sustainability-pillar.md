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

61) Convert payloads and files into optimized formats required by devices. For example, you can use Amazon Elastic Transcoder or AWS Elemental MediaConvert to convert large, high quality digital media files into formats that users can play back on mobile devices, tablets, web browsers, and connected televisions.

62)
The Priority List (Simplified)
When scaling in, AWS asks these questions in order:
AZ Balance: Which Availability Zone has the most instances? (Pick that AZ).
Allocation Strategy: Which type of instance (Spot vs. On-Demand) do I have "too many" of right now? (Pick that type).
Age: Which instance of that type is using the oldest Launch Template? (Pick that one).

63) 

| Storage Class | Min. Storage Duration | Retrieval Time (Latency) |
| :--- | :--- | :--- |
| **S3 Standard** | None | Milliseconds |
| **S3 Intelligent-Tiering** | None* | Milliseconds |
| **S3 Standard-IA** | 30 Days | Milliseconds |
| **S3 One Zone-IA** | 30 Days | Milliseconds |
| **S3 Glacier Instant Retrieval** | 90 Days | Milliseconds |
| **S3 Glacier Flexible Retrieval** | 90 Days | 1–5 min (Expedited), 3–5 hrs (Standard), 5–12 hrs (Bulk) |
| **S3 Glacier Deep Archive** | 180 Days | 12 hrs (Standard), 48 hrs (Bulk) |
