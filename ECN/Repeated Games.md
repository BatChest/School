
|     | L      | H      |
| --- | ------ | ------ |
| L   | 54, 54 | 72, 47 |
| H   | 47, 72 | 60, 60 |
- Here we just have the prisoner's dilemma where both parties defect will be the NE or where they cooperate with each other. 

*Finite Repeated Interaction (T)*
- ==dynamic game where a one-shot stage game is played repeatedly over a set number of time periods, or rounds==.
- If we play the previous game above 4 times we'll get 54,54 on the 4th try

*Infinite Repeated Interaction*
- *Trigger Strategies*
	- **Grim Trigger Strategy (GTS)**
	- **Tit-for-Tit Trigger Strategy** (TFT)

**Grim Trigger Strategy**
- Cooperate with someone until they decide not to and so you decide not to cooperate with them
- Ex: In the above game the two players are cooperating every round and suddenly one player decides to defect and so then the other player to decides to never cooperate with them ever again

**Tit-for-Tit Trigger Strategy**
- Whatever someone did to you last, you do to them next.
- But after this you resume business, things go back to normal
- Ex: In the above game one person decides to defect and you cooperate so then in the next round you decide to defect

**Why/When should we cooperate against GTS?**
- Lets say we're playing the prisoner's dilemma game from above
- Possibilities/Payoffs: 
	- Cooperate: 60,60,60,60, $\dots$
	- Defect: 72, 54, 54, $\dots$
- In the first period/round we cooperate so we get the payoff of 60:
- We use the following equation: $1 + \frac{1}{r}$
- Then on the fraction we have 60 too because we're going to keep getting 60 as our outcome as we are going to keep cooperating
$60 + \frac{60}{r}$
- Then we do the same for the second possibility where we defect
- In the first period we are going to get 72 in the first period and then in the next rounds they are going to stop cooperating so we get 54 for the remaining rounds
$72 + \frac{54}{r}$
Then we compare the two possibilities:
$60 + \frac{60}{r} > 72 + \frac{54}{r}$
- Then we solve for r:
= $\frac{6}{r} > 12$
= $6 > 12r$
= $r < \frac{1}{2}$


**Why/when should we cooperate against TFT?**
- Refer to the prisoner's dilemma again and the possibilities but this time we are running Tit-for-Tit
- Possibilities:
	- Cooperate: 60, 60, 60, 60, $\dots$
	- Defect: 72, 47, 60, 60, 60, $\dots$
- In this case we notice that if both cooperate then we are just going to keep getting 60
- In the defect the first two rounds we decide to defect and then the other player defects
- After that we both cooperate and get 60 every round after
- In this case we are only focusing on the first two rounds:
- In this case we'll use the following formula: $1 + \frac{1}{1+r}$
- In the cooperate possibility we get the following:
$60 + \frac{60}{1 +r}$
- In the defect possibility we get the following:
$72 + \frac{47}{1 + r}$
- Then we solve for r
= $\frac{13}{1 + r} > 12$
= $12 + 12r < 13$
= $12r < 1$
= $r < \frac{1}{12}$







