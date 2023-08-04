

# Creator-assisted-contextual-ranking
### Problem:

#### Say we have a creator who has uploaded many videos on YouTube. What he just does is that, he submits a ranking of the videos, according to his preference. So, he  would like the higher ranked videos to be watched more than the lower ranked ones. But, we cannot really present the same ranking while recommending to a particular user. This is a contextual problem, since it depends on the present context with which we are dealing with. That is, a particular user will have a particular choice at a particular time. Hence, we have to take care of that and recommend a ranking which balances he user as well as creator satisfaction.

We have a pool of videos which a particular creator has uploaded and his preference sorted accordingly. We also have a particular user for whom we shall present a ranking of recommendations.

## Steps:
- Choose a number N. Shortlist the top N options using info from the log file which is available.
  The log file stores the Pas-Student-Behaviours (PSBs). Those are data from the learning paths of previous students.
  
  For eg, if someone has the list of actions as a -> b -> c -> a -> b -> d, then it will store the frequency of each transition in the matrix.
  That is, | a -> b | = 2, | b -> c | = 1 and so on.

  On the row-side, it will contain the entire list of actions, while on the column side, it will contain only the videos of the particular creator.
  So, if the current student state is suppose $a_T$, And the student has followed a learning path of $a_1, a_2, ... , a_(t-1)$, then it will
  suggest the action will the highest correlation value, and which has been not been chosen before.


- After this, we use a Disjoint Payoff Model, where we compute the expected reward which we will get if we recommend that particular item to the
  user.

  In this, we have a weight matrix W, a feature vector of each arm $y_a$, a feature vector of the user as $x_a$.
  Then we estimate:

  $E[ r_a | W, x_a, y_a ] = x_a^T W y_a$

  Then we rank the arms according to this score and conclude that, this is the optimal ranking for the user.

- Now the last part is that, we need to arrive to an ranking which also takes care of the intital preferences submitted by the creator.
