Great, Vaishali! Here's a comprehensive list of **40 AWS CloudFront interview questions with answers** followed by **40+ real-time scenario-based questions** to help you prepare thoroughly.

---

## ✅ **40 AWS CloudFront Interview Questions with Answers**

### 🔹 Basic Level (1–15)

1. **What is Amazon CloudFront?**
   CloudFront is a content delivery network (CDN) service that securely delivers data, videos, applications, and APIs to users globally with low latency.

2. **What are edge locations in CloudFront?**
   These are data centers used to cache content closer to the users to reduce latency.

3. **What is an origin in CloudFront?**
   The origin is the source of the files that CloudFront will distribute, such as an S3 bucket or an EC2 instance.

4. **What is a CloudFront distribution?**
   A distribution tells CloudFront where you want content to be delivered from and how to track and manage content delivery.

5. **What are the types of CloudFront distributions?**

   * Web distribution (for websites, HTTP/HTTPS content)
   * RTMP distribution (deprecated; used for streaming media)

6. **What are cache behaviors in CloudFront?**
   They define how CloudFront responds to requests for content, including caching rules, methods allowed, and TTL settings.

7. **Can you restrict content delivery in CloudFront?**
   Yes, using signed URLs, signed cookies, and geo-restriction.

8. **What is TTL in CloudFront?**
   Time-To-Live defines how long content is cached at edge locations before CloudFront checks for updates.

9. **What is invalidation in CloudFront?**
   It forces CloudFront to remove cached files from edge locations before they expire.

10. **Can CloudFront serve dynamic content?**
    Yes, CloudFront can serve both static and dynamic content using features like Lambda\@Edge.

11. **What protocols does CloudFront support?**
    HTTP and HTTPS.

12. **What is Lambda\@Edge?**
    It's a feature of CloudFront that allows you to run functions to customize content delivery at CloudFront edge locations.

13. **How does CloudFront integrate with S3?**
    CloudFront can use S3 as an origin and distribute static content stored in S3 with better performance.

14. **What is field-level encryption in CloudFront?**
    It protects sensitive data (like PII) by encrypting specific data fields in an HTTP POST request.

15. **How do you enable HTTPS in CloudFront?**
    By using ACM (AWS Certificate Manager) for SSL/TLS certificates and configuring the distribution settings.

---

### 🔹 Intermediate Level (16–30)

16. **What is origin failover in CloudFront?**
    It's a feature that lets you specify a primary and secondary origin to improve availability.

17. **How does CloudFront handle DDoS attacks?**
    It integrates with AWS Shield Standard for automatic DDoS protection.

18. **How do signed URLs and signed cookies differ?**
    Signed URLs are used for individual files; signed cookies allow access to multiple restricted files.

19. **How does CloudFront work with Route 53?**
    Route 53 can be used to point your domain to a CloudFront distribution.

20. **How do you configure cache policies in CloudFront?**
    Cache policies define how CloudFront caches requests, including headers, query strings, and cookies.

21. **What are origin request policies?**
    These specify what information CloudFront includes in requests to the origin.

22. **Can CloudFront log user access?**
    Yes, by enabling standard or real-time access logs to S3 buckets or using CloudWatch.

23. **What are viewer request/response and origin request/response in Lambda\@Edge?**
    These are lifecycle events where custom code can run to modify requests/responses at edge locations.

24. **What is geo-restriction in CloudFront?**
    It restricts access to content based on geographic location.

25. **How does CloudFront handle content versioning?**
    By changing the object name (e.g., appending a version ID to the file name).

26. **Can CloudFront compress content?**
    Yes, it can automatically compress files using Gzip or Brotli.

27. **What is the default TTL in CloudFront?**
    By default, 24 hours if no Cache-Control or Expires header is set.

28. **What types of origins can CloudFront use?**
    S3 buckets, EC2 instances, ELB, API Gateway, or any HTTP-based server.

29. **What is the maximum file size CloudFront can deliver?**
    Up to 30 GB per file.

30. **How do you secure content delivery in CloudFront?**
    Using SSL, signed URLs, signed cookies, field-level encryption, and WAF.

---

### 🔹 Advanced Level (31–40)

31. **What are custom error responses in CloudFront?**
    You can return a custom error page and HTTP status code for specific error codes.

32. **How does CloudFront support multi-origin content?**
    Through multiple cache behaviors mapped to different origins.

33. **What is the difference between CloudFront and S3 website hosting?**
    S3 website hosting provides basic static hosting, while CloudFront adds caching, SSL, geo-restriction, and performance benefits.

34. **How does CloudFront interact with AWS WAF?**
    You can associate WAF web ACLs with CloudFront to filter HTTP/HTTPS requests.

35. **How can CloudFront reduce load on your origin server?**
    By caching content at edge locations and reducing the number of direct requests to the origin.

36. **What is price class in CloudFront?**
    It controls the set of edge locations used based on cost preference (e.g., Price Class 100, 200, All).

37. **What happens if an origin is not available?**
    CloudFront returns a 504 error or can be configured with failover to another origin.

38. **How to manage cache busting in CloudFront?**
    Use versioned URLs or invalidate specific paths.

39. **What is the difference between caching and content delivery in CloudFront?**
    Caching temporarily stores content for quicker delivery; delivery is the actual process of serving content globally.

40. **Can you use CloudFront to deliver private content?**
    Yes, using signed URLs, signed cookies, and origin access identity (for S3 origins).

you'd like, I can prepare this list in a PDF or spreadsheet format for download or revision. Let me know!

