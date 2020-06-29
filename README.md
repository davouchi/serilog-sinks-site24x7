# Serilog.Sinks.Site24x7 - A Serilog Sink that sends log event to Site24x7 logtype endpoint


## Table of Contents

- [Installation](#installation)
- [Usage](#usage)


## Installation

```csharp
ILogger log = new LoggerConfiguration()
  .MinimumLevel.Verbose()
  .WriteTo.Site24x7Url("http://www.logc.site24x7.com/event/receiver?token=[YOUR_TOKEN]", "Debug")
  .CreateLogger();
```
Or Use the namespace ```[Serilog.Settings.Configuration]``` and update your appsettings.json

```json
{
  "Serilog": {
    "MinimumLevel": "Verbose",
    "Enrich": [ "FromLogContext", "WithMachineName", "WithProcessId", "WithThreadId", "WithExceptionDetails" ],
    "WriteTo": [
      {
        "Name": "Site24x7Url",
        "Args": {
          "requestUri": "http://www.logc.site24x7.com/event/receiver?token=[YOUR_TOKEN]",
          "minimumLogLevel":"Debug"
        }
      }
    ]
  }
}
```
## Usage

This sink is a single line log event post using this site24x7 log pattern
```
json  $Timestamp:date:MM/dd/yyyy HH:mm:ss.SSS$ $Environment$ $Level$ $RequestPath$$RenderedMessage$$SourceContext$ $ActionName$ $ActionId$  $MachineName$ $ThreadId:number$ $TraceId$ $ProcessId:number$ $SpanId$ $ParentId$ $RequestId$
```
