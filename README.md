# Structuring-ML-Projects
_Tips on how to structure your machine learning project from deeplearning.ai_

## Assumptions in ML
#### 1. Fit Training set well on cost function - 
First, make sure that you're at least doing well on the training set. For some applications, this might mean doing comparably to human level performance. If your algorithm is not fitting the training set well on the cost function, then you might **train a bigger network** or switch to a **better optimization algorithm**, like the Adam optimization algorithm.

#### 2. Fit Dev set well on cost function - 
If your algorithm is not doing well on the dev set, **try regularization** or get a **bigger training set**.

#### 3. Fit Test set well on cost function - 
If it does well on the dev set but not the test set, it probably **means you've overtuned to your dev set**, and you need to go back and **find a bigger dev set**.

#### 4. Performs well in real world - 
If it does well on the test set, but it isn't delivering to you a happy cat picture app user, then what that means is that you want to go back and **change either the dev set** or the **cost function**. Because if doing well on the test set according to some cost function doesn't correspond to your algorithm doing what you need it to do in the real world, then it means that either **your dev test set distribution isn't set correctly**, or your **cost function isn't measuring the right thing**.

_When training a neural network, try not to use early stopping. It's not a bad technique, quite a lot of people do it. But early stopping difficult to think about. Because this is an op that simultaneously affects how well you fit the training set, because if you stop early, you fit the training set less well. It also simultaneously is often done to improve your dev set performance._ 
