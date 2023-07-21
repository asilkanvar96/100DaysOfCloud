<!-- This is a template you can use for quick progress days. It removes a lot of the steps we encourage you to share in the longer template 000-DAY-ARTICLE-LONG-TEMPLATE.MD-->

# Day 2 Monitoring and Metrics

## Cloud Research

Metric is a collection of data point which are gathered from your resources

$$
 Metrics / Time = Statistics


$$

    **Samples:**

For EC2 : CPU utilization
For S3: request of reading or writing objects
For RDS: DB connections, disk space consumption

CloudWatch can do:

- Detect anomalous behavior in your environments.
- Set alarms to alert you when something’s not right.
- Visualize logs and metrics with the AWS Management Console.
- Take automated actions like scaling.
- Troubleshoot issues.
- Discover insights to keep your applications healthy.

**CloudWatch Alarms**

- **OK:** The metric is within the defined threshold. Everything appears to be operating like normal.
- **ALARM:** The metric is outside of the defined threshold. This could be an operational issue.
- **INSUFFICIENT_DATA:** The alarm has just started, the metric is not available, or not enough data is available for the metric to determine the alarm state.
