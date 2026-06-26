# CW Console (legacy)

Role-based account/region switching in the CloudWatch console. Do not choose this for new work; migrate away from it.

## Timeline

| Date | Item | AWS News | AWS Blog | AWS Docs | Notes |
| --- | --- | --- | --- | --- | --- |
| 2019-11-08 | Cross-account cross-region dashboards | [News](https://aws.amazon.com/about-aws/whats-new/2019/11/amazon-cloudwatch-launches-cross-account-cross-region-dashboards/) | [Blog](https://aws.amazon.com/blogs/aws/cross-account-cross-region-dashboards-with-amazon-cloudwatch/) | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Cross-Account-Cross-Region.html) | Original role-based CloudWatch dashboard/account selector feature. |

## SR Migration Notice

This is an AWS Health / User Notifications item, not a public AWS News announcement.

| Date | Scope | Source | Reference docs | Notes |
| --- | --- | --- | --- | --- |
| 2026-07-13 | CW Console (legacy) | AWS Health / User Notifications | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Cross-Account-Cross-Region.html) | Affected accounts with `AWSServiceRoleForCloudWatchCrossAccount` must migrate to the service role path. |

Key points from the notice:

- Old role: `AWSServiceRoleForCloudWatchCrossAccount`.
- New/current role: `ServiceRoleForCloudWatchCrossAccountV2`.
- The new service role fully honors AWS Organizations SCPs.
- If the old role is absent, AWS says the account is not affected.
- This is CW Console (legacy), not CW OAM and not CW Centralization.

## Role Indicators

| Role | Where | Meaning |
| --- | --- | --- |
| `CloudWatch-CrossAccountSharingRole` | Source/sharing account | Grants the monitoring account read/view access. |
| `AWSServiceRoleForCloudWatchCrossAccount` | Monitoring account | Old affected service-linked role from the AWS Health notice. |
| `ServiceRoleForCloudWatchCrossAccountV2` | Monitoring account | New/current service role path. |
