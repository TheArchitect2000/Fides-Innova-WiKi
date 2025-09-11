---
description: >-
  In this section, we will review the proof generation phase of the protocol.
  This phase contains two parts; AHP proof and PFR proof. We also provide an
  example to clarify the method.
---
# 3- Proof Generation Phase
## 3-1- PFR Proof
$`Proof (\mathbb{F}, \mathbb{H}, \mathbb{K}, A, B, C)`$: This function outputs $`\pi_{PFR}=(\pi_{PFR}^1,\pi_{PFR}^2,\pi_{PFR}^3,\pi_{PFR}^4,\pi_{PFR}^5,\pi_{PFR}^6,\pi_{PFR}^7,\pi_{PFR}^8,\pi_{PFR}^9,\pi_{PFR}^{10})`$.
Note that in this polynomial oracle proof, the Prover wants to prove three following claims:\
1- $`row_{PFR_A}(x)`$, $`col_{PFR_A}(x)`$ and $`val_{PFR_A}(x)`$ is encoding of a $`t-SLT`$ matrix.\
2- $`row_{PFR_B}(x)`$, $`col_{PFR_B}(x)`$ and $`val_{PFR_B}(x)`$ is encoding of a $`t-SLT`$ matrix.\
3- $`row_{PFR_C}(x)`$, $`col_{PFR_C}(x)`$ and $`val_{PFR_C}(x)`$ is encoding of a $`t-Diag`$ matrix.

The proof of these claims is done in the following steps:\
1- To prove strictly lower triangularity of the matrices $`A`$ and $`B`$, the Prover must prove that $`\log^{row_{PFR_M}(\gamma^i)}_{\omega}> \log^{col_{PFR_M}(\gamma^i)}_{\omega}`$ for $`i \in `$ &lcub; $`0,1,..,m-1`$ &rcub; and $`M\in`$ &lcub; $`A,B`$ &rcub;. This does by Discrete log comparison protocol.\
2- To prove the first $`t`$ rows of $`A`$ and $`B`$ are all zeros, the Prover must prove that $`row_{PFR_M}(\mathbb{K})\subseteq\{\omega^t,\omega^{t+1},...,\omega^{n-1}\}`$. This does by $`subset\hspace{1mm}over\hspace{1mm} \mathbb{K}\hspace{1mm}protocol`$.\
3- To prove the diagonality of the matrix $`C`$, the Prover must prove that $`seq_{\mathbb{K}}(row_{PFR_C})=seq_{\mathbb{K}}(col_{PFR_C})`$ where $`seq_{\mathbb{K}}(h)=(h(k):k\in\mathbb{K})`$. This does by $`Geometric\hspace{1mm} sequence`$ and $`zero\hspace{1mm}over\hspace{1mm}\mathbb{K}\hspace{1mm}protocols`$.\
4- To prove the first $`t`$ rows of $`C`$ are all zeros, the Prover must prove that there is a vector $`v\in(\mathbb{F^*})^{n-t}`$ so that $`seq_{\mathbb{K}}(val_{PFR_C)}=\vec{v}||\vec{0}`$. This does by $`Geometric\hspace{1mm} sequence`$ and $`zero\hspace{1mm}over\hspace{1mm}\mathbb{K}\hspace{1mm}protocols`$.\
The steps 3 and 4 result that all the non-zero entries of the matrix $`C`$ are in the positions  $`(\omega^t,\omega^t),(\omega^{t+1},\omega^{t+1}),...,(\omega^n,\omega^n)`$.
## 3-2- AHP Proof
$`Proof (\mathbb{F}, \mathbb{H}, \mathbb{K}, A, B, C, X,W,Y)`$: This function outputs\
$`\Pi_{AHP}=(Com_{AHP_X},\pi_{AHP})`$
where\
$`Com_{AHP_X}=(Com_{AHP_X}^{1},Com_{AHP_X}^2,Com_{AHP_X}^3,Com_{AHP_X}^4,Com_{AHP_X}^5,Com_{AHP_X}^6,Com_{AHP_X}^7,Com_{AHP_X}^8,Com_{AHP_X}^9,`$ $`Com_{AHP_X}^{10},Com_{AHP_X}^{11},Com_{AHP_X}^{12},Com_{AHP_X}^{13})`$
and $`\pi_{AHP}=(\pi_{AHP}^{1},\pi_{AHP}^2,\pi_{AHP}^3,\pi_{AHP}^4,\pi_{AHP}^5,\pi_{AHP}^6,\pi_{AHP}^7,\pi_{AHP}^8,\pi_{AHP}^9,\pi_{AHP}^{10},\pi_{AHP}^{11},\pi_{AHP}^{12},\pi_{AHP}^{13},\pi_{AHP}^{14},\pi_{AHP}^{15},\pi_{AHP}^{16},\pi_{AHP}^{17})`$

as following:\
1- The Prover calculates $`z_A=Az`$, $`z_B=Bz`$, $`z_C=Cz`$ where  $`z=(1,X,W,Y)`$, for input $`X`$ that puts in $`Com_{AHP_X}^1`$.\
2- The Prover calculates polynomial $`z_A(x)`$ using indexing $`z_A`$ by elements of $`\mathbb{H}`$. Then, calculates polynomial $`\hat{z}_A(x)`$ using the polynomial $`z_A(x)`$such that $`\hat{z}_A(x)\in \mathbb{F}^{<|\mathbb{H}|+b}[x]`$ that agree with $`z_A(x)`$ on $`\mathbb{H}`$. Note that values of up to $`b`$ locations in this polynomial reveals no information about the witness $`w`$ provided the locations are in $`\mathbb{F}-\mathbb{H}`$. Similarly, calculates polynomial  $`\hat{z}_B(x)`$ so that $`\hat{z}_B(x)\in \mathbb{F}^{<|\mathbb{H}|+b}[x]`$ that agree with $`z_B(x)`$ on $`\mathbb{H}`$. Also, calculates polynomial  $`\hat{z}_C(x)`$ so that $`\hat{z}_C(x)\in \mathbb{F}^{<|\mathbb{H}|+b}[x]`$ that agree with $`z_C(x)`$ on $`\mathbb{H}`$.

Then, calculates polynomial $`\hat{W}(x)\in \mathbb{F}^{<n_g+b}[x]`$ that agree with $`\bar{W}(x)`$ on $`\mathbb{H}[>|X|+1]`$ where  $`\bar{W}:\mathbb{H}[>|X|+1]\to \mathbb{F}`$\
$`\bar{W}(h)=\frac{W(h)-\hat{X}(h)}{v_{\mathbb{H}[\leq |X|+1]}(h)}`$

Note that $`\mathbb{H}[>|X|+1]`$ includes the members of $`\mathbb{H}`$ except for the first $`|X|+1`$ members. Also, $`v_{\mathbb{H}[\leq |X|+1]}(h)`$ is vanishing polynomial on $`\mathbb{H}[\leq |X|+1]`$ and $`\hat{X}(h)`$ is the polynomial obtained using indexing $`x`$ by elements of $`\mathbb{H}[\leq |X|+1]`$.

3- The Prover finds polynomial  $`h_0(x)`$ so that $`\hat{z}_A(x)\hat{z}_B(x)-\hat{z}_C(x)=h_0(x)v_{\mathbb{H}}(x)`$.

4- The Prover samples a fully random $`s(x)\in\mathbb{F}^{<2|\mathbb{H}|+b-1}[x]`$ and computes sum $`\sigma_1=\sum_{k\in \mathbb{H}}s(k)`$

5- The Prover sends $`Com_{AHP_X}^2=\sum_{i=0}^{deg_{\hat{W}(x)}}\hat{w}_i\hspace{1mm}ck(i)`$,  $`Com_{AHP_X}^{3}=\sum_{i=0}^{deg_{\hat{z}_A(x)}}\hat{z}_{A_i}ck(i)`$, $`Com_{AHP_X}^{4}=\sum_{i=0}^{deg_{\hat{z}_B(x)}}\hat{z}_{B_i}ck(i)`$,  $`Com_{AHP_X}^{5}=\sum_{i=0}^{deg_{\hat{z}_C(x)}}\hat{z}_{C_i}ck(i)`$, $`Com_{AHP_X}^{6}=\sum_{i=0}^{deg_{h_0(x)}}h_{0_i}ck(i)`$, and  $`Com_{AHP_X}^{7}=\sum_{i=0}^{deg_{s(x)}}s_i\hspace{1mm}ck(i)`$, where $`\hat{w}_i`$ is coefficient of $`x^i`$ in polynomial $`\hat{W}(x)`$, $`\hat{z}_{A_i}`$ is coefficient of $`x^i`$ in polynomial $`\hat{z}_A(x)`$, $`\hat{z}_{B_i}`$ is coefficient of $`x^i`$ in polynomial $`\hat{z}_B(x)`$, $`\hat{z}_{C_i}`$ is coefficient of $`x^i`$ in polynomial $`\hat{z}_C(x)`$, $`h_{0_i}`$ is coefficient of $`x^i`$ in polynomial $`h_0(x)`$, $`s_{i}`$ is coefficient of $`x^i`$ in polynomial $`s(x)`$.

6- The Verifier chooses random numbers $`\alpha`$, $`\eta_A`$, $`\eta_B`$, $`\eta_C`$ and sends them to the Prover. (Note that the Prover can choose $`\alpha=hash(s(0)+s(1)+1)`$, $`\eta_A=hash(s(2)+s(3)+2)`$, $`\eta_B=hash(s(4)+s(5)+3)`$, $`\eta_C=hash(s(6)+s(7)+4)`$.

7- The Prover finds polynomials $`g_1(x)`$ and $`h_1(x)`$ so that
&#x20; $`s(x)+r(\alpha,x)\sum_{M}\eta_M\hat{z}_M(x)-(\sum_{M}\eta_Mr_M(\alpha,x))\hat{z}(x)=h_1(x)v_{\mathbb{H}}(x)+xg_1(x)+\frac{\sigma_1}{|\mathbb{H}|}`$ $`(1)`$
where $`\hat{z}(x)=\hat{W}(x)v_{\mathbb{H}[\leq |X|+1]}(x)+\hat{X}(x)`$ that agree with $`z`$ on $`\mathbb{H}`$ and $`r(x,y)=u_{\mathbb{H}}(x,y)=\frac{v_{\mathbb{H}}(x)-v_{\mathbb{H}}(y)}{x-y}`$, $`v_{\mathbb{H}}(x)=\prod_{h\in \mathbb{H}}(x-h)=x^{|\mathbb{H}|}-1`$. Therefore\
$`r(x,y)=\frac{x^{|\mathbb{H}|}-y^{|\mathbb{H}|}}{x-y}`$. (Note that $`$r(x,y)`$ satisfies two useful algebraic properties. First, the univariate polynomials $`(r(x,a))_{a\in \mathbb{H}}`$ are linearly independent and $`r(x,y)`$ is their (unique) low-degree extension. Second, $`r(x,y)`$ vanishes on the square $`\mathbb{H}\times \mathbb{H}`$ except for on the diagonal, where it takes on the (non-zero) values $`(r(a,a))_{a\in \mathbb{H}}`$.). Also $`r_M(x,y)=\sum_{k\in \mathbb{H}}r(x,k)\hat{M}(k,y)`$ for $`M\in \{A,B,C\}`$ where $`\hat{A}(x,y)`$ is a bivariate polynomial that passes from  25 points where theses points are obtained using indexing rows and columns of $$A$$ by elements of $`\mathbb{H}`$. This polynomial can obtain as following:
- $`\hat{A}(x,y)=\sum_{k\in \mathbb{K}}u_{\mathbb{H}}(x,\hat{row}_{AHP_A}(k))u_{\mathbb{H}}(y,\hat{col}_{AHP_A}(k))\hat{val}_{AHP_A}(k)`$, $$\hat{B}(x,y)$$ similarly as following:
- $`\hat{B}(x,y)=\sum_{k\in \mathbb{K}}u_{\mathbb{H}}(x,\hat{row}_{AHP_B}(k))u_{\mathbb{H}}(y,\hat{col}_{AHP_B}(k))\hat{val}_{AHP_B}(k)`$
and $`\hat{C}(x,y)`$ similarly as following:
- $`\hat{C}(x,y)=\sum_{k\in \mathbb{K}}u_{\mathbb{H}}(x,\hat{row}_{AHP_C}(k))u_{\mathbb{H}}(y,\hat{col}_{AHP_C}(k))\hat{val}_{AHP_C}(k)`$
- The Prover sends $`Com_{AHP_X}^{8}=\sum_{i=0}^{deg_{g_1(x)}}g_{1_i}ck(i)`$ and $`Com_{AHP_X}^{9}=\sum_{i=0}^{deg_{h_1(x)}}h_{1_i}ck(i)`$ to the Verifier where $`g_{1_i}`$ is coefficient of $`x^i`$ of polynomial $`g_1(x)`$ and $`h_{1_i}`$ is coefficient of $`x^i`$ of polynomial $`h_1(x)`$.

8- The Verifier selects $`\beta_1\in \mathbb{F}-\mathbb{H}`$ and sends it to the Prover. (The Prover can selects $`\beta_1=hash(s(8))\in \mathbb{F}-\mathbb{H}`$).&#x20;

9- The Prover calculates $`\sigma_2=\sum_{k\in\mathbb{H}}r(\alpha,k)\sum_{M}\eta_M\hat{M}(k,\beta_1)`$. Then, the Prover finds $`g_2(x)`$ and $`h_2(x)`$ so that $`r(\alpha,x)\sum_M \eta_M\hat{M}(x,\beta_1)=h_2(x)v_{\mathbb{H}}(x)+xg_2(x)+\frac{\sigma_2}{|\mathbb{H}|}`$
The Prover sends $`Com_{AHP_X}^{10}=\sum_{i=0}^{deg_{g_2(x)}}g_{2_i}ck(i)`$ and $`Com_{AHP_X}^{11}=\sum_{i=0}^{deg_{h_2(x)}}h_{2_i}ck(i)`$ where $`g_{2_i}`$ is coefficient of $`x^i`$ of polynomial $`g_2(x)`$ and $`h_{2_i}`$ is coefficient of $`x^i`$ of polynomial $`h_2(x)`$.

10- The Verifier selects $`\beta_2\in \mathbb{F}-\mathbb{H}`$ and sends it to the Prover.  (The Prover can select $`\beta_2=hash(s(9))\in \mathbb{F}-\mathbb{H}`$).&#x20;

11- The Prover calculates $`\sigma_3=\sum_{k\in\mathbb{K}}(\sum_M \eta_M\frac{v_{\mathbb{H}}(\beta_2)v_{\mathbb{H}}(\beta_1)\hat{val_{AHP_M}}(k)}{(\beta_2-\hat{row_{AHP_M}}(k))(\beta_1-\hat{col_{AHP_M}}(k))})`$. Then, the Prover finds polynomials $`g_3(x)`$ and $`h_3(x)`$ so that $`h_3(x)v_{\mathbb{K}}(x)=a(x)-b(x)(xg_3(x)+\frac{\sigma_3}{|\mathbb{K}|})`$ where $`a(x)=\sum_{M\in \{A,B,C\}} \eta_M v_{\mathbb{H}}(\beta_2)v_{\mathbb{H}}(\beta_1)\hat{val}_{AHP_M}(x)\prod_{N\in\{A,B,C\}-\{M\}}(\beta_2-\hat{row}_{AHP_N}(x))(\beta_1-\hat{col}_{AHP_N}(x))`$ and $`b(x)=\prod_{M\in\{A,B,C\}}(\beta_2-\hat{row}_{AHP_M}(x))(\beta_1-\hat{col}_{AHP_M}(x))`$;

The Prover sends $`Com_{AHP_X}^{12}=\sum_{i=0}^{deg_{g_3(x)}}g_{3_i}ck(i)`$ and $`Com_{AHP_X}^{13}=\sum_{i=0}^{deg_{h_3(x)}}h_{3_i}ck(i)`$ where $`g_{3_i}`$ is coefficient of $`x^i`$ of polynomial $`g_3(x)`$ and $`h_{3_i}`$ is coefficient of $`x^i`$ of polynomial $`h_3(x)`$.

12- The Prover sends $`\pi_{AHP}^1=\sigma_1`$, $`\pi_{AHP}^2=(\hat{w_0},\hat{w_1},\hat{w_3},...,\hat{w_{|W|+b-1}})`$,  
$`\pi_{AHP}^3=(\hat{z}_{A_0},\hat{z}_{A_1},...,\hat{z}_{A_{|H|+b-1}})`$, $`\pi_{AHP}^4=(\hat{z}_{B_0},\hat{z}_{B_1},...,\hat{z}_{B_{|H|+b-1}})`$, $`\pi_{AHP}^5=(\hat{z}_{C_0},\hat{z}_{C_1},...,\hat{z}_{C_{|H|+b-1}})`$, $`\pi_{AHP}^6=(h_{0_0},h_{0_1},...,h_{0_{|H|+2b-2}})`$ and  $`\pi_{AHP}^7=(s_0,s_1,...,s_{2|H|+b-2})`$ 

13- The Prover sends $`\pi_{AHP}^8=(g_{1_0},...,g_{1_{|H|-2}})`$ and $`\pi_{AHP}^{9}=(h_{1_0},...,h_{1_{|H|+b-2}})`$.

14-The Prover sends $`\pi_{AHP}^{10}=\sigma_2`$, $`\pi_{AHP}^{11}=(g_{2_0},...,g_{2_{|H|-2}})`$ and $`\pi_{AHP}^{12}=(h_{2_0},...,h_{2_{|H|-2}})`$.&#x20;

15- The Prover sends $$\pi_{AHP}^{13}=\sigma_3$$, $$\pi_{AHP}^{14}=(g_{3_0},...,g_{3_{|K|-2}})$$ and $$\pi_{AHP}^{15}=(h_{3_0},...,h_{3_{6|K|-6}})$$ .

16- The Prover chooses random values $`\eta_{row_{AHP_A}}`$, $`\eta_{col_{AHP_A}}`$, $`\eta_{val_{AHP_A}}`$, $`\eta_{row_{AHP_B}}`$, $`\eta_{col_{AHP_B}}`$, $`\eta_{val_{AHP_B}}`$, $`\eta_{row_{AHP_C}}`$, $`\eta_{col_{AHP_C}}`$, $`\eta_{val_{AHP_C}}`$,  $`\eta_{\hat{w}}`$, $`\eta_{\hat{z}_A}`$, $`\eta_{\hat{z}_B}`$, $`\eta_{\hat{z}_C}`$, $`\eta_{\hat{z}}`$, $`\eta_{h_0}`$, $`\eta_s`$, $`\eta_{g_1}`$, $`\eta_{h_1}`$, $`\eta_{g_2}`$, $`\eta_{h_2}`$, $`\eta_{g_3}`$ and $`\eta_{h_3}`$ of $`\mathbb{F}`$ The Verifier can choose as following:
$`\eta_{row_{AHP_A}}=hash(s(10))`$, $`\eta_{col_{AHP_A}}=hash(s(11))`$, $`\eta_{val_{AHP_A}}=hash(s(12))`$, $`\eta_{row_{AHP_B}}=hash(s(13))`$ , $`\eta_{col_{AHP_B}}=hash(s(14))`$ , $`\eta_{val_{AHP_B}}=hash(s(15))`$, $`\eta_{row_{AHP_C}}=hash(s(16))`$ , $`\eta_{col_{AHP_C}}=hash(s(17))`$ , $`\eta_{val_{AHP_C}}=hash(s(18))`$,
$`\eta_{\hat{w}}=hash(s(19))`$, $`\eta_{\hat{z}_A}=hash(s(20))`$, $`\eta_{\hat{z}_B}=hash(s(21))`$, $`\eta_{\hat{z}_C}=hash(s(22))`$,  $`\eta_{h_0}=hash(s(23))`$, $`\eta_{s}=hash(s(24))`$, $`\eta_{g_1}=hash(s(25))`$, $`\eta_{h_1}=hash(s(26))`$, $`\eta_{g_2}=hash(s(27))`$, $`\eta_{h_2}=hash(s(28))`$, $`\eta_{g_3}=hash(s(29))`$, $`\eta_{h_3}=hash(s(30))`$.

17- The Prover builds the linear combination

$`p(x)=\eta_{row_{AHP_A}}\hat{row}_{AHP_A}(x)+\eta_{col_{AHP_A}}\hat{col}_{AHP_A}(x)+\eta_{val_{AHP_A}}\hat{val}_{AHP_A}(x)+\eta_{row_{AHP_B}}\hat{row}_{AHP_B}(x)+\eta_{col_{AHP_B}}\hat{col}_{AHP_B}(x)+\eta_{val_{AHP_B}}\hat{val}_{AHP_B}(x)+`$

$`\eta_{row_{AHP_C}}\hat{row}_{AHP_C}(x)+\eta_{col_{AHP_C}}\hat{col}_{AHP_C}(x)+\eta_{val_{AHP_C}}\hat{val}_{AHP_C}(x)+\eta_{\hat{w}}\hat{w}(x)+\eta_{\hat{z}_A}\hat{z}_A(x)+\eta_{\hat{z}_B}\hat{z}_B(x)+\eta_{\hat{z}_C}\hat{z}_C(x)+\eta_{h_0}h_0(x)+\eta_ss(x)\eta_{g_1}g_1(x)+`$

$`\eta_{h_1}h_1(x)+\eta_{g_2}g_2(x)+\eta_{h_2}h_2(x)+\eta_{g_3}g_3(x)+\eta_{h_3}h_3(x)`$

18- The Prover calculates $`p(x)`$ in $`x=x'`$ (value of $`x'`$ is received from the Verifier. Also, can select as $`x'=hash(s(22)))`$, then puts it in $`\pi_{AHP}^{16}`$. Therefore, $`\pi_{AHP}^{16}=p(x')=y'`$.

19- The Prover computes $`\pi_{AHP}^{17}=PC.Eval(ck,p(x),d_p,r_p,x')`$ where $`d_p`$ is degree bound of $`p(x)`$ and $`r_p`$ is a random value. For example, if the polynomial commitment scheme $`KZG`$ is used, then the Prover calculates polynomial 
$`q(x)=\frac{p(x)-y'}{x-x'}`$ and $`\pi_{AHP}^{17}=g\hspace{1mm}q(\tau)`$ by using $`ck`$ as following: $`\pi_{AHP}^{17}=\sum_{i=0}^{deg_{q(x)}}q_i\hspace{1mm}ck(i)`$, where $`q_i`$ is the coefficient of $`x^i`$ of $`q(x)`$.

## 3-3- Proof Structure
Proof set is
$`\Pi_{AHP}=(Com_{AHP_X},\pi_{AHP})`$
where
$`Com_{AHP_X}=(Com_{AHP_X}^{1},Com_{AHP_X}^2,Com_{AHP_X}^3,Com_{AHP_X}^4,Com_{AHP_X}^5,Com_{AHP_X}^6,Com_{AHP_X}^7,Com_{AHP_X}^8,Com_{AHP_X}^9,`$ $`Com_{AHP_X}^{10},Com_{AHP_X}^{11},Com_{AHP_X}^{12},Com_{AHP_X}^{13})`$

$`Com_{AHP_X}^1=X`$,\
$`Com_{AHP_X}^2=\sum_{i=0}^{deg_{\hat{W}(x)}}\hat{w}_i\hspace{1mm}ck(i)`$, \
$`Com_{AHP_X}^{3}=\sum_{i=0}^{deg_{\hat{z}_A(x)}}\hat{z}_{A_i}ck(i)`$, \
$`Com_{AHP_X}^{4}=\sum_{i=0}^{deg_{\hat{z}_B(x)}}\hat{z}_{B_i}ck(i)`$,  \
$`Com_{AHP_X}^{5}=\sum_{i=0}^{deg_{\hat{z}_C(x)}}\hat{z}_{C_i}ck(i)`$,  \
$`Com_{AHP_X}^{6}=\sum_{i=0}^{deg_{h_0(x)}}h_{0_i}ck(i)`$,    \
$`Com_{AHP_X}^{7}=\sum_{i=0}^{deg_{s(x)}}s_i\hspace{1mm}ck(i)`$, \
$`Com_{AHP_X}^{8}=\sum_{i=0}^{deg_{g_1(x)}}g_{1_i}ck(i)`$,  \
$`Com_{AHP_X}^{9}=\sum_{i=0}^{deg_{h_1(x)}}h_{1_i}ck(i)`$,  \
$`Com_{AHP_X}^{10}=\sum_{i=0}^{deg_{g_2(x)}}g_{2_i}ck(i)`$,  \
$`Com_{AHP_X}^{11}=\sum_{i=0}^{deg_{h_2(x)}}h_{2_i}ck(i)`$, \
$`Com_{AHP_X}^{12}=\sum_{i=0}^{deg_{g_3(x)}}g_{3_i}ck(i)`$,\
$`Com_{AHP_X}^{13}=\sum_{i=0}^{deg_{h_3(x)}}h_{3_i}ck(i)`$;

and $`\pi_{AHP}=(\pi_{AHP}^{1},\pi_{AHP}^2,\pi_{AHP}^3,\pi_{AHP}^4,\pi_{AHP}^5,\pi_{AHP}^6,\pi_{AHP}^7,\pi_{AHP}^8,\pi_{AHP}^9,\pi_{AHP}^{10},\pi_{AHP}^{11},\pi_{AHP}^{12},\pi_{AHP}^{13},\pi_{AHP}^{14},\pi_{AHP}^{15},\pi_{AHP}^{16},\pi_{AHP}^{17})`$

$`\pi_{AHP}^1=\sigma_1`$, \
$`\pi_{AHP}^2=(\hat{w}_0,\hat{w}_1,\hat{w}_3,...,\hat{w}_{n_g+b-1})`$,  \
$`\pi_{AHP}^3=(\hat{z}_{A_0},\hat{z}_{A_1},...,\hat{z}_{A_{|H|+b-1}})`$, \
$`\pi_{AHP}^4=(\hat{z}_{B_0},\hat{z}_{B_1},...,\hat{z}_{B_{|H|+b-1}})`$,  \
$`\pi_{AHP}^5=(\hat{z}_{C_0},\hat{z}_{C_1},...,\hat{z}_{C_{|H|+b-1}})`$, \
$`\pi_{AHP}^6=(h_{0_0},h_{0_1},...,h_{0_{|H|+2b-2}})`$,\
$`\pi_{AHP}^7=(s_0,s_1,...,s_{2|H|+b-2})`$,\
$`\pi_{AHP}^8=(g_{1_0},...,g_{1_{|H|-2}})`$,\
$`\pi_{AHP}^{9}=(h_{1_0},...,h_{1_{|H|+b-2}})`$,\
$`\pi_{AHP}^{10}=\sigma_2`$,\
$`\pi_{AHP}^{11}=(g_{2_0},...,g_{2_{|H|-2}})`$,\
$`\pi_{AHP}^{12}=(h_{2_0},...,h_{2_{|H|-2}})`$, \
$`\pi_{AHP}^{13}=\sigma_3`$, \
$`\pi_{AHP}^{14}=(g_{3_0},...,g_{3_{|K|-2}})`$, \
$`\pi_{AHP}^{15}=(h_{3_0},...,h_{3_{6|K|-6}})`$,\
$`\pi_{AHP}^{16}=y'`$,\
$`\pi_{AHP}^{17}=\sum_{i=0}^{deg_{q(x)}}q_i\hspace{1mm}ck(i)`$.

where $`\hat{w}_i`$ is coefficient of $`x^i`$ in polynomial $`\hat{W}(x)`$, $`\hat{z}_{A_i}`$ is coefficient of $`x^i`$ in polynomial $`\hat{z}_A(x)`$, $`\hat{z}_{B_i}`$ is coefficient of $`x^i`$ in polynomial $`\hat{z}_B(x)`$, $`\hat{z}_{C_i}`$ is coefficient of $`x^i`$ in polynomial $`\hat{z}_C(x)`$, $`h_{0_i}`$ is coefficient of $`x^i`$ in polynomial $`h_0(x)`$, $`s_{i}`$ is coefficient of $`x^i`$ in polynomial $`s(x)`$, $`g_{1_i}`$ is coefficient of $`x^i`$ of polynomial $`g_1(x)`$ and $`h_{1_i}`$ is coefficient of $`x^i`$ of polynomial $`h_1(x)`$, $`g_{2_i}`$ is coefficient of $`x^i`$ of polynomial $`g_2(x)`$ and $`h_{2_i}`$ is coefficient of $`x^i`$ of polynomial $`h_2(x)`$, $`g_{3_i}`$ is coefficient of $`x^i`$ of polynomial $`g_3(x)`$ and $`h_{3_i}`$ is coefficient of $`x^i`$ of polynomial $`h_3(x)`$.

* Size of AHP proof: $`|\Pi_{AHP}|=10|\mathbb{H}|+7|\mathbb{K}|+|W|+8b+6`$.
* CommitmentID is explained on the Commitment Phase page.
* DeviceEncodedID = Base64\<MAC>
* Input and Output are the device input and output, respectively.

## 3-4- Proof JSON file format

<pre><code>{
    "commitmentId": 64-bit,
    "class": 32-bit Integer,
    "input": 64-bit Integer,
    "output": 64-bit Integer,    
       
    "P_AHP1": 64-bit Integer,
    "P_AHP2": 64-bit Array,
    "P_AHP3": 64-bit Array,
    "P_AHP4": 64-bit Array,
    "P_AHP5": 64-bit Array,
    "P_AHP6": 64-bit Array,
    "P_AHP7": 64-bit Array,
    "P_AHP8": 64-bit Array,
    "P_AHP9": 64-bit Array,
    "P_AHP10": 64-bit Integer,
    "P_AHP11": 64-bit Array,
    "P_AHP12": 64-bit Array,
    "P_AHP13": 64-bit Integer,
    "P_AHP14": 64-bit Array,
    "P_AHP15": 64-bit Array,
    "P_AHP16": 64-bit Integer, 
    "P_AHP17": 64-bit Array,
      
    "Com_AHP1_x": 64-bit Integer,
    "Com_AHP2_x": 64-bit Integer,
    "Com_AHP3_x": 64-bit Integer,
    "Com_AHP4_x": 64-bit Integer,
    "Com_AHP5_x": 64-bit Integer,
    "Com_AHP6_x": 64-bit Integer,   
    "Com_AHP7_x": 64-bit Integer,
    "Com_AHP8_x": 64-bit Integer,
    "Com_AHP9_x": 64-bit Integer,
    "Com_AHP10_x": 64-bit Integer,
    "Com_AHP11_x": 64-bit Integer,
    "Com_AHP12_x": 64-bit Integer,
    "Com_AHP13_x": 64-bit Integer
}
</code></pre>


## 3-5- ZKP Generation Time Results

| Class | Number of Gates | ZKP generation time in C++ - Qemu - Ubuntu | ZKP generation time in Rust - UBUNTU - AMD RYZEN 5 (Lib ARK-FF, NALGEBRA, RUSTNUMIAL, P=GitBook) | ZKP generation time in Rust - UBUNTU - AMD RYZEN 5 (Customized Lib, P=GitBook) | ZKP generation time in Rust - UBUNTU - AMD RYZEN 5 (Lib ARK-FF, NALGEBRA, RUSTNUMIAL, P=2^32-X) |
|:-----:|:---------------:|:-----------------------------------------------:|:---------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------------------:|
| 1     | 2               | 116 milliseconds                               | 1.3 milliseconds (Gold) (p=1,588,861)                                                         | 2.10 milliseconds                                                                                | 1.61 milliseconds (p=4,266,982,721)                                                               |
| 2     | 4               | 110 milliseconds                               | 1.8 milliseconds (Gold) (p=1,678,321)                                                         | 3.35 milliseconds                                                                                | 2.15 milliseconds (p=1,750,690,817)                                                               |
| 3     | 8               | 150 milliseconds                               | 2.2 milliseconds (Gold) (p=5,087,281)                                                         | 6.55 milliseconds                                                                                | 3.18 milliseconds (p=1,750,690,817)                                                               |
| 4     | 16              | 254 milliseconds                               | 4.3 milliseconds (Gold) (p=2,460,193)                                                         | 16.46 milliseconds                                                                               | 5.79 milliseconds (p=1,750,690,817)                                                               |
| 5     | 32              | 378 milliseconds                               | 10.1 milliseconds (Gold) (p=6,227,521)                                                        | 56.67 milliseconds                                                                               | 11.52 milliseconds (p=3,731,752,961)                                                              |
| 6     | 64              | 882 milliseconds                               | 32.33 milliseconds (Gold) (p=10,243,201)                                                      | 256 milliseconds                                                                                 | 43.42 milliseconds (p=3,731,752,961)                                                              |
| 7     | 128             | 2.809 seconds                                  | 139.9 milliseconds (Sophie) (p=2,060,801)                                                     | 1433 milliseconds                                                                                | 143.75 milliseconds (p=1,750,690,817)                                                             |
| 8     | 256             | 9.980 seconds                                  | 740.2 milliseconds (Sophie) (p=14,056,961)                                                    | 10187 milliseconds                                                                               | 821.09 milliseconds (p=3,731,752,961)                                                             |
| 9     | 512             | 38.092 seconds                                 | 4.62 seconds (Sophie) (p=138,403,841)                                                         | 81406 milliseconds                                                                               | 5122.83 milliseconds (p=4,101,888,001)                                                            |
| 10    | 1024            | 2.48 minutes                                   | 33.2798 seconds (Sophie) (p=270,592,001) → (p=4,xxx,xxx,xxx) → 45 or 37 sec                   | > 5 minutes                                                                                      | 37380.19 milliseconds (p=4,182,269,953)                                                           |
| 11    | 2048            | 9.88 minutes                                   | 5.1 minutes (Sophie)                                                                          | > 5 minutes                                                                                      |                                                                                                  |
| 12    | 4096            |                                               | 43.13 minutes (Sophie)                                                                        | > 5 minutes                                                                                      |                                                                                                  |
| 13    | 8192            |                                               | 4.97 hours (Sophie)                                                                           | > 5 minutes                                                                                      | > 5 minutes (p=3,503,718,401)                                                                     |
| 14    | 16384           |                                               | (Sophie)                                                                                      | > 5 minutes                                                                                      |                                                                                                  |
| 15    | 32768           |                                               | (Sophie)                                                                                      | > 5 minutes                                                                                      |                                                                                                  |
| 16    | 65536           |                                               | (Sophie)                                                                                      | > 5 minutes                                                                                      |                                                                                                  |



---
# 3- Proof Generation Phase (for logical operation "and")
$`Proof (\mathbb{F}, T)`$: This function outputs  $`\pi=`$\
The proof of these claims is done in the following steps:\
1- The Prover stores $`\alpha`$ sub-tables $`T_i`$ each of size $`n^{\frac{1}{c}}`$ corresponding with lookup table $`T`$ for operation "and", such that for any $`r\in \{0,1\}^{\log n}`$, the following holds:\
$`T(r)=g(T_1(r_1),...,T_{c}(r_c))`$\
where $n=2^w$ and $`w`$ is the size of register. For operation "and", we have,\
$`T(r)=\sum_{i=1}^{c} 2^{\frac{w}{c}(i-1)} T_i(r_i)`$\
2- The Prover calculates $`c`$ polynomials $`dim_1`$, $`dim_2`$, ..., $`dim_c`$ as following:\
$`dim_i:\{0,1\}^{\log s}\to \{0,1\}^{\log n^{\frac{1}{c}}}`$\
$`dim_i(x)`$= The row number of sub-table $`T_i`$ that is equal to $`i^{th}`$ $`\frac{w}{c}`$ bits of $`x^{th}`$ component of $`V`$.\
3- The Prover calculates $`c`$ polynomials $`E_1`$, $`E_2`$, ..., $`E_c`$ as following:\
$`E_i:\{0,1\}^{\log s}\to \{0,1\}^{\frac{w}{c}}`$\
$`E_i(x)=T_i(dim_i(x))`$\
4- The Prover commites to polynomials $`E_1(x)`$, $`E_2(x)`$, ..., $`E_c(x)`$ by KZG polynomial commitment as following:\
$`cm_{E_i}=\sum_{j=0}^{deg_{E_i(x)}}{E_i}_{j}ck(j)`$, where $`{E_i}_{j}`$ is the coefficient of $`x^j`$ of polynomial $`E_i(x)`$, $`i=1,2,...,c`$.\
5-  The Verifier chooses random numbers $`r \in \{0,1\}^{\log s}`$ and sends it to the Prover. (Note that the Prover can choose $`r=`$ The last $`\log s`$ bits of $`hash(h(1))`$, where $`h(x)`$ is a fully random polynomail selected by the Prover and send to the Verifier.)\
6- The Prover calculates value $`v`$ as following and send it to the Verifier.\
$`v=\sum_{i=1}^{c} 2^{\frac{w}{c}(i-1)} E_i(r)`$\
Note: value $`v`$ is $`r^{th}`$ component of vector $`V`$. In fact, in this step the Prover wants to calculate the multiplication $`M T`$ in a random row of $`M`$. The result of this multiplication, is\ 
$` \sum_{k\in \{0,1\}^{\log s}} M(r,k) T(k)`$ \
Now, since each row  of matrix $`M`$ has only one non-zero element (namely the 1), above value is rewrited as\
$`\sum_{k\in \{0,1\}^{\log s}} eq(r,k) T(dim(k))`$ \
where $`eq(r,k)`$ is equality function, defined as follows\
$`eq(r,k)=\begin{cases}1\hspace{2cm}r=k\\0\hspace{2.2cm}\text{otherwise}\end{cases}`$ \
Now, according to property in step 1, have \
$`\sum_{k\in \{0,1\}^{\log s}} eq(r,k) T(dim(k))=\sum_{k\in \{0,1\}^{\log s}} eq(r,k) g(T_1(dim_1(k)),...,T_c(dim_c(k)))=`$
$`\sum_{k\in \{0,1\}^{\log s}} eq(r,k) \sum_{i=1}^{c} 2^{\frac{w}{c}(i-1)} T_i(dim_i(k))`$\
Since $`dim_i(k)=E_i(k)`$, therefore, the above value is rewrited as\
$`\sum_{k\in \{0,1\}^{\log s}} eq(r,k) \sum_{i=1}^{c} 2^{\frac{w}{c}(i-1)} E_i(k)`$\
according to definition of equality function, above value is equal to $`v`$. \
7- 



