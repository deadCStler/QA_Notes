A software design pattern is a general, reusable solution to a commonly occurring problem within a given context in software design. It is not a finished design that can be transformed directly into source or machine code.

There are 3 major types of software design patterns:

- Creational : Way to create objects while hiding the creation logic
- Structural : Focuses on how classes and objects can be composed to form larger structures
- Behavioral : Concerned with the assignment of responsibilities between objects or encapsulating behavior in an object and delegating requests to it.

Some test design patterns are:

- Page Object Model
- Factory Design Pattern
- Façade Design Pattern
- Singleton Pattern

### Page Object Module

It is a **structural design pattern** in selenium that creates an object repository for storing all the web elements. It is useful in reducing code duplication and improves test case maintenance.
Advantages:
- Easy Maintenance
- Reusing code
- Readability and Reliability of Scripts

### Page Factory

It is needed to organize the locators and actions of a page in a single place.

It is a way of implementing POM. It is an inbuilt concept of POM, here, we follow the principle of separation of Page Object Repository and Test Methods, it provides an alternate way in terms of syntax and semantics for creating an object repository for the web elements on a page.

It uses the concept of Lazy initialization. This is used to identify web elements only when they are used in any operation or activity.
Page Factory annotations:

- @FindBy: used to locate web elements using different locators strategies
- @FindBys: used to locate a web element with more than one search criteria, AND condition
- @FindAll: locates the web element using more than one criteria, given that at least one criteria match. OR condition
- @CacheLookUp: is very useful when you are referring to the same web element multiple times.

| Page Object Model | Page Factory |
| -- | -- |
| Finding web elements using By |Finding web elements using @FindBy|
|Does not provide lazy initialization| Does provides lazy initialization|

