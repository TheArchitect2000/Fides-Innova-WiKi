---
description: In this section, we provide an example for the Setup phase settings.
---

# Example 1

$$Setup(1^{\lambda},N)$$:  This function outputs $$pp=PC.Setup(1^{\lambda},d)$$.&#x20;

We consider an input $$x$$ with size of 1. Hence,  $$n_i=1$$. Considering a program which requires three gates for its arithmatization, we have $$n_g=3$$.  In this example, the maximum number of registers which are changed during the execution is $$n_r=1$$. If the computation is done in $$\mathbb{F}$$ of order $$p=181$$, $$|\mathbb{F}|=181$$.  Also, $$|\mathbb{H}|=n=n_g+n_i+1=5$$. Also, $$b$$ is a random number in &lcub; $$1,...,\mid\mathbb{F}\mid-\mid\mathbb{H}\mid$$&rcub;
=&lcub; $$1,...,176$$ &rcub; such as $$b=2$$. Also, $$m=2n_g=6$$, $$|w|=n_g-n_r=2$$, $$|\mathbb{K}|=m=6$$. Hence:&#x20;

$`d=\{d_{AHP}(N,i,j)\}_{i=0,1,...,k_{AHP}, j=1,2,..,s_{AHP}(i)}=\{ 6,6,6,6,6,6,6,6,6,4,7,7,7,8,11,4,6,4,4,5,30\}`$

Now, we run $$KZG.\hspace{1mm}Setup(1^{\lambda},d)$$, considering a generator of $$\mathbb{F}$$, $$g=2$$, for each element in $$d$$:

&#x20;

$$KZG.Setup(1^{\lambda},6)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^5$, $$g \tau$$) 

that for secret element $$\tau=119$$ and generator  $$g=2$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^5$ $$=(2, 57, 86, 98, 78, 51)$$ and $$vk=57$$.

$$KZG.Setup(1^{\lambda},4)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^3$, $$g \tau$$)
 
 that for secret element $$\tau=119$$ and generator  $$g=2$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^3$ $$=(2,57,86,98)$$ and $$vk=57$$.&#x20;

$$KZG.Setup(1^{\lambda},7)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^6$, $$g \tau$$)
 
 that for secret element $$\tau=119$$ and generator  $$g=2$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^6$ $$=(2,57,86,98,78,51,96)$$ and $$vk=57$$.

$$KZG.Setup(1^{\lambda},8)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^7$, $$g \tau$$)
 
 that for secret element $$\tau=119$$ and generator  $$g=2$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^7$ $$=(2,57,86,98,78,51,96,21)$$ and $$vk=57$$.

$$KZG.Setup(1^{\lambda},11)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^{10}$, $$g \tau$$)
 
 that for secret element $$\tau=119$$ and generator  $$g=2$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^{10}$ $$=(2,57,86,98,78,51,96,21,146,179,124)$$ and $$vk=57$$.

$$KZG.Setup(1^{\lambda},6)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^5$, $$g \tau$$)
 
 that for secret element $$\tau=119$$ and generator  $$g=2$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^5$ $$=(2,57,86,98,78,51)$$ and $$vk=57$$.&#x20;


 # Example 1 ( for logical operation "and")

$$Setup(1^{\lambda},s)$$:  This function outputs $$pp=PC.Setup(1^{\lambda},s)$$.&#x20;

If the computation is done in $`\mathbb{F}`$ of order $`p=11`$ and program has $`s=4`$ gate "and", then 

$$KZG.Setup(1^{\lambda},4)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^{3}$, $$g \tau$$)
 
that for secret element $$\tau=3$$ and generator  $$g=2$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^{3}$ $$=(2, 6,7,10 )$$ and $$vk=6$$.

