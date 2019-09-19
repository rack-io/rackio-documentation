# Controls and Math Operations

*Controls* and *Rules* enable to perform some *Actions* on tag values, based on met *Conditions*. These tools allow you to build math driven automation tasks.

## Controls

A Rackio `Control` is defined by a Rackio `Condition` and a Rackio `Action`.

```python
from rackio.controls import Control
```

## Rules

A Rackio `Rule` works the same way as a Rackio Control but it can handle multiple actions with a single condition.

```python
from rackio.controls import Rule
```

So in order to define a `Control` or a `Rule`, we must define some conditions and actions ahead.

## Conditions

You can set some conditions based on the tag values and between tag values, typical comparison expressions like `>=`, `==` or even use logical expressions like `and` and `or`.

### Comparison Operators

```python
from rackio.controls import Condition

# Conditions definitions

condition1 = Condition("T1",">=", "T2")
condition2 = Condition("T1","<", "T2")
```

Where T1 and T2, are tags already defined in Rackio. Evaluating these conditions will return `True` or `False`.

### Logical Operators

```python
from rackio.controls import OrCondition, AndCondition

# Conditions definitions

condition1 = Condition("T1",">=", "T2")
condition2 = Condition("T1","<", "T2")

condition3 = OrCondition([condition1, condition2])
condition4 = AndCondition([condition1, condition2])
```

## Actions

Actions are the final step once a condition from a control or rule is met, you can choose between `ValueAction` or a `MathAction`. the first one takes a defined value and assigns to a defined tag, and the last one, can perform a mathematical expression on a tag value, this mathematical expression can contain other tags names and some math functions like `exp` or `sin`.

```python
from rackio.controls import ValueAction, MathAction

action1 = ValueAction("T3", 40)
action2 = MathAction("T3", "T1 + T2")
```

## Putting all together

Finally once you have defined conditions and actions, you can define your controls or rules.

```python
from rackio.controls import Control, Rule

control1 = Control("C1", condition1, action1)
rule1 = Rule("R1", condition2, [action1, action2])
```
You have to define your controls and rules with a string name, so you can query then the control manager for any control or rule based on this defined name.

## Control Manager

In order for Rackio to execute these controls and rules, they must be registered in the `ControlManager`.

```python
from rackio import Rackio

app = Rackio()

app.append_control(control1)
app.append_rule(rule1)

```

Once you execute your "app", the ControlWorker will handle all defined controls and rules in set time interval of 0.1 seconds.

---