---
title: Clarifying Linear Regression
layout: post
categories: ml
tags:
- machine leaning
---

At first of all we should make sure what is Regression. 
According to the Sir Francis Galton's definition in statistics, it  means regression toward  the mean. [WIKI](https://en.wikipedia.org/wiki/Regression_toward_the_mean)

And we are going to review two calculus rules that include both power and chain rules.

#### What is the Power rule? [Power rule](https://en.wikipedia.org/wiki/Power_rule)
> 
If $$ y=x^n\\ $$ , $$\dfrac{dy}{dx}=n\cdot x^{n-1} $$

#### What is the Chain rule? [Chain Rul](https://en.wikipedia.org/wiki/Chain_rule)

> If y = f(u) and u = g(x), $${\frac {dy}{dx}}={\frac {dy}{du}}\cdot {\frac {du}{dx}}$$
>
>If $$ {\displaystyle z=f(y)\!} $$ and $$ {\displaystyle y=g(x)\!}$$, so that $${\displaystyle z=f(g(x))=(f\circ g)(x)}$$
>
> Therefore,
> $${\displaystyle \left.{\frac {dz}{dy}}\right|_{y(x)}\cdot \left.{\frac {dy}{dx}}\right|_{x}=f'(y(x))g'(x)=f'(g(x))g'(x)}$$


#### Linear Regression
- Hypothesis $$ h(x)=w.x+b  \\ $$
- Error $$ e(x) =h(x)-y  $$ . `Y` is actual value.
- Cost  $$ Cost(_{w,b}) = \frac{1}{m}\sum_{i=1}^{m} e(x)^{2}  = \frac{1}{m}\sum_{i=1}^{m}(H(x{_{i}})-y_{i})^{2}\\$$
- Learning Rate $$ \alpha$$
> $$\Delta W  = -\alpha \frac{\partial f}{\partial w} = -\alpha\frac{1}{m}\sum_{i=1}^{m}2(Wx{_{i}}+b_{i}-y_{i})x_{i}  \\$$ 
> $$\Delta B  = -\alpha \frac{\partial f}{\partial b} =-\alpha\frac{1}{m}\sum_{i=1}^{m}2(Wx{_{i}}+b_{i}-y_{i})$$

#### Explanation

If $$f(x) = e(x)^{2}  $$ 

According to power and chain rule, $$-\alpha \frac{\partial f}{\partial w} = -\alpha.\frac{\partial f}{\partial e} .\frac{\partial e}{\partial w} 	=-\alpha.2e .\frac{\partial e}{\partial w}  \\$$

If I say partial derivative like derivative w, it means  everything else is a contant except w. thus, $$e(x)=w.x +b -y  = x.w +b -y $$,  $$\therefore \frac{\partial e}{\partial w} = x.1.w^{0} = x \\$$

Therefore, $$ -\alpha \frac{\partial f}{\partial w} =-\alpha.2e .x  =-\alpha.2(wx+b-y) . x \\ $$

Final conclusion is $$ W  := W -\alpha\frac{1}{m}\sum_{i=1}^{m}2(Wx{_{i}}+b_{i}-y_{i})x_{i}  \\$$

In the same way $$\Delta B  = -\alpha \frac{\partial f}{\partial b} = -\alpha.\frac{\partial f}{\partial e} . \frac{\partial e}{\partial b} \\$$

Because, $$e(x)=w.x +b -y   \therefore    \frac{\partial e}{\partial b} = 1.b^{0} = 1 \\$$

So, the result must be $$ B  := B -\alpha\frac{1}{m}\sum_{i=1}^{m}2(Wx{_{i}}+b_{i}-y_{i}) $$