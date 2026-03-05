1) If you have an EC2 Auto Scaling group (ASG) with running instances and you choose to delete the ASG, the instances will be terminated and the ASG will be deleted.

2) When you use Amazon EC2 Auto Scaling to scale your applications automatically, it is useful to know when EC2 Auto Scaling is launching or terminating the EC2 instances in your EC2 Auto Scaling group. Amazon SNS coordinates and manages the delivery or sending of notifications to subscribing clients or endpoints. You can configure EC2 Auto Scaling to send an SNS notification whenever your EC2 Auto Scaling group scales. Amazon SNS can deliver notifications as HTTP or HTTPS POST, email (SMTP, either plain-text or in JSON format), or as a message posted to an Amazon SQS queue. For example, if you configure your EC2 Auto Scaling group to use the autoscaling: EC2_INSTANCE_TERMINATE notification type, and your EC2 Auto Scaling group terminates an instance, it sends an email notification. This email contains the details of the terminated instance, such as the instance ID and the reason that the instance was terminated.

3) However, you can only specify one launch configuration for an EC2 Auto Scaling group at a time, and you can't modify a launch configuration after you've created it. Therefore, if you want to change the launch configuration for your EC2 Auto Scaling group, you must create a launch configuration and then update your EC2 Auto Scaling group with the new launch configuration. When you change the launch configuration for your EC2 Auto Scaling group, any new instances are launched using the new configuration parameters, but existing instances are not affected.

4) You don't have to manually terminate them! While updating the configuration doesn't automatically trigger a replacement, AWS provides a built-in feature to handle this for you.
To replace existing instances with new ones automatically, you use Instance Refresh.
How Instance Refresh Works
Instead of manual termination, you trigger an Instance Refresh on your Auto Scaling Group (ASG). AWS then:
Stops/Terminates a few old instances at a time.
Launches new instances using your new Launch Configuration (or Launch Template).
Waits for the new instances to pass health checks before moving to the next batch.
Key Benefits
Zero Downtime: You can set a "Minimum Healthy Percentage" (e.g., 90%) so the ASG always keeps enough instances running to handle traffic.
Automation: You don't have to track which instances are "old" vs "new."
Rollback: If the new instances fail health checks, AWS can stop the refresh, preventing a total outage.
Alternative Methods
If you don't use Instance Refresh, you have two other options:
Manual Termination: If you terminate an old instance, the ASG will notice the count is low and automatically launch a replacement using the new configuration.
Doubling the Capacity: Increase the "Desired Capacity" to double your instances. Once the new ones are healthy, decrease the capacity back to the original size. The ASG will typically terminate the oldest instances first (depending on your Termination Policy).
Important Note: AWS now strongly recommends using Launch Templates instead of Launch Configurations. Launch Templates support versioning, which makes this entire update process much cleaner.

5) EC2 Auto Scaling groups are regional constructs. They can span Availability Zones, but not AWS regions.

6) Q: If I have data installed in an EC2 Auto Scaling group, and a new instance is dynamically created later, is the data copied over to the new instances?
Data is not automatically copied from existing instances to new instances. You can use lifecycle hooks to copy the data, or an Amazon RDS database including replicas

7) Lifecycle hooks let you take action before an instance goes into service or before it gets terminated. This can be especially useful if you are not baking your software environment into an Amazon Machine Image (AMI). For example, launch hooks can perform software configuration on an instance to ensure that it’s fully prepared to handle traffic before Amazon EC2 Auto Scaling proceeds to connect it to your load balancer. One way to do this is by connecting the launch hook to an AWS Lambda function that invokes RunCommand on the instance. Terminate hooks can be useful for collecting important data from an instance before it goes away. For example, you could use a terminate hook to preserve your fleet’s log files by copying them to an Amazon S3 bucket when instances go out of service.

8) Amazon EC2 Auto Scaling performs health checks on each individual EC2 instance at regular intervals, and if the instance is connected to an Elastic Load Balancing load balancer, it can also perform ELB health checks.

9) Yes, you can temporarily suspend Amazon EC2 Auto Scaling health checks by using the SuspendProcesses API. You can use the ResumeProcesses API to resume automatic health checks.

10) If you are using Elastic Load Balancing (ELB) with your group, you should select an ELB health check. If you’re not using ELB with your group, you should select the EC2 health check.

11) When ELB notices that the instance is unhealthy, it will stop routing requests to it. However, prior to discovering that the instance is unhealthy, some requests to that instance will fail.

12) Vertical Health (One instance, multiple groups): If it fails anywhere, it is unhealthy everywhere (for that instance).
Horizontal Health (Many instances, one group): If one instance fails, it does not make its healthy neighbors unhealthy.

13) 
