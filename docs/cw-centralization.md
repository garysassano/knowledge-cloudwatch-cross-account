# CW Centralization

Managed copying of logs or metrics into a destination account/region using AWS Organizations centralization rules. Use this when the central account must own the telemetry copy.

## Timeline

| Date | Item | AWS News | AWS Blog | AWS Docs | Notes |
| --- | --- | --- | --- | --- | --- |
| 2025-09-17 | Cross-account cross-region log centralization | [News](https://aws.amazon.com/about-aws/whats-new/2025/09/amazon-cloudwatch-cross-account-cross-region-log-centralization/) | [Blog](https://aws.amazon.com/blogs/mt/simplifying-log-management-using-amazon-cloudwatch-logs-centralization/) | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CloudWatchLogs_Centralization.html) | Managed copying of new log events into a destination account. |
| 2026-02-27 | Customizable destination log group structure | [News](https://aws.amazon.com/about-aws/whats-new/2026/02/cloudwatch-centralization-custom-groups/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CloudWatchLogs_Centralization.html) | Destination log group naming using source account, region, log group, and AWS Organizations attributes. |
| 2026-03-30 | Logs centralization based on data source | [News](https://aws.amazon.com/about-aws/whats-new/2026/03/cloudwatch-centralization-datasource/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CloudWatchLogs_Centralization.html) | Source selection by data source name/type, such as VPC Flow Logs, EKS Audit Logs, and CloudTrail Logs. |
| 2026-06-15 | Cross-account metrics centralization GA | [News](https://aws.amazon.com/about-aws/whats-new/2026/06/amazon-cross-account-metrics-centralization/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatchMetrics_Centralization.html) | Managed replication of CloudWatch and OpenTelemetry metrics into a destination account. |

## Centralization Indicators

| Indicator | Meaning |
| --- | --- |
| AWS Organizations trusted access | Required for centralization rules. |
| Source account/OUs/regions | Rule selection scope. |
| Destination account/region | Where copied telemetry is stored. |
| `@aws.account` / `@aws.region` | Source metadata added to centralized telemetry. |
| `AWSObservabilityAdminLogsCentralizationServiceRolePolicy` | Logs centralization service-linked role policy. |
