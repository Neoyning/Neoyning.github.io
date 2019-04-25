---
layout: post
title:  "Sun Rise \"Probability\" and \"Uncertainty\""
date:   2019-03-24
categories: self-learning
---

Laplace asked the question: <br />
 - **_What is the probability that the sun will rise tomorrow, given that it has risen
every day before?_**

Let \\(X_i\\) be a random variable taking values in \\(\\{0,1\\}\\) . Let \\(\\{X_i = 1\\}\\) denote the
event that the sun has risen in day \\(i\\) and \\(\\{X_i = 0\\}\\) otherwise.<br />
Assume that the rising of the sum is a **Bernoulli process** with an unknown parameter(probability) \\(\theta\\).

There are two cases of defining \\(\theta\\),
 - the probability of sun rise **\\(\theta\\) is conatant**.
 - the probability of sun rise **\\(\theta\\) is uniformly distributed between \\([0,1]\\)**.
 
**Formulate the problem as: \\(P\\{X_{n}=1/(X_1=1,X_2=1,...,X_2=1,X_{n-1}=1)\\}\\)**

---
 
>**Bernoulli process**: a finite or infinite sequence of independent random variables \\(X_1,X_2,X_3,...\\), such that
> * For each \\(i\\), the value of \\(X_i\\) is either 0 or 1;
> * For all values of \\(i\\), the probability that \\(\\{X_i = 1\\}\\) is the same number \\(\theta\\). 

So the probability of sun has risen k days in a total n days can be expressed as:
\\[
P[\\text{sun rise k days in n days}]=\\binom{n}{k}\\theta^{k}(1-\theta)^{n-k}=\\frac{n!}{k!(n-k)!}\\theta^{k}(1-\theta)^{n-k}
\\]

---
 
For conditional probability, introducing **Bayes' theorem** and **Law of total probability**.
>**Bayes' theorem with Law of total probability:** 
> * \\(P(A_i/B)=\frac{P(A_i\cap B)}{P(B)}=\frac{P(B/A_i)P(A_i)}{P(B)}\underset{discrete}{=}\frac{P(B/A_i)P(A_i)}{\sum\limits_{j=1}^m P(B/A_j)P(A_j)}\underset{continuous}{=}\frac{P(B/a)f_A(a)}{\int_{a\in S_A}P(B/a)f_A(a)da}\\)
> * \\(\\{A_1,A_2,...,A_m\\}\\) are partitions of the sample space \\(S_A\\), \\(A\in S_A\\), \\(A_\square\\) : \\(A = A_\square\\)

---

### Case 1: \\(\theta=constant\\)
The probability of sun has risen \\(n-1\\) days:
\\[P\\{X_1=1,X_2=1,...,X_2=1,X_{n-1}=1\\}= \binom{n-1}{n-1}\theta^{n-1}(1-\theta)^0=\theta^{n-1}\\]
Similarly, the probability of sun has risen \\(n\\) days:
\\[P\\{X_1=1,X_2=1,...,X_2=1,X_{n}=1\\}= \theta^{n}\\]
From Bayes' theorem:
\\[P\\{X_{n}=1/(X_1=1,X_2=1,...,X_2=1,X_{n-1}=1)\\}=\frac{P\\{X_1=0,X_2=1,...,X_2=1,X_{n}=1\\}}{P\\{X_1=0,X_2=1,...,X_2=1,X_{n-1}=1\\}}=\theta\\]

---
 
### Case 2: \\(\theta\sim U(0,1)\\)
In this case, \\(\theta\sim U(0,1)\\), \\(\theta\\) is assigned a uniform distribution to describe the uncertainty about its true value. Set up the term as below,

\\[
 \begin{aligned}
	&\text{1. prior pdf: } f_\theta(\theta) = 1,\theta\in(0,1)\\\
	&\text{2. likelihood function: } P(X_1=1,X_2=1,...,X_{n-1}=1/\theta)=\theta^{n-1}\\\
	&\text{3. normalizing constant: }P(X_1=1,X_2=1,...,X_{n-1}=1)=\int_0^1 P(X_1=1,X_2=1,...,X_{n-1}=1/\theta) f_\theta(\theta) d\theta\\\
	&\text{4. posterior pdf: } f_{(\theta/X_1=1,X_2=1,...,X_{n-1}=1)}(\theta)=\frac{\text{likelihood function}\times \text{prior pdf}}{\text{normalizing constant}}=n\theta^{n-1}
 \end{aligned}
\\]
By using given information, we update our "believe" of \\(\theta\\) from a prior distribution to a posterior distribution
\\[f_\theta(\theta)=1\quad\longrightarrow\quad f_{(\theta/X_1=1,X_2=1,...,X_{n-1}=1)}(\theta)=n\theta^{n-1}\\]
\\[\theta\in(0,1)\\]
So we know the distribution of \\(\theta\\) given all previous \\(n-1\\) days sun has risen.

For a new day at \\(n\\), we use the posterior distribution of \\(\theta\\).

Let
\\[P\\{X_n=1/(X_1=1,X_2=1,...,X_2=1,X_{n-1}=1)\\}=P\\{X^\star_{n}=1\\}\\]
where \\(P\\{X^\star_{n}=1\\}\\) represents the probability of sun will rise at \\(n\\) day, using the posterior(updated) distribution of \\(\theta\\).<br />
By using the **Law of total probability** of continuous distribution.\\
\\[P\\{X^\star_{n}=1\\}=\int_0^1P[X^\star_{n}=1/\theta]f_{(\theta/X_1=1,X_2=1,...,X_{n-1}=1)}(\theta)d\theta=\int_0^1\theta\cdot n\theta^{n-1}d\theta=\frac{n}{n+1}\\]
finally, get
\\[P\\{X_{n}=1/(X_1=1,X_2=1,...,X_2=1,X_{n-1}=1)\\}=\frac{n}{n+1}\\]
