Here is a set of **interview-style answers** for all your EC2-related questions, optimized for DevOps/AWS job interviews:

---

### ✅ **1. What is an EC2 instance type, and how do you choose the right one?**

An **EC2 instance type** defines the compute, memory, storage, and networking capacity of an instance. Choose based on:

* **General purpose** (e.g., `t3`, `m6g`) → balanced
* **Compute optimized** (e.g., `c6g`) → high-performance CPUs
* **Memory optimized** (e.g., `r6g`) → RAM-heavy apps
* **Storage optimized** (e.g., `i3`) → IOPS-intensive apps
* **Accelerated computing** (e.g., `p5`, `g4`) → ML/AI

---

### ✅ **2. What is an EC2 instance family, and when would you use each?**

An **instance family** is a grouping of instance types with similar characteristics.
Examples:

* `t`: burstable (low-cost dev/test)
* `c`: compute-optimized (batch jobs, web servers)
* `r`: memory-optimized (in-memory DBs)
* `p/g`: GPU workloads

---

### ✅ **3. Typical steps to launch an EC2 instance:**

1. Choose AMI (OS)
2. Select instance type
3. Configure network & subnet
4. Add storage (EBS)
5. Add tags (Name, Env)
6. Configure security group
7. Add user data (optional)
8. Select or create key pair
9. Launch instance

---

### ✅ **4. What is EC2 user data?**

A **user data script** automates boot-time configuration, such as:

* Installing packages
* Setting environment variables
* Running application code

Written in Bash or cloud-init and passed during launch.

---

### ✅ **5. What is EC2 instance metadata?**

Metadata provides info about the instance (ID, IP, region, IAM role, etc.). Access from:

```bash
curl http://169.254.169.254/latest/meta-data/
```

Useful for scripts and automation.

---

### ✅ **6. How to create custom AMIs and why?**

Steps:

* Configure an EC2 instance
* Create image via console or CLI
  Benefits:
* Faster scaling (pre-baked configs)
* Custom environments
* Consistency across environments

---

### ✅ **7. What are security groups?**

**Virtual firewalls** controlling traffic to EC2. Key points:

* **Stateful**: response allowed automatically
* Define **inbound/outbound rules**
* Attached at instance level

---

### ✅ **8. What are NACLs and how are they different?**

**Network ACLs**:

* **Stateless**, applied at subnet level
* Allow/deny rules for **inbound and outbound**
* Use for layered security (VPC-wide)

---

### ✅ **9. How to use AWS WAF with EC2?**

* Place EC2 behind an **ALB**
* Associate **Web ACL** with the ALB
* Use rules for:

  * SQL injection
  * IP blocking
  * Rate limiting

---

### ✅ **10. What is Auto Scaling?**

Auto Scaling:

* Automatically adds/removes instances based on demand
* Ensures **availability** and **cost-efficiency**
* Tied to CloudWatch alarms and load balancer

---

### ✅ **11. What is Elastic Load Balancing (ELB)?**

ELB distributes traffic across EC2 instances:

* Ensures **fault tolerance**
* Types: ALB (L7), NLB (L4), CLB (legacy)
* Health checks to route traffic only to healthy targets

---

### ✅ **12. What is ECS on EC2?**

**Amazon ECS** is a container orchestration service.

* EC2 Launch Type: manually manage EC2 for containers
* Manages clusters, tasks, services
* Great for hybrid control before moving to Fargate

---

### ✅ **13. How to configure Route 53 for EC2?**

* Create **A or CNAME records**
* Point to ALB DNS or EC2 public IP
* Use **health checks**, weighted or latency-based routing for high availability

---

### ✅ **14. What is EC2 status check?**

There are two checks:

* **System check**: AWS hardware/network
* **Instance check**: OS boot errors, kernel panic, etc.

---

### ✅ **15. How to change instance type without downtime?**

1. Attach instance to **Auto Scaling Group**
2. Use **blue-green deployment**
3. Or:

   * Stop the instance
   * Change type
   * Start again (minimal downtime)

---

### ✅ **16. AMI vs Snapshot**

| Feature  | AMI                | Snapshot                     |
| -------- | ------------------ | ---------------------------- |
| Purpose  | Launch EC2         | Backup EBS volume            |
| Includes | OS + config + data | Only EBS volume data         |
| Usage    | Create instance    | Restore volume or create AMI |

---

### ✅ **17. Kernel Panic in EC2:**

* Use **EC2 serial console** (newer feature)
* **Detach root volume**, attach to another instance, fix files (e.g., `/etc/fstab`, `grub`)
* Create new AMI if persistent

---

### ✅ **18. Max IPs on EC2:**

* Depends on instance type
* E.g., `t3.medium` supports **3 ENIs**, each with multiple secondary IPs

---

### ✅ **19. EC2 purchasing options:**

* **On-Demand**: pay per hour/second
* **Reserved**: 1 or 3 years, discounted
* **Spot**: unused capacity, 90% cheaper, interruptible
* **Savings Plans**: flexible billing option
* **Dedicated Hosts/Instances**: physical isolation

---

### ✅ **20. AWS Placement Groups – Types**

| Type      | Description                           | Use Case               |
| --------- | ------------------------------------- | ---------------------- |
| Cluster   | Close proximity for low latency       | HPC, Big Data, ML      |
| Spread    | Separate hardware for fault tolerance | Critical small apps    |
| Partition | Grouped instances across partitions   | HDFS, Kafka, Cassandra |

---

### ✅ **21. Can you change Placement Group for a running instance?**

No. You must **stop** the instance, **create an AMI**, and launch a new instance in the desired group.

---

### ✅ **22. AZ vs Placement Group**

* **AZ**: Data center zone in a region
* **Placement Group**: Logical grouping within or across AZs for control over instance placement

---

### ✅ **23. Placement Group Best Practices**

* Same instance type and size
* Launch all instances **together**
* Use **enhanced networking** for better performance

---

### ✅ **24. Placement Group Limitations**

* Some types support limited instance types
* Limited capacity (cluster groups)
* No automatic distribution like Auto Scaling

---

### ✅ **25. Use Cases for EBS Types**

| Type    | Use Case                                    |
| ------- | ------------------------------------------- |
| gp2     | General use, boot volumes, dev/test         |
| gp3     | Better gp2 – cheaper with configurable IOPS |
| io1/io2 | High-IO DBs (MongoDB, Oracle, etc.)         |
| st1     | Streaming/logs, large sequential access     |
| sc1     | Cold data, archival                         |

---

### ✅ **26. What is Amazon EBS? How is it different from S3?**

* **EBS**: Block storage (like a hard drive), attached to EC2
* **S3**: Object storage, accessible via HTTP, scalable and distributed

---

### ✅ **27. Provisioned IOPS (PIOPS):**

* Used with `io1`, `io2` for consistent high I/O performance
* Choose when latency-sensitive workloads need **guaranteed throughput**

---

### ✅ **28. How to resize an EBS volume safely:**

1. Modify volume in console or CLI
2. Extend partition (e.g., using `growpart`, `resize2fs`)
   **Precautions**:

* Backup before resize
* Ensure volume type supports resizing

---

### ✅ **29. EBS Volume Types vs Size:**

* **Type** determines performance baseline (e.g., gp3 vs io2)
* **Size** affects throughput and burst (for gp2)
  Choose right size/type combo to match workload.

---

### ✅ **30. EBS Snapshots:**

* **Point-in-time backups** of volumes stored in S3
* Can be used to restore or create new volumes/AMIs
* Crucial for DR and backup

---

### ✅ **31. Snapshot Best Practices:**

* Schedule daily or weekly via AWS Backup
* Use tags for lifecycle policies
* Store in different regions for redundancy

---

### ✅ **32. Best Practices for EBS Encryption:**

* Enable encryption at creation (KMS key)
* Use encrypted AMIs
* All data in transit and at rest is secured
* Snapshot of encrypted volumes remain encrypted

---

### ✅ **33. EBS-backed vs Instance-store-backed EC2:**

| Feature     | EBS-backed          | Instance-store               |
| ----------- | ------------------- | ---------------------------- |
| Persistence | Survives stop/start | Data lost on stop/terminate  |
| Performance | Consistent IOPS     | Higher I/O for temp data     |
| Use Case    | DB, apps            | Cache, buffer, scratch space |

---

### ✅ **34. How to monitor EBS performance:**

* **CloudWatch Metrics**: `VolumeReadOps`, `VolumeWriteOps`, `VolumeIdleTime`
* Use **CloudWatch Alarms** for thresholds
* Enable **CloudTrail** and use **AWS Compute Optimizer**

---

Let me know if you want this in PDF format, a cheatsheet table, or mock interview set!
