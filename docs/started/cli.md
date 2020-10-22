
# Getting Started

You can start coding with Rackio fast and simple, having Python 3 installed you can install Rackio with `pip`.

## Installation

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

if __name__ == "__main__":

    app.run()
```

These are two of the main core components of Rackio. With these you can define tags before running your app.

A `Rackio` instance works as a singleton, so you can define and set your application in diferent modules of your application, the same behaviour for a `TagEngine` instance so you can read and write tags in each part of your application.