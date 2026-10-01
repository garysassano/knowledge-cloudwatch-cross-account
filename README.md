# Knowledge: CloudWatch Cross-Account

Last updated: 2026-10-01

Agent-oriented reference notes for overlapping CloudWatch cross-account / cross-region options and the announcements behind them.

## Contents

- [Approach Matrix](#approach-matrix)
- [Current Feature Support](#current-feature-support)
- [When To Use What](#when-to-use-what)
- [Category Timelines](#category-timelines)
- [Related But Not Core](#related-but-not-core)

## Approach Matrix

| Capability | CW Console (legacy) | CW OAM | CW Centralization | CW Omni |
| --- | --- | --- | --- | --- |
| Recommendation | Do not choose for new work; migrate away | Use for live observability | Use for central ownership/cross-region copy | Use as the team workspace on top of CW Centralization |
| Primary purpose | Console switching and legacy cross-account dashboards | Live cross-account observability | Central owned telemetry copy | AI-assisted investigation and agent observability in one place |
| Main mechanism | IAM role assumption | OAM sinks and links | AWS Organizations centralization rules | Organization domain + per account/region space, fed by CW Centralization |
| Moves telemetry | ❌ | ❌, except trace copy behavior | ✅ | ❌ itself; relies on CW Centralization |
| Cross-account | ✅ | ✅ | ✅ | ✅ via CW Centralization |
| Cross-region | ✅ | ❌ | ✅ | ✅ via CW Centralization |
| Programmatic access | ❌ for console experience | ✅ | ✅ | ✅ |
| Good for | Historical context and temporary migration state only | Live troubleshooting across accounts | Compliance, retention, analytics, backup, central alerting | One sign-in URL across the organization, natural-language investigation, AI agent evaluation |

## Current Feature Support

| Feature | CW OAM | CW Centralization | CW Omni |
| --- | --- | --- | --- |
| Logs | ✅ | ✅ | ✅ via CW Centralization |
| Metrics | ✅ | ✅ | ✅ via CW Centralization |
| Traces | ✅ | ❌ | ✅ via CW Centralization, with Transaction Search in each source account |
| Application Signals services/SLOs | ✅ | ❌ | Not documented; Omni has its own application map |
| Application Insights applications | ✅ | ❌ | Not documented |
| Internet Monitor monitors | ✅ | ❌ | Not documented |
| Cross-region | ❌ | ✅ | ✅ via CW Centralization |
| Central owned copy | ❌ | ✅ | ✅ via CW Centralization |

CW Centralization overlaps with CW OAM for logs and metrics, but does not currently cover traces or the broader application-observability resources. AWS describes these options as complementary. CW Omni does not use CW OAM; its cross-account view is exactly what CW Centralization copies into the space's account and region.

## When To Use What

| Requirement | Prefer |
| --- | --- |
| Live cross-account troubleshooting without copying telemetry | CW OAM |
| Central account must own copied logs/metrics | CW Centralization |
| Cross-region telemetry copy | CW Centralization |
| Traces or app-level observability across accounts | CW OAM |
| Existing CloudWatch account/region selector dashboards | Migrate away from CW Console (legacy); use CW OAM and/or CW Centralization depending on data ownership needs |
| One sign-in URL and AI-assisted investigation across the organization | CW Omni on top of CW Centralization |
| Custom log streaming to Kinesis, Firehose, Lambda, or downstream systems | Account-level subscription filters |

## Category Timelines

| Category | File | Introduced | Notes |
| --- | --- | --- | --- |
| CW Console (legacy) | [docs/cw-console-legacy.md](docs/cw-console-legacy.md) | 2019-11-08 | Historical role-based console sharing; migrate away. Includes SR migration notice. |
| CW OAM | [docs/cw-oam.md](docs/cw-oam.md) | 2022-11-27 | Live same-region cross-account observability using OAM sinks and links. |
| CW Centralization | [docs/cw-centralization.md](docs/cw-centralization.md) | 2025-09-17 logs, 2026-06-15 metrics | Cross-account/cross-region copied telemetry owned by the destination account. Log group tags propagate to the destination as of 2026-08-19. |
| CW Omni | [docs/cw-omni.md](docs/cw-omni.md) | 2026-09-23 | Organization-wide AI observability workspace; one space per account/region, fed by CW Centralization. Does not use CW OAM. |

## Related But Not Core

These are not additional base models. They are related CloudWatch capabilities layered on top of, or adjacent to, the core models above.

| Date | Item | AWS News | AWS Blog | AWS Docs | Notes |
| --- | --- | --- | --- | --- | --- |
| 2015-08 | CloudWatch Logs cross-account subscriptions | Not found | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CrossAccountSubscriptions.html) | Origin of `AWS::Logs::Destination`: receiver-owned destination wrapping a Kinesis stream (later Firehose), targeted by sender subscription filters. AWS News page retired; listed in the [AWS Week in Review, 2015-08-10](https://aws.amazon.com/blogs/aws/aws-week-in-review-august-10-2015/). |
| 2022-01-05 | Organizations support for cross-account Logs subscriptions | [News](https://aws.amazon.com/about-aws/whats-new/2022/01/amazon-cloudwatch-logs-aws-organizations-subscriptions/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CrossAccountSubscriptions.html) | Destination access policies can use `aws:PrincipalOrgID` / `aws:PrincipalOrgPath` instead of account lists. |
| 2024-01-11 | CloudWatch Logs account-level subscription filters | [News](https://aws.amazon.com/about-aws/whats-new/2024/01/amazon-cloudwatch-logs-account-level-subscription-filter/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/SubscriptionFilters-AccountLevel.html) | DIY/custom log streaming to Kinesis Data Streams, Firehose, or Lambda. |
| 2025-11-21 | Database Insights cross-account cross-region monitoring | [News](https://aws.amazon.com/about-aws/whats-new/2025/11/cloudwatch-database-insights-cross-account-region-monitoring/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Database-Insights-Cross-Account-Cross-Region.html) | Product-specific console capability. Requires both CW OAM and CW Console (legacy) setup first. |

Database Insights cross-account cross-region is not its own base model. AWS docs say it requires:

- CW OAM / CloudWatch cross-account observability, with Logs, Metrics, Traces, and Application Signals shared in each relevant region.
- CW Console (legacy) / cross-account cross-region CloudWatch console, with CloudWatch automatic dashboards and read-only Database Insights access enabled.
