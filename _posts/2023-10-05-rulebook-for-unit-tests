---
title: "Rules and best practices for writing unit tests"
date: 2023-10-05
author: "Ramaraj T"
tags: [general, c#]
---

 - Test One Thing at a Time

    Each unit test should focus on testing a single piece of functionality. Do not test multiple functionalities in a single unit test
    
    **Thumb rule:** One assert per test
 - Follow Arrange-Act-Assert (AAA) Pattern

    Arrange - Setup mock data objects, create objects, environment, define input
    
    Act - Call a public method you want to test
    
    Assert - Verify the expected output (Asserts doesn't have to be an output all the time. You can verify if a method in a mock object is called)
 - Isolate Dependencies
    
    Always mock the data, use any mocking framework. Real API calls, DB access, file access should be avoided
 - Use a framework for dependency injection
    
    Use any IOC container/dependency injection framework and register the app's dependency with that. Do not create the dependencies manually. Use the scope provided by the IOC container (Singleton, Transient...). This allows using different scopes for application and different scope for unit test
 - Follow MVVM
    Strictly follow the MVVM design pattern. Keep the code in their respective places. 
    
    **Thumb rule:** Have the platform namespaces only in the View. For e.g namespaces like Xamarin.Forms, Android.App should not be in ViewModel and the Model

    - Unit test should not test the View
    - Modal doesn't (shouldn't) have anything to test
    - Focus on ViewModel

 - Test Edge Cases
    
    Test all exceptional scenarios and edge cases that cannot be covered in black box testing. Do not just test the happy path. For e.g, in an app you might not be seeing the Delete button for a ViewOnly user. But test how the ViewModel handles the Delete method if a ViewOnly user initiates it.

    Not only try to bring the code coverage to a certain goal, but also try to assert each and every line in the ViewModel. If a class have 100% code coverage, then changing one line should fail at least one unit test

    You should try to test the entire spectrum of inputs and possibilities.

 - Keep tests independent

    The unit tests typically run in parallel. So one unit test should not rely on another unit test to function. For eg, you cannot expect to run the Login unit test before the FetchProjects unit test.

 - Minimize the use of Singleton
    
    Singletons are hard to test. Even if you have to use a singleton, use the IOC container's scope to create them. Do not create the singleton object manually.
 - Make use of Parameterized test
    
    When you can pass different type of inputs to a unit test, rather than writing duplicate unit test, use the parameterized unit test
 - Avoid using hard coded test data
    
    Avoid hardcoded test data as your unit test might pass for your hard coded test data but might fail if you use some random data. Use a test data creation framework like AutoFixture
 - Focus only on the public methods and properties of a class

    Write unit tests such that it targets the public methods and properties of a class. When you call a public method of the target class, it should either do a state change (like change it’s public member, or change a global variable…) or it might trigger a method in another class (which should be a mockable)
 - Do not worry about the private members of the class. 
    
    Interfaces everywhere

    Create interfaces wherever possible. Interfaces give a clear picture of what the class intends to do. You can also create mock objects for interfaces in the unit tests.

 - Use wrapper classes if needed
    
    We cannot create interfaces all the time. For e.g if you are using a library which exposes a class, we cannot create an interface for that class. For that, you can create your own wrapper class and wrap the functionality of the class from the library.

    This is applicable for the platform classes too. For e.g classes like DeviceInfo, MainThread are Xamarin classes which will not be exposed to the unit test. So create a wrapper class for them.
    
    You can also create wrapper classes for Time sensitive tasks (like testing a timer that runs for every 5 seconds, or if a state change happens only for certain period of time or date)
