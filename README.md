# App.Metrics.Reporting.Custom.Mackerel

Reporter to [Mackerel](https://mackerel.io/) of [App Metrics](https://www.app-metrics.io/).

Usage:
```cs
var metrics = AppMetrics.CreateDefaultBuilder()
    // configure a reporter
    .Report.ToMackerel(
        options =>
        {
            options.ApiKey = mackerelApiKey;
            options.HostId = mackerelHostId;

            options.HttpOptions.HttpPolicy.BackoffPeriod = TimeSpan.FromSeconds(30);
            options.HttpOptions.HttpPolicy.FailuresBeforeBackoff = 3;
            options.HttpOptions.HttpPolicy.Timeout = TimeSpan.FromSeconds(10);
            options.HttpOptions.Filter = filter;
            options.HttpOptions.FlushInterval = TimeSpan.FromSeconds(60);
        })
    .Build();
```
