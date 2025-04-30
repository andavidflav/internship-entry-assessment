# Programming Test

This test was composed to create a general overview of your knowledge regarding general programming and how it fits with the needs in our lab. Please try to answer all questions using your own knowledge and in your own words. If you get stuck on one of the exercises, still try to give a short answer.

---

## Exercise 1

### Task
Write a program in the language of your choice where:

1. The iteration number (starting from 1), followed by a random number between 1 and 100, is printed 100 times.
2. After every 5 iterations, write an additional separator (e.g., `---`).
3. Write “Lucky number!” after every random number that is divisible by 7.

### Solution:

import random

for i in range(1, 101):
    num = random.randint(1, 100)
    print(f"{i} {num}", end=" ")
    if num % 7 == 0:
        print("Lucky number!", end="")
    print() 
    if i % 5 == 0:
        print("---")

---

# Exercise 2

## 1. What is your understanding of the term “Design Patterns”?

Design patterns are reusable solutions to commonly occurring problems in software design.  
They provide a standard approach to solving coding challenges, improving maintainability and communication among developers.  
Instead of solving problems from scratch, design patterns help us apply proven methods that have been tested across many projects.

---

## 2. Explain the MVC Pattern

MVC stands for Model-View-Controller.

It is a software architectural pattern that separates an application into three main logical components:

- Model:  
  Manages the data, logic, and rules of the application. (Example: Databases, backend logic)

- View:  
  Represents the UI components and what the user sees. (Example: HTML pages, Mobile app screens)

- Controller:  
  Acts as a bridge between Model and View, handling user input and updating both accordingly. (Example: Button click handler)

Use Cases:
- Web Applications (Django, Ruby on Rails, Spring MVC)
- Mobile Applications (Flutter MVC, iOS apps)
- Desktop Applications where a clear separation of data and UI is needed

Simple flow:  
User action → Controller → Updates Model → View is refreshed.

---

## 3. List three other design patterns

### (a) Singleton Pattern
- Definition: Ensures a class has only one instance and provides a global access point to it.
- Use case: Managing database connections where only one connection is needed.

- Personal Experience:  
  I used Singleton Pattern in a college project where a centralized logging system was needed. This avoided multiple logger instances and ensured consistent log formatting.


### (b) Factory Pattern
- Definition: Provides a way to create objects without specifying the exact class of the object to be created.
- Use case: Building different types of users (Admin, Guest, Customer) dynamically.

- Personal Experience:  
  I applied the Factory Pattern in a web application to create different types of user profiles depending on their signup selection, without repeating code.

### (c) Observer Pattern
- Definition: Defines a one-to-many dependency between objects. When one object changes state, all its dependents are notified automatically.
- Use case: Notification systems, chat applications, live updates.

- Personal Experience:  
  I implemented the Observer Pattern in a group chat application, where when one user sent a message, all other users received real-time updates without refreshing the app.

## Exercise 3

### 1. Implementation Task  
   Based on the class diagram below, provide an implementation in any object-oriented programming language of your choice.
   
## Solution Code:

from abc import ABC, abstractmethod

class A(ABC):
    def __init__(self, name: str):
        self._name = name 

    @abstractmethod
    def PrintName(self):
        pass


class B(A):
    def __init__(self, name: str):
        super().__init__(name)

    def __PrintName(self, message: str): 
        print(f"B says: {message}")


class C(B):
    def __init__(self, name: str):
        super().__init__(name)

    def PrintName(self, message: str): 
        print(f"C says: {message}")


class D(A):
    def __init__(self, name: str):
        super().__init__(name)

    def PrintName(self):
        print(f"D's name is: {self._name}")



### 2. Key Questions  
   - Are you able to directly create a new instance of `ObjectA`? Please explain your answer. 
   ## Answer: 
      No, because `A` is an abstract class.  
      Abstract classes cannot be instantiated directly and must be extended by a subclass that implements the abstract methods.

   - Given an instance of `ObjectC`, are you able to call the method `PrintMessage` defined in `ObjectB`? Please explain your answer.  
   ## Answer:
      Yes, but with conditions.  
      `B` defines the method `PrintName` as private (indicated by `-` in the diagram).  
      In Python, this is typically implemented with double underscores (`__PrintName`).  
      Since it's private, `C` cannot directly call B's method unless it overrides it — which it does by defining its own public method `PrintName(message)`.

   - Try to explain as many key features of object-oriented programming as you can find in this example.
   ## Answer:                                                             
   Abstraction     - Class `A` is abstract and hides internal logic from users.
   Inheritance     - Class `B` inherits from `A`, and `C` inherits from `B`.
   Encapsulation   - Class `B` uses a private method `__PrintName`, hiding implementation.
   Polymorphism    - Class `C` overrides `PrintName` with its own implementation.
---

# Exercise 4

## 1. Working with Existing Code

To contribute effectively to an existing code base with minimal disruption:

- Understand the Architecture: I first explore the project structure, modules, and how data flows between them.
- Read Documentation: If available, I review the README, API docs, and internal wiki pages to get context.
- Start Small: I make small, non-breaking changes initially (like fixing typos, improving logs) to familiarize myself with the system.
- Use Debuggers & Logs: I use runtime debugging and logs to understand how key functions work in real-time.
- Follow Coding Style: I strictly follow existing naming conventions, formatting, and file structure.

## 2. Ensuring Maintainability

To keep the code base clean and maintainable:

- Follow SOLID Principles:
      Single Responsibility, Open-Closed, Interface Segregation, etc.
- Modular Design: I write code in small, testable modules or components.
- Consistent Naming: Clear, consistent naming for variables, functions, and classes.
- Use Version Control Properly: Small commits with descriptive messages, clear PRs.
- Write Unit Tests: I write tests for all new features or modules I introduce.
- Inline & External Documentation:
      I use clear inline comments and update Markdown/docs when needed.

## 3. Balancing Flexibility and Stability

To allow future changes without breaking existing functionality:

- Use Interface-Based Design: Code to interfaces, not implementations.
- Apply Design Patterns:
  - Strategy Pattern: To swap logic dynamically.
  - Factory Pattern: To manage object creation logic.
  - Adapter Pattern: To integrate legacy modules without changing them.
- Automated Testing:
  - Regression, unit, and integration testing to detect breakage.
- Code Reviews: I participate in peer reviews to ensure design quality and long-term impact.
- Documentation Updates: I update usage examples and technical references with every feature push.


