---
layout: layout
title: Page Object Pattern
---

The Page Object Pattern is a well known pattern to make life easier for us when performing automated UI testing.

This pattern is supported by both White and Seleno, each has it's own implementation which is covered in their documentation pages.

The use of the Page Object Pattern (POP) - sometimes referred to as page object models - provides a number of benefits:

- Less code duplication
- Lower long-term maintenance costs
- More readable and understandable test scenarios

##So What Is A Page Object Model (POM)?

Put simply, it is a class that models some of the UI items on a given screen or page in the application. In this way we are modelling what the page looks like to the end-user and thinking from their perspective, rather than from an internal implementation perspective.

The POM may contain properties that represent items on the screen, such as a string property that represents an order item quantity. This quantity property abstract away the actual UI automation code. Test code can them simply make use of this quantity property whenever it needs to read or set the quantity in the screen.

##Modelling Logical User Functions

In addition to simple properties to get/set individual UI control values, methods can also be added to a POM. These methods represent logical actions the end-user can make in the UI.

For example, a method LoginAs(string name, string password) could be added to the POM that represents a login screen. Internally this LoginAs method types the username and password into the UI and then clicks the login button.

Test code can now simply call the LoginAs method.

Now any tests that login, can reuse this method. The intent of the tests also becomes clearer as the flow of the test is not obscured with many individual UI get/sets/clicks/etc.

##Maintenance Benefits

Because UI interaction has been abstracted away from test code, when the UI changes only the POMs have to be updated.

For example, if the ID of the login button changed, only the login screen POM would need to be updated. Without POMs, every single test would be specifying this ID and would need to be changed individually.
