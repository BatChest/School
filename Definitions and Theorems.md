# Set Stuff
- A set is a collection of distinct objects called elements 
	- $n \in S$ "n is an element of the set S"
- A subset of S is a sub collection of elements in S
	- $A \subseteq S$ 
- The size of S is the number of elements in S
	- |S| = # S
- Integers are referred as $\mathbb{Z}$  
- Positive Integers are referred as $\mathbb{N}$ 
- Recall that [ n ] = {1,2,3,...,n}
- [ 4 ] = {1,2,3,4}
- Empty set $\emptyset$ contains no elements

- The union of two sets $S_1$ and $S_2$  is the set containing all the elements in $S_{1}\text{ and } S_{2}$ (no repeats) {1,3,5} $\cup$ [ 3 ] = {1,2,3,5}

- The intersection of two sets $S_1$ $\cap$ $S_2$ is the set containing only the common elements of $S_{1}\text{ and } S_2$ {1,3,5} $\cap$ [ 3 ] = {1,3}

- If $S_{1} \text{ and } S_{2}= \emptyset$ they are disjoint

# Addition Principle
- Suppose $S_{1}, S_{2}, \dots , S_{m}$ is a partition of S. Then $|S| = |S_{1}|+ |S_{2}|+ \dots |S_m|$ 

# Multiplication Principle
Let $S$ be a set of ordered pairs $(a,b)$ of objects, where the first object $a$ comes from a set of size $p$ and for each choice of objects $a$ there are $q$ choices for object $b$. Then $|S| = p \times q$ 

We can extend the multiplication principle to $n$ tasks 

# Subtraction Principle
Let $B \subseteq U$ and let $U$ \ $B$ be the set of all elements in $U$ that are not in $B$. Then |$U$ \ $B$|  = |$U$| - |$B$| 

# Division Principle
Let S be a finite set that is partitioned into $k$ parts so that each part contains $m$ objects. Then $k = \frac{|S|}{m}$


# Counting
A word or list is an ordered sequence of objects from some alphabet or set. A k-word or k-list is a word/list of length k

# Permutation
A permutation is a list of all objects in a set without repeats. A k-permutation is a permutation of length k. Let P(n,k) = # of k-permutations of a set of size n


# Combination
A combination or subset of a set S is an unordered selection of elements of S. A k-subset of S is a subset of size k. We define
$\binom{n}{k}$ = # of k-subsets of an n-element set 
"n choose k"

# THM
For $0 \le k \le n, \binom{n}{k} = \frac{(n)_{k}}{k!} = \frac{n(n-1)\dots(n-k+1)}{k!} = \frac{n!}{k! (n-k)!}$   

# Pascal's Formula (for 1 $\le$ k $\le$ n-1)
$\binom{n}{k}$ = $\binom{n-1}{k} + \binom{n-1}{k-1}$

# Functions and Bijections
Let A and B be sets. A function from A to B is a rule that maps each element in A to exactly one element in B. Write $f: A \rightarrow B$ 

![Pasted image 20240821202442](https://github.com/user-attachments/assets/5ffa4897-4e6a-4bea-8345-9e5d1227c19a)


## Injective
A function is injective if for all x,y $\in$ A with x $\neq$ y, x and y map to different elements in B.

## Surjective
A function is surjective if every b $\in$ B is mapped to by some a $\in$ A

## Bijective 
A function is bijective if it is injective and surjective (one-to-one)

![Pasted image 20240821202703](https://github.com/user-attachments/assets/b8b190b5-3a69-408d-8adc-865aa01d7599)


# Bijective Principle
Let A,B be sets |A| = |B| if and only if there is a bijection between them


# Foundations of Counting
If we are distributing $n$ objects into k positions

![Pasted image 20240821203035](https://github.com/user-attachments/assets/1f6f0a0f-e3e0-4f1e-badc-4c701aaa11f9)



# Multiset
A multiset M is a set with repeated elements. For x $\in$ M, the multiplicity of x in M is the # of copies of x in M

$(\binom{n}{k})$ = # of multisets of size k from a set of size n "n multi-choose k"
## Stars and Bars 
For $0 \le k,n$ $(\binom{n}{k}) = \binom{n-1+k}{k}$ 


# Pigeonhole Principle
If n+1 objects are distributed into n boxes, then at least one box contains two or more objects 

# Generalized PHP
If there are $k$ objects distributed into $n$ boxes, then there is a box that contains at least $[\frac{k}{n}]$ objects (note its the ceiling of $\frac{k}{n}$)
# Ramsey Theory
- Within enough chaos, there is order
## Party Problem
What is the smallest number of people needed in a group to guarantee that either there is a subset of 3 mutual friends or 3 mutual strangers?

Let $n_{1,}n_{2} \in \mathbb{N}.$ Define R($n_{1,}n_{2}$) = m to be the smallest integer so that any group of m people has either $n$, mutual friends or $n_2$ mutual strangers

R(3,3) = 6

# Binomial Theorem
Let $n \in \mathbb{N}$. (x+y)$^n$ = $\sum^{n}_{k=0} \binom{n}{k} x^{n-k} y^{k}$ 

## Cor1 
$2^{n} = \sum^{n}_{k=0} \binom{n}{k}$ 

## Cor2
$0 = \sum^{n}_{k=0} \binom{n}{k} (-1)^k$ 

## Cor3
$\binom{n}{0} + \binom{n}{2} + \dots = \binom{n}{1} + \binom{n}{3} + \dots (n \ge 1)$ 

## Cor4
$\binom{n}{0} + \binom{n}{2} + \dots = 2^{n-1}$ and $\binom{n}{1} + \binom{n}{3} + \dots = 2^{n-1}$


# Inclusion-Exclusion Thm
$N_{=}(S) = \sum\limits_{S \le J \le P} (-1)^{|J|-|S|} N_{\ge}(J)$ where we sum over all subsets of J
## Set up
- U = a collection of objects
- P = a collection of traits that the objects may or may not have = ${P_{1}, \dots, P_{k}}$ S $\subseteq$ P desired subset of properties
- *GOAL*: count objects with a given set of traits by counting the objects with at least those traits
- $N_{=}(S) :=$ number of objects that have exactly the properties in S
- $N_{\ge}(S) :=$ number of objects that have at least the traits in S

# Derangements
A derangement of [ n ] is a permutation $i, i_{2}\dots i_{n}$ of [ n ] such that $i_{j} \neq j$. We denote the number of derangements of [ n ] by $D_{n}$

## Thm
For $n \ge 1, D_{n} = n! (1 - \frac{1}{1!} + \frac{1}{2!} - \frac{1}{3!} + \dots + (-1)^{n} \frac{1}{n!})$ 

# Recurrence Relations
A sequence $h_{0,}h_{1}, h_{2}, \dots ,h_{n}, \dots$ is an (infinite) list of numbers, with $h_{n}$ = general term

## Arithmetic sequence: q constant
$h_{0}, h_{0}+q, h_{0}+2q, \dots , h_{0}+nq, \dots$
where $h_{0}+nq = h_n$ 
Rule: $h_{n}= h_{n-1} + q$ general term $h_{n} = h_{0} + nq$ 
$h_{n}= h_{n-1} \text{ where } n \ge 1$ and $h_{n} = h_{0} \text{ where } n \ge 0$ 

# Geometric Sequence: q constant
$h_{0}, qh_{0},q^{2}h_{0},\dots, q^{n}h_{0} \text{ where } q^{n}h_{0} = h_{n}$ 
Rule: $h_{n}=qh_{n-1} , \text{ general term } h_{n}=q^{n}h_{0}$
where $n \ge 1 \text{ for } h_{n}=qh_{n-1}$ and $n \ge 0 \text{ for } h_{n}=q^{n}h_{0}$

# Fibonacci Sequence
The sequence of numbers $f_{0}, f_{1}, f_{2}, \dots$ satisfying the recurrence relation and initial conditions
$f_{n}=f_{n-1}+f_{n-2} (n \ge 2) \text{ and } f_{0}=0, f_{1}=1$ is called the Fibonacci sequence and the recurrence relation is called the Fibonacci recurrence



