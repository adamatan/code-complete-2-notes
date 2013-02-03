Notes and reflections on Code Complete, Second Edition
=====================================================

## 3: Upstream prerequisites
### 3.1 Importance of prerequisites
1. Software can not overcome plan flaws (“Can’t design a Pontiac and get a Rolls Royce”).
1. Quality at beginning (design), middle (construction) and end (testing) of process.
1. Planning as a form of risk reduction: The most common risks are poor planning.

1. Common reasons for poor planning: 
  1. Inexperienced or untrained developers.
  1. Unenlightened boss wants to see developers coding, because *planning isn’t work*. Good counter-arguments: 
    * Simple logic - planning saves time, reduces risks, helps estimate costs
    * Analogy to non-software projects
    * Coordination between developers (UI waiting for BE on so on)
    * Hard data (page 29): The cost of fixing an error grows (exponentilly?) over time.

#### My thoughts
Huge open-source projects, most notably the Kernel, are not planned, at least not in the usual architect-designer-developer flow.


### 3.2 Determine the kind of software You’re working on
The development approach is derived from the type of software used. An internet site is fault-tolerant and has frequent spec changes. 
A pace maker changes 
Combining iterative design with prerequisites is very effective.
