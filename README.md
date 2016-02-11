# Serilog.Sinks.SizeRollingFile

This project has been developed to extend [Serilog](https://github.com/serilog/serilog) buit-in RollingFile, to limit the log files based on size, also purge old files to free up disk space.

## The nuget package  [![NuGet Status](https://img.shields.io/nuget/v/Serilog.Sinks.RollingFile.Extension.svg?style=flat)](https://www.nuget.org/packages/Serilog.Sinks.RollingFile.Extension/)

https://www.nuget.org/packages/Serilog.Sinks.RollingFile.Extension/

    PM> Install-Package Serilog.Sinks.RollingFile.Extension



## Configuring the logger


### 1. Through the code
 
```cs
new LoggerConfiguration()                                       
      .WriteTo.SizeRollingFile(@"C:\temp\log.txt", 
              retainedFileDurationLimit: TimeSpan.FromDays(2), 
              fileSizeLimitBytes: 1024 * 1024 * 10) // 10MB
      .CreateLogger();
```


### 2. Configuration file

```xml
<appSettings>
	<add key="serilog:using:SizeRollingFile" value="Serilog.Sinks.RollingFile.Extension"/>
    <add key="serilog:write-to:SizeRollingFile.pathFormat" value="C:\temp\log.txt"/>
    <add key="serilog:write-to:SizeRollingFile.fileSizeLimitBytes" value="10485760"/>
    <add key="serilog:write-to:SizeRollingFile.retainedFileDurationLimit" value="2.00:00:00"/>
</appSettings>
```
    
