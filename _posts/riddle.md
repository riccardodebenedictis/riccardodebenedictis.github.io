---
layout: post
title: A brief introduction to the RiDDLe language
---

In programming, a non-procedural language is one that doesn't require the programmer to outline the specific steps the computer needs to take to solve a task. Instead, these languages put an emphasis on defining the desired result or outcome of the program, rather than the steps to achieve it. By providing higher-level abstractions, non-procedural languages allow the programmer to concentrate on the problem at hand instead of technical details. One example of a non-procedural language is [RiDDLe](https://github.com/ratioSolver/RiDDLe), a dialect of C++ that enables the definition of problems related to semantic, logical, mathematical and causal reasoning. Unlike traditional programming languages, RiDDLe allows for the declaration of variables of various types, with the solver determining the values based on constraints defined using logical operators and relationships. The solver will then find the values that meet the constraints.

A nice example, to show the potential of this language, is the following. We have a duck, a dog and a cat. We know for each pair of these animals, its weight. Specifically, we know that the duck and the cat together weigh 10 kilos. The duck and the dog together weigh 20 kilos. While the dog and the cat together weigh 24 kilos. The problem asks for the combined weight of the three animals.

<figure class="figure" class="text-center">
  <img src="{{site.url}}/figures/introduction_to_riddle/weight_puzzle" class="figure-img img-fluid rounded" alt="...">
  <figcaption class="figure-caption">A duck, a dog and a cat. Given the weight of each pair of animals, determine the total weight of the three animals.</figcaption>
</figure>

This problem can be formulated, in RiDDLe, as follows:

```riddle
real duck;
real dog;
real cat;

duck + cat == 10;
duck + dog == 20;
dog + cat == 24;
```

As can be seen, the formulation of the problem is very simple and intuitive. The first three lines declare the variables that will be used to represent the weight of the duck, the dog and the cat. The last three lines define the constraints that the solver needs to satisfy. The solver will then find the values, for each variable, that meet the constraints. In this case, the duck weighs 3 kilos, the dog weighs 17 kilos and the cat weighs 7 kilos. The total weight of the three animals is hence 27 kilos.

Besides the definition of mathematical constraints, RiDDLe allows the definition of logical constraints. Consider a scenario where you have three light switches and three light bulbs. Each switch can be in either an "on" or "off" state, and each light bulb can be either "lit" or "unlit." You need to find a combination of switch states such that exactly two light bulbs are lit.

The problem can be formulated, in RiDDLe, as follows:

```riddle
bool x1;
bool x2;
bool x3;

x1 | x2 | x3;
!x1 | !x2 | x3;
x1 | !x2 | !x3;
```

Specifically, we have three light switches, x1, x2, and x3. The goal is to find an assignment of values to x1, x2, and x3 such that exactly two light bulbs are lit. The set of constraints represents all the possible combinations of switch states that result in exactly two light bulbs being lit. The solver will then find a solution (i.e., the values of x1, x2, and x3) that satisfy all the constraints.

## Primitive and Composite Types

RiDDLe supports the declaration of variables of various types. The following primitive types are supported: boolean, integer, real, string, and enums (i.e., a type that can take on one of a finite number of values). As an object-oriented language, RiDDLe also supports the declaration of composite types, i.e., types that are defined in terms of other types. We can, for example, define a type that represents a point in a two-dimensional space:

```riddle
class Point {
  real x;
  real y;
};
```

The above declaration defines a new type, `Point`, that has two fields, x and y, of type real. We can then declare a variable of type `Point`:

```riddle
Point p = new Point();
```

The above declaration creates a new instance of the `Point` type and assigns it to the variable p. We can then access the fields of the `Point` instance using the dot operator. It is worth noticing that the fields of a `Point` instance are variables which, as other variables, can be constrained. For example, we can constrain the fields of the `Point` instance to have the values 1 and 2, respectively:

```riddle
p.x == 1;
p.y == 2;
```

Composite types can also be instantiated as existential variables. For example, we can declare a variable of type `Point` that can take on any value among the previously defined points:

```riddle
Point p1 = new Point();
Point p2 = new Point();
Point p3 = new Point();

Point p;
```

The above declaration creates three instances of the `Point` type and assigns them to the variables p1, p2, and p3. The last line declares a variable of type `Point` that can take on any value among the previously defined points.

## Predicates

The real power of the RiDDLe language, however, manifests itself from the moment you start using predicates. Predicates allow the programmer to express complex constraints and relationships between variables, making it possible to solve more complex problems than what is possible with just variables and basic logical operators. Predicates provide a higher-level abstraction, allowing the programmer to focus on the problem domain and the relationships between variables, rather than on the technical details of how the problem will be solved.

## Conclusion

RiDDLe is a very powerful language that can be used to solve a wide range of problems. It is also very easy to use. A solver that can be used to solve problems formulated in RiDDLe can be downloaded from [here](https://github.com/ratioSolver/oRatio).