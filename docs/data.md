# Tag Based Engine

## Introduction

This is the main data repository of a Rackio application, you can set a list of tag definitions so they can be available in any process of the application, they are based on industrial standard tag systems, in which variables, parameters, information and data are assigned tag names for proper identification, e.g. `TEMP1`. Prior to you development process, in your design phase you must have a complete list of tag names, for all those tags that are involved in the application.

## Tags definitions

Tags are unique identifiers for a data point within your application, it is used to receive or send data in a acquisition process or to read or write data in an inner Rackio process, this way you can share data resources between modules and componentes in your application.

The tags data types can be set between *Float*, *Integer*, *Boolean* or *string*, which are the default data types. 

```python

tag_engine.set_tag("RAND1", "float")
tag_engine.set_tag("RAND2", "float")
tag_engine.set_tag("T1", "float")
tag_engine.set_tag("T2", "float")
tag_engine.set_tag("T3", "float")
```

---

## Custom Models

High end applications require data types more complex that the default data types. With Rackio you can define your own custom models for tag definitions in which attributes can be a custom combination of the default data types. In this way you can access custom tags by name or access custom tag properties, e.g. `Controller1.Set_Point` by using dot notation.

---