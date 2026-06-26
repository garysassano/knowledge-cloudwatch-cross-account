# Knowledge: CloudWatch Cross-Account

Last updated: 2026-06-19

Agent-oriented reference notes for overlapping CloudWatch cross-account / cross-region options and the announcements behind them.

## Contents

- [Approach Matrix](#approach-matrix)
- [Current Feature Support](#current-feature-support)
- [When To Use What](#when-to-use-what)
- [Category Timelines](#category-timelines)
- [Related But Not Core](#related-but-not-core)

## Approach Matrix

| Capability | CW Console (legacy) | CW OAM | CW Centralization |
| --- | --- | --- | --- |
| Recommendation | Do not choose for new work; migrate away | Use for live observability | Use for central ownership/cross-region copy |
| Primary purpose | Console switching and legacy cross-account dashboards | Live cross-account observability | Central owned telemetry copy |
| Main mechanism | IAM role assumption | OAM sinks and links | AWS Organizations centralization rules |
| Moves telemetry | ❌ | ❌, except trace copy behavior | ✅ |
| Cross-account | ✅ | ✅ | ✅ |
| Cross-region | ✅ | ❌ | ✅ |
| Programmatic access | ❌ for console experience | ✅ | ✅ |
| Good for | Historical context and temporary migration state only | Live troubleshooting across accounts | Compliance, retention, analytics, backup, central alerting |

## Current Feature Support

| Feature | CW OAM | CW Centralization |
| --- | --- | --- |
| Logs | ✅ | ✅ |
| Metrics | ✅ | ✅ |
| Traces | ✅ | ❌ |
| Application Signals services/SLOs | ✅ | ❌ |
| Application Insights applications | ✅ | ❌ |
| Internet Monitor monitors | ✅ | ❌ |
| Cross-region | ❌ | ✅ |
| Central owned copy | ❌ | ✅ |

CW Centralization overlaps with CW OAM for logs and metrics, but does not currently cover traces or the broader application-observability resources. AWS describes these options as complementary.

## When To Use What

| Requirement | Prefer |
| --- | --- |
| Live cross-account troubleshooting without copying telemetry | CW OAM |
| Central account must own copied logs/metrics | CW Centralization |
| Cross-region telemetry copy | CW Centralization |
| Traces or app-level observability across accounts | CW OAM |
| Existing CloudWatch account/region selector dashboards | Migrate away from CW Console (legacy); use CW OAM and/or CW Centralization depending on data ownership needs |
| Custom log streaming to Kinesis, Firehose, Lambda, or downstream systems | Account-level subscription filters |

## Category Timelines

| Category | File | Introduced | Notes |
| --- | --- | --- | --- |
| CW Console (legacy) | [docs/cw-console-legacy.md](docs/cw-console-legacy.md) | 2019-11-08 | Historical role-based console sharing; migrate away. Includes SR migration notice. |
| CW OAM | [docs/cw-oam.md](docs/cw-oam.md) | 2022-11-27 | Live same-region cross-account observability using OAM sinks and links. |
| CW Centralization | [docs/cw-centralization.md](docs/cw-centralization.md) | 2025-09-17 logs, 2026-06-15 metrics | Cross-account/cross-region copied telemetry owned by the destination account. |

## Related But Not Core

These are not fourth/fifth base models. They are related CloudWatch capabilities layered on top of, or adjacent to, the core models above.

| Date | Item | AWS News | AWS Blog | AWS Docs | Notes |
| --- | --- | --- | --- | --- | --- |
| 2024-01-11 | CloudWatch Logs account-level subscription filters | [News](https://aws.amazon.com/about-aws/whats-new/2024/01/amazon-cloudwatch-logs-account-level-subscription-filter/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/SubscriptionFilters-AccountLevel.html) | DIY/custom log streaming to Kinesis Data Streams, Firehose, or Lambda. |
| 2025-11-21 | Database Insights cross-account cross-region monitoring | [News](https://aws.amazon.com/about-aws/whats-new/2025/11/cloudwatch-database-insights-cross-account-region-monitoring/) | Not found | [Docs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Database-Insights-Cross-Account-Cross-Region.html) | Product-specific console capability. Requires both CW OAM and CW Console (legacy) setup first. |

Database Insights cross-account cross-region is not its own base model. AWS docs say it requires:

- CW OAM / CloudWatch cross-account observability, with Logs, Metrics, Traces, and Application Signals shared in each relevant region.
- CW Console (legacy) / cross-account cross-region CloudWatch console, with CloudWatch automatic dashboards and read-only Database Insights access enabled.
