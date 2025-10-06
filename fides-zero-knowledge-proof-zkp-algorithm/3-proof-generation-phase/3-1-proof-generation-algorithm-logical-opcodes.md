---
description: >-
  In this section, we will review the proof generation phase of the protocol.
  This phase contains two parts; AHP proof and PFR proof. We also provide an
  example to clarify the method.
---

# 3- Proof Generation Phase (for logical opcode "and")
$`Proof (\mathbb{F}, T)`$: This function outputs  $`\Pi_{Look\hspace{1mm}up}=(Com_{Look\hspace{1mm}up},\pi_{Look\hspace{1mm}up})`$\
The proof of these claim is done in the following steps:\
1- The Prover stores $`c`$ sub-tables $`T_i`$ each of size $`n^{\frac{1}{c}}`$ corresponding with lookup table $`T`$, such that for any $`r\in \{0,1\}^{\log n}`$, the following holds:\
$`T(r)=g(T_1(r_1),...,T_{c}(r_c))`$\
where $n=2^w$, $`w`$ is the size of register and $`r_i \in \{0,1\}^{\log {n^{\frac{1}{c}}}}`$. For operation "and", we have,\
$`T(r)=\sum_{i=1}^{c} 2^{\frac{w}{c}(i-1)} T_i(r_i)`$\
2- The Prover calculates $`c`$ polynomials $`dim_1`$, $`dim_2`$, ..., $`dim_c`$ as following:\
$`dim_i:\{0,1\}^{\log s}\to \{0,1\}^{\log n^{\frac{1}{c}}}`$\
$`dim_i(x)`$= The row number of sub-table $`T_i`$ that is equal to $`i^{th}`$ $`\frac{w}{c}`$ bits of $`x^{th}`$ component of $`V`$.\
3- The Prover calculates $`c`$ polynomials $`E_1`$, $`E_2`$, ..., $`E_c`$ as following:\
$`E_i:\{0,1\}^{\log s}\to \{0,1\}^{\frac{w}{c}}`$\
$`E_i(x)=T_i(dim_i(x))`$\
4- The Prover calculates committments to polynomials $`E_i(x)`$, $`i=1,2,...,c`$ by KZG polynomial commitment scheme as following:\
$`Com_{Look\hspace{1mm}up}^{i}=\sum_{j=0}^{deg_{E_i(x)}}{E_i}_{j}ck(j)`$, where $`{E_i}_{j}`$ is the coefficient of $`x^j`$ of polynomial $`E_i(x)`$, .\
5-  The Verifier chooses random numbers $`r \in \{0,1\}^{\log s}`$ and sends it to the Prover. (Note that the Prover can choose $`r=`$ The last $`\log s`$ bits of $`hash(h(1))`$, where $`h(x)`$ is a fully random polynomail selected by the Prover and send to the Verifier.)\
6- The Prover calculates value $`v`$ as following and sends $`\pi_{Look\hspace{1mm}up}^{1}=v`$ to the Verifier.\
$`v=\sum_{i=1}^{c} 2^{\frac{w}{c}(i-1)} E_i(r)`$\
Note: value $`v`$ is $`r^{th}`$ component of vector $`V`$. In fact, in this step the Prover wants to calculate the multiplication $`M.T`$ in a random row of $`M`$. The result of this multiplication, is\ 
$`\sum_{k\in \{0,1\}^{\log n}} M(r,k) T(k)`$ \
Now, since each row  of matrix $`M`$ has only one non-zero element (namely the 1), above value is rewrited as\
$`\sum_{k\in \{0,1\}^{\log s}} eq(r,k) T(dim(k))`$ \
where $`eq(r,k)`$ is equality function, defined as follows\
$`eq(r,k)=\begin{cases}1\hspace{2.2cm}r=k\\0\hspace{2.2cm}\text{otherwise}\end{cases}`$ \
Now, according to property in step 1, have \
$`\sum_{k\in \{0,1\}^{\log s}} eq(r,k) T(dim(k))=\sum_{k\in \{0,1\}^{\log s}} eq(r,k) g(T_1(dim_1(k)),...,T_c(dim_c(k)))=`$
$`\sum_{k\in \{0,1\}^{\log s}} eq(r,k) \sum_{i=1}^{c} 2^{\frac{w}{c}(i-1)} T_i(dim_i(k))`$\
Since $`dim_i(k)=E_i(k)`$, therefore, the above value is rewrited as\
$`\sum_{k\in \{0,1\}^{\log s}} eq(r,k) \sum_{i=1}^{c} 2^{\frac{w}{c}(i-1)} E_i(k)`$\
according to definition of equality function, above value is equal to $`v`$. \
7- The Prover calculates $`y_i=E_i(r)`$ for $`i=1,..,c`$ and sends $`\pi_{Look\hspace{1mm}up}^{i+1}=y_i`$ to the Verifier. Also, calculates the proofs for them by KZG polynomial commitment scheme as follows:\
7-1- The Prover calculates $`Q_i(x)=\frac{E_i(x)-y_i}{x-r}`$.\
7-2- The Prover calculates the proof for $`y_i=E_i(r)`$ as $`\pi_{Look\hspace{1mm}up}^{c+1+i}=\sum_{j=0}^{deg_{Q_i(x)}}{Q_i}_{j}ck(j)`$ where $`{Q_i}_{j}`$ is coefficient of $`x^j`$ in polynomial $`Q_i(x)`$.
##  Proof Structure
Proof set is
$`\Pi_{Look\hspace{1mm}up}=(Com_{Look\hspace{1mm}up},\pi_{Look\hspace{1mm}up})`$
where
$`Com_{Look\hspace{1mm}up}=(Com_{Look\hspace{1mm}up}^{1},Com_{Look\hspace{1mm}up}^2,...,Com_{Look\hspace{1mm}up}^{c})`$

$`Com_{Look\hspace{1mm}up}^1=\sum_{j=0}^{deg_{E_1(x)}}{E_1}_{j}ck(j)`$,\
$`Com_{Look\hspace{1mm}up}^2=\sum_{j=0}^{deg_{E_2(x)}}{E_2}_{j}ck(j)`$, \
:\
$`Com_{Look\hspace{1mm}up}^c=\sum_{j=0}^{deg_{E_c(x)}}{E_c}_{j}ck(j)`$;

and $`\pi_{Look\hspace{1mm}up}=(\pi_{Look\hspace{1mm}up}^{1},\pi_{Look\hspace{1mm}up}^2,...,\pi_{Look\hspace{1mm}up}^{c+1},\pi_{Look\hspace{1mm}up}^{c+2},...,\pi_{Look\hspace{1mm}up}^{2c+1})`$

$`\pi_{Look\hspace{1mm}up}^1=v`$, \
$`\pi_{Look\hspace{1mm}up}^2=y_1`$,  \
:\
$`\pi_{Look\hspace{1mm}up}^{c+1}=y_c`$, \
$`\pi_{Look\hspace{1mm}up}^{c+2}=\sum_{j=0}^{deg_{Q_1(x)}}{Q_1}_{j}ck(j)`$,  \
:\
$`\pi_{Look\hspace{1mm}up}^{2c+1}=\sum_{j=0}^{deg_{Q_c(x)}}{Q_c}_{j}ck(j)`$

where $`{E_i}_{j}`$ is coefficient of $`x^j`$ in polynomial $`{E_1}_{j}(x)`$, $`{Q_i}_{j}`$ is coefficient of $`x^j`$ in polynomial $`Q_i(x)`$.





