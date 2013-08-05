---
layout: layout
title: Seleno Configuration
order: 2
---

The simplest possible configuration to start using Seleno is just one line. If you are using an ASP.NET web application within the same solution as your test project then all Seleno needs to know is the name of the web project to test and the port number to run it on. SelenoHost is your portal to Seleno and you will need an instance of the class in order to talk to Seleno. This class takes care of a lot of things and is a relatively expensive class to "run" once per test. So you would normally create one instance and use it in all your tests. 

    public static class Host
    {
        public static readonly SelenoHost Instance = new SelenoHost();

        static Host()
        {
            Instance.Run("TestStack.Seleno.Samples.Movies", 19456);
        }
    }

This will deploy your web application with IIS Express and open up FireFox to run your tests. When the application domain unloads it will unload the browser and web server.

By default, Seleno uses:

- FireFox for the web browser
- IIS Express for the web server
- No logger
- No camera for taking screenshots

If you want to change these defaults, you can use a fluent configuration to override them. For example, if you wanted to use Chrome instead of Firefox (the default) and to log messages to the console, you could write:

    Instance.Run("TestStack.Seleno.Samples.Movies", 19456,
	    configure => configure
		    .WithRemoteWebDriver(BrowserFactory.Chrome)
		    .UsingLoggerFactory(new ConsoleFactory())
    );

> Note: To use the Chrome WebDriver you also need to download [ChromeDriver.exe](https://code.google.com/p/selenium/wiki/ChromeDriver) and make sure it is in your bin directory when you run your tests.

There are more things that you can configure too. The original use case for Seleno was to test Visual Studio web projects for ASP.Net and ASP.Net MVC and it defaults to doing this with IIS Express. Seleno attempts to be modular and easy to customise though, so to test any website instead is just a matter of swapping out the IisExpressWebServer for the InternetWebServer. For example, to test Google UK:

    Instance.Run(configure => configure
    	.WithWebServer(new InternetWebServer("www.google.co.uk")));
