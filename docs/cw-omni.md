# CW Omni

AI-first observability workspace reached through an organization-wide sign-in URL, with one space per account and region. Omni does not aggregate telemetry across accounts or regions on its own; it reads whatever CW Centralization rules replicate into the space's account and region.

## Timeline

| Date | Item | AWS News | AWS Blog | AWS Docs | Notes |
| --- | --- | --- | --- | --- | --- |
| 2026-09-23 | CloudWatch Omni GA | [News](https://aws.amazon.com/about-aws/whats-new/2026/09/amazon-cloudwatch-omni-ai/) | [Blog](https://aws.amazon.com/blogs/mt/introducing-amazon-cloudwatch-omni-observability-for-the-ai-era/) | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/omni-set-up-omni-for-your-organization.html) | Organization domain plus per-account spaces. Cross-account and cross-region data comes from CW Centralization rules targeting the space's account and region. Also ingests Azure workloads. Launched in us-east-1, us-west-2, and eu-west-1. |

## Omni Indicators

| Indicator | Meaning |
| --- | --- |
| Organization domain | Created once from the AWS Organizations management account; requires trusted access between Organizations and CloudWatch. Gives one sign-in URL for every member account's space. |
| `https://<domain-name>.cloudwatch-omni.global.app.aws` | Domain sign-in URL. Identity provider (IAM Identity Center) connects at the domain, not per space. |
| Space | One per account and region; sees only telemetry in that account and region. Cross-space queries are not supported. |
| CW Centralization rule with destination = space account/region | How a space sees other accounts and regions. Created from the management account or a delegated administrator. No backfill of telemetry from before the rule. |
| Transaction Search enabled in every source account | Required for traces to be centralized into the space; they then follow logs centralization. |
| `CloudWatchOmniOperatorRole` | Role Omni assumes to manage the space and query telemetry. |
| `CloudWatchOmniDatasetIntegrationExecutionRole` | Role CloudWatch assumes to expose telemetry to Omni through the CloudWatch Dataset. |
| CW OAM sinks and links | Not used by Omni. |
