# CW OAM

Live cross-account observability within a region using OAM sinks and links. Use this when operators need to troubleshoot across accounts without copying telemetry.

## Timeline

| Date | Item | AWS News | AWS Blog | AWS Docs | Notes |
| --- | --- | --- | --- | --- | --- |
| 2022-11-27 | CloudWatch cross-account observability | [News](https://aws.amazon.com/about-aws/whats-new/2022/11/amazon-cloudwatch-cross-account-observability-multiple-aws-accounts/) | [Blog](https://aws.amazon.com/blogs/aws/new-amazon-cloudwatch-cross-account-observability/) | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Unified-Cross-Account.html) | OAM launch: monitoring accounts, source accounts, sinks, and links. |
| 2023-09-27 | Application Insights across accounts | [News](https://aws.amazon.com/about-aws/whats-new/2023/09/analyze-multi-account-app-health-cloudwatch-application-insights/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/appinsights-cross-account.html) | Application Insights applications and problems from source accounts visible in the monitoring account. |
| 2023-12-08 | Cross-account Metrics Insights | [News](https://aws.amazon.com/about-aws/whats-new/2023/12/amazon-cloudwatch-cross-account-metrics-insights/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/query_with_cloudwatch-metrics-insights.html) | Metrics Insights SQL queries and alarms spanning OAM source accounts. |
| 2024-04-04 | Internet Monitor cross-account observability | [News](https://aws.amazon.com/about-aws/whats-new/2024/04/cross-account-observability-cloudwatch-internet-monitor/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cwim-cross-account.html) | Read-only access to Internet Monitor monitors in source accounts via OAM. |
| 2025-02-27 | Application Signals across accounts | [News](https://aws.amazon.com/about-aws/whats-new/2025/02/monitor-observe-apps-across-multiple-accounts-application-signals/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Unified-Cross-Account.html) | Application Signals services and SLOs from source accounts; SLOs can be set in the monitoring account. |
| 2025-04-18 | CloudWatch cross-account observability in GovCloud | [News](https://aws.amazon.com/about-aws/whats-new/2025/04/amazon-cloudwatch-cross-account-observability-govcloud/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Unified-Cross-Account.html) | Same OAM model expanded to AWS GovCloud (US) regions. |
| 2025-09-11 | OAM VPC endpoints | [News](https://aws.amazon.com/about-aws/whats-new/2025/09/amazon-cloudwatch-observability-access-manager-vpc-endpoints/) | Not found | [Docs](https://docs.aws.amazon.com/general/latest/gr/cloudwatchoam.html) | PrivateLink/VPC endpoint access for the OAM control plane. |
| 2025-11-20 | Application map cross-account views | [News](https://aws.amazon.com/about-aws/whats-new/2025/11/amazon-cloudwatch-application-map-un-instrumented-discovery/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Services.html) | Single application map across accounts, plus un-instrumented service discovery and change history. |

## Resource Indicators

| Resource | Meaning |
| --- | --- |
| `AWS::Oam::Sink` | Monitoring account attachment point. |
| `AWS::Oam::Link` | Source account link to a monitoring account sink. |
