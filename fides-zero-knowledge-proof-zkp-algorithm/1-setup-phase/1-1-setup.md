---
description: >-
  The first phase in our system is the setup phase. This phase should be run by
  a trusted party.
---

# 1- Setup Phase

The setup phase is crucial for generating the necessary cryptographic parameters. During this phase, a trusted party generates public parameters, $$pp$$. We have defined 18 setting classes for our proving system.

Fields utilized in ZKP:

* (Goldilock- $$\phi$$):  $$p=\phi^2-\phi+1$$ where $$\phi^2 = \phi-1 \hspace{1mm} mod \hspace{1mm} p$$
* (Sophie Germain- $$\phi$$):  a prime number where both p and (2p+1) are prime. $$\phi^2 = \phi-1 \hspace{1mm} mod \hspace{1mm} p$$

Condition for the field utilized in function-hiding ZKP system:

* $$m | (p-1)$$ and $$n | (p-1)$$&#x20;

<table><thead><tr><th width="91">Class</th><th width="74">Number of gates, ng</th><th width="97">Number of inputs, ni</th><th width="142">n=ni+ng+1</th><th width="110">m=2*ng</th><th width="250">Field size, prime number p</th><th width="315">Condition for function-hiding system ZKP</th><th width="275" data-type="number">Generator, g</th><th data-hidden>Row'A</th><th data-hidden>Col'A</th></tr></thead><tbody><tr><td>1</td><td>2</td><td>32</td><td>35</td><td>4</td><td>(Goldilock-1261) = <span class="math">(1261)^2-1261+1 = 1,588,861 </span> </td><td>4 | (1,588,861 -1 ) <br>35 | (1,588,861 -1 )</td><td>17</td><td>33</td><td>33</td></tr><tr><td>2</td><td>4</td><td>32</td><td>37</td><td>8</td><td>(Goldilock-1296) = <span class="math">(1296)^2-1296+1 = 1,678,321</span></td><td>8 | (1,678,321-1 ) <br>37 | (1,678,321-1 )</td><td>11</td><td>67</td><td>67</td></tr><tr><td>3</td><td>8</td><td>32</td><td>41</td><td>16</td><td>(Goldilock-2256) = <span class="math">(2256)^2-2256+1 = 5,087,281</span></td><td>16 | (5,087,281 -1 ) <br>41 | (5,087,281 -1 )</td><td>17</td><td>138</td><td>138</td></tr><tr><td>4</td><td>16</td><td>32</td><td>49</td><td>32</td><td>(Goldilock-1569) = <span class="math">(1569)^2-1569+1 = 2,460,193</span></td><td>32 | (2,460,193 -1 ) <br>49 | (2,460,193 -1 )</td><td>5</td><td>648</td><td>648</td></tr><tr><td>5</td><td>32</td><td>32</td><td>65</td><td>64</td><td>(Goldilock-2496) = <span class="math">(2496)^2-2496+1 = 6,227,521</span></td><td>64 | (6,227,521 -1 ) <br>65 | (6,227,521 -1 )</td><td>7</td><td>1,552</td><td>1,552</td></tr><tr><td>6</td><td>64</td><td>32</td><td>97</td><td>128</td><td>(Goldilock-3201) = <span class="math">(3201)^2-3201+1 = 10,243,201</span></td><td>128 | (10,243,201 -1 ) <br>97 | (10,243,201 -1 )</td><td>21</td><td>4,128</td><td>4,128</td></tr><tr><td>7</td><td>128</td><td>32</td><td>161</td><td>256</td><td>2,060,801  (Sophie Germain)</td><td>256 | (2,060,801 -1 ) <br>161 | (2,060,801 -1 )</td><td>3</td><td>12,352</td><td>12,352</td></tr><tr><td>8</td><td>256</td><td>32</td><td>289</td><td>512</td><td>14,056,961 (Sophie Germain)</td><td>512 | (14,056,961 -1 ) <br>289 | (14,056,961 -1 )</td><td>11</td><td>41,088</td><td>41,088</td></tr><tr><td>9</td><td>512</td><td>32</td><td>545</td><td>1,024</td><td>138,403,841 (Sophie Germain)</td><td>1,024 | (138,403,841 -1 ) <br>545 | (138,403,841 -1 )</td><td>15</td><td>147,712</td><td>147,712</td></tr><tr><td>10</td><td>1,024</td><td>32</td><td>1,057</td><td>2,048</td><td>270,592,001 (sophie Germain)</td><td>2,048 | (270,592,001 -1 ) <br>1,057 | (270,592,001 -1 )</td><td>15</td><td>557,568</td><td>557,568</td></tr><tr><td>11</td><td>2,048</td><td>32</td><td>2,081</td><td>4,096</td><td>272,760,833  (Sophie Germain)</td><td>4,096 | (272,760,833 -1 ) <br>2,081 | (272,760,833 -1 )</td><td>13</td><td>2,163,712</td><td>2,163,712</td></tr><tr><td>12</td><td>4,096</td><td>32</td><td>4,129</td><td>8,192</td><td>14,071,103,489 (Sophie Germain)</td><td>8,192 | (14,071,103,489 -1 ) <br>4,129 | (14,071,103,489 -1 )</td><td>3</td><td>8,521,728</td><td>8,521,728</td></tr><tr><td>13</td><td>8,192</td><td>32</td><td>8,225</td><td>16,384</td><td>673,792,001 (Sophie Germain)</td><td>16,384 | (673,792,001 -1 ) <br>8,225 | (673,792,001 -1 )</td><td>17</td><td>33,820,672</td><td>33,820,672</td></tr><tr><td>14</td><td>16,384</td><td>32</td><td>16,417</td><td>32,768</td><td>59,174,748,161 (Sophie Germain)</td><td>32,768 | (59,174,748,16 -1 ) <br>16,417 | (59,174,748,16 -1 )</td><td>3</td><td>134,750,208</td><td>134,750,208</td></tr><tr><td>15</td><td>32,768</td><td>32</td><td>32,801</td><td>65,536</td><td>236,461,096,961 (Sophie Germain)</td><td>65,536 | (236,461,096,961 -1 ) <br>32,801 | (236,461,096,961 -1 )</td><td>3</td><td>537,935,872</td><td>537,935,872</td></tr><tr><td>16</td><td>65,536</td><td>32</td><td>65,569</td><td>131,072</td><td>42,971,299,841 (Sophie Germain)</td><td>131,072 | (42,971,299,841 -1 ) <br>65,569 | (42,971,299,841 -1 )</td><td>3</td><td>2,149,613,568</td><td>2,149,613,568</td></tr></tbody></table>

## Function-hiding functional commitment Scheme

Function-hiding functional commitment scheme enables the Prover to commit to a secret function $$f$$ and later without revealing any other information about $$f$$, proves that $$y=f(x)$$ for public $$x$$ and $$y$$. This scheme is a tuple $$(Setup,\, Commitment,ProofGeneration, ProofVerification)$$ that contains two major phases, proof of function relation (PFR) phase and algebraic holographic proof (AHP) phase.&#x20;

### Major Phase 1 - A proof of function relation (PFR)

A proof of function relation, $$PFR$$, shows that a committed relation is a function.

### Major Phase 2 - An algebraic holographic proof (AHP)

An algebraic holographic proof, $$AHP$$, is scheme where the prover without revealing any information about function $$f$$, proves that $$y=f(x)$$ for public $$x$$ and $$y$$.  


Both PFR and AHP will be compiled to a standard interactive protocol using a univariate polynomial commitment, $$PC$$, scheme. A $$PC$$ is a commitment scheme for $$\mathbb{F}^{\leq d}[X]$$ with maximum degree $$d\in\mathbb{N}$$ and coefficients in the field $$\mathbb{F}$$. It supports an argument of knowledge for proving the correct evaluation of a committed polynomial at a given point. This scheme is a tuple $$PC=(PC.Setup,PC.Commit,PC.Eval,PC.Check)$$.

In the following section, we will review the setup phase of our system. We also provide an example to clarify the method.

## 1-1- PFR and AHP Setup     

$$Setup(1^{\lambda},N)$$:  This function outputs $$pp=PC.Setup(1^{\lambda},d)$$ where $$\lambda$$ is security parameter and the set&#x20;

 $` d=\{d_{AHP}(N,i,j)\}_{i\in \{0,1,...,k_{AHP}\}, j\in \{1,2,...,s_{AHP}\}}\bigcup \{d_f(N,i,j)\}_{i\in \{1,2,...,k_f\}, j\in \{1,2,...,s_f(j)\}}`$

where  $$N$$ is the maximum supported index size. Also, considering $$d_{AHP}:\mathbb{N}^3\to\mathbb{N}$$, $$d_{AHP}(N,i,j)$$ is the degree bound for $$j^{th}$$ polynomial in round $$i$$ of $$AHP$$.  $$k_{AHP}$$ is the number of rounds in $$AHP$$. Moreover, considering $$s_{AHP}:\mathbb{N}\to\mathbb{N}$$, $$s_{AHP}(i)$$ is the number of polynomials that the Prover sends to the Verifier in round $$i$$ of $$AHP$$. Considering $$d_f:\mathbb{N}^3\to\mathbb{N}$$,  $$d_f(N,i,j)$$ is the degree bound for $$j^{th}$$ polynomial that the Prover sends to the Verifier in round $$i$$  of $$PFR$$. $$k_f$$ is the number of rounds in $$PFR$$. Considering $$s_f:\mathbb{N}\to\mathbb{N}$$,  where $$s_f(i)$$ is the number polynomials that the Prover sends to the Verifier in  round $$i$$ of $$PFR$$.

Note that $$s_{AHP}(0)=s_{f}(0)$$ and for all $$i\in$$ &lcub; $$1,2,...,s_{AHP}(0)$$ &rcub;, $$d_{AHP}(N,0,i)=d_{f}(N,0,i)$$. Also,  there are  $$k_{AHP}=4$$ rounds in $$AHP$$ where in

Round $$0$$: \
$$s_{AHP}(0)=9$$, $$d_{AHP}(N,0,j)=m$$ for $$j\in$$ &lcub; $$1,2,...,s_{AHP}(0)=9$$ &rcub;,\
\
Round 1:\
$$s_{AHP}(1)=6$$, $$d_{AHP}(N,1,1)=|w|+b$$, $$d_{AHP}(N,1,2)=|\mathbb{H}|+b$$,  $$d_{AHP}(N,1,3)=|\mathbb{H}|+b$$,  $$d_{AHP}(N,1,4)=|\mathbb{H}|+b$$,  $$d_{AHP}(N,1,5)=|\mathbb{H}|+2b-1$$, $$d_{AHP}(N,1,6)=2|\mathbb{H}|+b-1$$,\
\
Round 2: \
$$s_{AHP}(2)=2$$, $$d_{AHP}(N,2,1)=|\mathbb{H}|-1$$, $$d_{AHP}(N,2,2)=|\mathbb{H}|+b-1$$, \
\
Round 3: \
$$s_{AHP}(3)=2$$, $$d_{AHP}(N,3,1)=|\mathbb{H}|-1$$,  $$d_{AHP}(N,3,2)=|\mathbb{H}|-1$$,  \
\
Round 4: \
$$s_{AHP}(4)=2$$, $$d_{AHP}(N,4,1)=|\mathbb{K}|-1$$ and  $$d_{AHP}(N,4,2)=6|\mathbb{K}|-6$$. &#x20;

Therefore, 

$`\{d_{AHP}(N,i,j)\}_{i=0,1,...,k_{AHP}, j=1,2,...,s_{AHP}(i)}=\{m,m,m,m,m,m,m,m,m,|w|+b,|\mathbb{H}|+b,|\mathbb{H}|+b,|\mathbb{H}|+b,|\mathbb{H}|+2b-1,`$\
$`2|\mathbb{H}|+b-1,|\mathbb{H}|-1,|\mathbb{H}|+b-1,|\mathbb{H}|-1,|\mathbb{H}|-1,|\mathbb{K}|-1,6|\mathbb{K}|-6\}`$ 

where $$m=2n_g$$ is maximum of number of non-zero entries of matrices $$A$$, $$B$$ and $$C$$ corresponding with arithmetic circuit of function $$f$$ with $$n_g$$ gates. Also, $$\mathbb{H}$$ and $$\mathbb{K}$$ are multiplicative subgroups of field $$\mathbb{F}$$ with order $$m$$ and $$n$$, where  $$n=n_g+n_i+1$$ and $$n_i$$ is the the size of input $$x$$. Note that all the computations are in filed $$\mathbb{F}$$ with order prime number $$p$$.  $$b$$ is a random number in 
&lcub; $$1,2,..,|\mathbb{F}|-|\mathbb{H}|$$ &rcub;. Also, $$w$$ are the intermediate values (witness) which are created when executing a program. $$|w|=n_g-n_r$$ where $$n_r$$ is the number of components in input $$x$$ which are changed during the program execution.&#x20;

For example, if polynomial commitment scheme $$KZG$$ is used in our scheme, $$pp=KZG.Setup(1^{\lambda},d)=(ck,vk)=$$ (&lcub; $$g\tau^i$$ &rcub; $_{i=0}^{d-1}$, $$g \tau$$) where $$ck$$ and $$vk$$ are commitment key and verifying key, respectively. Here $$\tau$$ is a secret element and must be discarded after the $$Setup$$. Also, $$g$$ is a generator of field $$\mathbb{F}$$ with large prime order $$p$$ such that $$p > 2^\lambda > d$$. Also, $$d$$ is maximum degree of polynomials that wants to be committed.

The above mentioned system is programmed in C++ and Rust. The code is available at: \
[https://github.com/FidesInnova/zkiot](https://github.com/FidesInnova/zkiot)

The output of this code are $$ck$$ and $$vk$$ keys stored in a json file and formatted as below.

## 1-2- Setup.json File Format

```
{
    "class":  32-bit Integer,
    "ck": 64-bit Integer Array,
    "vk": 64-bit Integer
}
```

* **`class`**: Represents the configuration's classification. It indicates the number of gates in the ZKP circuit, defining the complexity or size of the cryptographic proof structure.
* **`ck:`(Commitment Key)** The Commitment Key is used by the prover to create commitments to the witness (private inputs).
* **`vk`(Verification Key)**: Used by the verifier to validate the proof against the public inputs and commitments. It allows the verifier to efficiently check the proof without accessing the underlying secret data.

## References

\[1] **Function-hiding Paper:** Boneh, Dan, Wilson Nguyen, and Alex Ozdemir. "Efficient functional commitments: How to commit to a private function." _Cryptology ePrint Archive_ (2021).

\[2] **Marlin Paper:** Chiesa, A., Hu, Y., Maller, M., Mishra, P., Vesely, N., & Ward, N. (2020). Marlin: Preprocessing zkSNARKs with universal and updatable SRS. In _Advances in Cryptology–EUROCRYPT 2020: 39th Annual International Conference on the Theory and Applications of Cryptographic Techniques, Zagreb, Croatia, May 10–14, 2020, Proceedings, Part I 39_ (pp. 738-768). Springer International Publishing.‏‏

\[3] **Function-hiding with SIS Paper:** de Castro, Leo, and Chris Peikert. "Functional commitments for all functions, with transparent setup and from SIS." _Annual International Conference on the Theory and Applications of Cryptographic Techniques_. Cham: Springer Nature Switzerland, 2023.‏&#x20;

\[4] **Lookup table Paper:** Gabizon, Ariel, and Zachary J. Williamson. "plookup: A simplified polynomial protocol for lookup tables." _Cryptology ePrint Archive_ (2020).‏

\[5] **Lattice-based Function-hiding Paper:** Wee, Hoeteck, and David J. Wu. "Lattice-based functional commitments: Fast verification and cryptanalysis." _International Conference on the Theory and Application of Cryptology and Information Security_. Singapore: Springer Nature Singapore, 2023.

\[6] **KZG Polynomial Commitment:** A. Kate, G. M. Zaverucha, and I. Goldberg. Constant-size commitments to polynomials and their applications. In International conference on the theory and application of cryptology and information security, pages 177–194. Springer, 2010.
