# CW OAM

Live cross-account observability within a region using OAM sinks and links. Use this when operators need to troubleshoot across accounts without copying telemetry.

## Timeline

| Date | Item | AWS News | AWS Blog | AWS Docs | Notes |
| --- | --- | --- | --- | --- | --- |
| 2022-11-27 | CloudWatch cross-account observability | [News](https://aws.amazon.com/about-aws/whats-new/2022/11/amazon-cloudwatch-cross-account-observability-multiple-aws-accounts/) | [Blog](https://aws.amazon.com/blogs/aws/new-amazon-cloudwatch-cross-account-observability/) | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Unified-Cross-Account.html) | OAM launch: monitoring accounts, source accounts, sinks, and links. |
| 2025-04-18 | CloudWatch cross-account observability in GovCloud | [News](https://aws.amazon.com/about-aws/whats-new/2025/04/amazon-cloudwatch-cross-account-observability-govcloud/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch-Unified-Cross-Account.html) | Same OAM model expanded to AWS GovCloud (US) regions. |
| 2025-09-11 | OAM VPC endpoints | [News](https://aws.amazon.com/about-aws/whats-new/2025/09/amazon-cloudwatch-observability-access-manager-vpc-endpoints/) | Not found | [Docs](https://docs.aws.amazon.com/general/latest/gr/cloudwatchoam.html) | PrivateLink/VPC endpoint access for the OAM control plane. |

## Resource Indicators

| Resource | Meaning |
| --- | --- |
| `AWS::Oam::Sink` | Monitoring account attachment point. |
| `AWS::Oam::Link` | Source account link to a monitoring account sink. |
