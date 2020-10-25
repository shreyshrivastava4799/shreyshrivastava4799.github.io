---
layout: post
title: "Independence Dimension Inequality"
description: "An explanation for" 
tags: [ Backpropagation Algorithm, Generative Adversarial Networks, Multilayer Perceptron, Transformers]
comments: true
excerpt_separator: <!--more-->
---
 <!--more-->
For every linearly independent set of vectors $$x_1, x_2 ... x_k \in R^n$$, the cardinality of the set $$k$$ and dimension of vector space $$n$$, satisfy the following inequality $$k \le n$$.  This cardinality bound on the set of independent vectors also means that any set with $$n+1$$ vectors  $$\in R^n$$ is always linearly dependent. 


To prove this inequality, we employ Mathematical Induction.
### Base step: 
We first prove the above inequality for base case : $$n=1$$. We hypothesis a set of vectors $$x_1, x_2 ....x_k \in R^1$$ is a linearly independent and then try to find a bound on the maximum value of $$k$$. 

Now let us define our vectors $$x_i$$ =  $$\dfrac{x_i}{x_1}*x_1$$, observe that this representation is only possible for $$x_i \in R^1$$.  But validity of this representation proves that two vectors in $$R^1$$ can never be linearly independent. Thus the inequality $$k \le n$$ is satisfied for the base case.

### Inductive Step: 
We now prove the inequality for $$n \ge 2$$.
Assume that the given inequality is true for $$x_i \in R^{n-1}$$ and we need to prove it is true for $$x_i \in R^{n}$$ as well. 


The linearly independent set of vectors $$x_1, x_2 ....x_{k} \in R^{n-1}$$  i.e $$\sum_{i=1}^{k}\beta_{i}x_i = 0$$ only when $$\forall i \,\, \beta_i = 0$$ has a bound on cardinality $$k$$ s.t $$k \le n-1$$.  Now, lets define $$y_i = \begin{bmatrix} x_i \\ \alpha_i \end{bmatrix} \in R^n$$ where $$x_i \in R^{n-1}, \alpha_i \in R$$ then the cardinality $$k$$ of the set of linearly independent vector $$y_1, y_2 ... y_k \in R^n$$  satisfies the inequality $$k \le n$$. Here $$\alpha_i$$ can either be all zero or atleast one non-zero set of scalars. 


#### Case 1:
For the case $$\forall{i} \,\, \alpha_i = 0$$, we have assumed that the set of vectors $$y_1, y_2 ... y_k \in R^n$$  is linearly independent, thus $$\sum_{i=0}^{k} \beta_{i}y_i = 0$$ if and only if $$\forall i \,\, \beta_i = 0$$. Now because  $$y_i = \begin{bmatrix} x_i \\ 0 \end{bmatrix}$$, $$\sum_{i=1}^{k}\beta_{i}x_i = 0$$ if and only if $$\forall i \,\, \beta_i = 0$$. We have shown that linear independence of  $$y_1, y_2 ... y_k \in R^n$$ implies linear independence of $$x_1, x_2 ....x_{k} \in R^{n-1}$$. But we know by the inductive hypothesis that cardinality of a linearly independent set of vectors $$\in R^{n-1}$$ is bounded by $$n-1$$. Thus for this case $$k \le n-1$$. 

#### Case 2:
For the case $$\exists{i} \,\, \alpha_i \ne 0$$ , we assume $$\alpha_j \ne 0$$ and define a set of vectors $$z_i \in R^{n-1}$$ with cardinality $$k-1$$. 

$$  \Large z_i = x_i - \dfrac{\alpha_i}{\alpha_j}*x_j ,\,\,\, i = 1, 2, ...j-1$$

$$  \Large z_i = x_{i+1} - \dfrac{\alpha_{i+1}}{\alpha_j}*x_j ,\,\,\, i = j, j+1, ...k-1$$ 

Now $$\displaystyle \sum_{i=1}^{k-1}\beta_{i}z_i = 0$$

$$ \Large \displaystyle \sum_{i=0}^{j-1}  \beta_{i}(x_i - \dfrac{\alpha_i}{\alpha_j}*x_j) + \sum_{i=j}^{k-1}  \beta_{i}(x_{i+1} - \dfrac{\alpha_{i+1}}{\alpha_j}*x_j) = 0$$

Substituting index $$i$$ by $$i-1$$ in the second summation : 

$$ \Large \displaystyle \sum_{i=0}^{j-1}  \beta_{i}(x_i - \dfrac{\alpha_i}{\alpha_j}*x_j) + \sum_{i=j+1}^{k}  \beta_{i-1}(x_{i} - \dfrac{\alpha_{i}}{\alpha_j}*x_j) = 0$$

$$ \Large \displaystyle \sum_{i=0}^{j-1}\beta_{i}x_i -\dfrac{1}{\alpha_j}(\sum_{i=0}^{j-1}\beta_{i}\alpha_i + \sum_{i=j+1}^{k}\beta_{i-1}\alpha_i)x_j+ \sum_{i=j+1}^{k}\beta_{i-1}x_i = 0$$

Now we can establish equivalence between $$\displaystyle \sum_{i=1}^{k-1}\beta_{i}z_i = 0$$ and $$\displaystyle \sum_{i=0}^{k} \gamma_{i}y_i = 0$$  from the previous equation where $$\gamma_i = \beta_i$$ for  $$i = \{1, 2, ...j-1\}$$, $$\gamma_i = \beta_{i-1}$$ for  $$i = \{j+1, j+2, ...k\}$$ and $$\displaystyle \gamma_j = -\dfrac{1}{\alpha_j}(\sum_{i=0}^{j-1}\beta_{i}\alpha_i + \sum_{i=j+1}^{k}\beta_{i-1}\alpha_i)$$. But we know by the inductive hypothesis the set of vectors $$y_1, y_2...y_k \in R^n$$ is linearly independent thus $$\displaystyle \sum_{i=0}^{k} \gamma_{i}y_i = 0$$ only and only if $$\forall i \,\, \gamma_i = 0$$ which implies $$\forall i \,\, \beta_i = 0$$. We have shown that linear independence of the set of vectors $$y_i \in R^n$$ with cardinality $$k$$ implies linear independence of the set of vectors $$z_i \in R^{n-1}$$ with cardinality $$k-1$$. But we know by the inductive hypothesis that cardinality of a linearly independent set of vectors $$\in R^{n-1}$$ is bounded by $$n-1$$. Thus for this case $$k-1 \le n-1$$ or $$k \le n$$.

Hence proved.