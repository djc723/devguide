---
layout: page
title: Managing Code Complexity
section: developer-guide
permalink: /development-practices/managing-code-complexity/
---

### Status: Final Draft

## Introduction

Code complexity is an important issue to take into account during development to prevent technical debt from accruing and development slowing down. Unmanaged complexity leads to less structured code that puts an unnecessary burden on the developer’s mind. The [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)) principles promote an understandable and maintainable software design.

## Different types of complexity metrics

### [Cyclomatic complexity](https://en.wikipedia.org/wiki/Cyclomatic_complexity)

* Code structure

* Based purely on the execution flow (branches of execution in a function)

* Promotes splitting large functions into smaller, more manageable ones

* Any function with a cyclomatic complexity below 10 can be considered simple and testable while a cyclomatic complexity greater than 20 indicates an overly complex function, so an acceptance threshold for functions should be defined between 10 and 20, depending on the application domain.

    * Some applications and programming languages are inherently more manageable with higher cyclomatic complexity, so the exact threshold can vary from one application to another.

### [Cognitive complexity](http://redirect.sonarsource.com/doc/cognitive-complexity.html)

* Human understandability

* Based on code structure as well as cognitive factors in the code

    * E.g. takes into account recursive calls and ignores shorthand expressions when forming a cognitive complexity score

* How easy or difficult it is for a human being to understand the purpose and behavior of a piece of code

* Promotes reducing the amount of processing the developer has to do while reading the code

* SonarQube defines a cognitive complexity of 15 as the default threshold for functions. This is a good starting point.

### Depth of Inheritance

* It becomes less clear where an inherited method originates from when the number of levels in the inheritance tree grows. Consider composition over inheritance.

### Class coupling

* The number of unique interdependencies between classes can be used to identify classes that have high coupling. These classes might be a burden to reuse if they need developers to also include all the dependent classes.

### Lines of code in functions, classes and files

* Long functions might have multiple behaviors that should be separated into their own functions. The purpose becomes unclear when a function does many things. If the function does not fit on one screen, consider splitting it up.

* Large classes run the risk of becoming all-encompassing facades for a multitude of logical entities. A class should have a [single responsibility](https://en.wikipedia.org/wiki/Single_responsibility_principle).

* Long files make it difficult to find the required sections of code. This ties into the problem with too long classes, where a file contains so many features that it becomes a burden on the developer’s memory. A good rule of thumb is to have one class per file.

## Tools for enforcing complexity limits

* **Code reviews are the recommended way of manually assessing code complexity**

    * More of a fuzzy check since this is entirely subjective to the reviewer

    * Should answer the question ‘Is the code under review readable enough and understandable by other developers?’

* **SonarQube is the recommended automated tool for enforcing complexity limits**

    * Automatic rule sets for identifying both cognitive and cyclomatic complexity

    * There are several built-in rules in the Sonar analyzers for handling complexity on expression, function and class levels in supported languages. Just do a search in Sonar for all rules containing the string "complexity" and having the tag “brain-overload” to find all the relevant rules. “Brain-overload” is a tag for rules concerned with clarity and readability and there are many other rules to enforce clearer code in addition to those concerned with calculated complexity.