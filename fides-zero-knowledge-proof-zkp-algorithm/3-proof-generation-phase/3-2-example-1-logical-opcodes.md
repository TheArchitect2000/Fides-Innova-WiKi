
### Example 1 (for logical opcode "and")
$`Proof (\mathbb{F}, T)`$: This function outputs  $`\Pi_{Look\hspace{1mm}up}=(Com_{Look\hspace{1mm}up},\pi_{Look\hspace{1mm}up})`$

Assume the following simple sample code:\
\
\
and  R1, R2, R3                             => Gate 1,   p=11\
and  R2, R3, R4                             => Gate 2,  p=11\
and  R3, R1, R5                             => Gate 3,  p=11\
and  R4, R2, R5                              => Gate 4,  p=11




The constraints are as follows:

&#x20;               \
$$R_1^{(2)}=R_2^{(1)} and\hspace{1.3mm} R_3^{(1)}$$                                 \
$$R_2^{(2)}=R_3^{(1)} and\hspace{1.3mm} R_4^{(1)}$$                        \
$$R_3^{(2)}=R_1^{(2)} and\hspace{1.3mm} R_5^{(1)}$$\
$$R_4^{(2)}=R_2^{(2)}  and\hspace{1.3mm} R_5^{(1)}$$ 


Assume have 32 32-bits registers. Also,  assume the initial values of registers are $`R_1^{(1)}=3`$, $`R_2^{(1)}=8`$, $`R_3^{(1)}=15`$, $`R_4^{(1)}=2`$, $`R_5^{(1)}=6`$, $`R_6^{(1)}=...=R_{32}^{(1)}=0`$. Therefore, outputs of the sample code lines are $`R_1^{(2)}=8`$, $`R_2^{(2)}=2`$, $`R_3^{(2)}=0`$ and $`R_4^{(2)}=2`$. Define vector $`V \in \mathbb{F}^4`$ such that $`i^{th}`$ component of it equal to output of $`i^{th}`$ sample code line, i.e.

$$
V=\begin{bmatrix} 
00000000000000000000000000001000\\ 
00000000000000000000000000000010\\
00000000000000000000000000000000\\ 
00000000000000000000000000000010 
\end{bmatrix}
$$

Also, assume index of each row of $`V`$ is inputs of its value. It means that index of the first row is \$`00000000000000000000000000001000\hspace{1mm}00000000000000000000000000001111`$, \
index of the second row is\
$`00000000000000000000000000001111\hspace{1mm}00000000000000000000000000000010`$\
and $`...`$

The Lookup table $`T`$ corresponding to gate "and" has size $`n=2^{2w}=2^{64}`$ and is as following:

$$
T=\begin{bmatrix} 
00000000000000000000000000000000\\ 
00000000000000000000000000000000\\
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::\\
11111111111111111111111111111111
\end{bmatrix}
$$

where, each row of $`T`$ is indexed by possible 32-bits inputs and value of that row is equal to output of "and" operation on inputs corresponding to it. It means that for example, $`T[000010000110000000000000000011000\hspace{1mm}00001100011100000101000000001011]=00001000011000000000000000001000`$.

The proof of claim $`V\in T`$ is done in the following steps:

1- The Prover stores $`c=8`$ sub-tables $`T_i`$ each of size $`n^{\frac{1}{c}}=2^8`$ corresponding with lookup table $`T`$, such that for any $`r\in \{0,1\}^{64}`$ and $`r_i \in \{0,1\}^{8}`$ the following holds:\
$`T(r)=\sum_{i=1}^{8} 2^{4(i-1)} T_i(r_i)`$

In this example, we have for $`i=1,2..,8`$

$$
T_i=\begin{bmatrix} 
0000\\ 
0000\\
0000\\
0000\\
::::::::\\
1111
\end{bmatrix}
$$

where, each row of $`T_i`$ is indexed by possible 4-bits inputs and value of that row is equal to output of "and" operation on inputs corresponding to it.It means that for example, $`T_i[01001\hspace{1mm}1011]=0001`$.\
Now, see the equality $`T(r)=\sum_{i=1}^{8} 2^{4(i-1)} T_i(r_i)`$ for a value of $`r`$.\
For example, if $`r=000010000110000000000000000011000\hspace{1mm}00001100011100000101000000001011`$, have $`T[r]=00001000011000000000000000001000`$. \
Also, have $`r_1=1000\hspace{1mm}1011`$, $`r_2=0001\hspace{1mm}0000`$, $`r_3=0000\hspace{1mm}0000`$, $`r_4=0000\hspace{1mm}0101`$, $`r_5=0000\hspace{1mm}0000`$, $`r_6=0110\hspace{1mm}0111`$, $`r_7=1000\hspace{1mm}1100`$ and $`r_8=0000\hspace{1mm}0000`$. In this case, $`T_1[r_1]=1000`$, $`T_2[r_2]=0000`$, $`T_3[r_3]=0000`$, $`T_4[r_4]=0000`$, $`T_5[r_5]=0000`$, $`T_6[r_6]=0110`$, $`T_7[r_7]=1000`$ and $`T_8[r_8]=0000`$. Therfore, \
$`\sum_{i=1}^{8} 2^{4(i-1)} T_i(r_i)=T_1(r_1)+2^4T_2(r_2)+2^8T_3(r_3)+...+2^{24}T_7(r_7)+2^{28}T_8(r_8)=`$\
$`8+2^4\times 0+2^8\times 0+2^{12}\times 0+2^{16}\times 0+2^{20}\times 6+2^{24}\times 8+2^{28}\times 0=140509192\equiv 10 (\textrm{mod}\hspace{1mm}11)`$\
and also\
$`T(r)=2^3+2^{21}+2^{22}+2^{27}=140509192\equiv 10 (\textrm{mod}\hspace{1mm}11)`$.

2- The Prover calculates $`c=8`$ polynomials $`dim_1`$, $`dim_2`$, ..., $`dim_8`$ as following:\
$`dim_i:\{0,1\}^{2}\to \{0,1\}^{8}`$\
$`dim_i(x)`$= The row number of sub-table $`T_i`$ that is equal to $`i^{th}`$ $`8`$ bits of $`x^{th}`$ component of $`V`$.\
Here,

$`dim_1:\{0,1\}^{2}\to \{0,1\}^{8}`$\
$`dim_1(00)=10001111`$\
$`dim_1(01)=11110010`$\
$`dim_1(10)=10000110`$\
$`dim_1(11)=01100010`$

For each $`i=2,3,...,8`$,\
$`dim_i:\{0,1\}^{2}\to \{0,1\}^{8}`$\
$`dim_i(00)=00000000`$\
$`dim_i(01)=00000000`$\
$`dim_i(10)=00000000`$\
$`dim_i(11)=00000000`$\
3- The Prover calculates $`c=8`$ polynomials $`E_1`$, $`E_2`$, ..., $`E_8`$ as following:

$`E_i:\{0,1\}^{2}\to \{0,1\}^{4}`$\
$`E_i(x)=T_i(dim_i(x))`$\
Here,

$`E_1:\{0,1\}^{2}\to \{0,1\}^{4}`$\
$`E_1(00)=T_1(dim_1(00))=1000`$\
$`E_1(01)=T_1(dim_1(01))=0010`$\
$`E_1(10)=T_1(dim_1(10))=0000`$\
$`E_1(11)=T_1(dim_1(11))=0010`$

For each $`i=2,3,...,8`$,

$`E_i:\{0,1\}^{2}\to \{0,1\}^{4}`$\
$`E_i(00)=T_i(dim_i(00))=0000`$\
$`E_i(01)=T_i(dim_i(01))=0000`$\
$`E_i(10)=T_i(dim_i(10))=0000`$\
$`E_i(11)=T_i(dim_i(11))=0000`$



4- The Prover calculates committments to polynomials $`E_i(x)`$, $`i=1,2,...,8`$ by KZG polynomial commitment scheme as following:\
$`Com_{Look\hspace{1mm}up}^{i}=\sum_{j=0}^{deg_{E_i(x)}}{E_i}_{j}ck(j)`$, where $`{E_i}_{j}`$ is the coefficient of $`x^j`$ of polynomial $`E_i(x)`$.

Here, the first, the Prover calculates polynomial $`E_1(x)`$ by lagrange interpolation such that $`E_1(00)=1000`$, $`E_1(01)=0010`$, $`E_1(10)=0000`$ and $`E_1(11)=0010`$. That means that polynomial $`E_1(x)`$ passes through points $`(0,8)`$, $`(1,2)`$, $`(2,0)`$ and $`(3,2)`$. Therefore, $`E_1(x)=8L_1(x)+2L_2(x)+0L_3(x)+2L_4(x)`$. where 
$`L_1(x)=\frac{(x-1)(x-2)(x-3)}{(-1)(-2)(-3)}=9x^3+x^2+1`$,

$$L_2(x)=6x^3+3x^2+3x$$,

$$L_3(x)=5x^3+2x^2+4x$$, 

$$L_4(x)=2x^3+5x^2+4x$$

Therefore $`E_1(x)=2x^2+3x+8`$.

Now, the Prover calculates polynomials $`E_i(x)`$ for $`i=2,3,..,8`$ by lagrange interpolation such that $`E_i(00)=0000`$, $`E_i(01)=0000`$, $`E_i(10)=0000`$ and $`E_i(11)=0000`$. That means that polynomials $`E_i(x)`$ passes through points $`(0,0)`$, $`(1,0)`$, $`(2,0)`$ and $`(3,0)`$. Therefore, $`E_i(x)=0L_1(x)+0L_2(x)+0L_3(x)+0L_4(x)=0`$.

Therefore, 

$`Com_{Look\hspace{1mm}up}^{1}=\sum_{j=0}^{2}}{E_1}_{j}ck(j)=2ck(3)+3ck(2)+8ck(1)=48\equiv 4(\textrm{mod}\hspace{1mm}11`$

$`Com_{Look\hspace{1mm}up}^{i}=\sum_{j=0}^{0}}{E_i}_{j}ck(j)=0ck(1)=0\equiv 0(\textrm{mod}\hspace{1mm}11`$, $`i=2,3,...,8`$

5-  The Verifier chooses random number $`r \in \{0,1\}^{2}`$ and sends it to the Prover. (Note that the Prover can choose $`r=`$ The last 2 bits of $`hash(h(1))`$, where $`h(x)`$ is a fully random polynomail selected by the Prover and sent to the Verifier). Assume $`r=01`$\
6- The Prover calculates value $`v`$ as following\
$`v=\sum_{i=1}^{8} 2^{4(i-1)} E_i(01)=E_1(01)+2^4E_2(01)+2^8E_3(01)+...+2^{24}E_8(01)=2+0+0+...+0=2`$\
 and sends $`\pi_{Look\hspace{1mm}up}^{1}=v=2`$ to the Verifier.\
 7- The Prover calculates $`y_i=E_i(01)`$ for $`i=1,..,8`$ and sends\
 $`\pi_{Look\hspace{1mm}up}^{2}=y_1=E_1(01)=2`$ and $`\pi_{Look\hspace{1mm}up}^{i+1}=y_i=E_i(01)=0`$ for $`i=2,3,...,8`$ to the Verifier. Also, calculates the proofs for them by KZG polynomial commitment scheme as follows:\
7-1- The Prover calculates
$`Q_1(x)=\frac{E_1(x)-2}{x-1}=\frac{2x^2+3x+6}{x-1}=2x+5`$.\
$`Q_i(x)=\frac{E_i(x)-0}{x-1}=\frac{0}{x-1}=0`$, for $`i=2,3,...,8`$. \
7-2- The Prover calculates\
the proof for $`y_1=E_1(01)=2`$ as $`\pi_{Look\hspace{1mm}up}^{10}=\sum_{j=0}^{1}{Q_1}_{j}ck(j)=2ck(2)+5ck(1)=(2\times 6)+(5\times 2)=0`$.\
the proof for $`y_i=E_i(01)=0`$ as $`\pi_{Look\hspace{1mm}up}^{9+i}=\sum_{j=0}^{0}{Q_i}_{j}ck(j)=0\times ck(1)=0`$.
