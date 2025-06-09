Here are **interview-focused answers** for all your Amazon Route 53 questions:

---

### ✅ 1. **What are Top-Level Domains (TLDs) and Second-Level Domains (SLDs)?**

* **TLD**: The last segment of a domain name (e.g., `.com`, `.org`, `.in`)
* **SLD**: The part before the TLD (e.g., `example` in `example.com`)
* In Route 53, you register a **TLD/SLD combo** like `vaishali.tech` and manage DNS for subdomains (e.g., `app.vaishali.tech`)

---

### ✅ 2. **Primary Services Provided by Amazon Route 53**

* **Domain Registration**
* **DNS Service** (DNS hosting & routing)
* **Health Checks** (for routing decisions)
* **Traffic Flow** (advanced routing control)

---

### ✅ 3. **Registering a Domain with Route 53**

1. Go to Route 53 → **Registered Domains**
2. Search & choose available domain
3. Provide contact details
4. Configure optional DNS records (hosted zone auto-created)
5. Complete payment and wait for registration to complete

---

### ✅ 4. **Domain Registration vs DNS Hosting**

| Feature     | Domain Registration | DNS Hosting                         |
| ----------- | ------------------- | ----------------------------------- |
| Role        | Buy & own a domain  | Manage DNS records (A, CNAME, etc.) |
| Example     | `example.com`       | Pointing to `192.0.2.1`             |
| In Route 53 | Registered Domains  | Hosted Zones                        |

---

### ✅ 5. **Migrating a Domain to Route 53**

1. Unlock the domain at your current registrar
2. Get an **authorization code**
3. In Route 53 → **Transfer Domain**
4. Enter domain + auth code
5. Verify ownership
6. Confirm transfer via email

---

### ✅ 6. **Routing Policies in Route 53**

* **Simple**: Single value response (default)
* **Weighted**: Split traffic based on % weights
* **Latency-Based**: Direct to region with lowest latency
* **Geolocation**: Route based on user location
* **Failover**: Route to healthy resource using health checks
* **Multi-Value Answer**: Returns multiple healthy IPs (basic load balancing)

---

### ✅ 7. **Purpose of Weighted Routing Policy**

* Split traffic for:

  * **Blue-Green deployments**
  * **A/B Testing**
  * Gradual migration
* Example: 70% traffic to version A, 30% to version B

---

### ✅ 8. **Latency-Based Routing Policy**

* Directs users to the region with **lowest latency**
* Based on **AWS edge location** measurements
* Ideal for **global apps** needing **fast response**

---

### ✅ 9. **Health Checks in Route 53**

* Monitor resource availability (HTTP, TCP, HTTPS)
* Can be associated with:

  * Route 53 records (for failover)
  * CloudWatch alarms (trigger actions)
* Example: Mark instance as “unhealthy” if HTTP fails 3 times

---

### ✅ 10. **Failover Routing Policy + Health Checks**

* Create 2 records:

  * **Primary** (active)
  * **Secondary** (standby)
* Attach health check to Primary
* If Primary fails → Route 53 sends traffic to Secondary

---

### ✅ 11. **Best Practices: Route 53 for High Availability & Low Latency**

* Distribute records across **multiple regions/AZs**
* Use **Latency-Based or Geolocation Routing**
* Configure **health checks + failover**
* Combine with **CloudFront, ELB**, and **WAF**
* Automate changes using **Route 53 Traffic Flow**

---

### ✅ 12. **Use Cases for Route 53**

* **Global load balancing**: via latency/geolocation
* **Failover/DR**: auto switch on failure using health checks
* **Hybrid DNS**: AWS + on-prem DNS integration
* **Routing to regional services**: RDS replicas, EC2, ALBs

---

### ✅ 13. **Using Route 53 with ELB**

* Create an **Alias record** pointing to ELB DNS
* Alias record allows:

  * Integration with health checks
  * No extra cost (unlike CNAME)
* Ensures **scalable, fault-tolerant** endpoint

---

### ✅ 14. **DNS Record Types in Route 53**

| Record Type | Description                                       |
| ----------- | ------------------------------------------------- |
| **A**       | Maps name to IPv4 address                         |
| **AAAA**    | Maps name to IPv6 address                         |
| **CNAME**   | Alias of another domain name                      |
| **Alias**   | Like CNAME but works with AWS resources (ELB, S3) |
| **MX**      | Mail exchange server records                      |
| **NS**      | Delegates subdomain to name servers               |
| **SOA**     | Info about domain's zone (serial, refresh, retry) |
| **TXT**     | Text-based records (SPF, DKIM, verification)      |
| **SRV**     | Specifies host/port for services (like VoIP)      |

---

Would you like a visual mind map or scenario-based practice questions next?
