1) The total volume of data and number of objects you can store in Amazon S3 are unlimited. Individual Amazon S3 objects can range in size from a minimum of 0 bytes to a maximum of 50 TB. The largest object that can be uploaded in a single PUT is 5 GB. For objects larger than 100 MB, customers should consider using the multipart upload capability.

2) General purpose buckets are the original S3 bucket type, and a single general purpose bucket can contain objects stored across all storage classes except S3 Express One Zone.

3) S3 directory buckets only allow objects stored in the S3 Express One Zone storage class, which provides faster data processing within a single Availability Zone.

4) Each S3 directory bucket can support up to 2 million transactions per second (TPS), independent of the number of directories within the bucket.

5) A table bucket is purpose-built for storing tables using the Apache Iceberg format.

6) S3 table buckets are specifically optimized for analytics and machine learning workloads.

7) general purpose bucket accepts all classes except express one zone class. directory bucket only accepts express one zone class

8) 
