
# 1- Setup Phase (for logical opcode "and")
##  functional commitment Scheme
 Suppose that the verifier has a commitment to a Look up table $`T\in \mathbb{F}^n`$ corresponding to an operation for example "and". Also, Suppose vector $`V\in \mathbb{F}^s`$ includes the outputs of $`s`$ program lines. In this scheme, the Prover wishes to prove that all entries in vector $`V`$ are in the Look up table $`T`$. There is a simple, commonly known way to prove this statement:
 prove the existence of a matrix $`M\in\mathbb{F}^{s\times n}`$ where each row has only one non-zero element (namely the 1) such that the following statement works:\
 $`M·T=V`$
 
##  setup
The setup phase is crucial for generating the necessary cryptographic parameters. During this phase, a trusted party generates public parameters, $$pp$$. In this scheme, a polynomial commitment scheme is required. If polynomial commitment scheme $$KZG$$ is used in our scheme, $$pp=KZG.Setup(1^{\lambda},s)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^{s-1}$, $$g \tau$$) where $$ck$$ and $$vk$$ are commitment key and verifying key, respectively. Here $$\tau$$ is a secret element and must be discarded after the $$Setup$$. Also, $$g$$ is a generator of field $$\mathbb{F}$$ with large prime order $$p$$ such that $$p > 2^\lambda > s$$. Also, $$s$$ is the number operations in program which is operation "and".

