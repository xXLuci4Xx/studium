
$$X_1\space|\space(Y=y)$$
This means that the random variable $X_1$ under the condition that $Y$ has the value $y$.

From the exercise 1 of the Uebungsblatt 1 we have $X_1 =Y +N_1$, then after the conditioning on $Y = y$, the variable $Y$ is treated as known/fixed, so $X_1\space|\space(Y=y) = y + N_1$. 
This is still a random variable, because $N_1$ is still random. 

That's why $H(X_1|Y=y)$ isn't the same as $H(X_1|Y)$, because the first entropy is calculating the entropy of conditioned random variable $X_1\space|\space Y=y$, whereas the second formula is conditional differential entropy.   

Interpretation: $H(X_1|Y=y)$ entropy **at one fixed condition value** $y$, $H(X_1|Y)$ is **average** of those entropies over all $y$ 