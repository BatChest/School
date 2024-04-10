# Quiz Stuff
- Integrated Development Environments  
	- Features  
	- Benefits  
	- Activities supported by IDEs  
	- Protocols (LSP)  
	- Language-specific vs. Language-agnostic tools

# What can IDE do
1) Edit code files
2) Run code
3) Syntax highlighting
4) Linting
	1) Bringing attention to bad code
	2) Whenever you get a red underline, there is an error and when hovering over the text you get a reason for the red underline
	3) Other times whenever there are unused libraries being used in your code that display that library in a lighter color
5) Code Completion
6) File explorer
	1) Code Navigation
7) Code Formatting
	1) Enforces consistent style 
	2) Avoid meaningless diffs
		1) Meaningless Diff: Its a diff that has no impact on the functionality of the code
8) Version Control
9) Automation and Arbitrary Commands 
	1) Automating writing code, auto completion
	2) 


# What can be done without IDE
1) VIM, Nano
2) Terminal (ex: gcc -o myfile or python myfile/py)
3) N/A
4) Linter Binary

# Language Server Protocol
Developers of each language create a language server Below is a rough visualization:
![Pasted image 20240404125216](https://github.com/BatChest/School/assets/90287766/66cc4b72-4c71-4078-b596-4a4ffa965605)
- The whole point of this protocol is just a specified set of rules for how these two parties can interact 
- Example of LSP 
	- Python extension in VScode

 # Language-Specific tools 
- Designed to support developers to work on a specific programming language 
- It includes features that are tailored exclusively for that specific language 
- This can include IDE's like Clion for C++, Pycharm for python

# Language-agnostic tools
- Independent from any specific programming language 
- The tools aren't used for just one specific language as it can be used for all 
- It is used to solve problems that are common across different languages 

# Difference between the two
- Language-specific tools are limited to a particular language and are optimized for that specific language features and paradigms 
- Language-agnostic tools are more versatile and can used across different languages mostly focusing on solving the problem first then choosing the best language for the job 
- It makes it more flexible and adaptable but may not offer the same optimization that a language-specific tool may offer  
