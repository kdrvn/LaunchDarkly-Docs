---
title: "New Relic"
excerpt: ""
---
[block:api-header]
{
  "title": "Overview"
}
[/block]
This topic explains how to use the New Relic integration to annotate New Relic transactions with feature flag information. You can use this data to correlate feature flag variations with changes in application performance or error rates.
[block:callout]
{
  "type": "warning",
  "title": "SDK Support",
  "body": "Currently, New Relic integration is only available for Java and Ruby. Support for other platforms is coming soon."
}
[/block]

[block:api-header]
{
  "title": "Adding the New Relic integration"
}
[/block]
LaunchDarkly SDKs automatically detect whether you have New Relic installed without any additional configuration steps. If LaunchDarkly detects New Relic, 
LaunchDarkly adds a [custom attribute](https://docs.newrelic.com/docs/insights/new-relic-insights/decorating-events/insights-custom-attributes) for every feature flag request call made within a New Relic transaction trace.
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/HBeGFpHmT5SBze4akxR0_2015-04-23%20at%202.27%20PM.png",
        "2015-04-23 at 2.27 PM.png",
        "740",
        "815",
        "#eb7d67",
        ""
      ],
      "caption": "In this transaction, a feature flag with key `map.save.header` was requested, and the variation returned was `true`."
    }
  ]
}
[/block]
You can see custom attributes for particular transactions on your New Relic dashboard, or use [NRQL](https://docs.newrelic.com/docs/insights/new-relic-insights/using-new-relic-query-language/nrql-reference) to explore how feature flags impact performance across many transactions.