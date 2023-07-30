Welcome to the my sample website.

# Project : Sumolib

This library provides higher level interface to [Sumologic](https://www.sumologic.com/) Search API. Sumologic is a wonderful system to ingest and process textual logs for systems monitoring, debugging, telemetery and log insights.

Sumologic provides REST based [Search Apis](https://help.sumologic.com/APIs/Search-Job-API/About-the-Search-Job-API) to fire the queries on your log data.

The APIs are bit tricky and requires stateful communication of three request-response pairs. The method is outlined [here](https://help.sumologic.com/APIs/Search-Job-API/About-the-Search-Job-API#process-flow).

SumoLib hides all this complexity and provides the `IEnumerable<T>` to process the results using LINQ / loops.

Sumolib is available on Nuget at : https://www.nuget.org/packages/SumoLib/

The project is available at : [Sumolib](https://github.com/porechajp/sumolib)

```csharp
using SumoLib;

var data = await SumoClient.New().Query(@"_sourceCategory=appserver | parse""Login:*"" as uid | fields uid")
                                 .ForLast(TimeSpan.FromDays(1))
                                 .RunAsync(new {uid = ""});

Console.WriteLine($"Total Logins : {data.Stats.MessageCount}");
foreach (var record in data)
{
    Console.WriteLine(record.uid);
}

```

# About

![Jatan Porecha](assets/jatan-photo-removebg.png)
I am an experienced engineer always looking for some challenging and satisfying work !
