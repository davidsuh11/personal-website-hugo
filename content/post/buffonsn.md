---
title: "Exploiting linearity of $\\mathbb E$: Buffon's Noodle"
date: 2023-05-09T21:00:21-05:00
draft: false
tags: ['statistics']
---
### Introduction
In a normal treatment of probability theory, one of the first properties of taking expectation $\mathbb E$ is *linearity*: 
$$
\mathbb E[X + Y] = \mathbb E[X] + \mathbb E[Y].
$$

Though it is a pretty unassuming property for most students, it is actually a very useful and interesting property. A common use case is for problems where the different RV's are "obviously" independent.
> *Example 1: Sum of two dice*
>
> Suppose we have two dice. We can denote their pip values as $X_1,X_2$ and then note 
> $$\mathbb E[X_1+X_2] = \mathbb E[X_1] + \mathbb E[X_2] = 2\cdot 3.5 = 7. $$

But are there any more striking examples of using linearity of expectation? Yes -- a classical problem(s) known as *Buffon's {Needle | Noodle}*, with the latter being a short generalization of the former. We will first solve the Needle problem using usual probability theory, before providing a generalized result using expectation.

### Buffon's Needle
The problem statement is as follows: if we have a plane consisting of evenly spaced parallel lines (in one axis), if we have a randomly place line segment of length $\ell$ on the plane, what the probability that the segment intersects one of the lines? A more real-to-life statement often involves a wooden plank floor and the probability a needle (hence the name) intersects the border of two planes. To solve this problem, we first setup a couple of variables. We can denote $x$ as the distance from the center of the line segment to the nearest vertical line segment (where we use the usual notion of point-line distance). Then we can denote $\theta$ as the acute angle formed between the line segment and the vertical line axis.

![no image](/images/buffonsf1.png "Title")

*Diagram of setup variables*

Since the distance $x$ can vary from $0$ to $d$, where $d$ denotes the intervals between vertical lines, and clearly the distribution is uniform, we can conclude 
$$
f_x(t) = \frac{1}{d/2} = 2/d, \qquad t\in[0, d/2]
$$
where $f_x$ denotes the PDF of $x$. In a similar fashion, we can write 
$$
f_{\theta}(t) = 2/\pi, \qquad t\in[0, \pi/2].
$$
We can note that then the needle crosses a vertical line if 
$$
x \leq \frac\ell 2 \sin(\theta). 
$$
From here, we take two cases.

**[Short Needle]**. Suppose $\ell \leq t$. Thus with probability 1, the needle will only cross a single vertical line, if any. Then we can write the probability of crossing 
$$
\begin{align*}
P &= \int_{[0,t/2]\times [0,\pi/2]}f_{x,\theta}(x,\theta) \bm 1_{\\{ x \leq \frac\ell 2 \sin(\theta)\\}} \diff (x,\theta)\\\\
&=\int_{\theta=0}^{\pi/2}\int_{x=0}^{(\ell/2)\sin(\theta)} f_x(x) f_\theta(\theta) \diff x \diff \theta \\\\
&=\int_{\theta=0}^{\pi/2}\int_{x=0}^{(\ell/2)\sin(\theta)} \frac{4}{t\pi} \diff x \diff \theta \\\\
&= \frac{2l}{t\pi}.
\end{align*}
$$

**[Long Needle]**. In this case, we must take into consideration the cases where the needle is long enough to gurantee crossing a vertical line. In particular, if the horizontal component of the needle is longer than $t$, we know the needle is guranteed to cross a vertical line.
