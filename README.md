# Serilog.Sinks.Site24x7 - A Serilog Sink that sends log event to Site24x7 logtype endpoint


## Table of Contents

- [Installation](#installation)
- [Usage](#usage)


## Installation

```csharp
ILogger log = new LoggerConfiguration()
  .MinimumLevel.Verbose()
  .WriteTo.Site24x7Url("http://www.logc.site24x7.com/event/receiver?token=[YOUR_TOKEN]")
  .CreateLogger();
```
Or Use the namespace ```[Serilog.Settings.Configuration]``` and update your appsettings.json

```json
{
  "Serilog": {
    "MinimumLevel": "Verbose",
    "WriteTo": [
      {
        "Name": "Site24x7Url",
        "Args": {
          "requestUri": "http://www.logc.site24x7.com/event/receiver?token=[YOUR_TOKEN]"
        }
      }
    ]
  }
}
```
## Usage

The sink is a single line log event post using this site24x7 log pattern
```
json $RequestPath$ $ParentId$ $RequestId$ $Timestamp:date:yyyy-MM-dd'T'HH:mm:ss.SSS$ $SourceContext$ $MessageTemplate$ $ActionName$ $ActionId$ $RenderedMessage$ $MachineName$ $ThreadId:number$ $TraceId$ $Environment$ $Level$ $ProcessId:number$ $SpanId$
```
