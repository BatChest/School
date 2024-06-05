# Defect
- mistake committed by a human 
# Error
- Incorrect computation
# Failure
- Visible error: program violates its specification

# Defense in Depth
Swiss cheese model is where there are holes in one layer and then the next layer covers the holes. It might still have holes so the last layer covers the holes preventing anything to get through

![[Pasted image 20240604141832.png]]

## Levels of defense
1) Make errors impossible 
2) Don't introduce defects
	1) Get things right the first time
	2) Think before you code, don't code before you think
3) Make errors immediately visible
	1) assertions
	2) Reduce distance from error to failure
	3) Type checking 
	4) Don't program in ways that hide errors
4) Debugging is the last level/resort
	1) Work from effect (failure) to cause (defect)
	2) Use scientific method to gain information
	3) Easier to do in modular programs with good specs and test suites 


# Debugging Process
1) Find small repeatable test case that produces the failure 
2) Narrow down the locations and proximate cause 
	1) Loop (a) study the data (b) hypothesize (c) experiment
	2) Experiments often involve changing the code
3) Fix the defect 
	1) Is it simple typo or a design flaw
4) Add the test case to regression suite 
	1) Is this failure fixed? Are any other new failures introduced?

The Loop of debugging:

![[Pasted image 20240604143613.png]]

- Debugging should be systematic
	- Carefully decide what to do
	- Keep a record of everything that you do
	- Don't get sucked into fruitless avenue 

# Ways to make progress on debugging
- Logging events/keep record of everything that you do
- Restart the computer (sometimes this helps)
- Explain the problem to a friend 
- Make sure it is a bug

# Delta Debugging
- Using the following bug report as a running exmaple:
```
<SELECT NAME ="priority" MULTIPLE SIZE=7>
```
- How do we get about simplify this input?
	- Manually remove parts of the input and see if it still causes the program to crash
- For the above example assume that we remove characters from the input file 

The process of delta debugging goes as the following:
1) Identifying the failure 
2) Creating the hypothesis 
3) Running the trials
4) Observing the results 

- For the example above we basically split the string into smaller and smaller chunks and test those chunks to see what fails and what passes
- We are able to run these tests by running binary search over the parts of the string 

# Minimality 
- **minimality** refers to the smallest set of changes or inputs that still produce a failure
- The global minimum is the smallest input to the program that will make the program fail 
- Finding the global minimum might require to perform an exponential number of tests 
- $C_F$ = Set of all failing inputs 
![[Pasted image 20240604145429.png]]

# Monotonicity 
- Monotonicity in delta debugging refers to the assumption that adding more changes to a set that already causes a failure will not eliminate the failure
- If a certain subset changes leads to a bug, then any superset of those changes will also lead to the bug or another failure 

- Delta debugging is most effective for monotonicity and isn't very effective on cases that are non-monotonicity 

# Challenging Debugging environments
- **Complex Codebases**: 
	- Large-scale projects with intricate code structures increase the likelihood of bugs and make it harder to isolate them.
- **Unpredictable Bugs**: 
	- Bugs that occur sporadically or under specific conditions are harder to reproduce and fix.
- **Time Constraints**: 
	- Tight deadlines can pressure developers, leading to rushed debugging that may overlook deeper issues.
- **Dependency on External Systems**: 
	- Reliance on libraries, frameworks, and APIs introduces variables that are outside the developer’s control.
- **Concurrent Systems**: 
	- Debugging multi-threaded or distributed systems can be difficult due to the non-deterministic nature of concurrent processes.
- **Limited Access to Tools**: 
	- Environments without robust debugging tools or where such tools are hard to use can hinder the debugging process.
- **Poor Documentation**: 
	- Inadequate documentation makes it challenging to understand the intended behavior of the code, complicating the debugging process.