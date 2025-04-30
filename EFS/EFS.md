
## 🟢  Basic Level (1–20) 

 1. What is Amazon EFS?   
   Ans:  Amazon Elastic File System (EFS) is a scalable, fully-managed NFS file system for use with AWS Cloud services and on-premises resources.

 2. What type of storage does Amazon EFS provide?   
   Ans:  Amazon EFS provides file-level storage.

 3. Which protocol does Amazon EFS use?   
   Ans:  EFS uses the NFSv4.1 or NFSv4.0 protocol.

 4. Is Amazon EFS region-specific?   
   Ans:  Yes, EFS is a regional service that stores data within and across multiple Availability Zones in a region.

 5. Can EFS be accessed from multiple EC2 instances?   
   Ans:  Yes, EFS can be mounted concurrently on multiple EC2 instances.

 6. What are the two performance modes in EFS?   
   Ans:  General Purpose and Max I/O.

 7. What are the two throughput modes in EFS?   
   Ans:  Bursting Throughput and Provisioned Throughput.

 8. What is the default throughput mode in EFS?   
   Ans:  Bursting Throughput.

 9. How is storage billed in EFS?   
   Ans:  You are billed based on the amount of data stored in the file system.

 10. What are the EFS storage classes?   
   Ans:  EFS Standard and EFS One Zone.

 11. What is the purpose of EFS One Zone?   
   Ans:  It's a lower-cost storage class that stores data in a single AZ.

 12. Can EFS automatically scale?   
   Ans:  Yes, EFS automatically scales as you add or remove files.

 13. What kind of durability does EFS offer?   
   Ans:  EFS offers 99.999999999% (11 9’s) durability.

 14. Is EFS serverless?   
   Ans:  Yes, EFS is serverless, so there’s no need to provision or manage infrastructure.

 15. What is EFS Access Point?   
   Ans:  It's an application-specific entry point into an EFS file system with customized permissions.

 16. What is the purpose of file system policies in EFS?   
   Ans:  They help define permissions and access control for the file system.

 17. Can you use EFS with containers?   
   Ans:  Yes, EFS can be used with ECS and EKS for persistent storage.

 18. Is EFS encrypted?   
   Ans:  Yes, EFS supports encryption at rest and in transit.

 19. Can you back up EFS?   
   Ans:  Yes, using AWS Backup or third-party solutions.

 20. Is there a free tier for Amazon EFS?   
   Ans:  Yes, 5 GB/month is available in the AWS Free Tier.

 

## 🟡  Intermediate Level (21–30) 

 21. What is the max size limit of an EFS file system?   
   Ans:  There is no practical size limit; it automatically scales up to petabytes.

 22. What does "burst credit" mean in EFS throughput?   
   Ans:  It allows file systems to exceed baseline throughput temporarily.

 23. How is EFS mounted on EC2 Linux?   
   Ans:  Using the `mount` command with NFS, e.g., `sudo mount -t nfs4 ...`.

 24. How does EFS handle file locking?   
   Ans:  EFS supports advisory file locking with NFSv4.

 25. What IAM policy permissions are required for EFS mounting helper?   
   Ans:  `elasticfilesystem:DescribeMountTargets` and `elasticfilesystem:ClientMount`.

 26. Can you restrict access to EFS based on IP or VPC?   
   Ans:  Yes, using security groups and NFS permissions.

 27. What are the use cases of EFS Access Points?   
   Ans:  Multi-user applications, ECS/EKS persistent storage, or app-specific isolation.

 28. How does EFS differ from Amazon S3?   
   Ans:  EFS is a file system for EC2 access (NFS), while S3 is object storage accessed over HTTP.

 29. What is EFS lifecycle management?   
   Ans:  Automatically moves files to EFS Infrequent Access (IA) tier after a configured period.

 30. Can EFS be used in hybrid environments?   
   Ans:  Yes, using AWS Direct Connect or VPN.

 

## 🔴  Advanced Level (31–50) 

 31. How do you optimize costs in EFS?   
   Ans:  Use lifecycle management and EFS One Zone-Infrequent Access tier.

 32. How does EFS handle high throughput workloads?   
   Ans:  By using Max I/O performance mode and Provisioned Throughput.

 33. What is the mount target in EFS?   
   Ans:  A network endpoint in a VPC subnet used to connect EFS with NFS clients.

 34. How is EFS integrated with CloudWatch?   
   Ans:  You can monitor metrics like throughput, IOPS, and burst credit balance.

 35. How can EFS be used for high availability?   
   Ans:  By mounting it from multiple Availability Zones and using EFS Standard.

 36. How do you automate mounting EFS on EC2 at boot?   
   Ans:  By adding an entry in `/etc/fstab`.

 37. What are potential performance bottlenecks in EFS?   
   Ans:  Exceeding burst credit, using General Purpose mode for parallel workloads.

 38. How do you migrate on-prem file systems to EFS?   
   Ans:  Use AWS DataSync, rsync, or third-party tools.

 39. What is the difference between EFS General Purpose and Max I/O?   
   Ans:  General Purpose has lower latency; Max I/O supports more connections with higher latency.

 40. What’s the effect of changing throughput mode in EFS?   
   Ans:  You can adjust performance; changing to provisioned allows predictable throughput.

 41. Can you use EFS with Lambda?   
   Ans:  Yes, EFS can be mounted on AWS Lambda for persistent, shared storage.

 42. How does EFS IA (Infrequent Access) pricing work?   
   Ans:  Lower cost per GB, but additional per-access fee for reads/writes.

 43. What happens if a file is accessed in EFS-IA?   
   Ans:  It’s read from IA, incurring access costs but not moved to standard.

 44. How do you prevent unauthorized access to EFS?   
   Ans:  Use IAM, VPC security groups, and NFS access controls.

 45. Can EFS be used with Windows EC2 instances?   
   Ans:  Not directly; EFS is designed for Linux. For Windows, use FSx for Windows File Server.

 46. What is the role of the `amazon-efs-utils` package?   
   Ans:  It simplifies mounting EFS and supports encryption in transit.

 47. What does EFS provide in terms of latency?   
   Ans:  Sub-millisecond latency for file operations in General Purpose mode.

 48. How do EFS and FSx differ in performance and compatibility?   
   Ans:  EFS is for Linux/NFS; FSx provides Windows-compatible SMB support and better Windows integration.

 49. Can you restrict EFS access to a particular EC2 role?   
   Ans:  Yes, using IAM policies and EFS access points.

 50. What happens if a mount target fails?   
   Ans:  EFS automatically fails over to another AZ mount target if available.

 
## 🔵  Real-Time Scenario-Based EFS Questions (50–70) 

 50.   Your EC2 instance is unable to mount the EFS file system. What are the possible causes?   
     Ans:   
    - Security group rules not allowing NFS port 2049.  
    - Mount target not in the same VPC or subnet.  
    - EFS not available in the AZ of the EC2.  
    - IAM permission issues if using EFS Access Points.  
    - `amazon-efs-utils` not installed or incorrectly configured.

 51.   Your application stores logs on EFS but performance is lagging under heavy traffic. What can you do?   
     Ans:   
    - Switch to  Max I/O performance mode .  
    - Enable  Provisioned Throughput .  
    - Use  multiple threads or processes  for parallel writes.  
    - Avoid small, frequent write operations.


 52.   You need to share a common file system between ECS containers in different AZs. What AWS service should you use?   
     Ans:   
    - Use  Amazon EFS  with  Access Points  for per-container permissions.  
    - Mount it via ECS Task Definitions.


 53.   You’re migrating a legacy file system to EFS but need to sync only specific file types. What’s the best approach?   
     Ans:   
    - Use  AWS DataSync  with include/exclude filters.  
    - Alternatively, use `rsync` with `--include` and `--exclude` options.

 54.   Your team wants to enable Lambda functions to read large reference files stored on EFS. How can you do it?   
     Ans:   
    - Attach EFS to Lambda using  VPC configuration .  
    - Use  Access Points  for each Lambda function.  
    - Ensure your Lambda function has appropriate IAM and security group settings.


 55.   How would you automate EFS mounting on EC2 at boot time?   
     Ans:   
    - Add the mount command to `/etc/fstab`, e.g.:
      ```bash
      fs-12345678.efs.us-east-1.amazonaws.com:/ /mnt/efs nfs4 defaults,_netdev 0 0
      ```

 56.   An EFS file system used by Kubernetes pods becomes unresponsive. What would you check?   
     Ans:   
    - Network policies or security groups.  
    - NFS connection from the node.  
    - EFS mount targets in correct subnets.  
    - Node IAM permissions if using EFS CSI driver.

 57.   How would you set up cost optimization for EFS in a multi-AZ production setup?   
     Ans:   
    - Enable  lifecycle management  to move files to  Infrequent Access (IA) .  
    - Regularly monitor usage with  CloudWatch metrics .  
    - Delete unused or temporary files periodically.
      
 58.   Your organization wants to isolate access for multiple microservices to different folders within the same EFS. How can this be achieved?   
     Ans:   
    - Use  EFS Access Points  configured with different root directories and POSIX permissions.

 59.   An EC2 instance loses access to EFS after a reboot. What might be wrong?   
     Ans:   
    - Mount script not in fstab or init script.  
    - Security group changed.  
    - Network interface or routing table misconfigured.

 60.   You’re creating an HA web application with Apache servers on EC2. How can EFS help?   
     Ans:   
    - Store shared content like static files and media on EFS, allowing all EC2 instances to access the same data.

 61.   Your CI/CD pipeline needs to push build artifacts to a central shared volume. What AWS file system would you use?   
     Ans:   
    - Use  EFS  mounted across build agents or EC2-based runners.

 62.   A data processing app needs high throughput but files are rarely accessed after processing. How do you optimize cost and performance?   
     Ans:   
    - Enable  Provisioned Throughput  and  Lifecycle Management to EFS-IA .

 63.   Your app on EC2 needs persistent storage across AZs. EBS won’t work. What's the solution?   
     Ans:   
    - Use  EFS , which is AZ-independent and mountable across multiple instances.

 64.   How would you monitor and alert on EFS throughput usage?   
     Ans:   
    - Set up  CloudWatch Alarms  on `BurstCreditBalance` and `ThroughputUtilization`.

 65.   You need to mount EFS securely on a public subnet EC2. How do you secure it?   
     Ans:   
    - Use  mount helper with TLS encryption .  
    - Limit NFS access via  security groups  and  private IP  communication.

 66.   Why would you choose EFS over S3 in an analytics workload?   
   Ans:   
  - When your application needs  POSIX-compliant  file access or shared file system semantics.

 67.   Your multi-user system requires that each user has access only to their own directory on EFS. What’s the best solution?   
     Ans:   
    - Create  EFS Access Points  per user with `uid/gid` settings and path isolation.

 68.   What tools can you use to migrate large NFS workloads to EFS efficiently?   
     Ans:   
    -  AWS DataSync , `rsync`, or AWS Storage Gateway (for hybrid migrations).

 69.   A customer asks if EFS supports file-level backup. What would you recommend?   
     Ans:   
    - Use  AWS Backup  for automated file system-level backups.  
    - For file-level recovery, combine EFS with  versioning/snapshot scripts .

 70.   You are running a video rendering farm on EC2 Spot Instances. Which storage backend suits shared scratch storage?   
     Ans:   
    - Use  Amazon EFS  with  Max I/O  for parallel processing and high IOPS.
