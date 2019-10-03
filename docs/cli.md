
# Getting Started

You can start coding with Rackio fast and simple, having Python 3 installed you can install Rackio with `pip`.

# Installation

```
pip install Rackio
```

## Requirements

- Python 3.6+
- falcon 
- pyBigParser
- peewee
- python-statemachine

These requirements are installed automatically.

---

## Basic Setup

You can start developing with Rackio by just import two things.


```python
from rackio import Rackio, TagEngine

app = Rackio()
tag_engine = TagEngine()
```

## Tags definitions

These are two on the main core components of Rackio. With these you can define tags before running your app.

```python

tag_engine.set_tag("RAND1", "float")
tag_engine.set_tag("RAND2", "float")
tag_engine.set_tag("T1", "float")
tag_engine.set_tag("T2", "float")
tag_engine.set_tag("T3", "float")

if __name__ == "__main__":

    app.run()
```

Tags are unique identifiers for a data point within your application, it is used to receive or send data in a acquisition process or to read or write data in an inner Rackio process, this way you can share data resources between modules and componentes in your application.