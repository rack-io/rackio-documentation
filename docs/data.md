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

```python
from rackio import Rackio, TagEngine
from rackio.models import Model, FloatField, IntegerField, BooleanField


class Car(Model):

    engine_size = FloatField(default=1.8)
    seats = IntegerField(default=5)
    air_conditioning = BooleanField(default=True)
    mileage = FloatField(default=0.0)

    def drive(self):

        self.mileage += 0.5

if __name__ == "__main__":

    tag_engine = TagEngine()

    new_car = Car(engine_size=2.2)

    tag_engine.set_tag("car1", Car)
    tag_engine.write_tag("car1", new_car)

    new_car.drive()

    tag_engine.write_tag("car1", new_car)
```

You can define your models with custom parameters and custom methods, so you can abstract and encapsulate object behaviour, and save these in tags.


---