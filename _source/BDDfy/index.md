---
layout: layout
title: BDDfy
---

BDDfy (pronounced B D Defy) is the simplest BDD framework for .Net EVER! The name comes from the fact that it allows you to turn your tests into BDD behaviors simply. 

A few quick facts about BDDfy:

 - It can run with any testing framework. Actually you don't have to use a testing framework at all. You can just apply it on your POCO (test) classes!
 - It does not need a separate test runner. You can use your runner of choice. For example, you can write your BDDfy tests using NUnit and run them using NUnit console or GUI runner, Resharper or TD.Net and regardless of the runner, you will get the same result.
 - It can run standalone scenarios. In other words, although BDDfy supports stories, you do not necessarily have to have or make up a story to use it. This is useful for developers who work in non-Agile environments but would like to get some decent testing experience.
 - You can use underscored or pascal or camel cased method names for your steps.
 - You do not have to explain your scenarios or stories or steps in string, but you can if you need full control over what gets printed into console and HTML reports.
 - BDDfy is very extensible: it's core barely has any logic in it and it delegates all it's responsibilities to it's extensions all of which are configurable; e.g. if you don't like the reports it generates, you can write your custom reporter in a few lines of code.

Using BDDfy, it is easier to switch to BDD. So if you are on a project with a couple of hundred tests already written and you think using BDD could make your tests more valuable, then BDDfy can help you with that. You are still going to need to make some changes; but hopefully they will be minimal.

To use BDDfy:

 - Install NuGet if you have not already.
 - Go to 'Tools', 'Library Package Manager', and click 'Package Manager Console'.
 - In the console, type `Install-Package TestStack.BDDfy` and enter.

This adds BDDfy assembly and its dependencies to your test project. If this is the first time you are using BDDfy you may want to check out the samples on NuGet. Just run `Install-Package TestStack.BDDfy.Samples` and it will load two fully working samples to your project.

...