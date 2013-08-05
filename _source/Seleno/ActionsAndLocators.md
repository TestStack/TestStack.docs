---
layout: layout
title: Actions and Locators
order: 3
---

Page Objects tend to either perform actions or find items on the page. Seleno Page Objects provide a number of Actions and Locators that you can use.

## Actions ##
### Navigator ###
Used to perform actions that take you to another page, such as clicking a button or a link, or navigating to a URL. There is a strongly typed option to navigate with a controller expression using routing. Page Objects expose the Navigator class with the Navigate() method.

    Navigate().To<RegisterPage>(By.LinkText("Register"));

### Page Reader ###
Read values from the page using view model based strongly typed methods. Page Objects that extend `Page<T>`expose the Page Reader class with the Read() method. For example, to read all fields into a new instance of the current model type (`T`) in a page you can use the `ModelFromPage` method:

    var model = Read().ModelFromPage();

Read() is currently only available with the generically-typed page object for now, but if you want this functionality with non-generic page objects (by instead supplying strings for the id) then to add an issue to our Github site so we can prioritise it.

### Page Writer ###
Write values to the page using view model based strongly typed methods. Page Objects that extend `Page<T>`expose the Page Writer class with the Input() method. For example, to write all fields from a model of the current type (`T`) from the form on a page you can use the `Model` method:

    Input().Model(modelInstanceToFillInFormUsing);

Input() is currently only available with the generically-typed page object for now, but if you want this functionality with non-generic page objects (by instead supplying strings for the id) then to add an issue to our Github site so we can prioritise it.

### Script Executor ###
If none of the above meet your needs then you have the ultimate control by executing JavaScript with the Script Executor class. Page Objects expose the Script Executor class with the Execute() method.

    return Execute().ScriptAndReturn<TReturn>(string.Format("$('#{0}').attr('{1}')",Id,attributeName));

## Locators ##
### Element Finder ###
Finds Selenium IWebElement items on the page, using the Selenium By selectors or the Seleno jQuery selectors. Page Objects expose the Element Finder class with the Find() method.

    var selector = string.Format("$('#{0} option:selected')", Id);
    return Find().Element(By.jQuery(selector), WaitInSecondsUntilElementAvailable);

# Navigation #
A great way to slow down your tests is to start each test on the home page and then navigate to the page you want to test! It's much better to navigate directly to the page that you want to test. You can do this by calling the NavigateToInitialPage method on SelenoHost instance and passing in the *relative* URL (to the root of the site being tested) or an absolute URL.

    var page = <AnInstanceOfSelenoHost>.NavigateToInitialPage<RegisterPage>("/Account/Register");

In addition, if you are using ASP.NET MVC then you can also use strongly typed controller action expressions to navigate to the page via routing. 

    var page = <AnInstanceOfSelenoHost>.NavigateToInitialPage<AccountController, RegisterPage>(x => x.Register());

If you are using these MVC expressions, just remember to register the application routes when you are initializing Seleno.

    <AnInstanceOfSelenoHost>.Run("MvcMusicStore", 12345);
    MvcApplication.RegisterRoutes(RouteTable.Routes); 
