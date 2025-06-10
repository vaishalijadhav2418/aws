Great, Vaishali! Here's a comprehensive list of **40 AWS CloudWatch interview questions with answers**, followed by **40 real-time scenario-based questions** (Q41–Q80) to help you prepare effectively.

---

### ✅ **Part 1: AWS CloudWatch – Interview Questions with Answers (Q1–Q40)**

#### **Basic Questions**

1. **What is Amazon CloudWatch?**
   *Amazon CloudWatch is a monitoring and observability service that provides data and actionable insights to monitor applications, respond to system-wide performance changes, and optimize resource utilization.*

2. **What types of data can CloudWatch collect?**
   *Metrics, logs, events, and traces.*

3. **What is a CloudWatch Metric?**
   *A metric is a time-ordered set of data points that are published to CloudWatch.*

4. **What is the difference between default and custom metrics?**
   *Default metrics are provided by AWS services automatically; custom metrics are those you publish using the AWS CLI or SDK.*

5. **What is CloudWatch Logs?**
   *A feature that allows you to collect and store logs from AWS resources, applications, and services.*

6. **What is the retention period for CloudWatch Logs?**
   *It can be set from 1 day to indefinitely.*

7. **What is a CloudWatch Alarm?**
   *An alarm watches a single metric or a math expression and performs actions based on the value of the metric.*

8. **What are the supported actions in CloudWatch Alarms?**
   *Send notifications (SNS), perform EC2 actions (stop, terminate, reboot, recover), or trigger Auto Scaling.*

9. **What is the difference between Alarm state: OK, ALARM, and INSUFFICIENT\_DATA?**
   *OK: metric is within threshold, ALARM: metric exceeds threshold, INSUFFICIENT\_DATA: not enough data to determine state.*

10. **What is a CloudWatch Dashboard?**
    *A customizable home page in the CloudWatch console to monitor metrics and alarms in one view.*

#### **Intermediate Questions**

11. **How do you publish custom metrics to CloudWatch?**
    *Using AWS CLI (`put-metric-data`) or SDKs.*

12. **Can CloudWatch monitor on-premises servers?**
    *Yes, using the CloudWatch Agent installed on those servers.*

13. **What is the CloudWatch Agent?**
    *A tool that collects system-level metrics and logs from EC2 instances or on-prem servers.*

14. **How does CloudWatch integrate with Auto Scaling?**
    *It can trigger Auto Scaling policies based on alarms tied to metrics like CPU usage.*

15. **What is the frequency of metric collection for EC2?**
    *Every 5 minutes by default; 1-minute granularity with detailed monitoring.*

16. **How does CloudWatch Logs work with Lambda?**
    *Lambda functions automatically send their logs to CloudWatch Logs.*

17. **How do you control access to CloudWatch?**
    *Using IAM policies and roles.*

18. **What is a metric filter in CloudWatch Logs?**
    *It extracts metric data from log events for monitoring and alarming.*

19. **Can CloudWatch trigger AWS Lambda functions?**
    *Yes, using CloudWatch Events (EventBridge).*

20. **What is a Contributor Insights rule in CloudWatch?**
    *A rule that analyzes log data to determine top contributors to system performance.*

#### **Advanced Questions**

21. **How do you monitor memory usage of an EC2 instance?**
    *Install and configure the CloudWatch Agent to collect memory metrics.*

22. **Can you create custom namespaces for CloudWatch metrics?**
    *Yes, custom metrics can be placed into your own namespaces.*

23. **How does anomaly detection work in CloudWatch?**
    *It applies machine learning to create a model for metric behavior and detects outliers.*

24. **What is the use of composite alarms?**
    *They combine multiple alarms using logical operators (AND, OR) to reduce alarm noise.*

25. **How does CloudWatch Logs Insights help?**
    *It provides a query language to analyze log data interactively.*

26. **What is the maximum number of dashboards allowed?**
    *Up to 500 dashboards per AWS account per Region.*

27. **How do you monitor application logs with CloudWatch?**
    *Install CloudWatch Agent or use AWS SDK to send logs directly to CloudWatch Logs.*

28. **How do you archive old logs in CloudWatch Logs?**
    *Use Log Groups' retention policy or export logs to Amazon S3.*

29. **How do you reduce CloudWatch Logs cost?**
    *Set log retention policies, compress/export logs to S3, and limit logging verbosity.*

30. **Can CloudWatch trigger cross-account actions?**
    *Yes, with appropriate IAM roles and permissions.*

#### **Comparison and Integration Questions**

31. **CloudWatch vs CloudTrail – What’s the difference?**
    *CloudWatch monitors performance and logs; CloudTrail records API activity.*

32. **CloudWatch vs X-Ray – What’s the difference?**
    *CloudWatch is for monitoring/logs; X-Ray is for distributed tracing.*

33. **Can you use CloudWatch with ECS and EKS?**
    *Yes, both services emit metrics and logs that can be monitored.*

34. **How does CloudWatch integrate with EventBridge?**
    *Events from AWS services can be routed to targets like Lambda, Step Functions, etc.*

35. **Can CloudWatch send logs to a third-party application?**
    *Yes, using subscription filters and destinations (like Kinesis).*

36. **What is the limit on log data ingestion per account?**
    *Default is 5 TB per Region per account per month (can be increased).*

37. **How do you tag CloudWatch resources?**
    *Tags can be added using the AWS CLI, SDKs, or Console.*

38. **How does CloudWatch help in troubleshooting latency?**
    *By analyzing request logs, custom metrics, and response time metrics.*

39. **What are insights rules in CloudWatch Logs?**
    *Pre-built dashboards for log analysis (e.g., VPC Flow Logs, Lambda, etc.)*

40. **How can CloudWatch help in DevOps automation?**
    *Through alarms, event triggers, and integration with CI/CD tools.*


### ✅ Part 2: AWS CloudWatch – Real-Time/Scenario-Based Questions with Answers (Q41–Q80)

#### Q41. Alert when EC2 CPU usage >85% for 3 consecutive 5-min intervals?

* Create a CloudWatch Alarm:

  * Metric: EC2 -> CPUUtilization
  * Threshold: Greater than 85
  * Period: 300 seconds (5 min)
  * Evaluation Periods: 3
  * Action: Send notification via SNS

#### Q42. EC2 Memory usage not visible in CloudWatch?

* Install and configure the CloudWatch Agent
* Add memory metrics to `amazon-cloudwatch-agent.json`
* Restart the agent

#### Q43. Logs not appearing in CloudWatch?

* Verify IAM permissions
* Check agent configuration
* Ensure logs are written to correct file path
* Restart agent or application

#### Q44. Lambda not triggered by CloudWatch Event?

* Check EventBridge rule and target config
* Validate Lambda permissions
* Review CloudWatch Logs for rule failures

#### Q45. Monitor disk usage on Windows EC2?

* Install CloudWatch Agent
* Include disk metrics in the config JSON
* Restart agent

#### Q46. Reduce CloudWatch Logs cost?

* Set retention period
* Use filters to reduce noise
* Export to S3 and archive
* Enable compression

#### Q47. Too many false alarms from bursty CPU usage?

* Use longer evaluation periods
* Use anomaly detection
* Use percentile metrics (e.g., p95)

#### Q48. View multiple metrics in one place?

* Create a CloudWatch Dashboard
* Add widgets for each metric

#### Q49. Metric shows INSUFFICIENT\_DATA?

* Metric not being pushed
* Incorrect namespace or dimension
* Delay in data ingestion

#### Q50. Auto-reboot EC2 if unresponsive?

* Create a CloudWatch Alarm
* Action: EC2 -> Reboot instance

#### Q51. Monitor top IPs from logs?

* Use CloudWatch Logs Insights:

  * `fields @ip | stats count() by @ip | sort by count desc`

#### Q52. Alert only if CPU & Memory are high?

* Use composite alarm combining both conditions with AND logic

#### Q53. Single alert for multiple conditions?

* Use a composite alarm

#### Q54. Analyze log patterns for past 24 hours?

* Use CloudWatch Logs Insights with custom query and time range

#### Q55. Store logs in S3 at midnight?

* Use subscription filter to send logs to Lambda/Kinesis
* Lambda schedules S3 upload via EventBridge rule

#### Q56. Push Docker container metrics?

* Use CloudWatch Agent with Docker
* Mount Docker socket and collect container-level metrics

#### Q57. Enable CloudWatch in Auto Scaling?

* Ensure launch template includes detailed monitoring
* IAM role with CloudWatch access

#### Q58. React to failed login attempts?

* Create metric filter from logs
* Create alarm for high count
* Trigger SNS or Lambda

#### Q59. Export logs for compliance?

* Use CloudWatch Logs Export to S3
* Schedule daily with EventBridge and Lambda

#### Q60. Read-only access to dashboards?

* Attach IAM policy with `cloudwatch:Describe*` permissions

---

#### Q61. Alarm not triggering SNS email?

* Check alarm state
* Confirm SNS topic subscription
* Verify email subscription is confirmed

#### Q62. Visualize EKS metrics?

* Enable Container Insights
* Use CloudWatch Dashboards

#### Q63. Centralized monitoring across accounts?

* Use CloudWatch cross-account dashboards
* Set up cross-account roles and sharing

#### Q64. CloudWatch in CI/CD pipeline?

* Monitor build logs
* Trigger alarms for failures
* Use events for automated rollback

#### Q65. Monitor API Gateway errors/latency?

* Use default metrics: 4XXError, 5XXError, Latency
* Set alarms

#### Q66. Custom metrics from Python app?

* Use `boto3` to call `put_metric_data`

#### Q67. Large log group?

* Set retention
* Archive to S3
* Rotate logs regularly

#### Q68. Secure logs with sensitive data?

* Use KMS encryption
* Restrict access via IAM

#### Q69. Monitor 404/500 errors?

* Use metric filters on log patterns
* Create alarms based on thresholds

#### Q70. Alert if no logs from Lambda for 15 mins?

* Create metric filter counting log entries
* Alarm on `Missing Data` state

#### Q71. Monitor billing anomalies?

* Enable billing metrics in CloudWatch
* Set alarm on `EstimatedCharges`

#### Q72. Monitor third-party on-prem app?

* Use CloudWatch Agent
* Send metrics/logs using `put-metric-data` or Fluent Bit

#### Q73. DevOps dashboard for 100 servers?

* Install agent on each server
* Use custom namespace
* Create unified dashboard

#### Q74. Monitor behavior changes over time?

* Use anomaly detection
* Store historical metrics

#### Q75. Notify Slack from alarm?

* SNS topic -> Lambda -> Slack webhook

#### Q76. Multi-Region dashboard?

* Use CloudWatch cross-Region dashboard widgets

#### Q77. EC2 crashed, investigate?

* Check EC2 logs, CloudWatch metrics (CPU, disk, etc.)
* Review system logs and alarms

#### Q78. Measure request processing time?

* Instrument code to publish metrics
* Use custom metric for request duration

#### Q79. Create dashboards programmatically?

* Use AWS CLI or SDK (`put-dashboard`)

#### Q80. Daily performance reports via email?

* CloudWatch Dashboard snapshot
* Scheduled Lambda job to email via SES or Slack
