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

## Single number evaluation metric

This is used to improve your efficiency or the efficiency of your team in making those decisions. It tells you quickly if the new thing you just tried is working better or worse than your last idea

| Classifier | Precision | Recall| F1 score |

| A  | 95% | 90% | 92.4% |
| B | 98% | 85 | 91.0% |

The definition of **precision** is, of the examples that your classifier recognizes as cats, **What percentage actually are cats?** If classifier A has 95% precision, this means that when classifier A says something is a cat, there's a 95% chance it really is a cat.

And **recall** is, of all the images that really are cats, **what percentage were correctly recognized by your classifier?** So what percentage of actual cats, Are correctly recognized? So if classifier A is 90% recall, this means that of all of the images in, say, your dev sets that really are cats, classifier A pulled out 90% of them correctly.

There's often a tradeoff between precision and recall, and you care about both. The problem with using precision recall as your evaluation metric is that if classifier A does better on recall, which it does here, the classifier B does better on precision, then you're not sure which classifier is better. Therefore, pick a classifier, you just have to find a new evaluation metric that combines precision and recall. = **F1-score**

It is the average of precision, P, and recall, R. The F1 score is defined by this formula, it's **2 / (1/P + 1/R)**.

So what I found for a lot of machine learning teams is that **having a well-defined dev set**, which is **how you're measuring precision and recall**, plus a single number evaluation metric aka single row number evaluation metric allows you to quickly tell if classifier A or classifier B is better, and therefore having a dev set plus single number evaluation metric distance to speed up iterating. 

## Satisficing and Optimizing metric

Let's say that you've decided you care about the classification accuracy of your cat's classifier, this could have been F1 score or some other measure of accuracy, but let's say that in addition to accuracy you also care about the running time. So how long it takes to classify an image and classifier A takes 80 milliseconds, B takes 95 milliseconds, and C takes 1,500 milliseconds, that's 1.5 seconds to classify an image. So one thing you could do is combine accuracy and running time into an overall evaluation metric. And so the costs such as maybe the overall cost is accuracy minus 0.5 times running time.

| Classifier | Accuracy | Running Time | 
|----------|-----------|-------|
| A  | 90% | 80ms |
| B  | 92% | 95ms |
| C  | 95% | 1500ms |










