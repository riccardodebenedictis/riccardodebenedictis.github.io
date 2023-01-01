---
layout: post
title: Divide et Impera
---

The old Latin phrase of [Divide et Impera](https://en.wikipedia.org/wiki/Divide_and_rule) is often used in Computer Science to simplify complex systems by breaking them down into simpler subsystems. It is therefore time to apply it to the [oRatio](https://github.com/pstlab/oRatio) solver, whose subcomponents are already divided into libraries, but are all kept in the same repository, making them difficult to be used by external components. For this reason I decided to create a new [organization](https://github.com/ratioSolver), fully dedicated to the solver, which will allow to host the different components within their respective repositories.

The current component organization of *oRatio*, in particular, is schematized in the following figure. As you can see, the components are varied and, more importantly, many of them can be used for different purposes. It is therefore inconvenient for users to have to download them all in order to use only a few of them.

<figure class="figure" class="text-center">
  <img src="{{site.url}}/figures/2022-07-20-divide_et_impera/oRatioComponents.png" class="figure-img img-fluid rounded" alt="...">
  <figcaption class="figure-caption">Different components of the oRatio framework.</figcaption>
</figure>

What would happen if you wanted to use the SMT constraint network to solve a different type of problem from those that *oRatio* is able to solve? What if we wanted to create a new solver capable of solving the same kind of problems without making use of the SMT technology? For these, and for other reasons, assigning each component its own repository would ensure greater agility in implementation. Let's see in a little more detail what services the different components provide.

### SeMiTONE

At the lowest abstraction level, in particular, there is the **SeMiTONE** (Satisfiability Module TheOries NEtwork) library which, nomen omen, offers, from an [SMT](https://en.wikipedia.org/wiki/Satisfiability_modulo_theories) perspective, services equivalent to those that a constraint-network offers for a [CSP](https://en.wikipedia.org/wiki/Constraint_satisfaction_problem) solver.

Based on [MiniSat](http://minisat.se), this library allows the definition and propagation of different types of constraints depending on the implemented *theories*. At the moment a *Linear Real Arithmetic (LRA)* theory is implemented, for the management of linear constraints between real variables. In addition, a *Difference Logic (DL)* theory is also available. This theory, implemented on both reals and integers, is able to impose disjunctive temporal constraints as in a disjunctive temporal network \[[1](#r1)\]. An *Object Variable (OV)* theory allows to define (in) equality constraints between object variables. Finally, the MiniSat-based core allows for the imposition of classical propositional constraints.

It is worth noting that, as in any constraint-network, *SeMiTONE* is unable to solve constraint problems defined on the underlying theories. Problem solving, in particular, is entrusted to an external solver who, being aware of the types of problems that he has to solve, can exploit its own heuristics. *SeMiTONE*, nonetheless, allows the propagation of the solvers' choices, assigning to variables values which are consistent with the current choices. In case of inconsistencies, furthermore, *SeMiTONE* analyzes the conflicting choices, generates a *no-good*, backtracks to the first useful branch ([backjumping](https://en.wikipedia.org/wiki/Backjumping)) and adds the learnt no-good as a new constraint, thus avoiding that, in a subsequent moment of the search, the same problem occurs in another branch of the search tree.

### RiDDLe

The second fundamental component is the **RiDDLe** (Rational Domain Definition Language) language parser. The *RiDDLe* language takes inspiration from the DDL.1 language \[[2](#r2)\]. The current proposal, however, introduces a pure object-oriented approach to the definition of timeline-based domains and problem definitions and, therefore, allows an higher decomposition of the domain model and an increase of modularity with a consequent reduction of the the overall complexity at design phase. Furthermore, thanks to the object-oriented approach, UML modeling features can be naturally exploited to enhance the design phase. In addition, aspects related to first order logic are further made explicit, allowing a uniform representation of planning and scheduling concepts. Finally, although the language is based on a multi-sorted first order logic core, from which the object-oriented approach comes, it has been designed for allowing extensibility and is, hence, agnostic of complex types such as state-variables or resources.

This component, specifically, allows solvers, with a minimum of implementation effort, to parse the *RiDDLe* language.

### The core

The **core** is a component that allows the management of the objects within the logical environment described by the *RiDDLe* language. This component provides the high-level functions to handle complex *RiDDLe* *types*, *methods*, *constructors*, creating new objects, etc. In other words, it provides high-level services for the management of the logical environment, relieving the solvers who use it of the burden of their management.

Should you intend to develop a new solver, this component greatly simplifies the task, allowing to focus solely on the search and heuristics aspects.

### The solver

The **solver** component is the one that actually deals with the concrete resolution of the semantic-causal problem described in the *RiDDLe* language. This component deals with the creation and management of *flaws* and *resolvers*, their relationships, how they define a *causal graph* and how the topology of this graph can be used to define *heuristics* that suggest the best flaw to solve. with the best resolver \[[3](#r3)\].

### The executor

Once the semantic-causal problem has been solved, it must be carried out. The **executor** takes care of managing this task. Through the [callback](https://en.wikipedia.org/wiki/Callback_(computer_programming)) functions, in particular, the user of the *executor* is notified, in due time, of the various tasks to be performed.

The task of the executor, however, is not limited to a mere dispatching of the different planned tasks to be performed at scheduled time. In fact, the executor is also able to manage any *adaptations* that, in the meantime, have emerged from the real environment in which the plan is actually carried out. Adaptations, in particular, can concern the *delay* in starting or ending a task, the *failure* to execute a task or, even, the *addition* of new tasks.

### ROS API

The [Robot Operating System (ROS)](https://www.ros.org) is a set of software libraries and tools that help you build robot applications. ROS represents a de-facto standard for robotics. The **ROS API** provides, through ROS [messages](http://wiki.ros.org/msg) and [services](http://wiki.ros.org/Services), the possibility to different ROS [nodes](http://wiki.ros.org/Nodes) to create semantic-causal problems, to solve them, to execute them and, if needed, to adapt them. In other words, it provides a ROS environment with the ability to use the services offered by the *executor* component.

### Java API

What if C++ isn't your favorite language? The **Java API** allows, through [Java Native Interface (JNI)](https://en.wikipedia.org/wiki/Java_Native_Interface), to interface [Java](https://www.java.com) software with the executor. In other words, via the *Java API*, a Java programmer can, once again, create semantic-causal problems, solve them, execute them and, if needed, adapt them.

This solution is particularly convenient in those situations where there is a need to use *oRatio* in a web backend environment.

The addition of a similar [Python](https://www.python.org) API is expected as soon as possible!

### Web GUI

The last described component concerns the Graphical User Interface (GUI) of the solver. At the moment the interface is rather spartan and coarse. However, it is particularly useful for debugging semantic-causal problems. Thanks to the use of [WebSocket](https://en.wikipedia.org/wiki/WebSocket), in particular, the graphic interface allows to view, during the resolution process, the changes to the current *partial plan* and to the *causal graph* introduced dynamically as a consequence of the planner's choices. Furthermore, the [JavaScript](https://en.wikipedia.org/wiki/JavaScript) components for the visualization of the partial plan and the causal graph can be used to easily embed the generated graphs within web pages.

### Conclusions

In the next days the *oRatio* components will be reorganized into separate libraries that will be usable by users in "classic" mode, compiling and installing them, or, depending on the needs, directly importing them via [submodule](https://github.blog/2016-02-01-working-with-submodules/).

Some of these libraries, such as the [SeMiTONE](https://github.com/ratioSolver/SeMiTONE) library and the [RiDDLe](https://github.com/ratioSolver/RiDDLe) library, are already available. Feel free to use them as you please and send me feedback! The core library will be rolled out shortly. The other components will come accordingly.


### References

[<a name="r1"></a>1] Tsamardinos, I. & Pollack, M. E. (2003). *Efficient solution techniques for disjunctive temporal reasoning problems*. Artificial Intelligence. 151 (1–2). 43-89.

[<a name="r2"></a>2] & Cesta, A. & Oddi, A. (1996). *DDL.1: A Formal Description of a Constraint Representation Language for Physical Domains*. New Directions in AI Planning. IOS Press. 341–352.

[<a name="r3"></a>3] De Benedictis, R. & Cesta, A. (2020). *Lifted Heuristics for Timeline-based Planning*. ECAI 2020. IOS Press. 2330-2337 ([pdf](https://ebooks.iospress.nl/volumearticle/55157)).