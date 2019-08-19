# Tag Based Engine

## Introduction

This is the main data repository of a Rackio application, you can set a list of tag definitions so they can be available in any process of the application, they are based on industrial standard tag systems, in which variables, parameters, information and data are assigned tag names for proper identification, e.g. `TEMP1`. Prior to you development process, in your design phase you must have a complete list of tag names, for all those tags that are involved in the application.

The tags data types can be set between *Float*, *Integer*, *Boolean* or *String*, which are the default data types. 

---

## Custom Models

High end applications require data types more complex that the default data types. With Rackio you can define your own custom models for tag definitions in wich attributes can be a custom combination of the default data types. In this way you can access custom tags by name or access custom tag properties, e.g. `Controller1.Set_Point` by using dot notation.

---