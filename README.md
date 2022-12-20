# random-walk-conditional-probability

In this notebook, I will show a trick of using NumPy to solve a classical conditional probability problem of random walks:

> Give an standard random walk (start at origin and with the probability of moving toward each direction 1/2 and 1/2), what is the probability of reaching 10 before reaching -20?

My Physics PhD friend mentioned this question to me as his interview question at Renaissance (a top quantitative trading company). I was interested by it and came up with the following trick. Since I never see others using this trick, I feel I have the responsibility to share it on GitHub so that it could also benefit others.


The same technique can be adapted with solve many other time-series conditional probability questions. The general steps are:

- Create a large number of independent simulations.
- Within each simulation, mark the first time step (and afterward) that the condition #1 is satisfied as 'True'. We get a vector A of 'True's and 'False's.
- Within each simulation, mark the first time step (and afterward) that the condition #2 is satisfied as 'True'. We get a vector B of 'True's and 'False's.
- A & (negation of B) will have at least one 'True' if the condition #1 is reached before reaching condition #2. It will all be 'False' otherwise.
- Count the number of vectors which pass the test in the above step and divide this number of the total number of simulations is our wanted conditional probability.
