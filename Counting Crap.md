
# **Repetition allowed and ordered $n^k$**
```ad-example
Creating a password or license of length k and we have $n$ choices to make for each position
```

**How many different functions are there from [5] to [3]**?

To define a function we need every element from [5] to be assigned to either 1,2 or 3. 
f(1) $\rightarrow$ 3 options
f(2) $\rightarrow$ 3 options
f(3) $\rightarrow$ 3 options
f(4) $\rightarrow$ 3 options
f(5) $\rightarrow$ 3 options
By MP, $3^5$ different functions from [5] to [3]

**License Plates look like DLLLDDD where D's are digits {0,1,...,9} and L's are letters {A,B,...,Z}**
**a) How many distinct license plates?**

| Note | Duration |
|------|----------|
| D    | 10       |
| L    | 26       |
| L    | 26       |
| L    | 26       |
| D    | 10       |
| D    | 10       |
$10^{4} \times 26^3$

**b) How many have no repeated letters?**

| Note | Duration |
|------|----------|
| D    | 10       |
| L    | 26       |
| L    | 25       |
| L    | 24       |
| D    | 10       |
| D    | 10       |
$10^{4} \times (26)_{3}$ 

### Example: Permutations of {a, b, …, z} with No Two Vowels Consecutive

**Problem:** How many permutations of {a, b, …, z} exist with no two vowels (a, e, i, o, u) occurring consecutively?

**Solution:**

1. **Order the 21 consonants:** ( $\rightarrow 21!$ ) ways
    
2. **Insert the vowels so that no two vowels are next to each other:**
    - Represent the list of 21 consonants as:
        
        ```
        ___ ___ ___ ___ ___ ... ___ ___ ___
        ```
        
        (22 options for vowel insertion)
        
    - Since two vowels cannot use the same position, there are: $22 \times 21 \times 20 \times 19 \times 18 = (22)_5 \text{ ways}$ 
        

By the Multiplication Principle (MP), the total number of permutations is:  $21! \times (22)_5 = \text{number of lists of } {a, b, \dots, z} \text{ with no two vowels consecutive} \text{ or }  \frac{21! \times 22!}{17!}$

# Combinations
You plan to buy 3 books at a bookstore, but there are 10 books you want. There are:
$\binom{10}{3}$ = $\frac{10!}{3!7!} = \frac{10(9)(8)}{3(2)(1)} = 10 \times 3 \times 4 = 120$




## Arrangement of a Deck of Cards

**Each card is distinct, so no repeats. A 52-deck of cards has 4 suits, each with 13 cards.**

**Goal:** Determine the number of ways to order the cards if all suits are together.

1. **Order the Hearts:** (13!) ways
2. **Order the Diamonds:** (13!) ways
3. **Order the Spades:** (13!) ways
4. **Order the Clubs:** (13!) ways

Since the suits are distinct, we also need to order the suits without repeats:

5. **Order the Suits:** (4!) ways

By the Multiplication Principle (MP), the total number of ways to order the cards is: $(13!)^4 \times 4$! 

# Choosing ( k ) People to be on a Committee from a Group of Size ( n )

## Example:

**Biking home, we travel 3 blocks west and 5 blocks north. How many different routes are there?**

Encode a bike route as a sequence:
```
___ ___ ___ ___ ___ ___ ___ ___
```

of 8 choices: west to north.

Alphabet: ({W, W, W, N, N, N, N, N})

_Note: These W’s and N’s are identical._

We want to **choose** 3 positions in the sequence where the bike goes west:
$\binom{8}{3}$

The remaining positions will all be N’s.

# Multiset 
M = {1,1,3,4,4,4} = {$1^{2}, 2^{0}, 3^{1}, 4^{3}$} is a multiset of [4] or [5] with no copies of 5.

We have 20 distinct kinds of donuts and we want to select a multiset of size 12
($\binom{n}{k}$) = # of multisets of size k from a set of size n "n multi-choose k"

**THM:** For $0 \le k,n$ ($\binom{n}{k}$) = $\binom{n-1+k}{k}$ 

**Example 1:** A donut shop has glaze, chocolate, jelly donuts and we want 6 donuts:
total number of donut multisets = ($\binom{3}{6}$) = $\binom{3-1+6}{6}$ = $\binom{8}{6}$


**Example 2:** How many ways are there to select 6 donuts from 3 distinct options {G, C, J} if we want at least one of each kind?

**Sol:** We can start by putting one of each kind on our multiset : {G, C, J, __, __, __}. With the remaining 3 spaces we can select a multiset of size 3 in ($\binom{3}{3}$) = $\binom{3-1+3}{3}$ = $\binom{5}{3}$ = $\frac{5*4}{2*1}$ = 10 ways. By MP, 1 $\times$ 10 = # of donuts with at least one of each

**Example 3:** Once we've selected our multiset of donuts, how many ways are there to arrange them in the box?
{G, G, C, J, J, J} arrange these letters in a list of length 6

**Task 1:** Choose 2 positions for the G's $\binom{6}{2}$ 
**Task 2:** Choose 1 position from the remaining 4 positions for the C $\binom{6-2}{1}$
**Task 3:** Choose 3 positions from the remaining 3 positions for the J's $\binom{6-2-1}{3}$
3 positions for the J's
By the **MP**, $\binom{6}{2} \binom{4}{1} \binom{3}{3}$ = $\frac{6!}{2!4!} \times \frac{4!}{1!3!} \times \frac{3!}{0!3!} = \frac{6!}{2!1!3!} \text{ ways }$ 




