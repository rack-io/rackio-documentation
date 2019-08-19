
# Rackio: The Python Framework

<div class="admonition attention">
    <p class="first admonition-title">Attention</p>
    <p class="last">
        This Framework is still under development process, some features are still in test, use them with caution.
    </p>
</div>

## Rackio Framework
Rackio is a modern Python Framework for microboard automation and control applications development, it uses a declarative syntax to set your own applications in a bit.

It was developed to bring automation and control engineers the capability of developing high end industrial solutions. Inspired by [Django](https://google.com), [Flask](https://google.com) and [Scrapy](https://google.com), Rackio comes with built-in batteries to make common operations and tasks in the automation field.
You can fork the source right on [Github-Rackio Framework](https://github.com/rack-io/rackio-framework)
---

## Why Rackio?
Plain simple and honest, we'll there wasn't such a thing before, there is enough information out there in the Internet about how to do a data acquisition and actuation with Python, but too short about how to architect these systems, we built Rackio to solve common real problems found in the Industrial Field, so you can focus, as automation developer, more in the solution rather than the code to achieve your solution.

As we started designing automation systems ourselves, we found out that we needed a way to code applications in such a way that this code would be modular, reusable, maintainable and extensible. We where tired of those codes of infinite while loops, we wanted to create code to produce code in a organized way so that our job would be simplified.

And this way Rackio was born, as a Python Framework, a set of declarative constructs so you can code and configure your automation and control applications, we want to build a culture of code the same way Django does for web applications and Scrapy for web scraping, Rackio is inspired on these Frameworks among others and it's improving each day.

## What can you do with Rackio?

With Rackio you can build complex and advanced automation and control architectures deployable in any pc-based controller that can run Python. Rackio enables the capability of defining sytems and subsystems that can perform tasks and operation in concurrency, appropiate features can handle integration within these systems, so you can deliver high end solutions to your automation and control problems.

## So, where is the HMI?

Rackio doesn't come with a default HMI, since it is a server application framework, it comes with an API so you can connect your custom HMI developed in any technology you want. On the other hand, Rackio comes with an Admin Web Interface (inspired by Django), so you can monitor and set Tags value, Trends, Alarms, Events and much more.

## Requirements

- Python 3.6+
- falcon 
- pyBigParser
- peewee
- python-statemachine

# Installation

```
pip install Rackio
```
---

## Built-In Batteries

Rackio comes with some built-in features that .
Rackio comes with some out of the box that features let you start creating rapid and fast coding prototypes and Rackio ppplications, here is a list of these features:

* Tag based engine
* Custom Models Definitions
* Controls and Math Operations
* State Machine Definitions
* Custom Observers
* Custom Continous Tasks
* Trend based Logging
* Automatic Data Logging 
* Event History
* Alarm Management System
* RESTful API
* Web Based Admin

Each of these features are presented as declarative classes so you can define how your application will behave and interact with-in its own internals.

---

## Custom Observers

Most of the core functionalities of Rackio are based on the Observer Pattern, in which tags are observed for new changes, after these chages some operations are made. You can define your own Custom Oberserver functions, in which it is required to be executed after a new value for a tag has occured, this can be used for those tasks or commands that the Rackio math parser can not handle, like some Neural Network evaluation.

---

## Trend based Logging

Some variables or tags are required to be monitored in time, with Rackio can perform some automatic data logging for trends and historical display, you can set the tags and their frequency and Rackio will save these in a local database.

---

## Automatic Data Logging

<div class="admonition note">
    <p class="first admonition-title">Note</p>
    <p class="last">
        This feature is under development process
    </p>
</div>

Tag values can be save to a local database for the next restart of the application in this way you can preserve the state of your automation applications.

---

## Event History

<div class="admonition note">
    <p class="first admonition-title">Note</p>
    <p class="last">
        This feature is under development process
    </p>
</div>

Using the same local database, Rackio holds a register of all of the events occured in the application, you can use this feature to add custom events to the history.

---

## RESTful API

<div class="admonition note">
    <p class="first admonition-title">Note</p>
    <p class="last">
        This feature is under development process
    </p>
</div>

Rackio is focuses on new trend technologies and promotes web development for automation applications, all of the Rackio Features can be access by using the RESTful API, being Rackio a service or backend application, you can define your custom views or HMI with other front-end technologies.

---

## Web Based Admin

Rackio comes with its own basic web admin system, in which you can monitor tags values, controls definitions, state-machine transitions, trends, logged data and alarms.

---

# Support

You can ask questions and join the development discussion: