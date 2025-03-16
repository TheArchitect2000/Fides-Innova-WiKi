# Example 1

Assume the following sample code:\
\
\
mul R1, R1, 5                              => Gate 1,   p=181\
add R1, R1, 11                             => Gate 2,  p=181\
mul  R1, R1, 26                          => Gate 3,  p=181




The constraints are as follows considering $$p=181$$:

&#x20;               \
$$R_1^{(2)}-5R_1^{(1)}=0$$                                 \
$$R_1^{(3)}-R_1^{(2)}-11=0$$                        \
$$R_1^{(4)}-26R_1^{(3)}=0$$


To keep the example simple and understandable, we continue with $$n_g=3$$ and $$n_i=1$$.

The Prover calculates square matrices $$A$$, $$B$$ and $$C$$ of order $$n_g+n_i+1=3+1+1=5$$ based on above construction:

$$
A=\begin{bmatrix} 
0&0&0&0&0\\ 
0&0&0&0&0\\ 
0&1&0&0&0\\ 
1&0&0&0&0\\ 
0&0&0&1&0
\end{bmatrix}
$$

$$
B=\begin{bmatrix}
0&0&0&0&0\\
0&0&0&0&0\\
5&0&0&0&0\\
11&0&1&0&0\\
26&0&0&0&0
\end{bmatrix}
$$

$$
C=\begin{bmatrix}
0&0&0&0&0\\
0&0&0&0&0\\
0&0&1&0&0\\
0&0&0&1&0\\
0&0&0&0&1
\end{bmatrix}
$$

At we see, the matrices $$A$$ and $$B$$ are $$2-SLT$$ and matrix $$C$$ is $$2-Diag$$. Also $$Az\hspace{1mm}o\hspace{1mm}Bz=Cz$$.

We consider multiplicative subgroup $$\mathbb{H}$$ of order $$n=n_g+n_i+1=5$$ with generator\
&#x20;$$\omega=2^{36}\equiv 59 (\textrm{mod}\hspace{1mm}181)$$. Note that if $$g$$ is a generator of field $$\mathbb{F}$$ of order $$p$$, then, $$g^{\frac{p-1}{n}}$$ is a generator of a multiplicative subgroup of it of order $$n$$. Therefore, $$\mathbb{H}=$$ &lcub; $$1,\omega,\omega^2,\omega^3,\omega^4$$ &rcub; = &lcub; $$1,59,42,125,135$$ &rcub;.

Also, consider multiplicative subgroup $$\mathbb{K}$$ of order $$m=2n_g=6$$ where $$t=n_i+1=2$$ with generator $$\gamma=g^{\frac{p-1}{m}}=2^{30}\equiv49(\textrm{mod}\hspace{1mm}181)$$. Therefore, $$\mathbb{K}=$$ &lcub; $$1,\gamma,\gamma^2,...,\gamma^5$$ &rcub; = &lcub; $$1,49,48,180,132,133$$ &rcub; .

### &#x20;PFR Commitment

$$Commit(ck=(2,66,83,91,96,24,2,66,83),m_f=(A,B,C),s\in R)$$:&#x20;

1-  The Prover Selects  $$s=(s_1,...,s_{s_{AHP}(0)})$$ of random space $$R$$.

2- The Prover calculates $$\overrightarrow{O}=Enc(m_f=(A,B,C))$$ as encoded index as following:.

First, calculates the polynomial $$row_{PFR_A}(x)$$. Since matrix $$A$$ has  three non-zero entries that the first of them is in the second row, so $$c_0=2$$ and $$row_{PFR_A}(\gamma^0)=\omega^2$$ , note that rows numbered of zero, the second is in the third row, so $$c_1=3$$ and $$row_{PFR_A}(\gamma^1)=\omega^3$$ and the third is in the fourth row, so $$c_2=4$$ and  $$row_{PFR_A}(\gamma^2)=\omega^4$$.  Note that to construct all three polynomials, we read the entries in the matrix in row or column order. Here they are read in row order.

According to the values ​​defined for $$\gamma$$ and $$\omega$$, we have $$row_{PFR_A}(1)=42$$, $$row_{PFR_A}(43)=125$$ and $$row_{PFR_A}(39)=135$$. Therefore based on Lagrange polynomials, have $$row_{PFR_A}(x)=\sum_{i=1}^{3}y_iL_i(x)$$, so $$row_{PFR_A}(x)=42L_1(x)+125L_2(x)+135L_3(x)$$, where $$L_1(x)=\frac{(x-43)(x-39)}{(1-43)(1-39)}=\frac{(x-43)(x-39)}{(-42)(-38)}$$. Now, since $$-42\equiv139\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$, $$-38\equiv143\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$, $$-43\equiv138\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ and $$-39\equiv142\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ ,  therefore $$L_1(x)=\frac{(x+138)(x+142)}{(139)(143)}$$ and since $$(139)(143)\equiv 148\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ and $$148^{-1}\equiv 170\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ , have $$L_1(x)=170(x+138)(x+142)=170x^2+178x+15$$ .  We get in a similar way that $$L_2(x)=167x^2+17x+178$$ and $$L_3(x)=25x^2+167x+170$$ . Therefore $$row_{PFR_A}(x)=77x^2+109x+37$$ .

Now,  calculates $$col_{PFR_A}(x)$$. Since  matrix $$A$$ has  three non-zero entries that the first of them is in the first column, so $$r_0=1$$ and $$col_{PFR_A}(\gamma^0)=\omega^1$$ , note that columns numbered of zero, the second is in the zero column, so $$r_1=0$$ and $$col_{PFR_A}(\gamma^1)=\omega^0$$ and the third is in the third column, so $$r_2=3$$ and  $$col_{PFR_A}(\gamma^2)=\omega^3$$.  Therefore $$col_{PFR_A}(1)=59$$, $$col_{PFR_A}(43)=1$$ and $$col_{PFR_A}(39)=125$$. So $$col_{PFR_A}(x)=59L_1(x)+L_2(x)+125L_3(x)=109x^2+81x+50$$.&#x20;

Now, calculates $$val_{PFR_A}(x)$$. Since matrix $$A$$ has  three non-zero entries such that the value of all of them is one, therefore $$v_0=v_1=v_2=1$$. So, $$val_{PFR_A}(x)=L_1(x)+L_2(x)+L_3(x)=1$$.

Therefore, the matrix $$A$$ is encoded by   $$row_{PFR_A}(x)=77x^2+109x+37$$, $$col_{PFR_A}(x)=109x^2+81x+50$$ and $$val_{PFR_A}(x)=1$$.

Now,  encodes the matrix $$B$$. First, calculates the polynomial $$row_{PFR_B}(x)$$. Since matrix $$B$$ has four non-zero entries such that the first of them is in the second row, so $$c_0=2$$ and $$row_{PFR_B}(\gamma^0)=\omega^2$$ . The second and the third are in the third row, so $$c_1=c_2=3$$ and $$row_{PFR_B}(\gamma^1)=row_{PFR_B}(\gamma^2)=\omega^3$$ and the fourth is in the fourth row, so $$c_3=4$$ and  $$row_{PFR_B}(\gamma^3)=\omega^4$$.  Therefore, $$row_{PFR_B}(1)=42$$, $$row_{PFR_B}(43)=125$$, $$row_{PFR_B}(39)=125$$ and $$row_{PFR_B}(48)=135$$. So $$row_{PFR_B}(x)=42L_1(x)+125L_2(x)+125L_3(x)+135L_4(x)$$ where $$L_1(x)=\frac{(x-43)(x-39)(x-48)}{(1-43)(1-39)(1-48)}=\frac{(x+138)(x+142)(x+133)}{(139)(143)(134)}=\frac{(x+138)(x+142)(x+133)}{103}$$. Since $$103^{-1}\equiv58\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$, so $$L_1(x)=58(x+138)(x+142)(x+133)=58x^3+62x^2+116x+127$$. We get in a similar way that $$L_2(x)=39x^3+7x^2+19x+116$$, $$L_3(x)=138x^3+155x^2+7x+62$$ and $$L_4(x)=127x^3+138x^2+39x+58$$. Therefore $$row_{PFR_B}(x)=76x^3+35x^2+174x+119$$.

Now, calculates $$col_{PFR_B}(x)$$. Since  matrix $$B$$ has  four non-zero entries that the first, second and fourth of them are in zero column, so $$r_0=r_1=r_3=0$$ and $$col_{PFR_B}(\gamma^0)=col_{PFR_B}(\gamma^1)=col_{PFR_B}(\gamma^3)=\omega^0$$ and the third is in the second column, so $$r_2=2$$ and $$col_{PFR_B}(\gamma^2)=\omega^2$$ .  Therefore $$col_{PFR_B}(1)=1$$, $$col_{PFR_B}(43)=1$$, $$col_{PFR_B}(39)=42$$ and $$col_{PFR_B}(48)=1$$. So $$col_{PFR_B}(x)=L_1(x)+L_2(x)+42L_3(x)+L_4(x)=47x^3+20x^2+106x+9$$.

Now, calculates $$val_{PFR_B}(x)$$. Since matrix $$B$$ has four non-zero entries that value of them are $$5$$, $$11$$, $$1$$ and $$26$$, respectively. Therefore $$v_0=v_1=v_2=1$$ $$val_{PFR_B}(\gamma^0)=5$$, $$val_{PFR_B}(\gamma^1)=11$$, $$val_{PFR_B}(\gamma^2)=1$$ and $$val_{PFR_B}(\gamma^3)=26$$. So,  $$val_{PFR_B}(1)=5$$, $$val_{PFR_B}(43)=11$$, $$val_{PFR_B}(39)=1$$ and $$val_{PFR_B}(48)=26$$. Therefore,  $$val_{PFR_B}(x)=5L_1(x)+11L_2(x)+L_3(x)+26L_4(x)=177x^3+148x^2+42$$.

Therefore, the matrix $$B$$ is encoded by $$row_{PFR_B}(x)=76x^3+35x^2+174x+119$$, $$col_{PFR_B}(x)=47x^3+20x^2+106x+9$$ and  $$val_{PFR_B}(x)=177x^3+148x^2+42$$.

Now, calculates polynomial $$row_{PFR_C}(x)$$.  In a similar way, Since  matrix $$C$$ has  three non-zero entries that are in the third, fourth and fifth rows, therefore  $$row_{PFR_C}(\gamma^0)=\omega^2$$ ,  $$row_{PFR_C}(\gamma^1)=\omega^3$$ and  $$row_{PFR_C}(\gamma^2)=\omega^4$$.  Then  $$row_{PFR_C}(1)=42$$ ,  $$row_{PFR_C}(43)=125$$ and  $$row_{PFR_C}(39)=135$$. So  $$row_{PFR_C}(x)=42L_1(x)+125L_2(x)+135L_3(x)$$, therefore $$row_{PFR_C}(x)=77x^2+109x+37$$.

Now, since $$C$$ is a diagonal matrix, polynomials $$row_{PFR_C}(x)$$ and $$col_{PFR_C}(x)$$ are equal. Also, since the matrix $$C$$ has  three non-zero entries such that the value of all of them is one, therefore $$v_0=v_1=v_2=1$$. So, $$val_{PFR_C}(x)=L_1(x)+L_2(x)+L_3(x)=1$$.

Therefore, the matrix $$C$$ is encoded by  $$row_{PFR_C}(x)=77x^2+109x+37$$, $$col_{PFR_C}(x)=77x^2+109x+37$$ and $$val_{PFR_C}(x)=1$$. Therefore, encoding of $$m_f=(A,B,C)$$ calculates as following: $$\overrightarrow{O}_{PFR}=(37,109,77,0,0,0,0,0,0,50,81,109,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0,119,174,35,76,0,0,0,0,0,9,106,20,47,0,0,0,0,0,42,0,148,177,0,0,0,0,0,37,109,77,0,0,0,0,0,0,37,109,77,0,0,0,0,0,0,37,109,77,0,0,0,0,0,0,1,0,0,0,0,0,0,0,0)$$

3- The Prover calculates commitment by using of KZG commitment scheme  as following:

$$Com_{T}=\sum_{i=0}^{deg_T}a_ig\tau^i=\sum_{i=0}^{deg_T}a_ick(i)$$  where  $$a_i$$ is coefficient of $$x^i$$ in polynomial  $$T(x)$$.

Therefore&#x20;

$$Com_{PFR}^0=\sum_{i=0}^{2}row_{PFR_{A_i}}(g\tau^i)=\sum_{i=0}^{2}row_{PFR_{A_i}}ck(i)=37ck(0)+109ck(1)+77ck(2)=37\times2+109\times 57+77\times 86\equiv\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$

$$Com_{PFR}^1=$$

\
$$Com_{PFR}^2=$$

and similarly

$$Com_{PFR}^3=$$, $$Com_{PFR}^4=$$, $$Com_{PFR}^5=$$, $$Com_{PFR}^6=$$, $$Com_{PFR}^7=$$ and $$Com_{PFR}^8=$$.

4- The Prover sends $$Com_{PFR}=$$ to the Verifier.

### &#x20;AHP Commitment

$$Commit(ck,m_f=(A,B,C),s\in R)$$:&#x20;

1 -  The Prover Selects  $$s=(s_1,...,s_{s_{AHP}(0)})$$ of random space $$R$$.\
&#x20; 2- The Prover calculates $$\overrightarrow{O}_{AHP}=Enc(m_f=(A,B,C))$$ as encoded index as following:

The polynomial $$row_{AHP_A}:\mathbb{K}=$$ &lcub; $$1,49,48,180,132,133$$ &rcub; $$\to\mathbb{H}=$$ &lcub; $$1,59,42,125,135$$ &rcub; with $$row_{AHP_A}(k=\gamma^i)=\omega^{r_i}$$ for $$1\leq i\leq ||A||$$ , and otherwise $$row_{AHP_A}(k)$$ returns an arbitrary element in $$\mathbb{H}$$. \
So $$row_{AHP_A}(k)$$ on $$\mathbb{K}$$ is a polynomial so that $$row_{AHP_A}(1)=42$$ , $$row_{AHP_A}(49)=125$$, $$row_{AHP_A}(48)=135$$ and otherwise $$row_{AHP_A}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example $$row_{AHP_A}(180)=125$$, $$AHProw_A(132)=135$$, $$AHProw_A(133)=1$$ . Therefore, $$row_{AHP_A}(x)=\sum_{i=1}^{6}y_iL_i(x)=162x^5+62x^4+161x^3+169x^2+88x+124$$.

Also,  $$col_{AHP_A}:\mathbb{K}=$$ &lcub; $$1,49,48,180,132,133$$ &rcub; $$\to\mathbb{H}=$$ &lcub; $$1,59,42,125,135$$ &rcub; with $$col_{AHP_A}(k=\gamma^i)=\omega^{c_i}$$ for $$1\leq i\leq ||A||$$ and otherwise $$col_{AHP_A}(k)$$ returns an arbitrary element in $$\mathbb{H}$$. \
So $$col_{AHP_A}(k)$$ on $$\mathbb{K}$$ is a polynomial so that $$col_{AHP_A}(1)=59$$ , $$col_{AHP_A}(49)=1$$, $$col_{AHP_A}(48)=125$$ and otherwise  $$col_{AHP_A}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example $$col_{AHP_A}(180)=125$$, $$col_{AHP_A}(132)=135$$ and $$col_{AHP_A}(133)=1$$. Therefore, $$col_{AHP_A}(x)=\sum_{i=1}^{6}y_iL_i(x)=128x^5+150x^4+32x^3+109x^2+169x+14$$

and ,  $$val_{AHP_A}:\mathbb{K}=$$ &lcub; $$1,49,48,180,132,133$$ &rcub; $$\to\mathbb{H}=$$ &lcub; $$1,59,42,125,135$$ &rcub; with $$val_{AHP_A}(k=\gamma^i)=\frac{v_i}{u_{\mathbb{H}}(row_{AHP_A}(k),row_{AHP_A}(k))u_{\mathbb{H}}(col_{AHP_A}(k),col_{AHP_A}(k))}$$ for $$1\leq i\leq ||A||$$ where $$v_i$$ is value of  $$i^{th}$$ nonzero entry and otherwise $$val_{AHP_A}(k)$$ returns zero. Note that based on definition of $$u_{\mathbb{H}}(x,y)$$, for each $$x \in \mathbb{H}$$, $$u_{\mathbb{H}}(x,x)=|\mathbb{H}|x^{|\mathbb{H}|-1}=5x^4$$. So $$val_{AHP_A}(1)=\frac{1}{(5row_{AHP_A}^4(1))(5col_{AHP_A}^4(1))}=\frac{1}{5\times 42^4\times5\times59^4}=\frac{1}{145}\equiv 5\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$, $$val_{AHP_A}(49)=\frac{1}{(5row_{AHP_A}^4(49))(5col_{AHP_A}^4(49))}=\frac{1}{5\times 125^4\times5\times1^4}=\frac{1}{145}\equiv 5\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ , $$val_{AHP_A}(48)=\frac{1}{(5row_{AHP_A}^4(48))(5col_{AHP_A}^4(48))}=\frac{1}{5\times 135^4\times5\times 125^4}=\frac{1}{48}\equiv 132\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ and $$val_{AHP_A}(k)=0$$ for $$k\in \mathbb{K}-$$ &lcub; $$1,49,48$$ &rcub;. Therefore $$val_{AHP_A}(x)=\sum_{i=1}^{6}y_iL_i(x)=72x^5+79x^4+22x^3+111x^2+180x+84$$.

Now, $$\hat{row_{AHP_A}}$$, $$\hat{col_{AHP_A}}$$ and $$\hat{val_{AHP_A}}$$ are extensions of $$row_{AHP_A}$$, $$col_{AHP_A}$$ and $$val_{AHP_A}$$ so that are agree on $$\mathbb{K}$$.&#x20;

Similarly, $$row_{AHP_B}:\mathbb{K}=$$ &lcub; $$1,49,48,180,132,133$$ &rcub; $$\to\mathbb{H}=$$ &lcub; $$1,59,42,125,135$$ &rcub; so that  $$row_{AHP_B}(1)=42$$, $$row_{AHP_B}(49)=125$$,  $$row_{AHP_B}(48)=125$$, $$row_{AHP_B}(180)=135$$ and for the rest values of $$\mathbb{K}$$,  $$row_{AHP_B}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example  $$row_{AHP_B}(132)=135$$ and $$row_{AHP_B}(133)=1$$. Therefore $$row_{AHP_B}(x)=\sum_{i=1}^{6}y_iL_i(x)=20x^5+85x^4+37x^3+151x^2+168x+124$$.

Also,  $$col_{AHP_B}:\mathbb{K}=$$ &lcub; $$1,49,48,180,132,133$$ &rcub; $$\to\mathbb{H}=$$ &lcub; $$1,59,42,125,135$$ &rcub; so that $$col_{AHP_B}(1)=1$$ , $$col_{AHP_B}(49)=1$$, $$col_{AHP_B}(48)=42$$, $$col_{AHP_B}(180)=1$$ and for the rest values of $$\mathbb{K}$$ , $$col_{AHP_B}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example  $$col_{AHP_B}(132)=135$$ and $$col_{AHP_B}(133)=1$$. Therefore $$col_{AHP_B}(x)=\sum_{i=1}^{6}y_iL_i(x)=18x^5+164x^4+180x^3+18x^2+164x$$

and ,  $$val_{AHP_B}:\mathbb{K}=$$ &lcub; $$1,49,48,180,132,133$$ &rcub; $$\to\mathbb{H}=$$ &lcub; $$1,59,42,125,135$$ &rcub; so that  $$val_{AHP_B}(1)=\frac{5}{(5row_{AHP_B}^4(1))(5col_{AHP_B}^4(1))}=\frac{5}{5\times 42^4\times5\times1^4}=\frac{5}{48}\equiv 117\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$, $$val_{AHP_B}(49)=\frac{11}{(5row_{AHP_B}^4(49))(5col_{AHP_B}^4(49))}=\frac{11}{5\times 125^4\times5\times1^4}=\frac{11}{145}\equiv 55\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ , $$val_{AHP_B}(48)=\frac{1}{(5row_{AHP_B}^4(48))(5col_{AHP_B}^4(48))}=\frac{1}{5\times 125^4\times5\times 42^4}=\frac{1}{25}\equiv 29\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ , $$val_{AHP_B}(180)=\frac{26}{(5row_{AHP_B}^4(180))(5col_{AHP_B}^4(180))}=\frac{26}{5\times 135^4\times5\times 1^4}=\frac{26}{27}\equiv 68\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ and $$val_{AHP_B}(k)=0$$ for $$k\in \mathbb{K}-\{1,49,48,180\}$$. Therefore $$val_{AHP_B}(x)=\sum_{i=1}^{6}y_iL_i(x)=86x^5+53x^4+34x^3+55x^2+176x+75$$.

Now, $$\hat{row_{AHP_B}}$$, $$\hat{col_{AHP_B}}$$ and $$\hat{val_{AHP_B}}$$ are extensions of $$row_{AHP_B}$$, $$col_{AHP_B}$$ and $$val_{AHP_B}$$ so that are agree on $$\mathbb{K}$$.&#x20;

Similarly, $$row_{AHP_C}:\mathbb{K}=$$ &lcub; $$1,49,48,180,132,133$$ &rcub; $$\to\mathbb{H}=$$ &lcub; $$1,59,42,125,135$$ &rcub; so that  $$row_{AHP_C}(1)=42$$, $$row_{AHP_C}(49)=125$$,  $$row_{AHP_C}(48)=135$$ and for the rest values of $$\mathbb{K}$$,  $$row_{AHP_C}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example  $$row_{AHP_C}(180)=125$$, $$row_{AHP_C}(132)=135$$ and $$row_{AHP_C}(133)=1$$. Therefore $$row_{AHP_C}(x)=\sum_{i=1}^{6}y_iL_i(x)=162x^5+62x^4+161x^3+169x^2+88x+124$$.

Also,  $$col_{AHP_C}:\mathbb{K}=$$ &lcub; $$1,49,48,180,132,133$$ &rcub; $$\to\mathbb{H}=$$ &lcub; $$1,59,42,125,135$$ &rcub;so that $$col_{AHP_C}(1)=42$$ , $$col_{AHP_C}(49)=125$$, $$col_{AHP_C}(48)=135$$, $$col_{AHP_C}(180)=125$$ and for the rest values of $$\mathbb{K}$$ , $$col_{AHP_C}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example  $$col_{AHP_C}(132)=135$$ and $$col_{AHP_C}(133)=1$$. Therefore $$col_{AHP_C}(x)=\sum_{i=1}^{6}y_iL_i(x)=162x^5+62x^4+161x^3+169x^2+88x+124$$.

and ,  $$val_{AHP_C}:\mathbb{K}=$$ &lcub; $$1,49,48,180,132,133$$ &rcub; $$\to\mathbb{H}=$$ &lcub; $$1,59,42,125,135$$ &rcub; so that  $$val_{AHP_C}(1)=\frac{1}{(5row_{AHP_C}^4(1))(5col_{AHP_C}^4(1))}=\frac{1}{5\times 42^4\times5\times42^4}=\frac{1}{27}\equiv 114\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$, $$val_{AHP_C}(49)=\frac{1}{(5row_{AHP_C}^4(49))(5col_{AHP_C}^4(49))}=\frac{1}{5\times 125^4\times5\times125^4}=\frac{1}{117}\equiv 82\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ , $$val_{AHP_C}(48)=\frac{1}{(5row_{AHP_C}^4(48))(5col_{AHP_C}^4(48))}=\frac{1}{5\times 135^4\times5\times135 ^4}=\frac{1}{145}\equiv 5\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ and $$val_{AHP_C}(k)=0$$ for $$k\in \mathbb{K}-\{1,49,48\}$$. Therefore $$val_{AHP_C}(x)=\sum_{i=1}^{6}y_iL_i(x)=65x^5+61x^4+157x^3+53x^2+16x+124$$.

Now, $`\hat{row}_{AHP_C}`$, $`\hat{col}_{AHP_C}`$ and $`\hat{val}_{AHP_C}`$ are extensions of $$row_{AHP_C}$$, $$col_{AHP_C}$$ and $$val_{AHP_C}$$ so that are agree on $$\mathbb{K}$$.&#x20;

Therefore, $$\overrightarrow{O}_{AHP}=(124,88,169,161,62,162,14,169,109,32,150,128,84,180,111,22,79,$$\
$$72,124,168,151,37,85,20,0,164,18,180,164,18,75,176,55,34,53,86,124,88,169,$$\
$$161,62,162,124,88,169,161,62,162,124,16,53,157,61,65)$$.

3- The Prover calculates commitment by using of $$KZG$$ commitment scheme as following:

$$Com_{T}=\sum_{i=0}^{deg_T}a_ig\tau^i=\sum_{i=0}^{deg_T}a_ick(i)$$  where  $$a_i$$ is coefficient of $$x^i$$ in polynomial  $$T(x)$$.

4- The Prover sends


$`Com_{AHP}^0=\sum_{i=0}^{5}\hat{row}_{AHP_{A_i}}\hspace{1.1mm}ck(i)=124ck(0)+88ck(1)+169ck(2)+161ck(3)+62ck(4)+162ck(5) \equiv 166\hspace{1mm}(\textrm{mod}\hspace{1mm} 181)`$

and similarly

$$Com_{AHP}^1=36$$, $$Com_{AHP}^2=108$$, $$Com_{AHP}^3=58$$, $$Com_{AHP}^4=73$$, $$Com_{AHP}^5=157$$, $$Com_{AHP}^6=166$$, $$Com_{AHP}^7=166$$ and $$Com_{AHP}^8=36$$.

## &#x20;AHP Commitment JSON File Example 1

IoT\_Manufacturer\_Name = "zkIoT"\
IoT\_Device\_Name = "MultiSensor"\
Device\_Hardware\_Version = "1.0"\
Firmware\_Version = "1.0"\
Device Picture= <>\
Lines = \[200, 350, 4000-4010]

```
{
    "commitmentId": String,
    "deviceType": String,
    "deviceIdType": String,
    "deviceModel": String,
    "manufacturer": String,
    "softwareVersion": String,
    "class": 32-bit Integer,
    "m": 6,
    "n": 5,
    "p": 181,
    "g": 2,   
        
    // PFR Commitment   
    "row_PFR_A": 64-bit Array,
    "col_PFR_A": 64-bit Array,
    "val_PFR_A": 64-bit Array,
    "row_PFR_B": 64-bit Array,
    "col_PFR_B": 64-bit Array,
    "val_PFR_B": 64-bit Array,
    "row_PFR_C": 64-bit Array,
    "col_PFR_C": 64-bit Array,
    "val_PFR_C": 64-bit Array,
    
    "Com_PFR0": 64-bit Integer,
    "Com_PFR1": 64-bit Integer,
    "Com_PFR2": 64-bit Integer,
    "Com_PFR3": 64-bit Integer,
    "Com_PFR4": 64-bit Integer,
    "Com_PFR5": 64-bit Integer,
    "Com_PFR6": 64-bit Integer,
    "Com_PFR7": 64-bit Integer,
    "Com_PFR8": 64-bit Integer,   

    // AHP Commitment       
    "row_AHP_A":[124,88,169,161,62,162],
    "col_AHP_A":[14,169,109,32,150,128],
    "val_AHP_A":[84,180,111,22,79,72],
    "row_AHP_B":[124,168,151,37,85,20],
    "col_AHP_B":[0,164,18,180,164,18],
    "val_AHP_B":[75,176,55,34,53,86],
    "row_AHP_C":[124,88,169,161,62,162],
    "col_AHP_C":[124,88,169,161,62,162],
    "val_AHP_C":[124,16,53,157,61,65],
    
    "Com_AHP0":166,
    "Com_AHP1":36,
    "Com_AHP2":108,
    "Com_AHP3":58,
    "Com_AHP4":73,
    "Com_AHP5":157,
    "Com_AHP6":166,
    "Com_AHP7":166,
    "Com_AHP8":36,
    
    "curve": "bn128",
    "polynomialCommitment": "KZG"
}
```

