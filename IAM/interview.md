Here are well-structured, **interview-ready answers** for your AWS IAM-related questions:

---

### ✅ **1. How do you control access to AWS services and resources using IAM?**

Access is controlled using:

* **IAM policies** (JSON-based): define permissions
* Attach policies to **users, groups, or roles**
* Use **least privilege principle** to give only necessary permissions

---

### ✅ **2. Difference: User vs Group vs Role vs Policy**

| Component  | Description                                      |
| ---------- | ------------------------------------------------ |
| **User**   | Entity with credentials for an individual        |
| **Group**  | Collection of users sharing the same permissions |
| **Role**   | Temporary access, assumed by users/services      |
| **Policy** | JSON document defining allowed/denied actions    |

---

### ✅ **3. IAM User Best Practices**

* Enforce **MFA**
* No root account use (except emergencies)
* Assign permissions using **groups**
* Apply **least privilege**
* Enable **CloudTrail** for auditing

---

### ✅ **4. Enable MFA for IAM Users**

1. Go to IAM > Users > Select user
2. Click **"Security credentials"**
3. Click **"Manage MFA"**
4. Choose **Virtual MFA device** (e.g., Google Authenticator)
5. Scan QR code and verify

---

### ✅ **5. Setting Up Cross-Account Access**

* Create **IAM Role** in **Account A**
* Set **Account B** as trusted entity
* Attach required policy to role
* In Account B, users assume role via `sts:AssumeRole`

---

### ✅ **6. What is AWS Identity Federation?**

* Allows external identity providers (e.g., **AD, Google, SAML, Cognito**) to access AWS
* Users get **temporary STS tokens** via IAM roles
* No need to create IAM users for each external user

---

### ✅ **7. IAM Policy vs Resource-based Policy**

| Type               | Scope                           | Example                             |
| ------------------ | ------------------------------- | ----------------------------------- |
| **IAM Policy**     | Attached to **user/role/group** | S3 access policy attached to a role |
| **Resource-based** | Attached to **resource itself** | S3 bucket policy, Lambda policy     |

---

### ✅ **8. Rotate Access Keys for IAM Users**

Steps:

1. Create a **second key**
2. Update apps to use the **new key**
3. Deactivate and then delete the **old key**

**Why it's important**:

* Limits impact of key exposure
* Complies with security audits

---

### ✅ **9. What is AWS Cognito?**

* Manages **user authentication and access** for web/mobile apps
* Provides **user pools** (directory) and **identity pools** (temporary AWS access)
* Integrates with IAM for **fine-grained permissions**

---

### ✅ **10. What is AWS STS (Security Token Service)?**

* Issues **temporary credentials** for IAM roles
* Credentials expire automatically (short-lived)
* Used in:

  * **Cross-account access**
  * **Federated access**
  * **Apps assuming roles securely**

---

### ✅ **11. IAM Role Policy Attachment Limits**

* Max **10 managed policies**
* Plus **1 inline policy** (if needed)
* Try to consolidate permissions to avoid hitting the limit

---

### ✅ **12. What is a Trusted Entity?**

* Entity (user/service/account) allowed to **assume a role**
* Defined in the **trust policy** of an IAM role
  Example:

```json
"Principal": {
  "AWS": "arn:aws:iam::111122223333:root"
}
```

---

### ✅ **13. Complex IAM Scenario Example**

**Problem**: A developer needed access to an S3 bucket in another AWS account.

**Solution**:

* Created a **role with S3 access** in target account
* Set the **source account as trusted entity**
* Provided an **assume-role script** using AWS CLI
* Verified access via CloudTrail

---

### ✅ **14. Secure Access Key Rotation Strategy**

* Enforce **key rotation policy** (via IAM or automation)
* Use **AWS Config** to detect unused keys
* Implement script/automation to:

  * Generate new keys
  * Test new keys
  * Disable & delete old ones
* Integrate with **Secrets Manager** for app key management

---

### ✅ **15. Seamless IAM Migration for On-Prem Apps**

* Use **AWS SSO** or **Cognito** with identity federation
* Integrate with **Active Directory** via AWS Directory Service
* Map existing user roles to IAM roles via **SAML or OIDC**

---

### ✅ **16. IAM Best Practices with AWS Organizations**

* Use **Service Control Policies (SCPs)** to enforce org-wide rules
* Create **OU-based** structure (e.g., prod/dev)
* Centralize IAM user management via **IAM Identity Center (SSO)**
* Enable **CloudTrail + GuardDuty** org-wide

---

Let me know if you want these grouped into a **cheat sheet**, **mock interview**, or **Flashcards** for fast revision.
