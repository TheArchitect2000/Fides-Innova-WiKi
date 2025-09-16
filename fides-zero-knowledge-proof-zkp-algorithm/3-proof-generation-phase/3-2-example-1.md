# Example 1

### PFR Proof

The Prover interpolates polynomial $$h$$ such that $$seq_{\mathbb{K}}(h)=\omega^t,\omega^{t+1},..,\omega^{n-1},0,..,0$$. Here $$t=2$$ and $$n=5$$, therefore $$seq_{\mathbb{K}}(h)=\omega^2,\omega^3,\omega^4,0,..,0$$. This means that $`\{h(k):\hspace{1mm}k\in\mathbb{K}=\{1,43,39,48,73,62,132,65,80\}\}=\{\omega^2,\omega^3,\omega^4,0,..,0\}=\{42,125,135,0,0,0,0,0,0\}`$ . Therefore $$h(1)=42$$, $$h(43)=125$$ , $$h(39)=135$$, $$h(48)=h(73)=h(62)=h(132)=h(65)=h(80)=0$$. So $$h(x)=42L_1(x)+125L_2(x)+135L_3(x)$$ where $$L_1(x)=\frac{(x-43)(x-39)(x-48)(x-73)(x-62)(x-132)(x-65)(x-80)}{(-42)(-38)(-47)(-72)(-61)(-131)(-64)(-79)}=161x^8+161x^7+161x^6+161x^5+161x^4+161x^3+161x^2+161x+161$$,

$$L_2(x)=45x^8+125x^7+126x^6+169x^5+27x^4+75x^3+148x^2+29x+161$$,

$$L_3(x)=125x^8+169x^7+75x^6+29x^5+45x^4+126x^3+27x^2+148x+161$$,

Therefore $$h(x)=121x^8+133x^7+57x^6+127x^5+103x^4+24x^3+128x^2+140x+114$$. The Prover sends $$\pi_1=(h_0,h_1,...,h_8)$$ where $$h_i$$ is coefficients of polynomial $$h(x)$$ to the Verifier.

#### 3-5-1-2- Step 2

The Prover and the Verifier do $$Geometric\hspace{1mm}Sequence\hspace{1mm}Test$$ on $$h$$ (to verify correct construction of polynomial $$h$$). In $$Geometric\hspace{1mm} Sequence\hspace{1mm} Test$$ want to prove that $`Seq_{\mathbb{K}}(h)=a_1,a_1r,..,a_1r^{c_1-1},a_2, a_2r,..., a_2r^{c_2-1},...,a_v,a_vr,...,a_vr^{c_v-1}`$.

#### 3-5-1-2- Step 2-A- Geometric Sequence Test

Since $$h(\gamma^0)=\omega^2$$, $$h(\gamma^1)=\omega^3$$ ,$`h(\gamma^2)=\omega^4`$ and $$h(\gamma^3)=...=h(\gamma^8)=0$$, then Geometric Sequence Test with $$a_1=\omega^2$$, $$a_2=0$$, $$r=\omega$$, $$c_1=n-t=3$$ and $$c_2=m-(n-t)=9-3=6$$ run. Let $$p_i=\sum_{j<i}c_j$$ for $$i\in \{1,2,..,v\}$$. Here $$v$$ is the number of $$c_i$$ that are non-zero. Therefore $$v=2$$ ,  $$p_1=0$$ and $$p_2=c_1=3$$.&#x20;

The Prover and the Verifier run  $$Zero\hspace{1mm}Over\hspace{1mm}\mathbb{K}$$ (see the next section) to check that for all $$k\in\mathbb{K}$$, have $$(h(\gamma k)-rh(k))\prod_{i=1}^{v}(k-\gamma^{p_i+c_i-1})=0$$. Here, $$Zero\hspace{1mm}Over\hspace{1mm}\mathbb{K}$$ run to check that for all $$k\in\mathbb{K}=\{1,\gamma,\gamma^2,..,\gamma^8\}$$, have $$(h(\gamma k)-\omega h(k))(k-\gamma^2)(k-\omega^8)=0$$. \
$$Note$$: It is clear that if the construction of $$h$$ is correct, it applies this equality, because if $$k=1$$, $$h(\gamma k)=h(\gamma)=\omega h(1)$$ then $$h(\gamma k)-\omega h(k)=0$$. If $$k=\gamma$$, $$h(\gamma k)=h(\gamma^2)=\omega h(\gamma)$$, then $$h(\gamma k)-\omega h(k)=0$$. If $$k=\gamma^2$$, then $$k-\gamma^2=0$$. If $$k=\omega^3,...,\omega^7$$, then $$h(\gamma k)=\omega h(k)=0$$ and if $$k=\gamma^8$$, then $$k-\gamma^8=0$$.

#### 3-5-1-2-Step 2-B- Zero over K

In  $`Zero\hspace{1mm}Over\hspace{1mm}\mathbb{K}`$, want to prove that for all $`k\in\mathbb{K}`$, $$F(k)=0$$ where $`F(x)=G(x,f_{j_1}(\alpha_1x),f_{j_2}(\alpha_2x),...,f_{j_{t}}(\alpha_{t}x))`$. Here  $`F(x)=(h(\gamma x)-\omega h(x))(x-\gamma^2)(x-\gamma^8)`$, therefore since $$t=2$$, $`F(x)=G(x,f_{j_1}(\alpha_1x),f_{j_2}(\alpha_2x))=(h(\gamma x)-\omega h(x))(x-\gamma^2)(x-\gamma^8)`$, so $`h_1=f_{j_1}=h`$, $$h_2=f_{j_2}=h$$, $`\alpha_1=\gamma`$ and $$\alpha_2=1$$.&#x20;

2-2-1 The Prover selects polynomials $`r_i\in \mathbb{F}^{<2}[x]`$, $`i\in \{1,2,..,t\}`$. Then computes masks $`m_i(x)=r_i(\alpha_i^{-1}x)Z_{\mathbb{K}}(\alpha_i^{-1}x)`$ and computes $`h'_i(x)=h_i(x)+m_i(x)`$ for $`i\in\{1,2,..,t\}`$.&#x20;

Here, the Prover selects $$r_1,r_2$$. For example, let $$r_1(x)=2+x$$ and $$r_2(x)=2x$$. Therefore $`m_1(x)=r_1(\alpha_1^{-1}x)Z_{\mathbb{K}}(\alpha_1^{-1}x)`$ where $$\alpha_1=\gamma=48$$ and $`Z_{\mathbb{K}}(x)=\prod_{x\in\mathbb{K}}(x-k)=(x-1)(x-43)(x-39)(x-48)(x-73)(x-62)(x-132)(x-65) (x-80)=x^9+180`$. Therefore $`m_1(x)=r_1(80x)Z_{\mathbb{K}}(80x)=80x^{10}+2x^9+101x+179`$\
$`m_2(x)=r_2(\alpha_2^{-1}x)Z_{\mathbb{K}}(\alpha_2^{-1}x)=r_2(x)Z_{\mathbb{K}}(x)=2x(x^9+180)=2x^{10}+179x`$.  Then computes $`h'_1(x)=h_1(x)+m_1(x)=h(x)+m_1(x)=80x^{10}+2x^9+121x^8+133x^7+57x^6+127x^5+103x^4+`$\
$`24x^3+128x^2+60x+112`$  and $`h'_2(x)=h_2(x)+m_2(x)=h(x)+m_2(x)=2x^{10}+121x^8+133x^7+`$\
$$57x^6+127x^5+103x^4+24x^3+128x^2+138x+114$$.

2-2-2- The Prover computes $`F'(x)=G(x,h'_1(\alpha_1x),h'_2(\alpha_2x),...,h'_t(\alpha_tx))`$ and $`q_1(x)=\frac{F'(x)}{Z_{\mathbb{K}}(x)}`$ then the Prover sends $`\pi_{PFR_{1+i}}=(m_{i1},...,m_{ideg(m_i)})`$ where $`m_{ij}`$s are coefficients of polynomial  $$m_i(x)$$,  $$\pi_{PFR_{1+t+i}}=(r_{i1},...,r_{ideg(r_i)})$$ where $`r_{ij}`$s are coefficients of polynomial $$r_i(x)$$ and $`\pi_{PFR_{2t+2}}=(q_{11},...,q_{1deg(q_1)})`$ where $`q_{1j}`$s are coefficients of polynomial $$q_1(x)$$

Here $`F'(x)=G(x,h'_1(43x),h'_2(x))=(h'_1(43x)-\omega h'_2(x))(x-\gamma^2)(x-\gamma^8)=64x^{12}+169x^{11}+168x^{10}+51x^9+117x^3+12x^2+13x+130`$\
and then $`q_1(x)=\frac{F'(x)}{Z_{\mathbb{K}}(x)}=64x^3+169x^2+168x+51`$.

The Prover sends  $`\pi_{PFR_{2}}=(179,101,0,0,0,0,0,0,0,2,80)`$,  $`\pi_{PFR_{3}}=(0,179,0,0,0,0,0,0,0,0,2)`$ , $$\pi_{PFR_4}=(2,1)$$,   $$\pi_{PFR_5}=(0,2)$$  and $`\pi_{PFR_6}=(51,168,169,64)`$ to the Verifier.

2-2-3- The Verifier derives  $`h'_i=h_i+m_i`$ through additive homomorphism. Then samples $$\beta_1$$, $$\beta_2$$ and $$c$$ of $`\mathbb{F}^{*}-\mathbb{K}`$ and sends $$c$$ to the Prover. Suppose $$\beta_1=65$$, $$\beta_2=21$$ and $$c=171$$. The Verifier sends $$c=171$$ to the Prover.

2-2-4- The Prover computes $`q_2=r_1+cr_2+...+c^{t-1}r_t`$ and the Verifier derives concrete oracle $$q_2$$ through additive homomorphism. Here, the Prover computes $`q_2(x)=r_1(x)+cr_2(x)=2+x+171(2x)=162x+2`$.

2-2-5- Let $$M(x)=m_1(\alpha_1 x)+cm_2(\alpha_2 x)+...+c^{t-1}m_t(\alpha_t x)$$. The Verifier computes $$Z_{\mathbb{K}}(\beta_1)$$, $$Z_{\mathbb{K}}(\beta_2)$$, queries $`q_1(\beta_1)`$and $`q_2(\beta_2)`$ and for $`i\in \{1,2,..,t\}`$, queries $`h'_i(\alpha_i\beta_1)`$ and $`m_i(\alpha_i\beta_2)`$to compute $`F'(\beta_1)`$ and $$M(\beta_2)$$. The Verifier asserts two identities $`M(\beta_2)-q_2(\beta_2)Z_{\mathbb{K}}(\beta_2)=0`$ and $$F'(\beta_1)-q_1(\beta_1)Z_{\mathbb{K}}(\beta_1)=0$$.

Here, $$M(x)=m_1(\alpha_1 x)+cm_2(\alpha_2 x)=m_1(\gamma x)+171m_2(x)=162x^{10}+2x^9+19x+179$$. The Verifier computes $$Z_{\mathbb{K}}(\beta_1)=Z_{\mathbb{K}}(65)=65^9+180=0$$ and $$Z_{\mathbb{K}}(\beta_2)=Z_{\mathbb{K}}(21)=21^9+180=30$$ and queries $$q_1(\beta_1)=86$$ and $$q_2(\beta_2)=146$$. Also queries  values $$h'_1(\alpha_1\beta_1)=h'_1(\gamma\times 65)=h'_1(80)=0$$ ,  $`h'_2(\alpha_2\beta_1)=h'_2(65)=0`$, $`m_1(\alpha_1\beta_2)=m_1(\gamma\times 21)=m_1(179)=147`$ and $$m_2(\alpha_2\beta_2)=m_2(21)=174$$. Then checks $`M(\beta_2)-q_2(\beta_2)Z_{\mathbb{K}}(\beta_2)=0`$ , that means $`36-30\times 146=36-36\equiv 0\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, and $`F'(\beta_1)-q_1(\beta_1)Z_{\mathbb{K}}(\beta_1)=0`$, that means $`0-86\times 0\equiv 0\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$.

3- The Prover and the Verifier run $$Subset\hspace{1mm}over\hspace{1mm}\mathbb{K}$$ between $$row_A$$ and $$h$$ to prove that $$row_A(\mathbb{K})\subset h(\mathbb{K})$$ where $`row_A(\mathbb{K})=\{row_A(k):\hspace{1mm}k\in\mathbb{K}\}`$and  $`h(\mathbb{K})=\{h(k)\hspace{1mm}:\hspace{1mm}k\in\mathbb{K}\}`$.&#x20;

#### 3-5-1-2- Step 3- Subset over $$\mathbb{K}$$

#### .................&#x20;

4- The Prover and the Verifier run $$Discrete-log\hspace{1mm} Comparison$$ between $$row_A$$ and $$col_A$$ as following:&#x20;

#### 3-5-1-2- Step 4- Discrete-log Comparison

Let parameters $$(\Delta \in \mathbb{F}, n = |\mathbb{H}|)$$ such that $$ord(\Delta) = 2n$$ and $$\Delta^2=\omega$$.\
&#x20;    Here, $$\omega=59$$, $$\Delta=56$$ and $$ord(\Delta)=2n=10$$.

3-5-1-2- Step 4-Substep A- The Prover interpolates polynomial $$s$$ so that agrees with $`\frac{row_A}{col_A}1$ on $$\mathbb{K}$$. Then send them to the Verifier.

Here, $`s(1)=\frac{row_A(1)}{col_A(1)}=\frac{42}{59}\equiv 59\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, $`s(43)=\frac{row_A(43)}{col_A(43)}\equiv125\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, $`s(39)=\frac{row_A(39)}{col_A(39)}=\frac{135}{125}\equiv59\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, $`s(48)=\frac{row_A(48)}{col_A(48)}=\frac{48}{45}\equiv 170\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, \
$`s(73)=\frac{row_A(73)}{col_A(73)}=\frac{36}{22}\equiv 51\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, $`s(62)=\frac{row_A(62)}{col_A(62)}=\frac{151}{166}\equiv 2\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$,\
$`s(132)=\frac{row_A(132)}{col_A(132)}=\frac{21}{46}\equiv 28\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, $`s(65)=\frac{row_A(65)}{col_A(65)}=\frac{131}{127}\equiv 135\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$ and\
$`s(80)=\frac{row_A(80)}{col_A(80)}=\frac{6}{40}\equiv 154\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$. Therefore, $`s(x)=59L_1(x)+125L_2(x)+59L_3(x)+170L_4(x)+51L_5(x)+2L_6(x)+28L_7(x)+135L_8(x)+154L_9(x)`$.&#x20;

where $$L_1(x)$$, $$L_2(x)$$ and $$L_3(x)$$ are computed in step $$1$$ and the rest of $$L_i(x)s$$ are\
$$L_4(x)=126x^8+75x^7+161x^6+126x^5+75x^4+161x^3+126x^2+75x+161$$,\
$$L_5(x)=169x^8+29x^7+126x^6+148x^5+125x^4+75x^3+45x^2+27x+161$$,\
$$L_6(x)=27x^8+45x^7+75x^6+125x^5+148x^4+126x^3+29x^2+169x+161$$,\
$$L_7(x)=75x^8+126x^7+161x^6+75x^5+126x^4+161x^3+75x^2+126x+161$$,\
$$L_8(x)=148x^8+27x^7+126x^6+45x^5+29x^4+75x^3+169x^2+125x+161$$ and\
$$L_9(x)=29x^8+148x^7+75x^6+27x^5+169x^4+126x^3+125x^2+45x+161$$.

Therefore $$s(x)=41x^8+101x^7+34x^6+38x^5+x^4+25x^3+152x^2+123x+87$$. The Prover sends $$s(x)$$ to the Verifier.

3-5-1-2- Step 4-Substep B-  For $$b\in\{row_A, col_A, s\}$$, the Prover interpolates polynomial $$b'$$ so that for all $$k\in \mathbb{K}$$, $$b'(k)=\Delta^{\log_{\omega}^{b(k)}}$$.

Here, if $$b=row_A$$, $`row'_A(k)=\Delta^{\log_{\omega}^{row_A(k)}}=56^{\log_{59}^{row_A(k)}}`$ that means $`row'_A(1)=56^{\log_{59}^{42}}=56^2\equiv 59\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, $`row'_A(43)=56^{\log_{59}^{125}}=56^3\equiv 46\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$,\
$`row'_A(39)=56^{\log_{59}^{135}}=56^4\equiv 42\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, $`row'_A(48)=56^{\log_{59}^{48}} \equiv 49\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$,\
$`row'_A(73)=56^{\log_{59}^{36}} \equiv 114\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, $`row'_A(62)=56^{\log_{59}^{151}} \equiv  \hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$.


Therefore $`row'_A(x)=59L_1(x)+46L_2(x)+42L_3(x)+49L_4(x)+114L_5(x)+...`$.

if $$b=col_A$$,  $`col'_A(k)=\Delta^{\log_{\omega}^{col_A(k)}}=56^{\log_{59}^{col_A(k)}}`$ that means $`col'_A(1)=56^{\log_{59}^{59}}=56^1\equiv 56\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$, $`col'_A(48)=56^{\log_{59}^{1}}=56^5\equiv 180\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$ and $`col'_A(132)=56^{\log_{59}^{125}}=56^3\equiv 46\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$. Therefore $`col'_A(x)=56L_1(x)+180L_2(x)+46L_3(x)=96x^2+47x+94`$.

if $$b=s$$,  $`s'(k)=\Delta^{\log_{\omega}^{s(k)}}=56^{\log_{59}^{s(k)}}`$ that means $$s'(1)=56^{\log_{59}^{59}}=56^1\equiv 56\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$,  $`s'(48)=56^{\log_{59}^{125}}=56^3\equiv 46\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$ and $`s'(132)=56^{\log_{59}^{59}}=56^1\equiv 56\hspace{1mm}(\textrm{mod}\hspace{1mm}181)`$. Therefore $$s'(x)=56L_1(x)+46L_2(x)+56L_3(x)=21x^2+103x+113$$.

Then the Prover sends $$row'_A$$, $$col'_A$$ and $$s'$$ to the Verifier.

3-5-1-2- Step 4-Substep C-  The Prover interpolates polynomial $$h$$ so that $`seq_{\mathbf{K}}(h)=1,\Delta,\Delta^2,..,\Delta^{n-1},0,0,..,0`$.

Here $`seq_{\mathbf{K}}(h)=1, 56, 59, 46, 42`$.

### &#x20;AHP Proof

Since in this example $$n_i=1$$, therefore input and output are not vector. So,  we denote input by $$x$$  and output by $$y$$  instead of $$X$$ and $$Y$$.

$$Proof (\mathbb{F}_{181}, \mathbb{H}=\{1,59,42,125,135\}, \mathbb{K}=\{1,49,48,180,132,133\}, A, B, C, x=4,W=(20,31),y=82)$$

1- The Prover puts  $$x=4$$ in $$Com_{AHP_X}^1$$ .  We consider $$z=(1,x,w_1,w_2,y)$$ where $$w_1=5x$$,  $$w_2=w_1+11$$ and $$y=26w_2$$. Therefore $$z=(1,x,W,y)=(1,4,20,31,82)$$. The Prover calculates $`z_A=Az=\begin{bmatrix}0&0&0&0&0\\0&0&0&0&0\\0&1&0&0&0\\1&0&0&0&0\\0&0&0&1&0\\ \end{bmatrix}\begin{bmatrix}1\\4\\20\\31\\82\\\end{bmatrix}=\begin{bmatrix}0\\0\\4\\1\\31\\\end{bmatrix}`$, $`z_B=Bz=\begin{bmatrix}0&0&0&0&0\\0&0&0&0&0\\5&0&0&0&0\\11&0&1&0&0\\26&0&0&0&0\\\end{bmatrix}\begin{bmatrix}1\\4\\20\\31\\82\end{bmatrix}=\begin{bmatrix}0\\0\\5\\31\\26\\\end{bmatrix}`$and $`z_C=Cz=\begin{bmatrix}0&0&0&0&0\\0&0&0&0&0\\0&0&1&0&0\\0&0&0&1&0\\0&0&0&0&1\\\end{bmatrix}\begin{bmatrix}1\\4\\20\\31\\82\\\end{bmatrix}=\begin{bmatrix}0\\0\\20\\31\\82\\\end{bmatrix}`$

2- The Prover calculates the polynomial $`z_A(x)`$using indexing $$z_A$$ by elements of $$\mathbb{H}$$ that mean $$z_A(x)$$ is the polynomial where $$z_A(1)=0$$, $$z_A(59)=0$$, $$z_A(42)=4$$, $$z_A(125)=1$$ and $$z_A(135)=31$$.&#x20;

Then calculates polynomial $$\hat{z}_A(x)$$ using the polynomial $$z_A(x)$$ such that $$\hat{z}_A(x)\in \mathbb{F}^{<|\mathbb{H}|+b}[x]$$ that agree with $$z_A(x)$$ on $$\mathbb{H}$$ . Note that values of up to $$b$$ locations in this polynomial reveals no information about the witness $`w`$ provided the locations are in $$\mathbb{F}-\mathbb{H}$$.\
Here, for simplicity, let $$b=2$$. The Prover calculates $$\hat{z}_A(x)$$  such that agree with $$z_A(x)$$ on $$\mathbb{H}$$ and also $$\hat{z}_A(150)=5$$, $$\hat{z}_A(80)=47$$.&#x20;

Therefore, we have $$\hat{z}_A(x)=4L_3(x)+L_4(x)+31L_5(x)+5L_6(x)+47L_7(x)$$ where $$L_3(x)=133x^6+155x^5+117x^4+27x^3+48x^2+73x+171$$, $$L_4(x)=4x^6+123x^5+25x^4+48x^3+27x^2+113x+22$$, $$L_5(x)=75x^6+115x^5+27x^4+25x^3+117x^2+154x+30$$, $$L_6(x)=132x^6+119x^5+49x+62$$ and $$L_7(x)=97x^6+111x^5+84x+70$$. \
So $$\hat{z}_A(x)=116x^6+165x^5+63x^4+26x^3+45x^2+141x+168$$.

Similarly, calculates polynomial  $$\hat{z}_B(x)$$ so that $$\hat{z}_B(x)\in \mathbb{F}^{<|\mathbb{H}|+b}[x]$$ that agree with $$z_B(x)$$ on $$\mathbb{H}$$ that mean $$\hat{z}_B(1)=0$$, $$\hat{z}_B(59)=0$$, $$\hat{z}_B(42)=5$$, $$\hat{z}_B(125)=31$$, $$\hat{z}_B(135)=26$$ and also $$b=2$$ random locations $$\hat{z}_B(150)=15$$ and $$\hat{z}_B(80)=170$$. So,  $$\hat{z}_B(x)=5L_3(x)+31L_4(x)+26L_5(x)+15L_6(x)+170L_7(x)=32x^6+178x^5+71x^4+101x^3+137x^2+81x+124$$

Similarly, calculates polynomial  $$\hat{z}_C(x)$$ such that $$\hat{z}_C(x)\in \mathbb{F}^{<|\mathbb{H}|+b}[x]$$ that agree with $$z_C(x)$$ on $$\mathbb{H}$$ that mean $$\hat{z}_C(1)=0$$, $$\hat{z}_C(59)=0$$, $$\hat{z}_C(42)=20$$, $$\hat{z}_C(125)=31$$, $$\hat{z}_C(135)=82$$ and also $$b=2$$ random locations $$\hat{z}_C(150)=1$$ and $$\hat{z}_C(80)=100$$. So $$\hat{z}_C(x)=20L_3(x)+31L_4(x)+82L_5(x)+L_6(x)+100L_7(x)=123x^6+50x^5+80x^4+96x^3+169x^2+157x+49$$

The Prover calculates polynomial $$\hat{W}(x)\in \mathbb{F}^{<n_g+b}[x]$$ that agree with $$\bar{W}(x)$$ on $$\mathbb{H}[>|x|+1]$$ where&#x20;

&#x20;                                           $$\bar{W}:\mathbb{H}[>|x|+1]=\{42,125,135\}\to \mathbb{F}$$

&#x20;                                               $$\bar{W}(h)=\frac{W(h)-\hat{x}(h)}{v_{\mathbb{H}[\leq |x|+1]}(h)}$$

and $$v_{\mathbb{H}[\leq |x|+1]}(h)$$ is vanishing polynomial on $$\mathbb{H}[\leq |x|+1]=\{1,59\}$$, therefore $$v_{\mathbb{H}[\leq |x|+1]}(h)=(h-1)(h-59)$$. Also $$\hat{x}(h)$$ is the polynomial such that $$\hat{x}(1)=1$$ and $$\hat{x}(59)=4$$, therefore $$\hat{x}(h)=128h+54$$. Therefore,

$$\bar{W}(42)=\frac{W(42)-\hat{x}(42)}{(42-1)(42-59)}=\frac{20-0}{(41)(-17)}\equiv 108\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$, $$\bar{W}(125)=\frac{W(125)-\hat{x}(125)}{(125-1)(125-59)}=\frac{31-126}{(124)(66)}\equiv 160\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$ and $$\bar{W}(135)=\frac{W(135)-\hat{x}(135)}{(135-1)(135-59)}=\frac{82-139}{(134)(76)}\equiv 78\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$.&#x20;

Now,  calculates $$\hat{W}(x)\in\mathbb{F}^{<n_g+b=3+2}[x]$$ so that $$\hat{W}(42)=108$$, $$\hat{W}(125)=160$$ , $$\hat{W}(135)=78$$ and also $$b=2$$ random locations $$\hat{W}(150)=42$$ and $$\hat{W}(80)=180$$.  Therefore, $$\hat{W}(x)=108L_1(x)+160L_2(x)+78L_3(x)+42L_4(x)+180L_5(x)$$ where $$L_1(x)=\frac{(x-125)(x-135)(x-150)(x-80)}{(-83)(-93)(-108)(-38)}\equiv 152x^4+92x^3+73x^2+43x+112\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$,\
$$L_2(x)=156x^4+39x^3+84x^2+86x+171$$, $$L_3(x)=161x^4+157x^3+131x^2+159x+6$$,\
$$L_4(x)=60x^4+67x^3+118x^2+50x+20$$ and $$L_5(x)=14x^4+7x^3+137x^2+24x+54$$. Therefore, \
$$\hat{W}(x)=149x^4+97x^3+161x^2+121x+166$$.

3- The Prover finds polynomial  $$h_0(x)$$ so that $`\hat{z}_A(x)\hat{z}_B(x)-\hat{z}_C(x)=h_0(x)v_{\mathbb{H}}(x)`$. Since $`\hat{z}_A(x)\hat{z}_B(x)-\hat{z}_C(x)=`$\
$`92x^{12}+45x^{11}+164x^{10}+x^9+20x^8+61x^7+152x^6+49x^5+180x^4+161x^3+28x^2+165x+149`$ and $`v_{\mathbb{H}}(x)=\prod_{h\in\mathbb{H}}(x-h)=(x-1)(x-59)(x-42)(x-125)(x-135)=x^5+180`$, The Prover finds $`h_0(x)=92x^7+45x^6+164x^5+x^4+20x^3+153x^2+16x+32`$.

4- The Prover samples a fully random $`s(x)\in\mathbb{F}^{<2|\mathbb{H}|+b-1=11}[x]`$. Consider $`s(x)=5x^{10}+101x^8+17x^7+x^5+20x^4+3x+115`$. Then, the Prover computes sum $`\sigma_1=\sum_{k\in \mathbb{H}}s(k)=s(1)+s(59)+s(42)+s(125)+s(135)=81+47+141+46+109\equiv 62\hspace{1mm}(\hspace{1mm}\textrm{mod}\hspace{1mm}181)`$.

5- The Prover sends $`Com_{AHP_X}^2=\sum_{i=0}^{deg_{\hat{w}(x)}}\hat{w}_i\hspace{1mm}ck(i)=30`$,  \
$`Com_{AHP_X}^{3}=\sum_{i=0}^{deg_{\hat{z}_A(x)}}\hat{z}_{A_i}ck(i)=160`$,  $`Com_{AHP_X}^{4}=\sum_{i=0}^{deg_{\hat{z}_B(x)}}\hat{z}_{B_i}ck(i)=69`$,  \
$`Com_{AHP_X}^{5}=\sum_{i=0}^{deg_{\hat{z}_C(x)}}\hat{z}_{C_i}ck(i)=11`$,  $`Com_{AHP_X}^{6}=\sum_{i=0}^{deg_{h_0(x)}}h_{0_i}ck(i)=18`$ and  \
$`Com_{AHP_X}^{7}=\sum_{i=0}^{deg_{s(x)}}s_i\hspace{1mm}ck(i)=178`$.

6- The Verifier chooses random numbers  $$\alpha$$, $$\eta_A$$, $$\eta_B$$, $$\eta_C$$ and sends them to the Prover.  ( Note that the Prover can choose $$\alpha=hash(s(0))$$, $$\eta_A=hash(s(1))$$, $$\eta_B=hash(s(2))$$, $$\eta_C=hash(s(3))$$. Let $$\alpha=10$$, $$\eta_A=2$$, $$\eta_B=30$$ and $$\eta_C=100$$.

7- The Prover finds polynomials $$g_1(x)$$ and $$h_1(x)$$ such that&#x20;

&#x20; $`s(x)+r(\alpha,x)\sum_{M}\eta_M\hat{z}_M(x)-(\sum_{M}\eta_Mr_M(\alpha,x))\hat{z}(x)=h_1(x)v_{\mathbb{H}}(x)+xg_1(x)+\frac{\sigma_1}{|\mathbb{H}|}`$   $$(1)$$

where  $$r(x,y)=u_{\mathbb{H}}(x,y)=\frac{v_{\mathbb{H}}(x)-v_{\mathbb{H}}(y)}{x-y}$$ ,  $$v_{\mathbb{H}}(x)=\prod_{h\in \mathbb{H}}(x-h)=x^{|\mathbb{H}|}-1$$.  Therefore $$r(x,y)=\frac{x^5-y^5}{x-y}$$ . Also $$r_M(x,y)=\sum_{k\in \mathbb{H}}r(x,k)\hat{M}(k,y)$$ for $$M\in \{A,B,C\}$$.&#x20;

Now, since $`\sum_M\eta_M\hat{z}_M(x)=\eta_A\hat{z}_A(x)+\eta_B\hat{z}_B(x)+\eta_C\hat{z} _C(x)=98x^6+172x^5+120x^4+12x^3+104x^2+131x+87`$and $$r(\alpha,x)=r(10,x)=\frac{10^5-x^5}{10-x}$$, so the second term of the left of equation $$(1)$$ is $$r(\alpha,x)\sum_M\eta_M\hat{z}_M(x)=98x^{10}+66x^9+56x^8+29x^7+32x^6+153x^5+56x^4+136x^3+123x^2+42x+114$$

Also, $`\hat{z}(x)=\hat{W}(x)v_{\mathbb{H}[\leq |x|+1]}(x)+\hat{x}(x)=(149x^4+97x^3+161x^2+121x+166)(x-1)(x-59)+128x+54=`$\
$`149x^6+26x^5+55x^4+166x^3+52x^2+22x+74`$ that agree with $$z$$ on $$\mathbb{H}$$.  Also, $$r_A(10,x)=\sum_{k\in \mathbb{H}}r(10,k)\hat{A}(k,x)$$ where $$\hat{A}(x,y)$$ is a polynomial such that $$\hat{A}(42,59)=1$$, $$\hat{A}(125,1)=1$$, $$\hat{A}(135,125)=1$$ and $$\hat{A}(x,y)=0$$ for the rest of points in $$\mathbb{H}\times\mathbb{H}$$. So, $$\hat{A}(x,y)$$ is a bivariate polynomial that passes from these 25 points. This polynomial can obtain as following:\
$`\hat{A}(x,y)=\sum_{k\in \mathbb{K}}u_{\mathbb{H}}(x,\hat{row}_{AHP_A}(k))u_{\mathbb{H}}(y,\hat{col}_{AHP_A}(k))\hat{val}_{AHP_A}(k)=\sum_{k\in \mathbb{K}}\frac{x^5-\hat{row}_{AHP_A}(k)^5}{x-\hat{row}_{AHP_A}(k)}\frac{y^5-\hat{col}_{AHP_A}(k)^5}{y-\hat{col}_{AHP_A}(k)}\hat{val}_{AHP_A}(k)`$\
Therefore, $`\hat{A}(x,y)=5\frac{x^5-1}{x-42}\frac{y^5-1}{y-59}+5\frac{x^5-1}{x-125}\frac{y^5-1}{y-1}+132\frac{x^5-1}{x-135}\frac{y^5-1}{y-125}`$. So $`r_A(10,x)=\sum_{k\in\mathbb{H}}r(10,k)\hat{A}(k,x)=70\hat{A}(1,x)+13\hat{A}(59,x)+150\hat{A}(42,x)+26\hat{A}(125,x)+147\hat{A}(135,x)`$where $`\hat{A}(1,x)=\hat{A}(59,x)=0`$, $`\hat{A}(42,x)=5\times82\times\frac{x^5-1}{x-59}=48(x^4+59x^3+42x^2+125x+135)=48x^4+117x^3+25x^2+27x+145`$, $`\hat{A}(125,x)=5\times 29\times\frac{x^5-1}{x-1}=145(x^4+x^3+x^2+x+1)=145x^4+145x^3+145x^2+145x+145`$, $`\hat{A}(135,x)=132\times 114\times\frac{x^5-1}{x-125}=25(x^4+125x^3+59x^2+135x+42)=25x^4+48x^3+27x^2+117x+145`$

Now, calculates $$\hat{B}(x,y)$$ similarly as following:

$`\hat{B}(x,y)=\sum_{k\in \mathbb{K}}u_{\mathbb{H}}(x,\hat{row}_{AHP_B}(k))u_{\mathbb{H}}(y,\hat{col}_{AHP_B}(k))\hat{val}_{AHP_B}(k)=\sum_{k\in \mathbb{K}}\frac{x^5-\hat{row}_{AHP_B}(k)^5}{x-\hat{row}_{AHP_B}(k)}\frac{y^5-\hat{col}_{AHP_B}(k)^5}{y-\hat{col}_{AHP_B}(k)}\hat{val}_{AHP_B}(k)`$

Therefore, $`\hat{B}(x,y)=117\frac{x^5-1}{x-42}\frac{y^5-1}{y-1}+55\frac{x^5-1}{x-125}\frac{y^5-1}{y-1}+29\frac{x^5-1}{x-125}\frac{y^5-1}{y-42}+68\frac{x^5-1}{x-135}\frac{y^5-1}{y-1}`$. So, $`r_B(10,x)=\sum_{k\in\mathbb{H}}r(10,k)\hat{B}(k,x)=70\hat{B}(1,x)+13\hat{B}(59,x)+150\hat{B}(42,x)+26\hat{B}(125,x)+147\hat{B}(135,x)`$\
where $`\hat{B}(1,x)=\hat{B}(59,x)=0`$, $$\hat{B}(42,x)=117\times 82\times \frac{x^5-1}{x-1}=1\times(x^4+x^3+x^2+x+1)=x^4+x^3+x^2+x+1$$, $`\hat{B}(125,x)=55\times 29\times\frac{x^5-1}{x-1}+29\times 29\times\frac{x^5-1}{x-42}=147(x^4+x^3+x^2+x+1)+117(x^4+42x^3+135x^2+59x+125)=`$\
$`83x^4+174x^3+14x^2+172x+111`$and $`\hat{B}(135,x)=68\times 114\times \frac{x^5-1}{x-1}=150(x^4+x^3+x^2+x+1)=150x^4+150x^3+150x^2+150x+150`$

Now, calculates $$\hat{C}(x,y)$$ similarly as following:\
$`\hat{C}(x,y)=\sum_{k\in \mathbb{K}}u_{\mathbb{H}}(x,\hat{row}_{AHP_C}(k))u_{\mathbb{H}}(y,\hat{col}_{AHP_C}(k))\hat{val}_{AHP_C}(k)=\sum_{k\in \mathbb{K}}\frac{x^5-\hat{row}^5_{AHP_C}(k)}{x-\hat{row}_{AHP_C}(k)}\frac{y^5-\hat{col}^5_{AHP_C}(k)}{y-\hat{col}_{AHP_C}(k)}\hat{val}_{AHP_C}(k)`$\

Therefore, $`\hat{C}(x,y)=114\frac{x^5-1}{x-42}\frac{y^5-1}{y-42}+82\frac{x^5-1}{x-125}\frac{y^5-1}{y-125}+5\frac{x^5-1}{x-135}\frac{y^5-1}{y-135}`$. So, $`r_C(10,x)=70\hat{C}(1,x)+13\hat{C}(59,x)+150\hat{C}(42,x)+26\hat{C}(125,x)+147\hat{C}(135,x)`$ where $`\hat{C}(1,x)=\hat{C}(59,x)=0`$, $`\hat{C}(42,x)=114\times 82\times\frac{x^5-1}{x-42}=117(x^4+42x^3+135x^2+59x+125)=117x^4+27x^3+48x^2+25x+145`$, $`\hat{C}(125,x)=82\times 29\times\frac{x^5-1}{x-125}=25(x^4+125x^3+59x^2+135x+42)=25x^4+48x^3+27x^2+117x+145`$and $`\hat{C}(135,x)=5\times 114\times\frac{x^5-1}{x-135}=27(x^4+135x^3+125x^2+42x+59)=27x^4+25x^3+117x^2+48x+145`$

Therefore, the third term of the left of equation $$(1)$$ is&#x20;

$`(\sum_M \eta_M r_M(\alpha,x))\hat{z}(x)=(2r_A(10,x)+30r_B(10,x)+100r_C(10,x))\hat{z}(x)=(23x^4+72x^3+144x^2+10x+19)`$\
$`(149x^6+26x^5+55x^4+166x^3+52x^2+22x+74)=169x^{10}+104x^9+158x^8+161x^7+86x^6+57x^5+85x^4+43x^3+99x^2+72x+139`$

Therefore, the left of equation $$(1)$$ is $`s(x)+r(\alpha,x)\sum_M \eta_M \hat{z}M(x)-(\sum_M \eta_M r_M(\alpha,x))\hat{z}(x)=115x^{10}+143x^9+180x^8+66x^7+127x^6+97x^5+172x^4+93x^3+24x^2+154x+90`$

Now, the Prover finds polynomials $$g_1(x)$$ and $$h_1(x)$$ such that $`h_1(x)v_{\mathbb{H}}(x)+xg_1(x)+\frac{\sigma_1}{|\mathbb{H}|}=115x^{10}+143x^9+180x^8+66x^7+127x^6+97x^5+172x^4+93x^3+24x^2+154x+90`$

that means, the Prover finds polynomials $$g_1(x)$$ and $$h_1(x)$$ such that $$h_1(x)(x^5+180)+xg_1(x)+121=115x^{10}+143x^9+180x^8+66x^7+127x^6+97x^5+172x^4+93x^3+24x^2+154x+90$$

In this case, polynomials $$g_1(x)= 134x^3+92x^2+90x+100$$ and $$h_1(x)=115x^5+143x^4+180x^3+66x^2+127x+31$$ are obtained.  The Prover sends   , \
$$Com_{AHP_X}^{8}=\sum_{i=0}^{deg_{g_1(x)}}g_{1_i}ck(i)=129$$ and $$Com_{AHP_X}^{9}=\sum_{i=0}^{deg_{h_1(x)}}h_{1_i}ck(i)=33$$ to the Verifier where $$g_{1_i}$$ is coefficient of $$x^i$$ of polynomial $$g_1(x)$$ and  $$h_{1_i}$$ is coefficient of $$x^i$$ of polynomial $$h_1(x)$$.

8- The Verifier selects $$\beta_1\in \mathbb{F}-\mathbb{H}$$ and sends it to the Prover. (The Prover can selects $$\beta_1=hash(s(8))$$). Let  $$\beta_1=22$$.&#x20;

9- The Prover calculates $`\sigma_2=\sum_{k\in\mathbb{H}}r(\alpha,k)\sum_{M}\eta_M\hat{M}(k,\beta_1)=r(10,1)\sum_{M}\eta_M\hat{M}(1,22)+r(10,59)\sum_{M}\eta_M\hat{M}(59,22)+r(10,42)\sum_{M}\eta_M\hat{M}(42,22)+r(10,125)`$
$`\sum_{M}\eta_M\hat{M}(125,22)+r(10,135)\sum_{M}\eta_M\hat{M}(135,22)`$ that is $`\sigma_2=70\times 0+13\times 0+150\times 135+26\times 88+147\times 22=70`$.&#x20;

Then, the Prover finds $$g_2(x)$$ and $$h_2(x)$$ such that $$r(\alpha,x)\sum_M \eta_M\hat{M}(x,\beta_1)=h_2(x)v_{\mathbb{H}}(x)+xg_2(x)+\frac{\sigma_2}{|\mathbb{H}|}$$

where $$r(\alpha,x)\sum_M\eta_M \hat{M}(x,\beta_1)=r(10,x)(2\hat{A}(x,22)+30\hat{B}(x,22)+100\hat{C}(x,22))$$ where$`\hat{A}(x,22)=5\frac{x^5-1}{x-42}\frac{22^5-1}{22-59}+5\frac{x^5-1}{x-125}\frac{22^5-1}{22-1}+132\frac{x^5-1}{x-135}\frac{22^5-1}{22-125}=159\frac{x^5-1}{x-42}+56\frac{x^5-1}{x-125}+114\frac{x^5-1}{x-135}=159(x^4+42x^3+135x^2+59x+125)+`$\
$`56(x^4+125x^3+59x^2+135x+42)+114(x^4+135x^3+125x^2+42x+59)=148x^4+108x^3+104x^2+9x+174`$,$`\hat{B}(x,22)=117\frac{x^5-1}{x-42}\frac{22^5-1}{22-1}+55\frac{x^5-1}{x-125}\frac{22^5-1}{22-1}+29\frac{x^5-1}{x-125}\frac{22^5-1}{22-42}+68\frac{x^5-1}{x-135}\frac{22^5-1}{22-1}=146x^4+37x^3+95x^2+100x+165`$and $`\hat{C}(x,22)=114\frac{x^5-1}{x-42}\frac{22^5-1}{22-42}+82\frac{x^5-1}{x-125}\frac{22^5-1}{22-125}+5\frac{x^5-1}{x-135}\frac{22^5-1}{22-135}=6(x^4+42x^3+135x^2+59x+125)+5(x^4+125x^3+59x^2+135x+42)+`$\
$`177(x^4+135x^3+125x^2+42x+59)=7x^4+156x^3+62x^2+137x`$

Therefore, $`r(\alpha,x)\sum_M \eta_M \hat{M}(x,\beta_1)=\frac{10^5-x^5}{10-x}(127x^4+93x^3+27x^2+66x+49)=(x^4+10x^3+100x^2+95x+45)(127x^4+93x^3+27x^2+66x+49)=`$
$`127x^8+96x^7+82x^6+162x^5+40x^4+84x^3+77x^2+23x+33`$

Hence, the Prover finds $$g_2(x)=40x^3+30x^2+173x+105$$ and $$h_2(x)=127x^3+96x^2+82x+162$$ such that $$h_2(x)v_{\mathbb{H}}(x)+xg_2(x)+\frac{\sigma_2}{|\mathbb{H}|}=h_2(x)(x^5+180)+xg_2(x)+\frac{70}{5}=127x^8+96x^7+82x^6+162x^5+40x^4+84x^3+77x^2+23x+33$$

The Prover sends  ,  $$Com_{AHP_X}^{10}=\sum_{i=0}^{deg_{g_2(x)}}g_{2_i}ck(i)=100$$ and\
$$Com_{AHP_X}^{11}=\sum_{i=0}^{deg_{h_2(x)}}h_{2_i}ck(i)=179$$ where $$g_{2_i}$$ is coefficient of $$x^i$$ of polynomial $$g_2(x)$$ and $$h_{2_i}$$ is coefficient of $$x^i$$ of polynomial $$h_2(x)$$.&#x20;

10- The Verifier selects $$\beta_2\in \mathbb{F}-\mathbb{H}$$ and sends it to the Prover. For example $$\beta_2=80$$.

11-  The Prover calculates

$`\sigma_3=\sum_{k\in\mathbb{K}}(\sum_M \eta_M\frac{v_{\mathbb{H}}(\beta_2)v_{\mathbb{H}}(\beta_1)\hat{val'_M}(k)}{(\beta_2-\hat{row'_M}(k))(\beta_1-\hat{col'_M}(k))})=(2\frac{72\times 18\times 5}{38\times 144}+30\frac{72\times 18\times 117}{38\times 21}+100\frac{72\times 18\times 114}{38\times 161})+
(2\frac{72\times 18\times 5}{136\times 21}+30\frac{72\times 18\times 55}{136\times 21}+100\frac{72\times 18\times 82}{136\times 78})+`$\
$`(2\frac{72\times 18\times 132}{126\times 78}+30\frac{72\times 18\times 29}{136\times 161}+100\frac{72\times 18\times 5}{126\times 68})+(30\frac{72\times 18\times 68}{126\times 21})=84`$

Then, the Prover finds polynomials $$g_3(x)$$ and $$h_3(x)$$ such that $`h_3(x)v_{\mathbb{K}}(x)=a(x)-b(x)(xg_3(x)+\frac{\sigma_3}{|\mathbb{K}|})`$ where $`a(x)=\sum_{M\in \{A,B,C\}} \eta_M v_{\mathbb{H}}(\beta_2)v_{\mathbb{H}}(\beta_1)\hat{val}_{AHP_M}(x)\prod_{N\in\{A,B,C\}-\{M\}}(\beta_2-\hat{row}_{AHP_N}(x))(\beta_1-\hat{col}_{AHP_N}(x))`$and $`b(x)=\prod_{M\in\{A,B,C\}}(\beta_2-\hat{row}_{AHP_M}(x))(\beta_1-\hat{col}_{AHP_M}(x))`$.&#x20;

Therefore, since $$v_{\mathbb{H}}(\beta_1)=22^5+180=18$$ and $$v_{\mathbb{H}}(\beta_2)=80^5+180=72$$ ,&#x20;

$`a(x)=2\times 72\times 18\hat{val}_{AHP_A}(x)(80-\hat{row}_{AHP_B}(x))(22-\hat{col}_{AHP_B}(x))(80-\hat{row}_C(x))(22-\hat{col}_{AHP_C}(x))+30\times72\times18\hat{val}_{AHP_B}(x)(80-\hat{row}_{AHP_A}(x))`$\
$`(22-\hat{col}_{AHP_A}(x))(80-\hat{row}_{AHP_C}(x))(22-\hat{col}_{AHP_C}(x))+100\times72\times 18\hat{val}_{AHP_C}(x)(80-\hat{row}_{AHP_A}(x))(22-\hat{col}_{AHP_A}(x))(80-\hat{row}_{AHP_B}(x))`$\
$`(22-\hat{col}_{AHP_B}(x))=63x^{25 }+ 56x^{24} + 45x^{23} + 27x^{22} + 81x^{21} + 80x^{20} + 66x^{19} + 152x^{18} + 97x^{17} + 55x^{16} + 170x^{15} + 142x^{14} + 3x^{13} + 96x^{12} +`$\
$` 11x^{11} + 69x^{10} + 43x^9 + 10x^8 + 75x^7 + 21x^6 + 109x^5 + 31x^4 + 90x^3 + 159x^2 + 119x + 79`$

and&#x20;

$`b(x)=(80-\hat{row}_{AHP_A}(x))(22-\hat{col}_{AHP_A}(x))(80-\hat{row}_{AHP_B}(x))(22-\hat{col}_{AHP_B}(x))(80-\hat{row}_{AHP_C}(x))(22-\hat{col}_{AHP_C}(x))=23x^{30} + 176x^{29} + 75x^{28} + 63x^{27} + 174x^{26} + 13x^{25} + 43x^{24} + 169x^{23} + 35x^{22 }+ 66x^{21} + 160x^{20} + 99x^{19} + 150x^{18} + 31x^{17} + 69x^{16} + 83x^{15} + 93x^{14} + 179x^{13} + 30x^{12} + 111x^{11} + 58x^{10} + 131x^9 + 18x^8 + 36x^7 + 56x^6 + 59x^5 + 15x^4 + 171x^3 + 47x^2 + 110x + 142`$

Therefore,

$$g_3(x)= 110x^4 + 123x^3 + 161x^2 + 111x + 134$$ &#x20;

\
and

$$h_3(x)=4x^{29} + 74x^{28} + 65x^{27} + 16x^{26} + 139x^{25} + 135x^{24} + 92x^{23} + 139x^{22} + 60x^{21} + 75x^{20} + 75x^{19} + 99x^{18} + 98x^{17} + 71x^{16} + 15x^{15} + 53x^{14} + 138x^{13} + 128x^{12} + 18x^{11} + 147x^{10} + 111x^9 + 37x^8 + 18x^7 + 97x^6 + 143x^5 + 136x^4 + 53x^3 + 50x^2 + 177x + 99$$

The Prover sends ,  $$Com_{AHP_X}^{12}=\sum_{i=0}^{deg_{g_3(x)}}g_{3_i}ck(i)=169$$ and $$Com_{AHP_X}^{13}=\sum_{i=0}^{deg_{h_3(x)}}h_{3_i}ck(i)=166$$  \
where $$g_{3_i}$$ is coefficient of $$x^i$$ of polynomial $$g_3(x)$$ and $$h_{3_i}$$ is coefficient of $$x^i$$ of polynomial $$h_3(x)$$.

12- The Prover sends $`\pi_{AHP}^1=62`$,  $`\pi_{AHP}^2=(166,121,161,97,149)`$, $`\pi_{AHP}^3=(168,141,45,26,63,165,116)`$,  $`\pi_{AHP}^4=(124,81,137,101,71,178,32)`$,  $`\pi_{AHP}^5=(49,157,169,96,80,50,123)`$, $`\pi_{AHP}^6=(32,16,153,20,1,164,45,92)`$ and $`\pi_{AHP}^7=(115,3,0,0,20,1,0,17,101,0,5)`$\
&#x20;to the Verifier that are  value of $`\sigma_1`$, coefficients of polynomials $`\hat{W}(x)`$, $`\hat{z}_A(x)`$, $`\hat{z}_B(x)`$, $`\hat{z}_C(x)`$, $`h_0(x)`$ and $`s(x)`$, respectively.

13- The Prover sends $$\pi_{AHP}^8=(100,90,92,134)$$ and $$\pi_{AHP}^{9}=(31,127,66,180,143,115)$$ to the Verifier that are coefficients of polynomials $$g_1(x)$$ and $$h_1(x)$$, respectively.

14-The Prover sends $$\pi_{AHP}^{10}=70$$, $$\pi_{AHP}^{11}=(105,173,30,40)$$ and $$\pi_{AHP}^{12}=(162,82,96,127)$$ that are value of $$\sigma_2$$ and coefficients of polynomials $$g_2(x)$$ and $$h_2(x)$$, respectively.&#x20;

15- The Prover sends $`\pi_{AHP}^{13}=84`$, $`\pi_{AHP}^{14}=(134,111,161,123,110)`$ and 
$`\pi_{AHP}^{15}=(99,177,50,53,136,143,97,18,37,111,147,18,128,138,53,15,71,98,99,75,75,60,139,92,135,139,16,65,74,4)`$
&#x20;that are value of $`\sigma_3`$ and coefficients of polynomials $`g_3(x)`$ and $`h_3(x)`$, respectively.

16-  The Prover chooses random values $`\eta_{\hat{w}}`$, $`\eta_{\hat{z}_A}`$, $`\eta_{\hat{z}_B}`$, $`\eta_{\hat{z}_C}`$,  $`\eta_{h_0}`$, $`\eta_s`$, $`\eta_{g_1}`$, $`\eta_{h_1}`$, $`\eta_{g_2}`$, $`\eta_{h_2}`$, $`\eta_{g_3}`$ and $`\eta_{h_3}`$ of $`\mathbb{F}`$. For example,  $`\eta_{\hat{w}}=1`$, $`\eta_{\hat{z}_A}=4`$, $`\eta_{\hat{z}_B}=10`$, $`\eta_{\hat{z}_C}=8`$, $`\eta_{h_0}=32`$, $`\eta_s=45`$, $`\eta_{g_1}=92`$, $`\eta_{h_1}=11`$, $`\eta_{g_2}=1`$, $`\eta_{h_2}=5`$, $`\eta_{g_3}=25`$ and $`\eta_{h_3}=63`$.

17- The Prover calculates the linear combination $`p(x)=\eta_{\hat{w}}\hat{w}(x)+\eta_{\hat{z}_A}\hat{z}_A(x)+\eta_{\hat{z}_B}\hat{z}_B(x)+\eta_{\hat{z}_C}\hat{z}_C(x)+\eta_{h_0}h_0(x)+\eta_ss(x)+\eta_{g_1}g_1(x)`$\
&#x20;             $`+\eta_{h_1}h_1(x)+\eta_{g_2}g_2(x)+\eta_{h_2}h_2(x)+\eta_{g_3}g_3(x)+\eta_{h_3}h_3(x)`$.

The Prover obtains&#x20;

$$p(x)=71x^{29} + 137x^{28} + 113x^{27} + 103x^{26} + 69x^{25} + 179x^{24} + 4x^{23} + 69x^{22} + 160x^{21} + 19x^{20} + 19x^{19} + 83x^{18} + 20x^{17} + 129x^{16} + 40x^{15} + 81x^{14} + 6x^{13} + 100x^{12} + 48x^{11} + 74x^{10} + 115x^9 + 179x^8 + 137x^7 + 88x^6 + 126x^5 + 8x^4 + 124x^3 + 37x^2 + 72x + 114$$

18- The Prover calculates $$p(x)$$ in $$x=x'$$ (value of $$x'$$ is received from the Verifier), then puts it in $$\pi_{AHP}^{16}$$ . Therefore  $$\pi_{AHP}^{16}=p(x')=y'$$. For example, if $$x'=2$$, then $$\pi_{AHP}^{16}=p(2)=119$$.

19- The Prover computes $$\pi_{AHP}^{17}=PC.Eval(ck,p(x),d_p,r_p,x')$$ where $$d_p$$ is degree bound of $$p(x)$$ and $$r_p$$ is a random value.\
For example, if the polynomial commitment scheme $$KZG$$ is used, then the Prover builds polynomial \
$$q(x)=\frac{p(x)-y'}{x-x'}=\frac{p(x)-119}{x-2}=71x^{28} + 98x^{27} + 128x^{26} + 178x^{25} + 63x^{24} + 124x^{23} + 71x^{22} + 30x^{21} + 39x^{20} + 97x^{19} + 32x^{18} + 147x^{17} + 133x^{16} + 33x^{15} + 106x^{14} + 112x^{13} + 49x^{12} + 17x^{11} + 82x^{10} + 57x^9 + 48x^8 + 94x^7 + 144x^6 + 14x^5 + 154x^4 + 135x^3 + 32x^2 + 101x + 93$$\
and calculates $$\pi_{AHP}^{17}=gq(\tau)$$ by using $$ck$$ as following:\
$$\pi_{AHP}^{17}=\sum_{i=0}^{deg_{q(x)}}q_i\hspace{1mm}ck(i)=149$$ where $$q_i$$ is the coefficient of $$x^i$$ of $$q(x)$$.

## Proof JSON file Example 1

IoT\_Manufacturer\_Name = "zkIoT"\
IoT\_Device\_Name = "MultiSensor"\
Device\_Hardware\_Version = "1.0"\
Firmware\_Version = "1.0"\
Device Picture= <>\
Lines = \[200, 350, 4000-4010]

```
    {
    "commitmentId": 64-bit,
    "class": 32-bit Integer,
    "input": 4
    "output": 82    
       
    "P_AHP1": 62
    "P_AHP2": [166,121,161,97,149],
    "P_AHP3": [168,141,45,26,63,165,116],
    "P_AHP4": [124,81,137,101,71,178,32],  
    "P_AHP5": [49,157,169,96,80,50,123], 
    "P_AHP6": [32,16,153,20,1,164,45,92],
    "P_AHP7": [115,3,0,0,20,1,0,17,101,0,5],
    "P_AHP8": [100,90,92,134],
    "P_AHP9": [31,127,66,180,143,115],
    "P_AHP10": 70
    "P_AHP11": [105,173,30,40],
    "P_AHP12": [162,82,96,127],
    "P_AHP13": 84
    "P_AHP14": [134,111,161,123,110],
    "P_AHP15": [99,177,50,53,136,143,97,18,37,111,147,18,128,138,53,15,71,98,99,75,75,60,139,92,135,139,16,65,74,4]
    "P_AHP16": 119
    "P_AHP17": 149
      
    "Com_AHP1_x": 4,
    "Com_AHP2_x": 30,
    "Com_AHP3_x": 160,
    "Com_AHP4_x": 69,
    "Com_AHP5_x": 11,
    "Com_AHP6_x": 18,  
    "Com_AHP7_x": 178,
    "Com_AHP8_x": 129,
    "Com_AHP9_x": 33,
    "Com_AHP10_x": 100,
    "Com_AHP11_x": 179,
    "Com_AHP12_x": 169,
    "Com_AHP13_x": 166
}
```

### Example 1 (for operation "and")
$`Proof (\mathbb{F}, T)`$: This function outputs  $`\Pi_{Look\hspace{1mm}up}=(Com_{Look\hspace{1mm}up},\pi_{Look\hspace{1mm}up})`$\

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

Here, the first, the Prover calculates polynomial $`E_1(x)`$ by lagrange interpolation such that $`E_1(00)=1000`$, $`E_1(01)=0010`$, $`E_1(10)=0000`$ and $`E_1(11)=0010`$. That means that polynomial $`E_1(x)`$ passes through points $`(0,8)`$, $`(1,2)`$, $`(2,0)`$ and $`(3,2)`$. Therefore, $`E_1(x)=8L_1(x)+2L_2(x)+0L_3(x)+2L_4(x)`$. where $`L_1(x)=\frac{(x-1)(x-2)(x-3)}{(-1)(-2)(-3)}=9x^3+x^2+1`$, $`L_2(x)=6x^3+3x^2+3x`$, 



$`L_2(x)=6x^3+3x^2+3x `$, $`L_3(x)=5x^3+2x^2+4x`$, $`L_4(x)=2x^3+5x^2+4x`$

Therefore $`E_1(x)=2x^2+3x+8`$.

Now, the Prover calculates polynomials $`E_i(x)`$ for $`i=2,3,..,8`$ by lagrange interpolation such that $`E_i(00)=0000`$, $`E_i(01)=0000`$, $`E_i(10)=0000`$ and $`E_i(11)=0000`$. That means that polynomials $`E_i(x)`$ passes through points $`(0,0)`$, $`(1,0)`$, $`(2,0)`$ and $`(3,0)`$. Therefore, $`E_i(x)=0L_1(x)+0L_2(x)+0L_3(x)+0L_4(x)=0`$.

Therefore, 

$`Com_{Look\hspace{1mm}up}^{1}=\sum_{j=0}^{2}}{E_1}_{j}ck(j)=2ck(3)+3ck(2)+8ck(1)=48\equiv 4(\textrm{mod}\hspace{1mm}11`$

$`Com_{Look\hspace{1mm}up}^{i}=\sum_{j=0}^{0}}{E_i}_{j}ck(j)=0ck(1)=0\equiv 0(\textrm{mod}\hspace{1mm}11`$, $`i=2,3,...,8`$

