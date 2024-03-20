1) Everything from the Midterm Review
2) Given a WFST, calculate joint, conditional, and marginal probabilities
![[Pasted image 20240319183844.png]]
![[Pasted image 20240319184753.png]]
![[Pasted image 20240319184827.png]]
![[Pasted image 20240319185401.png]]
![[Pasted image 20240319185428.png]]

3) Parse a sentence in accordance with rules given by a CFG, or use a CFG to determine whether a given string is accepted/rejected 
If you find a valid parse (a way to generating the string from the CFG) then we accept and if not we reject
Basically make a sentence by a given grammar so if we were given the following CFG:
![[Pasted image 20240319185848.png]]
The following would be an accepted sentence:
![[Pasted image 20240319185959.png]]
*The Right side NP is suppose to be VP*
The following sentence wouldn't be accepted by the CFG:
The cat walks and the dog walks.

We can either use top-down
	Starting from S, generate all possible parses, see whether one matches the input 
Bottom-up:
	Starting from the input, generate all possible parses working up

4) Extract a CFG or a PCFG from a treebank
To extract a CFG from a treebank you can just simply go down the different tress and categorize starting with the rule S and then we work our way down so for the above tree we can extract the following rules:
S - NP VP
NP - Det N
VP - V
Det - The 
N - cat
V - walks
Obviously there are going the be more trees to extract rules from but this is just how you would do it for a single tree.

Extracting a PCFG from a treebank:
From HW5 were ask to extract the PCFG from the following treebank
![[Pasted image 20240319190909.png]]
Here is how I did it:
![[Pasted image 20240319190934.png]]
You want to start at the very top which will always be the S rule. Since there are 3 trees and the same S rule is used once in each tree then it's probability is 1 ($\frac{3}{3}$) and we would continue this same step for the rest of the grammar rules from these three treebanks.
To each rule's probability you would look at a specific rule lets say the NP rule. There are two different NP rules that we can find from these three tress and there are a total of 11 NP rules that were used between the three. So lets look at NP - NP PP, it seems to only be used 2 times out of the three trees and so its probability would be $\frac{2}{11}$ as that specific rule was used twice out the 11 NP rules that were used in total

5) Calculate the probabilities of a parse from a PCFG
   When calculating the probabilities you would need to take a tree so from the HW using the above CFG that we extracted from the treebank we were able to make the following tree:
   ![[Part2Q2ParseTree1.jpg]]
   To get the probability of this we simply just multiply each rule's probability to each other:
   ![[Pasted image 20240319192127.png]]
   
6) Use formal language to model aspects of natural languages
	1) Compare grammatical/ungrammatical sentences of English with sentences that are accepted/rejected by a CFG


7) Identify when a sentence has multiple possible interpretations, and how these interpretations map onto different parse trees/constituent structures.
From the HW the sentence: “The dogs chased the cats in the house.” in which it had five different parses

**First Interpretation:** The dogs are chasing the cats where this is happening in the house

**Second Interpretation:** The dogs are chasing the cats, as the cats were in the house. 

The two parse trees that were created:
**Interpretation 2**
![[Pasted image 20240319193124.png]]
**Interpretation 1:**
![[Pasted image 20240319193135.png]]

8) Identify intransitive, transitive, and ditransitive uses of verbs.

**Transitivity:** properties of verbs in context

**Intransitive**: Only takes a subject, no object
Ex: Bob sleeps quietly 

**Transitive**: Takes a subject and object
Ex: Bob eats apples everyday
where **Bob** is the subject and the **apples** is the object

**Ditransitive**: Takes three arguments(subject, two objects)
Ex: Bob sent Larry a letter in the mail.
Where Bob is the subject, Larry and letter are the two objects

Bob and Tom sleeps quietly
Bob and Tom are considered a single object so this is still intransitive. 

9) Identify the location in the Chomsky Hierarchy for key languages discussed in class (e.g. {$a^nb^n$}, the copy language, the reversal language, and natural languages).

![[Pasted image 20240319195739.png|800]]



