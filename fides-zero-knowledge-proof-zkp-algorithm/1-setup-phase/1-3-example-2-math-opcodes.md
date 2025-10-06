# Example 2 ( for math opcode )

$$Setup(1^{\lambda},N)$$:  This function outputs $$pp=PC.Setup(1^{\lambda},d)$$.&#x20;

We consider an input $$x$$ with size of 32. Hence,  $$n_i=32$$. Considering a program which requires 4  gates for its arithmatization, we have $$n_g=4$$.  In this example, the maximum number of registers which are changed during the execution is $$n_r=2$$ (Please see Example 2 in the Commitment phase). If the computation is done in $$\mathbb{F}$$ of order $$p=1,678,321$$, $$|\mathbb{F}|=1678321$$.  Also, $$|\mathbb{H}|=n=n_g+n_i+1=37$$. Also, $$b$$ is a random number in &lcub; $$1,...,|\mathbb{F}|-|\mathbb{H}|$$&rcub; = &lcub; $$1,...,1678321-37=1678284$$ &rcub; such as $$b=2$$. Also, $$m=2n_g=8$$, $$|w|=n_g-n_r=2$$, $$|\mathbb{K}|=m=8$$. Hence:&#x20;

$`d=\{d_{AHP}(N,i,j)\}_{i=0,1,...,k_{AHP}, j=1,2,..,s_{AHP}(i)}=\{ 8,8,8,8,8,8,8,8,8,4,39,39,39,40,75,36,38,36,36,7,42\}`$

Now, we run $$KZG.\hspace{1mm}Setup(1^{\lambda},d)$$, considering a generator of $$\mathbb{F}$$, $$g=11$$, for each element in $$d$$:

&#x20;

$$KZG.Setup(1^{\lambda},138)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^{137}$, $$g \tau$$) 

that for secret element $$\tau=119$$ and generator  $$g=11$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^{137}$ $$=(11,1309,...)$$ and $$vk=1309$$.

$$KZG.Setup(1^{\lambda},4)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^{3}$, $$g \tau$$) 

that for secret element $$\tau=119$$ and generator  $$g=11$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^{3}$ $$=(11,1309,...)$$ and $$vk=1309$$.

$$KZG.Setup(1^{\lambda},39)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^{38}$, $$g \tau$$) 

that for secret element $$\tau=119$$ and generator  $$g=11$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^{38}$ $$=(11,1309,...)$$ and $$vk=1309$$.

$$KZG.Setup(1^{\lambda},40)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^{39}$, $$g \tau$$) 

that for secret element $$\tau=119$$ and generator  $$g=11$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^{39}$ $$=(11,1309,...)$$ and $$vk=1309$$.

$$KZG.Setup(1^{\lambda},75)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^{74}$, $$g \tau$$) 

that for secret element $$\tau=119$$ and generator  $$g=11$$  outputs $$ck=$$ &lcub; $$g\tau^i$$ &rcub; $_{i=0}^{74}$ $$=(11,1309,...)$$ and $$vk=1309$$.



