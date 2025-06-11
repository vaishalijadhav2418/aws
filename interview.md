1. What is a Port Number?
Answer:
A port number is a 16-bit numeric value (0–65535) used to identify specific processes or services on a device within a network. It helps in routing network traffic to the correct application.
| Range       | Use                          |
| ----------- | ---------------------------- |
| 0–1023      | Well-known ports (HTTP, SSH) |
| 1024–49151  | Registered ports             |
| 49152–65535 | Dynamic/private ports        |

2. What are the 7 Layers of the OSI Model?
   
Answer:
1. Physical – Transmits raw bits over the physical medium
2. Data Link – Error detection and MAC addressing
3. Network – Routing and IP addressing
4. Transport – End-to-end communication (TCP/UDP)
5. Session – Establishes and manages sessions
6. Presentation – Data formatting and encryption
7. Application – End-user interaction (HTTP, FTP)

________________________________________________________________________
3. What are the 4 Layers of the TCP/IP Model?
4. 
Answer:
1. Network Interface – Maps to OSI's Physical + Data Link
2. Internet – Maps to OSI's Network layer (IP, ICMP)
3. Transport – TCP/UDP (same as OSI Transport)
4. Application – Combines OSI’s Session, Presentation, Application

_____________________________________________________________
4. What is SDLC?
Answer:
The Software Development Life Cycle (SDLC) is a structured approach to software development. It consists of phases like planning, analysis, design, implementation, testing, deployment, and maintenance.

5. Common SDLC Models:
Waterfall: Linear and sequential
Agile: Iterative and incremental
Spiral: Risk-driven model combining Waterfall + Prototyping
V-Model: Verification and validation at each stage
DevOps Model: Continuous integration, testing, and delivery

6. What is DevOps?
Answer:
DevOps is a set of practices that combines software development (Dev) and IT operations (Ops) to shorten the development lifecycle and provide continuous delivery.

7. What is the difference between Monolithic and Microservices architecture?
 Answer:
   Monolithic is a single unit; Microservices split into independent services for flexibility and scalability.

Great questions, Vaishali! These are fundamental concepts every AWS DevOps Engineer should be clear about. Here are the answers in simple, interview-friendly language:

---

### ✅ **1. What is Compute Service?**

**Answer:**
Compute services provide the processing power required to run applications and workloads. In the cloud, these services help you **launch virtual machines, run containers, or execute functions** without owning physical hardware.

**Examples in AWS:**

* **Amazon EC2** – Virtual servers in the cloud
* **AWS Lambda** – Run code without servers (serverless)
* **Amazon ECS / EKS** – Run and manage containers

---

### ✅ **2. Why choose AWS over GCP and Azure?**

**Answer:**

* **Market Leader:** AWS is the most mature and widely adopted cloud platform.
* **More Services:** Offers 200+ fully featured services, more than GCP and Azure.
* **Global Reach:** Largest number of regions and availability zones worldwide.
* **Strong Ecosystem:** Rich documentation, certifications, community support.
* **Innovation & Reliability:** Regularly introduces new services with a strong SLA (uptime).

✅ Example: Many top companies (Netflix, Airbnb, NASA) prefer AWS for its flexibility and scalability.

---

### ✅ **3. What is AWS (Amazon Web Services)?**

**Answer:**
AWS is a **cloud computing platform** by Amazon that offers on-demand services such as:

* **Compute (EC2, Lambda)**
* **Storage (S3, EBS)**
* **Database (RDS, DynamoDB)**
* **Networking (VPC, Route 53)**
* **Security (IAM, KMS)**
  ...and many more, to help businesses build and scale applications without managing physical infrastructure.

---

### ✅ **4. What is Virtualization or Virtual Services?**

**Answer:**
Virtual services simulate physical hardware (like servers, storage, networks) in software.

**Examples:**

* Virtual Machines (VMs) in EC2
* Virtual Storage (EBS)
* Virtual Networks (VPC)

Virtualization allows **multiple services to run on the same hardware**, reducing costs and increasing flexibility.

---

### ✅ **5. What is a Service (in cloud context)?**

**Answer:**
A **service** in the cloud is a managed feature or tool provided by a cloud provider to perform a specific function.

**Types of AWS Services:**

* **Compute** – EC2, Lambda
* **Storage** – S3, EBS
* **Database** – RDS, DynamoDB
* **Security** – IAM, WAF
* **DevOps Tools** – CodePipeline, CloudFormation

---

### ✅ **6. What is Cloud Computing?**

**Answer:**
Cloud computing is the **delivery of computing services (like servers, storage, databases, networking, and software)** over the Internet (“the cloud”).

Instead of owning hardware, you **rent it from a cloud provider** (e.g., AWS, Azure, GCP).

---

### ✅ **7. Why use Cloud?**

**Answer:**

* **Cost-effective:** Pay-as-you-go pricing; no upfront hardware costs
* **Scalable:** Easily scale up/down based on traffic
* **Flexible:** Access from anywhere, anytime
* **Reliable:** High availability with multiple data centers
* **Secure:** Strong built-in security features and compliance
* **Fast Deployment:** Quickly launch apps and infrastructure

