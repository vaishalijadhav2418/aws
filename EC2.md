1.  Q: What is Amazon EC2?   
    A:  Amazon EC2 is a web service that provides resizable compute capacity in the cloud, allowing users to run virtual servers known as instances.

2.  Q: What is an EC2 instance?   
    A:  An EC2 instance is a virtual server in Amazon’s Elastic Compute Cloud (EC2) for running applications on the AWS infrastructure.

3.  Q: What are EC2 instance types?   
    A:  Instance types are combinations of CPU, memory, storage, and networking capacity designed to suit different use cases (e.g., General Purpose, Compute Optimized, Memory Optimized).

4.  Q: What is an AMI?   
    A:  AMI (Amazon Machine Image) is a pre-configured template that contains the software configuration (OS, application server, applications) to launch an instance.

5.  Q: What is the difference between EBS and instance store?   
    A:  EBS (Elastic Block Store) is persistent storage, while instance store is temporary and data is lost when the instance stops or terminates.

6.  Q: What are EC2 pricing options?   
    A:  On-Demand, Reserved, Spot, and Savings Plans.

7.  Q: What is a key pair in EC2?   
    A:  A key pair is used to securely access EC2 instances. It consists of a public key (stored by AWS) and a private key (stored by the user).

8.  Q: What is user data in EC2?   
    A:  User data is a script that is run automatically when an EC2 instance starts, often used for bootstrapping.

9.  Q: What is the default root volume size for Amazon Linux 2 AMI?   
    A:  8 GB.

10.  Q: Can we stop a Spot instance?   
     A:  No, Spot instances can be terminated by AWS when the capacity is no longer available or price exceeds the bid.

11.  Q: What is EC2 Auto Scaling?   
     A:  Auto Scaling automatically adjusts the number of EC2 instances in a group based on demand.

12.  Q: What is a Security Group?   
     A:  A virtual firewall that controls inbound and outbound traffic for EC2 instances.

13.  Q: What is the use of Elastic IP?   
     A:  It is a static, public IPv4 address designed for dynamic cloud computing, allowing consistent access to an instance.

14.  Q: What is a Placement Group?   
     A:  A placement strategy that determines how instances are placed on underlying hardware for better performance.

15.  Q: Can you attach multiple EBS volumes to one EC2 instance?   
     A:  Yes.

16.  Q: What is the maximum number of security groups per network interface?   
     A:  5 by default (can be increased).

17.  Q: What happens when you reboot an EC2 instance?   
     A:  It retains its instance ID and attached volumes. The reboot is like restarting a physical machine.

18.  Q: What happens when an EC2 instance is terminated?   
     A:  The instance is permanently deleted and associated ephemeral storage is lost unless EBS volumes are preserved.

19.  Q: What is EC2 Hibernate?   
     A:  Hibernate saves the in-memory RAM to EBS and resumes the instance to its previous state on restart.

20.  Q: What are Dedicated Hosts?   
     A:  Physical servers fully dedicated to your use to meet compliance or licensing requirements.

21.  Q: What is an Elastic Load Balancer (ELB)?   
     A:  It automatically distributes incoming application traffic across multiple EC2 instances.

22.  Q: Can we resize an EC2 instance?   
     A:  Yes, by stopping the instance and changing its type.

23.  Q: What are instance metadata and user data used for?   
     A:  Instance metadata provides information about the instance, and user data is used to automate configuration tasks.

24.  Q: What is the difference between Public IP and Elastic IP?   
     A:  Public IP is dynamically assigned and lost when the instance stops; Elastic IP is static.

25.  Q: What is the default EC2 instance limit per region?   
     A:  20 On-Demand instances per region by default (can be increased).

26.  Q: What are tags in EC2?   
     A:  Key-value pairs assigned to instances for categorization and management.

27.  Q: Can we assign multiple IPs to an EC2 instance?   
     A:  Yes, by assigning secondary private IP addresses to the network interface.

28.  Q: What is the difference between stopping and terminating an EC2 instance?   
     A:  Stopping keeps the instance and its root volume; terminating deletes them (unless configured otherwise).

29.  Q: Can an EC2 instance have multiple network interfaces?   
     A:  Yes, using Elastic Network Interfaces (ENIs).

30.  Q: What is EC2 Instance Store-backed and EBS-backed instance?   
     A:  Store-backed uses temporary storage that is deleted on stop/terminate; EBS-backed uses persistent storage.
