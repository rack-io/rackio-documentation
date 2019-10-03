## Custom Continuous Tasks

In some cases State Machines is not enough and you need to perform some complex continuous task in a specified frequency, e.g. a data acquisition process, with Rackio you can use decorators that allow you to register a function definition as a Rackio plugging. Once your application is up an running these continuous tasks will start working until the end of times.

---

## Continous Tasks

### Rack It!!!

Rackio can be extended to add custom continous tasks and operations

```python
@app.rackit(1)
def writer1():

    tag_engine.write_tag("T1", 15)
    tag_engine.write_tag("T2", 40)

    direction = 1

    while True:

        time.sleep(0.5)

        value = 24 + 2 * random()
        tag_engine.write_tag("RAND1", value)

        T1 = tag_engine.read_tag("T1")
        T1 += direction

        tag_engine.write_tag("T1", T1)

        if T1 >= 60:
            direction *= -1

        if T1 <= 5:
            direction *= -1
```

### Rack It On!!!

You can register a defined function as a continous task to be perform by Rackio. You can also provide functions as list of instructions.

```python
@app.rackit_on(period=1)
def reader():

    rand1 = tag_engine.read_tag("RAND1")
    rand2 = tag_engine.read_tag("RAND2")
    T1 = tag_engine.read_tag("T1")
    T2 = tag_engine.read_tag("T2")
    T3 = tag_engine.read_tag("T3")
        
    print("")
    print("RAND1: {}".format(rand1))
    print("RAND2: {}".format(rand2))
    print("T1   : {}".format(T1))
    print("T2   : {}".format(T2))
    print("T3   : {}".format(T3))
```

By specify its ```period```, you can keep control of the time execution for these tasks.

The main difference between ```rackit``` and ```rackit_on``` is that the first, executes only one, if you define a ```while True``` inside this functions, the execution continues in an isolated thread.

