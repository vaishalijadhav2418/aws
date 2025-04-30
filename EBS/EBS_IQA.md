Interview Question:
What is Amazon EBS, and how does it differ from Amazon S3?

✅ Sample Answer:
Amazon EBS (Elastic Block Store) is a block-level storage service designed to be used with Amazon EC2 instances. It provides persistent storage volumes that can be attached to EC2 instances and used like a hard drive. You can


✅ 1. What is Amazon EBS?
Answer: Amazon EBS is a block-level storage service provided by AWS. It allows you to create storage volumes that can be attached to Amazon EC2 instances. EBS volumes behave like raw, unformatted block devices and can be formatted and mounted as file systems. They are ideal for use cases requiring persistent storage like databases or file systems.

✅ 2. What are the different types of EBS volumes?
Answer: Amazon EBS offers several volume types optimized for different workloads:

gp3: General Purpose SSD, cost-effective for a wide variety of workloads.

gp2: Older General Purpose SSD (being phased out in favor of gp3).

io2/io1: Provisioned IOPS SSD, designed for high-performance and I/O-intensive workloads like large databases.

st1: Throughput Optimized HDD, good for streaming workloads like big data.

sc1: Cold HDD, for infrequently accessed data.

✅ 3. What is the difference between EBS and S3?
Answer:


Feature	EBS	S3
Type	Block Storage	Object Storage
Access	Attached to EC2 only	Accessible over internet
Use Case	Databases, file systems	Static websites, backups
Performance	High IOPS possible	Not suitable for IOPS-heavy
Persistence	Yes	Yes
✅ 4. Is Amazon EBS data persistent?
Answer: Yes, Amazon EBS volumes are persistent. The data on EBS volumes persists independently of the lifecycle of the EC2 instance to which they are attached. If an EC2 instance is stopped or terminated, the EBS volume can still be preserved and re-attached to another instance.

✅ 5. Can you attach one EBS volume to multiple EC2 instances?
Answer:

By default, an EBS volume can be attached to only one EC2 instance at a time.

However, EBS Multi-Attach is a feature available for io1 and io2 volumes, which allows a single volume to be attached to multiple instances in the same Availability Zone. This is useful for clustered applications like Oracle RAC.

✅ 6. How do EBS snapshots work?
Answer: EBS snapshots are point-in-time backups of your EBS volumes stored in Amazon S3. They are incremental, which means only the blocks that have changed since the last snapshot are saved, reducing storage costs and backup time.

✅ 7. What are the benefits of gp3 over gp2 volumes?
Answer:

gp3 volumes allow you to provision performance independently of storage capacity.

gp3 offers baseline performance of 3,000 IOPS and 125 MB/s throughput, regardless of volume size.

Cheaper than gp2 and more predictable performance.

✅ 8. What is the maximum size of an EBS volume?
Answer: As of now, the maximum size of a single EBS volume is 16 TiB (terabytes).



🔄 9. Scenario: How would you migrate data from one EBS volume to another with minimal downtime?
Answer: You can use the following steps:

Take a snapshot of the existing volume.

Create a new volume from the snapshot.

Detach the old volume (after stopping services if needed).

Attach the new volume to the EC2 instance.

Mount it using the same mount point.

If zero downtime is required, use LVM or RAID across volumes and shift the traffic gradually.

🔐 10. How does EBS encryption work and what does it encrypt?
Answer: EBS encryption uses AWS KMS to encrypt data at rest, in transit between EC2 and EBS, and all snapshots and volumes created from the encrypted volume. Encryption includes:

Data stored on the volume

Disk I/O

Snapshots

Data copied between volumes

It is completely transparent to the user.

🚀 11. How can you improve EBS volume performance?
Answer:

Use provisioned IOPS (io1/io2) for high-performance workloads.

Upgrade from gp2 to gp3, and manually increase IOPS and throughput.

Use EBS-optimized instances.

Use RAID 0 for striping across multiple volumes (increases throughput, not redundancy).

Monitor performance using CloudWatch metrics and fine-tune as needed.

🧩 12. Scenario: Your EC2 instance is running slow. How do you check if the EBS volume is the bottleneck?
Answer:

Check CloudWatch metrics for EBS volume:

VolumeReadOps, VolumeWriteOps

VolumeQueueLength (should generally be < 1)

VolumeThroughputPercentage and VolumeConsumedReadWriteOps

If IOPS is maxed out, consider:

Upgrading to a gp3/io1/io2 volume

Provisioning more IOPS

Distributing load across multiple volumes

💾 13. Can EBS volumes be resized? How do you do it?
Answer: Yes, EBS volumes can be resized:

Modify the volume using the AWS Console or CLI (aws ec2 modify-volume).

Wait for the state to be optimizing.

Resize the file system inside the EC2 instance:

For ext4: sudo resize2fs /dev/xvdf

For XFS: sudo xfs_growfs /mount-point

No need to stop the instance.

☁️ 14. What is EBS Snapshots Lifecycle Manager (SLM)?
Answer: EBS SLM is an AWS feature that automates the creation, retention, and deletion of EBS snapshots. It helps manage backup policies without needing custom scripts or manual work.

🔄 15. What is the difference between EBS-backed and instance store-backed EC2 instances?
Answer:


Feature	EBS-backed	Instance Store-backed
Data persistence	Persists after instance stop	Lost after stop or termination
Root volume type	EBS	Ephemeral storage
Flexibility	Can resize and move volumes	Cannot resize or move
Use case	General purpose workloads	Temporary storage, cache, buffer


💰 16. EBS Cost Optimization – How can you reduce EBS costs?
Answer:

Choose the right volume type:

Use gp3 instead of gp2 for cost-effective SSD performance.

Use st1 or sc1 for cold/throughput workloads.

Delete unused volumes:

Monitor and remove unattached EBS volumes (these still incur charges).

Use Snapshots instead of always-on volumes:

If you don’t need a volume 24/7, create a snapshot and delete the volume.

Automate snapshot lifecycle:

Use EBS Lifecycle Manager to clean up old backups.

Resize over-provisioned volumes:

Monitor usage and reduce volume size if possible (requires snapshot and restore).

🧯 17. How do you implement disaster recovery using EBS?
Answer: To ensure DR readiness with EBS:

Regular snapshots:

Schedule periodic EBS snapshots to backup data.

Cross-region snapshot copy:

Use the copy-snapshot feature to store backups in a different AWS region.

Automation:

Use AWS Backup or Lambda + EventBridge to automate multi-region DR.

Recovery Plan:

Pre-create launch templates and IAM roles.

Use snapshots to spin up a new EC2 with the same volume in another region.

🌎 18. How do you implement cross-region EBS backup strategy?
Answer:

Create a snapshot of the EBS volume.

Use copy-snapshot to duplicate the snapshot to a target region:

bash
Copy
Edit
aws ec2 copy-snapshot \
  --source-region us-east-1 \
  --source-snapshot-id snap-0123456789abcdef0 \
  --destination-region us-west-2
Encrypt if needed using a CMK in the destination region.

Automate the above using Lambda or AWS Backup with cross-region policies.

You can then restore from the copied snapshot in the new region to recover EC2 + EBS.

🧪 19. Scenario: You need to back up critical EBS volumes daily and retain backups for 30 days. How would you do it efficiently?
Answer:

Use Amazon Data Lifecycle Manager (DLM):

Create a snapshot lifecycle policy.

Set backup frequency to daily.

Configure retention to 30 snapshots.

Tag volumes with Backup=true, then set the policy to target those.

This approach is scalable, automated, and cost-effective.

⚠️ 20. What are some best practices for EBS disaster recovery?
Answer:

Enable CloudWatch alarms on EBS health/performance.

Tag all volumes for easy filtering and management.

Keep critical volumes encrypted and keys backed up in KMS.

Regularly test your recovery procedures from snapshots in a test environment.

Document and version control your DR scripts and procedures.



🖥️ 21. CLI: How do you create, attach, and mount an EBS volume using AWS CLI?
Answer: Here’s a step-by-step example for Linux:

Step 1: Create a volume

bash
Copy
Edit
aws ec2 create-volume \
  --availability-zone us-east-1a \
  --size 8 \
  --volume-type gp3
Step 2: Attach volume to EC2 instance

bash
Copy
Edit
aws ec2 attach-volume \
  --volume-id vol-xxxxxxxx \
  --instance-id i-xxxxxxxx \
  --device /dev/xvdf
Step 3: On the EC2 instance (SSH in), format and mount

bash
Copy
Edit
sudo mkfs -t ext4 /dev/xvdf
sudo mkdir /data
sudo mount /dev/xvdf /data
Step 4: Add to /etc/fstab for persistence

bash
Copy
Edit
echo '/dev/xvdf /data ext4 defaults,nofail 0 2' | sudo tee -a /etc/fstab
🧵 22. Scenario: Your app runs on EC2 with EBS. During traffic spikes, latency increases. What do you do?
Answer:

Check EBS CloudWatch metrics:

High VolumeQueueLength → volume is overwhelmed.

High BurstBalance consumption (on gp2) → consider upgrading to gp3.

Options to fix:

Move to gp3 and increase IOPS/throughput.

Switch to io1/io2 for consistent high IOPS.

Use multiple EBS volumes in RAID 0 for better performance.

Enable EBS-optimized instance type.

📊 23. How do you benchmark EBS performance on an EC2 instance?
Answer: Use tools like fio or dd:

Using fio:

bash
Copy
Edit
sudo yum install -y fio
fio --name=test --size=1G --filename=/data/testfile \
--bs=4k --rw=randwrite --ioengine=libaio --iodepth=32 --numjobs=4
Using dd:

bash
Copy
Edit
dd if=/dev/zero of=/data/testfile bs=1M count=1024 oflag=dsync
Then monitor:

IOPS

Throughput (MB/s)

Latency (ms)

🔄 24. CLI: How do you take and restore an EBS snapshot?
Take a snapshot:

bash
Copy
Edit
aws ec2 create-snapshot \
  --volume-id vol-xxxxxxxx \
  --description "Daily backup"
Restore from snapshot:

bash
Copy
Edit
aws ec2 create-volume \
  --snapshot-id snap-xxxxxxxx \
  --availability-zone us-east-1a \
  --volume-type gp3
Attach and mount as usual.

🧪 25. Scenario: You need to replicate an EC2 instance (with EBS) in another region. How?
Answer:

Take a snapshot of the EBS volume.

Use copy-snapshot to replicate it to the target region.

In the target region:

Create a volume from the snapshot.

Launch a new EC2 instance.

Attach the volume and mount it.



🧾 EBS + EC2 Cheat Sheet
🚀 EC2 Basics:
Launch EC2 with an EBS volume (default root).

Stop/Start retains EBS data; terminate does not unless DeleteOnTermination=true.

📦 EBS Volume Types:

Type	Best For	Max IOPS	Notes
gp3	General purpose SSD	16,000	Set IOPS & throughput
io1/io2	High-performance DBs	64,000	Supports Multi-Attach
st1	Big data, streaming logs	500	HDD, good throughput
sc1	Infrequent access, archives	250	Cheapest HDD
🔧 Key CLI Commands:
bash
Copy
Edit
aws ec2 create-volume ...
aws ec2 attach-volume ...
aws ec2 create-snapshot ...
aws ec2 copy-snapshot ...
aws ec2 describe-volumes
aws ec2 delete-volume ...
📊 Monitoring:
Use CloudWatch for:

VolumeQueueLength

BurstBalance (gp2)

VolumeReadOps, VolumeWriteOps

🎤 Mock Interview Q&A
Q: How would you increase performance on a database that’s hitting EBS IOPS limits?
A:

Move to io2 or gp3 with provisioned IOPS.

Consider RAID 0 striping across multiple volumes.

Ensure EBS-optimized EC2 instance.

Monitor and tweak with CloudWatch.

Q: What happens to data on an EBS volume when the instance is stopped?
A: Nothing is lost. Data persists unless the volume is explicitly deleted or flagged DeleteOnTermination.

Q: What is EBS Multi-Attach? When would you use it?
A: It allows io1/io2 volumes to be attached to multiple EC2s in the same AZ. Used for clustered applications like Oracle RAC or shared file systems.

🧠 Mini Practice Test (5 Questions)
Q1: Which EBS volume type is best for frequent, small read/write operations at scale?

A) sc1

B) io2

C) st1

D) gp2
✅ Answer: B

Q2: What is the maximum size of a single EBS volume?

A) 1 TiB

B) 16 TiB

C) 64 TiB

D) 100 TiB
✅ Answer: B

Q3: You have an EC2 instance with gp2 EBS. IOPS are spiking and latency is high. What do you do?

A) Increase instance type

B) Switch to gp3 and provision IOPS

C) Create a snapshot

D) Add swap memory
✅ Answer: B

Q4: Which command copies a snapshot to another region?

bash
Copy
Edit
aws ec2 _____
A) move-snapshot

B) replicate-snapshot

C) copy-snapshot

D) export-snapshot
✅ Answer: C

Q5: What happens if you terminate an EC2 instance with DeleteOnTermination=false on the root EBS?

A) Volume is deleted

B) Volume is retained
✅ Answer: B
