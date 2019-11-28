## State Machine Definitions

According to the Wikipedia, a state machine has the following definition:

> A finite-state machine (FSM) or finite-state automaton (FSA, plural: automata), finite automaton, or simply a state machine, is a mathematical model of computation. It is an abstract machine that can be in exactly one of a finite number of states at any given time. The FSM can change from one state to another in response to some external inputs; the change from one state to another is called a transition. An FSM is defined by a list of its states, its initial state, and the conditions for each transition. 
>
> -- [Finite-state machine](https://en.wikipedia.org/wiki/Finite-state_machine)

State Machines are widely used in the automation field, this is a concept in which you can define a system that is continuously transitioning between states in order to perform some tasks or operations, in a automated or semiautomated way.

With Rackio you can use a declarative approach to define your custom state machines.

---

## Working with State Machines

Let's say you want to code a two steps state machine, you can use *Rackio* and use the following syntax:

```python
import logging
from rackio import RackioStateMachine, State


class TwoStep(RackioStateMachine):

    # states

    state1  = State('State1', initial=True)
    state2  = State('State2')

    # transitions
    
    forward = state1.to(state2)
    back = state2.to(state1)

    # parameters

    count = 0

    def on_back(self):

        self.count = 0

    def while_state1(self):

        self.count += 1

        logging.warning("{}: {}".format(self.name, self.count))
        if self.count == 5:
            self.forward()

    def while_state2(self):

        self.count += 1

        logging.warning("{}: {}".format(self.name, self.count))
        if self.count >= 10:
            self.back()
```

The `RackioStateMachine` class is the based class for building state machines, you will have to inherit to define your own custom state machines. The `State` class will define each of the states defined for your custom state machine, the `initial` argument must be set to `true` to set the first initial state for each instance of this machine class once `rackio` is up and running.

The transitions between each defined state must be linked using the `to` method of each state, and must be assigned to a class attribute. So this state machine class will have the states `state1` and `state2`, and will have the following transitions `forward` and `back`.

You can define custom behaviour for your state machine while remaining on a single state, or on a transition (changing from one state to another), for this purpose you must define methods for this class using the `while_` and `on_` syntax for the method names respectively.

Once you have defined your state machine, you can create instances of this class and attach it to the rackio engine for continous execution.

```python
app = Rackio()

machine1 = TwoStep("machine 1")
machine2 = TwoStep("machine 2")

app.append_machine(machine1, 1)
app.append_machine(machine2, 2)

if __name__ == "__main__":

    app.set_log(file="app.log")
    app.run()
```

Using the method `append_machine` you will register a new state machine as plugin to be executed by the rackio engine, the second parameter is the machine execution time in seconds, meaning that this machine will be executed each *n* seconds as time interval.

In the log file you see information about the execution of the state machines, and you will find also details about any execution error found.

## Reserved attributes

In order to use other features of the framework, the `RackioStateMachine` comes with three class attributes for module interaction. You can make use of them using the following syntax.

```python
class TwoStep(RackioStateMachine):

    def while_some_state(self):
        
        tag_engine = self.tag_engine
        logger_engine = self.logger_engine
        query_logger = self.query_logger
```

The `tag_engine` is an instance of the tag data engine, you can use it to read or write tags, this way you can perform transitions from another rackio process or even better control the execution of another rackio process.

The `logger_engine` can be used to log tags values or any other custom structure.

The `query_logger` can be used for querying already saved trends, signals or waveforms, and even trends history.