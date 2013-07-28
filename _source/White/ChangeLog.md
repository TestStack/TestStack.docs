---
layout: layout
title: Change Log
order: 9
---

## Version 0.10.0
Version 0.10.0 removed the log4net dependency in TestStack.White, we now rely on [Castle.Core's Logging abstractions](http://old.castleproject.org/services/logging/index.html).

By default White uses the `ConsoleFactory` which will cause all logging to be directed to the console, which most unit test frameworks and build servers will pick up. 

To set your own simply override the logger factory in White's configuration.

    CoreAppXmlConfiguration.Instance.LoggerFactory = new Log4netFactory();

By removing this hard dependency you can use whatever logging framework you would like with White.