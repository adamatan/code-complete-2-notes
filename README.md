Notes and reflections on Code Complete, Second Edition
=====================================================

# Part I: Laying the foundations

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
    * Hard data (page 29): The cost of fixing an error grows (exponentially?) over time.

#### My thoughts
Huge open-source projects, most notably the Kernel, are not planned, at least not in the usual architect-designer-developer flow.


### 3.2 Determine the kind of software You’re working on (pp. 31)
The development approach is derived from the type of software used. An internet site is fault-tolerant and has frequent spec changes. A pace maker can not tolerate faults, and its spec never changes. Therefore, an internet site should be developed iteratively, while a pacemaker should be developed sequentially.

Combining iterative design with prerequisites is very effective.

#### My thoughts
Prerequisites are interfaces: Between customer and code, and between code components.

### 3.3 Problem-definition prerequisite (pp. 36)
A "clear statement of the *problem*" is the first step. It should not be stated in software terms (unless it's a software project like a compiler), but in the client's terms, e.g. *"We don't know where are all the company's vehicles during the day."*. Note that the problem can sometimes be solved without a software. Without a clear problem, the entire development process might be wasted on irrelevant issues.

### 3.4 Requirements prerequisite (pp. 38)
The requirements are still phrased in the user, rather than the developer, language: *"The vehicles' location should be updated every 5 minutes."*

The requirements are seldom frozen. Therefore, a change mechanism should be agreed on with the client before the development process begins, with a clear price and time tags for each requested change.

#### My thoughts
The requirement checklist is the important part of the section.

### 3.5 Architecture prerequisite (pp. 43)
Architecture: "The high level part of software design." This grand design should translate the business requirements into a software structure with coherent design and rationale, clear objectives, and flexible structure.

 > "When you look at the architecture, you should be pleased by how natural and easy the solution seems." (pp.52)

Typical parts (My opinion: ✔✔ YES!  ✔ yes, ☹ depends, ✘ never)

1. ✔✔ Program organization, overview: That's what I need from an architect - a clear overview of interactions and expectations in the system.
1. ✘ Major classes: Never. That's over-designing. Give the developers interfaces, and let them construct implementations.
1. ☹ Data design: major files and table designs: Only those used externally, either by end users or other components. And the later should be better decided by the developers themselves - they simply know the problem better.
1. ✔✔ Business rules ("customer data should not be more than 30 seconds out of date"): Sure - I don't want to aim at wrong targets.
1. ☹ (Scarce) Resource management, such as DB connection, threads and handles: Only in cases where a shared where the resource is shared and truly scarce.
1. ✔ Security
1. ✔ Performance goals
1. ✔ Scalability
1. ✔ Internationalization
1. ✘ I/O technique (look-ahead, look-behind): These should be *politely suggested* to the developers. They should know better than the architect. How low-level is this getting?
1. ☹ Error processing and handling
1. ✔ Fault tolerance
1. ✔ Feasibility: The architect should convince the management (and the developers!) that the system construction is possible and reliable.
1. ✔✔ Prevent Overengineering and Underengineering:Which parts are expected to face heavier load and must not fail? Which parts should "just work" without scale and performance consideration?
1. ✔✔ Buy vs. Build vs. Reuse decisions
1. ✔✔ Change strategy: Forecast change, design a change-tolerant system that can embrace expected changes without requiring overhauls.

The reasoning behind decisions should be clear, rather than "we've always done things that way".

> The architecture should tread the line between underspecifying and overspecifying.


#### My thoughts
* The greatest caveat of underspecifying. Architecture should almost never go into implementation details. That being said, recommendations (e.g. *Look-ahead should be considered here because*) are most welcome - oftentimes the architect is a very experienced developer.
* The architecture is a translation of business requirements to software components.
* The architecture should assist the development effort by creating an coherent general design, defining a common language and splitting  work to comprehensible bytes. 
* The architecture should be a *request for comment* paper for the developers, not a fixed final design.

### 3.6 Amount of Time to Spend on Upstream Prerequisites (pp. 55)

> Generally, a well-run project devotes about 10-20 percent of its efforts and 20-30 percent of its schedule to requirements, architecture, and up-front planning.

For large projects, the architectural effort is a project by itself, and its schedule should be planned as well. 

#### My thoughts
Considering a typical two-week sprint with 10 work days, that sums up to 2-3 days for architecture (excluding design!). That's probably a little bit too much for a small project.

## 4: Key Construction Decisions

### 4.1 Choosing Programming language (pp. 61)

Criteria: Developer's familiarity with the language, Lean towards higher-level languages.

#### My thoughts
* Prefer a language that fits naturally to the job. For example, spending a day learning AWK for a large log-processing job might be a good idea, even if your natural language is C++ or Java. **Good developers fancy the opportunity to learn a new skill**.
* Prefer a popular language for maintainability sake.

### 4.2 Programming Conventions (pp. 66)

A common convention reduces confusion and lets the mind focus on the actual programming flow. It's important to define convention beforehand, because changing it afterwards is almost impossible.

#### My thoughts

The conventions should focus on interfaces rather than nitpicking on variable names. It's really nice to have a project with, say, `getPixelName`, `getPixelAge` and `getPixelStatus` in one class, and `getPixelNameImpl`, `getPixelAgeImpl` and `getPixelStatusImpl` on another class, all written by different developers adhering to the same convention.

1. Should largely rely on the language specs (java CamelCaseClasses, Python's underscore_methods)
1. Huge risk of overspecifying. 






