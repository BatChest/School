1) Everything from the Midterm Review
## 2) Given a WFST, calculate joint, conditional, and marginal probabilities
![Pasted image 20240319183844](https://github.com/BatChest/Winter2024/assets/90287766/88203ab9-e8e1-4242-800a-987dbeb42f8d)

![Pasted image 20240319184753](https://github.com/BatChest/Winter2024/assets/90287766/cb0e1a49-f6e9-42a8-8263-db3d94015dbe)

![Pasted image 20240319184827](https://github.com/BatChest/Winter2024/assets/90287766/24a73073-7777-4563-8037-e5356bb4fcdc)

![Pasted image 20240319185401](https://github.com/BatChest/Winter2024/assets/90287766/720b6e65-186e-43d6-b2fc-656e723539ce)

![Pasted image 20240319185428](https://github.com/BatChest/Winter2024/assets/90287766/e473098b-1398-42f7-831c-18673721b459)


## 3) Parse a sentence in accordance with rules given by a CFG, or use a CFG to determine whether a given string is accepted/rejected 
If you find a valid parse (a way to generating the string from the CFG) then we accept and if not we reject
Basically make a sentence by a given grammar so if we were given the following CFG:

![Pasted image 20240319185848](https://github.com/BatChest/Winter2024/assets/90287766/2a840b4e-4f92-4792-9be3-b27fd788ff41)

The following would be an accepted sentence:

![Pasted image 20240319185959](https://github.com/BatChest/Winter2024/assets/90287766/3a45c875-79fa-4d99-a42a-d674c501ac04)

*The Right side NP is suppose to be VP*
The following sentence wouldn't be accepted by the CFG:
The cat walks and the dog walks.

We can either use top-down
	Starting from S, generate all possible parses, see whether one matches the input 
Bottom-up:
	Starting from the input, generate all possible parses working up

## 4) Extract a CFG or a PCFG from a treebank
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
![Pasted image 20240319190909](https://github.com/BatChest/Winter2024/assets/90287766/6a3791f5-39d5-45be-bc44-5b9562420b96)

Here is how I did it:
![Pasted image 20240319190934](https://github.com/BatChest/Winter2024/assets/90287766/acc70a22-3f2e-43d1-ae1f-42cc4f22b292)

You want to start at the very top which will always be the S rule. Since there are 3 trees and the same S rule is used once in each tree then it's probability is 1 ($\frac{3}{3}$) and we would continue this same step for the rest of the grammar rules from these three treebanks.
To each rule's probability you would look at a specific rule lets say the NP rule. There are two different NP rules that we can find from these three tress and there are a total of 11 NP rules that were used between the three. So lets look at NP - NP PP, it seems to only be used 2 times out of the three trees and so its probability would be $\frac{2}{11}$ as that specific rule was used twice out the 11 NP rules that were used in total

## 5) Calculate the probabilities of a parse from a PCFG
   When calculating the probabilities you would need to take a tree so from the HW using the above CFG that we extracted from the treebank we were able to make the following tree:
   ![Part2Q2ParseTree1](https://github.com/BatChest/Winter2024/assets/90287766/6611ced8-72f0-492a-a8ca-4136256c3864)

   To get the probability of this we simply just multiply each rule's probability to each other:
   ![Pasted image 20240319192127](https://github.com/BatChest/Winter2024/assets/90287766/2cd42e0c-6212-47b2-989a-65e96c598f59)

   
## 6) Use formal language to model aspects of natural languages
	1) Compare grammatical/ungrammatical sentences of English with sentences that are accepted/rejected by a CFG


## 7) Identify when a sentence has multiple possible interpretations, and how these interpretations map onto different parse trees/constituent structures.
From the HW the sentence: “The dogs chased the cats in the house.” in which it had five different parses

**First Interpretation:** The dogs are chasing the cats where this is happening in the house

**Second Interpretation:** The dogs are chasing the cats, as the cats were in the house. 

The two parse trees that were created:
**Interpretation 2**

![Pasted image 20240319193124](https://github.com/BatChest/Winter2024/assets/90287766/78883059-877e-421b-9c92-b175978e582f)

**Interpretation 1:**

![Pasted image 20240319193135](https://github.com/BatChest/Winter2024/assets/90287766/5debbe57-fe0f-4522-847e-aec7f8ad8c4f)


## 8) Identify intransitive, transitive, and ditransitive uses of verbs.

### **Transitivity:** properties of verbs in context

### **Intransitive**: Only takes a subject, no object
Ex: 
Bob sleeps quietly. 
Sally **sneezed**.
The teacher **slept**.
A teacher from the school **slept**.
The picture of a teacher from the school **cracked**.

### **Transitive**: Takes a subject and object, a verb that has one object. 
Ex: 
Bob eats apples everyday.
where **Bob** is the subject and the **apples** is the object.

Sally **found** a tissue.
*Sally found

The teacher **congratulated** the student.
*The teacher congratulated

The teacher **congratulated** the student from the school with the mascot.

### **Ditransitive**: Takes three arguments(subject, two objects), one that takes two objects.
Ex: Bob sent Larry a letter in the mail.
Where Bob is the subject, Larry and letter are the two objects.

Sally gave the student a picture.

The teacher told the principle a story about the school.

The mascot sent the captain a picture of the team.

### Special Case:
Bob and Tom sleeps quietly.

Bob and Tom are considered a single object so this is still intransitive. 

## 9) Identify the location in the Chomsky Hierarchy for key languages discussed in class (e.g. {a^n b^n}, the copy language, the reversal language, and natural languages).


![Pasted image 20240320131708](https://github.com/BatChest/Winter2024/assets/90287766/2e1f0c69-dbd0-4372-90fa-ce8f930c80cd)




