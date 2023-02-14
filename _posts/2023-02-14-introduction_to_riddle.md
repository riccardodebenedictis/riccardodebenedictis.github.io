---
layout: post
title: A brief introduction to the RiDDLe language
---

In programming, a non-procedural language is one that doesn't require the programmer to outline the specific steps the computer needs to take to solve a task. Instead, these languages put an emphasis on defining the desired result or outcome of the program, rather than the steps to achieve it. By providing higher-level abstractions, non-procedural languages allow the programmer to concentrate on the problem at hand instead of technical details. One example of a non-procedural language is [RiDDLe](https://github.com/ratioSolver/RiDDLe), a dialect of C++ that enables the definition of problems related to semantic, logical, mathematical and causal reasoning. Unlike traditional programming languages, RiDDLe allows for the declaration of variables of various types, with the solver determining the values based on constraints defined using logical operators and relationships. The solver will then find the values that meet the constraints.

A nice example, to show the potential of this language, is the following. We have a duck, a dog and a cat. We know for each pair of these animals, its weight. Specifically, we know that the duck and the cat together weigh 10 kilos. The duck and the dog together weigh 20 kilos. While the dog and the cat together weigh 24 kilos. The problem asks for the combined weight of the three animals.

<figure class="figure" class="text-center">
  <img src="{{site.url}}/figures/2023-02-14-introduction_to_riddle/weight_puzzle.png" class="figure-img img-fluid rounded" alt="...">
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

As can be seen, the formulation of the problem is very simple and intuitive. The first three lines declare the variables that will be used to represent the weight of the duck, the dog and the cat. The last three lines define the constraints that the solver needs to satisfy. The solver will then find the values, for each variable, that meet the constraints. In this case, the solver will easily find that the duck weighs 3 kilos, the dog weighs 17 kilos and the cat weighs 7 kilos. The total weight of the three animals is hence 27 kilos.

The above example only showcases the solver solving a set of linear equations. The true potential of the RiDDLe language comes into play when using [predicates](https://github.com/ratioSolver/RiDDLe/wiki/Predicates). Predicates allow for the expression of intricate constraints and relationships between variables, enabling the solution of complex problems beyond what is achievable with variables and basic logical operators alone. Predicates offer a higher level of abstraction, letting the programmer concentrate on the problem's nature and the relationships between variables, instead of being concerned with the technical aspects of solving the problem.

## Conclusion

RiDDLe is a very powerful language that can be used to solve a wide range of problems. It is also very easy to use. A solver that can be used to solve problems formulated in RiDDLe can be downloaded from [here](https://github.com/ratioSolver/oRatio). In a future post, I will show how to use operators and how to define composite types in the RiDDLe language. I will also show how to use predicates to express and solve more complex problems.