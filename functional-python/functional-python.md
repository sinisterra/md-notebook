# Functional Python

[TOC]

## Chapter 1: Understanding functional programming

- expressions + evaluation, encapsulated in function definitions
- avoids state change and mutable objects
- expressiveness
- Python offers some functional tools
- Solutions are focused on EDA (Exploratory data analysis)

## Identifying a paradigm

- functional vs imperative (in the context of state)
- imperative paradigm: statements advance the computation of a state. the final state is described and then the preconditions (statements) are defined to make it work
- functional paradigm: relies on composition. Low-level functions are defined, then composed to make complex statements. Succint, expressive and efficient.

### Python functional hybrid paradigm

- applications will be functions, until objects are reached
- the runtime environment is supported by objects, until libraries are reached
- Python stands on libraries

### Exploratory data analysis

- Data preparation: extraction and transformation for source apps
- Data exploration: statistical functions
- Data modelling and machine learning
- Evaluation and comparison: deciding on model alternatives

------

## Chapter 2: Essential functional concepts

- First-class and higher-order functions (pure functions)
- Immutable data
- strict and non-strict evaluation (eager vs lazy)
- recursion instead of explicit loops
- functional type systems

### First-class functions

- created with `def` and `lambda`
- functions are first-class objects that can be manipulated just as all other objects

### Pure functions

- expressiveness comes from the lack of side effects
- allow optimizations by changing evaluation order
- easier to understand (the same input always delivers the same output)

### Immutable data

- use of tuples and named tuples
- not many classes
- wrapper pattern: 
  - higher-order function
  - wrap-process-unwrap (fst, snd) functions

### Strict and non-strict evaluation

- deferring a computation
- generator expressions and functions are lazy: `range` expressions

### Functional type systems

- strict type systems could be seen as a workaround for a dynamic type system
- python has type hints through tools such as mypy or pylint

### Familiar territory

- When doing API design, there are several paradigms:
  - suffix notation: `object.do_something().then_that()`
  - prefix notation: `then_that(do_something(obj))`
- Functional paradigms favor prefix notation

### Learning some advanced concepts

- Referential transparency: handling multiple routes to a result that might not be optimized properly because there is no compiler
- currying: reducing multi-argument functions to single-argument ones
- monads: building sequential, flexible pipelines.

### Summary

- first-class & higher-order functions: functions as arguments and output of other functions
- immutability: mutable cases might be more difficult to reason about
- strict evaluation
- recursion: hand-optimizations are required in Python
- type system: rely on Python's dynamic type system

## Chapter 3: Functions, Iterators and Generators

Introduction to several Python functions that are important for a functional perspective.

* Pure functions
* Functions as objects
* use of Python strings
* tuples & namedtuples
* iterable collections

Generator examples for:

* conversions
* restructuring
* complex calculations

### Writing pure functions

```python
def m(n: int) -> int:
    return 2 ** n - 1 
```

* The return value depends only on the input.
* No mutations

Balancing python's statefulness with functional  programming is possible.

Code should avoid using global objects, such as files or database connections.

Use `with` keyword when working with files in python.

### Functions as first-class objects

* functions can be assigned to variables
* can be used as arguments
* can be returned by other functions
* These techniques can be used to create higher-order functions

#### Strategy design patterns

* Depends on other objects to provide parts on an algorithm.
* On `__init__` , the object takes a `Callable` (a function)

An example:

```python
from typing import Callable

# A nice example of a Strategy design pattern
class Mersenne1:
	def __init__(self, algorithm: Callable[[int], [int]]) -> None:
        self.pow2 = algorithm
    def __call__(self, arg: int) -> int:
        # here it uses the callable passed on __init__
        return self.pow2(arg) - 1
```

Then, define some algorithms to pass to the strategy:

```python
def shifty(b: int) -> int:
    return 1 << b

def faster(b: int) -> int:
    if b == 0: return 1
    if b % 2 == 1: return 2 * faster(b - 1)
    t = faster(b // 2)
    return t * t
```

Create your strategies:

```python
m1s = Mersenn1(shifty)
m1f = Mersenne1(faster)
```

