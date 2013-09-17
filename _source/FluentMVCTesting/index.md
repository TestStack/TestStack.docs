---
layout: layout
title: Fluent MVC Testing
---

This library provides a fluent interface for creating terse, expressive and (where possible) type-safe tests against ASP.NET MVC controllers.

In general we recommend that you keep your MVC controllers really lean (2 or 3 lines) in which case the controller probably doesn't need a test since it will be clear at a glance that it's correct or not and it will be unlikely to have regressions. This library is great for those situations where you have to have a meaty controller that warrants test coverage.

This library is testing framework agnostic, so you can combine it with the testing library of your choice (e.g. NUnit, xUnit, etc.).

The library is compatible with the AAA testing methodology, although it combines the Act and Assert parts together (but you can also have other assertions after the Fluent assertion). See the code examples in the usage instructions for more information.

This library was inspired by the [MVCContrib.TestHelper](http://mvccontrib.codeplex.com/wikipage?title=TestHelper) library.

Motivation
-----------

The motivation behind this library is to provide a way to test MVC actions quickly, tersely and maintainably.

Most examples we find on MVC controller testing are incredibly verbose, repetitive and time-consuming to write and maintain and we've also noticed most examples of controller testing having a lot of magic strings being used to test view and action names.

This library aims to make the time to implement controller tests really small for those situations where you find yourself needing to write them and it also aims to (where possible) utilise the type system to resolve a lot of those nasty magic strings thus ensuring your tests are more maintainable and require less re-work when you perform major refactoring of your code.

Installation
------------

You can install this library using NuGet into your Test Library; it will automatically reference System.Web and System.Web.Mvc (via NuGet packages, sorry it also installs a heap of other dependencies - it would be cool if Microsoft provided a package with just the MVC dll!) for you.

If you are using ASP.NET MVC 4 then:

    Install-Package TestStack.FluentMVCTesting

If you are using ASP.NET MVC 3 then:

    Install-Package TestStack.FluentMVCTesting.Mvc3

Known Issues
------------

If you get the following exception:

    System.Security.VerificationException : Method FluentMVCTesting.ControllerExtensions.WithCallTo: type argument 'MyApp.Controllers.MyController' violates the constraint of type parameter 'T'.

It means you are referencing a version of System.Web.Mvc that isn't compatible with the one that was used to build the dll that was generated for the NuGet package. Ensure that you are using the correct package for your version of MVC and that you are using the [AspNetMvc packages on nuget.org](https://nuget.org/packages/aspnetmvc) rather than the dll from the GAC.

Usage
------

See the [usage instructions](usage.html).

Any questions, comments or additions?
-------------------------------------

Leave an issue on the [issues page](https://github.com/TestStack/TestStack.FluentMVCTesting/issues) or send a [pull request](https://github.com/TestStack/TestStack.FluentMVCTesting/pulls).