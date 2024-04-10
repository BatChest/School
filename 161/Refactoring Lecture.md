# Quiz Stuff
 - What is it?  
  - Technical debt, code smells  
  - Name a refactoring operation

# Abstract Definition
- Modification to the software 
- Not about adding new functionality 
	- We're not adding new methods
	- Not adding new endpoints for our API
- Keeping the functionality of the software ideally exactly the same but making changes to the software that enhances it in some other way
- Through the process of refactoring you might identify a bug and fix them along the way 
- Might be code objects that might be needed
- Get rid of repetitive code and just make it a single function instead of having duplicate functions that does the same thing
- The goal is to make the code easier to maintain in the future 

- When adding new code it creates 
	- new functionality
	- but it also leads to externalities 
	- new opportunities for bugs 
- Refactoring is trying to mitigate the externalities and bugs when adding new code


# Technical Debt
- When working on projects you might implement something in not the absolute best way
- It can sustainable but as the number of externalities grow and grow and points in your code is implemented poorly, those increase
- It comes to the point where it chokes you out from being able to do any development
- Using old solutions become sub-optimal over time and as you keep moving forward with this solution it becomes harder to implement changes later 
- With ongoing development on the project the old solution or method in the code starts to become less optima and now there is a better method as time moves on
- It isn't a bad thing as technical debt does occur but being able to reduce the amount of debt is necessary in order to move development forward

# Refactoring Example
- A method or function in one of your class that might be used by more features of another class than the class that its defined in
- We can create a new method with similar body in the class it uses most
- So if we had a function called "aMethod()" in Class 1 and it uses stuff from class 2 more 
- It would make more sense to just move "aMethod()" to Class 2 as it would keep the functionality of the code the same

# Issues with Refactoring
- When refactoring like moving some functionality around the code it can cause the risk of creating new bugs in the process  

# Why Refactor?
- Getting the design of the code can be very difficult and might not know exactly what we need to implement the first time around
- Reducing the code size 
	- Take confusing code and rewrite it in a way that's easier to read 


# Example 2
- Introduce Null Object
- There are many checks for null
- Instead just make a null value into a null object
- This can get rid of if statements by replacing checks for null with a null object that does the right thing for "null" value

# Example 3
- Replace conditional with polymorphisms 
- You have a conditional that chooses different behavior depending on the type of an object
- You would move each leg of the conditional to an overriding method in a subclass. Make the original method abstract

# When to Refactor
- Before adding a new feature
- When need to fix a bug or 
- do peer review 

# Code Smells 
- Code that stinks or bad things done in code like bad patterns in the code
```python
if () 
elif()
elif()
elif()
else()
```
- Sometimes you could have long switch cases and there could be a better way of approaching it 
- Things that you can notice about the code 
- While the code is technically correct but they still indicate you're going to run into maintainability issues in the long run
- Each code smell will sometimes have a definite way to resolve that code

# Example of Code Smells
- Duplicated code
	- DRY: Don't Repeat Yourself 
	- If you some code in one place and copy pasted it into another place 
		- Example: having two classes that implement the same method and copy paste the method from the first one to the second one 
		- If you ever need to change anything about the first implementation of that then you'll need to change it in both places 
		- Rewriting this method defeats the purpose of the advantage of programming languages 
- Long Method 
	- Code that is extremely long makes it harder to understand 
	- It can harder to understand and often would like to break it out of that functionality into separate functions  
- Large Classes 
	- Classes that do too much which reduces cohesion
- Long Parameter List
	- Hard to understand, can become inconsistent 
- Divergent Change
	- One type of change requires changing one subset of the methods 
	- Another type of change requires changing another 
	- So this would mean you should have something that is two classes or two inherited classes rolled into one 
	- Thinking about separating it out into two separate things 
- Lazy Class
	- Just has one method in it that's not really doing much and could be combined with something else 
- Speculative Generality
	- Might see some code that is written with the idea that eventually we'll need to do some extensions 
	- You might have some hooks in the class that can be called whenever the class is instantiated 
	- You had those hooks for a while and haven't found any use for them so you might just get rid of it if never find a use for them
- Comments
	- Are used to hide bad code 
	- Explain why you did the way you did (deodorant) 

# Example of Refactoring (Rename Symbol)
- Command + Shift + P (VScode)
- We have some code and we can highlight some of the code and some sort of regex and replace the variable name of one of the variable 
- This can be done to make the name more specific to what we are doing in our code 
- If we want to replace the variable across the entire project you can just click rename symbol on VScode and type in the new name for that variable
- This will rename each instance of the variable 
