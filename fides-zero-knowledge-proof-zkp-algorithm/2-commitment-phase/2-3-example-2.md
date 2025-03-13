# Example 2

Assume the following sample code:\
\
\
$$add\hspace{2mm} R_1, R_1, 5$$                              => Gate 1\
$$mul\hspace{2mm} R_2, R_2, R_{10}$$                        => Gate 2\
$$add\hspace{2mm} R_2,R_2,10$$                            => Gate 3\
$$mul\hspace{2mm} R_1,R_1,R_{19}$$                         => Gate 4


The constraints are as follows considering $$p= 1678321$$:

&#x20;              \
$$R_1^{(2)}=R_1^{(1)}+5$$                                 \
$$R_2^{(2)}=R_2^{(1)}\times R_{10}^{(1)}$$ \
$$R_2^{(3)}=R_2^{(2)}+10$$     \
$$R_1^{(3)}=R_1^{(2)}\times R_{19}^{(1)}$$                


We continue with $$n_g=4$$ and $$n_i=32$$.

The Prover calculates square matrices $$A$$, $$B$$ and $$C$$ of order $$n_g+n_i+1=4+32+1=37$$ based on above construction:

$$
A=\begin{bmatrix}
0&0&0&...&0&0&0&0\\
0&0&0&...&0&0&0&0\\
.&.&.&...&.&.&.&.\\
.&.&.&...&.&.&.&.\\
.&.&.&...&.&.&.&.\\
.&.&.&...&.&.&.&.\\
1&0&0&...&0&0&0&0\\
0&0&1&...&0&0&0&0\\
1&0&0&...&0&0&0&0\\
0&0&0&...&1&0&0&0
\end{bmatrix}
$$, 
$$
B=\begin{bmatrix}
0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&...&0&0&0&0\\
0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&...&0&0&0&0\\
.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&...&.&.&.&.\\
.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&...&.&.&.&.\\
.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&...&.&.&.&.\\
.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&.&...&.&.&.&.\\
5&1&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&...&0&0&0&0\\
0&0&0&0&0&0&0&0&0&0&1&0&0&0&0&0&0&0&0&0&..&0&0&0&0\\
10&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&...&0&1&0&0\\
0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&0&1&...&0&0&0&0
\end{bmatrix}
$$ , 
$$
C=\begin{bmatrix}
0&0&...&0&0&0&0\\
0&0&...&0&0&0&0\\
.&.&...&.&.&.&.\\
.&.&...&.&.&.&.\\
.&.&...&.&.&.&.\\
.&.&...&.&.&.&.\\
0&0&...&1&0&0&0\\
0&0&...&0&1&0&0\\
0&0&...&0&0&1&0\\
0&0&...&0&0&0&1
\end{bmatrix}
$$

At we see, the matrices $$A$$ and $$B$$ are $$33-SLT$$ and matrix $$C$$ is $$33-Diag$$. Also $$Az\hspace{1mm}o\hspace{1mm}Bz=Cz$$.

We consider multiplicative subgroup $$\mathbb{H}$$ of order $$n=n_g+n_i+1=37$$ with generator\
&#x20;$$\omega=11^{\frac{p-1}{37}}\equiv 1101389 (\textrm{mod}\hspace{1mm}p)$$.  Therefore, $$\mathbb{H}=$$ &lcub; $$1,\omega,\omega^2,\omega^3,\omega^4,...,\omega^{36}$$ &rcub; = &lcub; $$1, 1101389, 876941, 1253722, 373750, 668759, 747302, 1444226, 727349, 1364683, 1298322, 1224122, 644775, 127745, 1610054, 257937,$$

$$1257144, 1496263, 722913, 1195510, 1536124,1669124, 870923, 784349, 1262357, 1500979, 469942, 1466322, 1364193, 358753, 1173208,$$

$$586481, 1605555, 1190739, 1632256, 159545, 899305$$ &rcub;

Note that based on construction for matrices $$A$$, $$B$$ and $$C$$, we can conclude that the most number nonzero entries in $$A$$ and $$C$$ is $$n_g$$ and in $$B$$ is $$2n_g$$, therefore we can consider $$m=2n_g$$.\
Therefore, consider multiplicative subgroup $$\mathbb{K}$$ of order $$m=2n_g=8$$ with generator $$\gamma=11^{\frac{p-1}{8}}\equiv  216  (\textrm{mod}\hspace{1mm}p)$$. Therefore, $$\mathbb{K}=\{1,\gamma,\gamma^2,...,\gamma^{7}\}=\{1,216, 46656, 7770, 1678320, 1678105, 1631665, 1670551 \}$$.

### &#x20;AHP Commitment

$$Commit(ck,m_f=(A,B,C),s\in R)$$:&#x20;

1 -  The Prover Selects  $$s=(s_1,...,s_{s_{AHP}(0)})$$ of random space $$R$$.\
&#x20; 2- The Prover calculates $$\overrightarrow{O}_{AHP}=Enc(m_f=(A,B,C))$$ as encoded index as following:

The polynomial $$row_{AHP_A}:\mathbb{K}\to\mathbb{H}$$ with $$row_{AHP_A}(k=\gamma^i)=\omega^{r_i}$$ for $$1\leq i\leq ||A||$$ , and otherwise $$row_{AHP_A}(k)$$ returns an arbitrary element in $$\mathbb{H}$$. \
So $$row_{AHP_A}(k)$$ on $$\mathbb{K}$$ is a polynomial so that $$row_{AHP_A}(1)=\omega^{33}$$ , $$row_{AHP_A}(\gamma)=\omega^{34}$$, $$row_{AHP_A}(\gamma^2)=\omega^{35}$$ , $$row_{AHP_A}(\gamma^3)=\omega^{36}$$  and otherwise $$row_{AHP_A}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example $$row_{AHP_A}(\gamma^i)=\omega^i$$ for $$4\leq i\leq 7$$. Therefore,&#x20;

$$row_{AHP_A}(x)=\sum_{i=1}^{8}y_iL_i(x)=739930x^7 + 100821x^6 + 664621x^5 + 147929x^4 + 1066695x^3 + 902750x^2 + 454730x + 469905$$

Also,  $$col_{AHP_A}:\mathbb{K}\to\mathbb{H}$$ with $$col_{AHP_A}(k=\gamma^i)=\omega^{c_i}$$ for $$1\leq i\leq ||A||$$ and otherwise $$col_{AHP_A}(k)$$ returns an arbitrary element in $$\mathbb{H}$$. \
So, $$col_{AHP_A(}k)$$ on $$\mathbb{K}$$ is a polynomial so that $$col_{AHP_A}(1)=1$$ , $$col_{AHP_A}(\gamma)=\omega^2$$, $$col_{AHP_A}(\gamma^2)=1$$ , $$col_{AHP_A}(\gamma^3)=\omega^{33}$$  and  otherwise  $$col_{AHP_A}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example $$col_{AHP_A}(\gamma^i)=\omega^i$$ for $$4\leq i\leq 7$$. Therefore, $$col_{AHP_A}(x)=\sum_{i=1}^{8}y_iL_i(x)=344425x^7 + 1483132x^6 + 490249x^5 + 246919x^4 + 662128x^3 + 101801x^2 + 833805x + 872505$$

and ,  $$val_{AHP_A}:\mathbb{K}\to\mathbb{H}$$ with $$val_{AHP_A}(k=\gamma^i)=\frac{v_i}{u_{\mathbb{H}}(row_{AHP_A}(k),row_{AHP_A}(k))u_{\mathbb{H}}(col_{AHP_A}(k),col_{AHP_A}(k))}$$ for $$1\leq i\leq ||A||=4$$ where $$v_i$$ is value of  $$i^{th}$$ nonzero entry and otherwise $$val_{AHP_A}(k)$$ returns zero. Note that based on definition of $$u_{\mathbb{H}}(x,y)$$, for each $$x \in \mathbb{H}$$, $$u_{\mathbb{H}}(x,x)=|\mathbb{H}|x^{|\mathbb{H}|-1}=37x^{36}$$. So $$val_{AHP_A}(1)=\frac{1}{(37row_{AHP_A}^{36}(1))(37col_{AHP_A}^{36}(1))}=\frac{1}{37\times (\omega^{33})^{36}\times37\times1}$$, $$val_{AHP_A}(\gamma)=\frac{2}{(37row_{AHP_A}^{36}(\gamma))(37col_{AHP_A}^{36}(\gamma))}=\frac{2}{37\times (\omega^{34})^{36}\times37\times(\omega^2)^{36}}$$ , $$val_{AHP_A}(\gamma^2)=\frac{1}{(37row_{AHP_A}^{36}(\gamma^2))(37col_{AHP_A}^{36}(\gamma^2))}=\frac{1}{37\times (\omega^{35})^{36}\times37\times1}$$, $$val_{AHP_A}(\gamma^3)=\frac{7}{(37row_{AHP_A}^{36}(\gamma^3))(37col_{AHP_A}^{36}(\gamma^3))}=\frac{7}{37\times (\omega^{36})^{36}\times37\times(\omega^{33})^{36}}$$ ,\
&#x20;and $$val_{AHP_A}(k)=0$$ for $$k\in \mathbb{K}-\{1,\gamma,\gamma^2,\gamma^3\}$$. Therefore $$val_{AHP_A}(x)=\sum_{i=1}^{8}y_iL_i(x)=1349736x^7 + 870027x^6 + 189189x^5 + 1024786x^4 + 201373x^3 + 194896x^2 + 1568354x + 1218943$$

Now, $$\hat{row}_{AHP_A}$$, $$\hat{col}_{AHP_A}$$ and $$\hat{val}_{AHP_A}$$ are extensions of $$row_{AHP_A}$$, $$col_{AHP_A}$$ and $$val_{AHP_A}$$ so that are agree on $$\mathbb{K}$$.&#x20;

Similarly, $$row_{AHP_B}:\mathbb{K}\to\mathbb{H}$$ so that  $$row_{AHP_B}(1)=\omega^{33}$$, $$row_{AHP_B}(\gamma)=\omega^{33}$$,  $$row_{AHP_B}(\gamma^2)=\omega^{34}$$ ,   $$row_{AHP_B}(\gamma^3)=\omega^{35}$$, $$row_{AHP_B}(\gamma^4)=\omega^{35}$$,  $$row_{AHP_B}(\gamma^5)=\omega^{36}$$ and for the rest values of $$\mathbb{K}$$,  $$row_{AHP_B}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example  $$row_{AHP_B}(\gamma^i)=\omega^i$$ for $$6\leq i\leq 7$$.  Therefore $$row_{AHP_B}(x)=\sum_{i=1}^{8}y_iL_i(x)=745068x^7 + 1550888x^6 + 311204x^5 + 1053454x^4 + 781197x^3 + 709275x^2 + 356449x + 718167$$

Also,  $$col_{AHP_B}:\mathbb{K}\to\mathbb{H}$$ so that $$col_{AHP_B}(1)=1$$ , $$col_{AHP_B}(\gamma)=\omega$$, $$col_{AHP_B}(\gamma^2)=\omega^{10}$$,  $$col_{AHP_B}(\gamma^3)=1$$ , $$col_{AHP_B}(\gamma^4)=\omega^{34}$$, $$col_{AHP_B}(\gamma^5)=1$$  and for the rest values of $$\mathbb{K}$$ , $$col_{AHP_B}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example, $$col_{AHP_B}(\gamma^i)=\omega^i$$ for $$6\leq i\leq 7$$.  Therefore $$col_{AHP_B}(x)=\sum_{i=1}^{8}y_iL_i(x)=757883x^7 + 1334841x^6 + 941775x^5 + 1041045x^4 + 898965x^3 + 1498879x^2 + 781052x + 1137166$$

and ,  $$val_{AHP_B}:\mathbb{K}\to\mathbb{H}$$ so that  $$val_{AHP_B}(1)=\frac{5}{(37row_{AHP_B}^{36}(1))(37col_{AHP_B}^{36}(1))}=\frac{5}{37\times (\omega^{33})^{36}\times37\times1}=$$, $$val_{AHP_B}(\gamma)=\frac{1}{(37row_{AHP_B}^{36}(\gamma))(37col_{AHP_B}^{36}(\gamma))}=\frac{1}{37\times (\omega^{33})^{36}\times37\times(\omega)^{36}}$$ , \
$$val_{AHP_B}(\gamma^2)=\frac{1}{(37row_{AHP_B}^{36}(\gamma^2))(37col_{AHP_B}^{36}(\gamma^2))}=\frac{1}{37\times (\omega^{34})^{36}\times37\times1}$$ , $$val_{AHP_B}(\gamma^3)=\frac{10}{(37row_{AHP_B}^{36}(\gamma^3))(37col_{AHP_B}^{36}(\gamma^3))}=\frac{10}{37\times (\omega^{35})^{36}\times37\times1}$$, $$val_{AHP_B}(\gamma^4)=\frac{1}{(37row_{AHP_B}^{36}(\gamma^4))(37col_{AHP_B}^{36}(\gamma^4))}=\frac{1}{37\times (\omega^{35})^{36}\times37\times(\omega^{34})^{36}}$$ , $$val_{AHP_B}(\gamma^5)=\frac{1}{(37row_{AHP_B}^{36}(\gamma^5))(37col_{AHP_B}^{36}(\gamma^5))}=\frac{1}{37\times (\omega^{36})^{36}\times37\times1}$$ , \
and $$val_{AHP_B}(k)=0$$ for $$k\in \mathbb{K}-\{1,\gamma,\gamma^2,\gamma^3,\gamma^4,\gamma^5\}$$. Therefore $$val_{AHP_B}(x)=\sum_{i=1}^{8}y_iL_i(x)=1592245x^7 + 169676x^6 + 1573426x^5 + 1612428x^4 + 256156x^3 + 1249861x^2 + 995621x + 462292$$

Now, $$\hat{row}_{AHP_B}$$, $$\hat{col}_{AHP_B}$$ and $$\hat{val}_{AHP_B}$$ are extensions of $$row_{AHP_B}$$, $$col_{AHP_B}$$ and $$val_{AHP_B}$$ so that are agree on $$\mathbb{K}$$.&#x20;

Similarly, $$row_{AHP_C}:\mathbb{K}\to\mathbb{H}$$ so that  $$row_{AHP_C}(1)=\omega^{33}$$, $$row_{AHP_C}(\gamma)=\omega^{34}$$,  $$row_{AHP_C}(\gamma^2)=\omega^{35}$$, $$row_{AHP_C}(\gamma^3)=\omega^{36}$$ and for the rest values of $$\mathbb{K}$$,  $$row_{AHP_C}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example  $$row_{AHP_C}(\gamma^i)=\omega^{i}$$ for $$4\leq i\leq 7$$. Therefore $$row_{AHP_C}(x)=\sum_{i=1}^{8}y_iL_i(x)=739930x^7 + 100821x^6 + 664621x^5 + 147929x^4 + 1066695x^3 + 902750x^2 + 454730x + 469905$$

Also,  $$col_{AHP_C}:\mathbb{K}\to\mathbb{H}$$ so that $$col_{AHP_C}(1)=\omega^{33}$$ , $$col_{AHP_C}(\gamma)=\omega^{34}$$,  $$col_{AHP_C}(\gamma^2)=\omega^{35}$$, $$col_{AHP_C}(\gamma^3)=\omega^{36}$$  and for the rest values of $$\mathbb{K}$$ , $$col_{AHP_C}(k)$$ returns arbitrary elements of $$\mathbb{H}$$, for example  $$col_{AHP_C}(\gamma^i)=\omega^i$$ for $$4\leq i\leq 7$$. Therefore $$col_{AHP_C}(x)=\sum_{i=1}^{8}y_iL_i(x)=739930x^7 + 100821x^6 + 664621x^5 + 147929x^4 + 1066695x^3 + 902750x^2 + 454730x + 469905$$

and ,  $$val_{AHP_C}:\mathbb{K}\to\mathbb{H}$$ so that \
&#x20;$$val_{AHP_C}(1)=\frac{1}{(37row_{AHP_C}^{36}(1))(37col_{AHP_C}^{36}(1))}=\frac{1}{37\times (\omega^{33})^{36}\times37\times(\omega^{33})^{36}}$$, $$val_{AHP_C}(\gamma)=\frac{1}{(37row_{AHP_C}^{36}(\gamma))(37col_{AHP_C}^{36}(\gamma))}=\frac{1}{37\times (\omega^{34})^{36}\times37\times(\omega^{34})^{36}}$$ , $$val_{AHP_C}(\gamma^2)=\frac{1}{(37row_{AHP_C}^{36}(\gamma^2))(37col_{AHP_C}^{36}(\gamma^2))}=\frac{1}{37\times (\omega^{35})^{36}\times37\times(\omega^{35})^{36}}$$ ,$$val_{AHP_C}(\gamma^3)=\frac{1}{(37row_{AHP_C}^{36}(\gamma^3))(37col_{AHP_C}^{36}(\gamma^3))}=\frac{1}{37\times (\omega^{36})^{36}\times37\times(\omega^{36})^{36}}$$ \
&#x20;and $$val_{AHP_C}(k)=0$$ for $$k\in \mathbb{K}-\{1,\gamma,\gamma^2,\gamma^3\}$$. Therefore $$val_{AHP_C}(x)=\sum_{i=1}^{8}y_iL_i(x)=435354x^7 + 1188860x^6 + 1158417x^5 + 525698x^4 + 1126753x^3 + 467855x^2 + 544916x + 1083027$$

Now, $$\hat{row}_{AHP_C}$$, $$\hat{col}_{AHP_C}$$ and $$\hat{val}_{AHP_C}$$ are extensions of $$row_{AHP_C}$$, $$col_{AHP_C}$$ and $$val_{AHP_C}$$ so that are agree on $$\mathbb{K}$$.&#x20;

Therefore,&#x20;

$$\overrightarrow{O}_{AHP}=469905,  454730, 902750, 1066695,  147929, 664621, 100821, 739930,872505 ,$$\
$$833805, 101801, 662128,246919, 490249, 1483132, 344425,1218943,1568354, 194896$$\
$$201373, 1024786, 189189,870027, 1349736,718167,356449, 709275, 781197,1053454,$$\
$$311204,1550888,745068, 1137166,  781052,  1498879, 898965, 1041045, 941775, 1334841,$$\
$$757883,462292, 995621, 1249861,256156, 1612428, 1573426, 169676,1592245,469905,$$\
$$454730,902750, 1066695,147929,664621,100821,739930,469905,454730, 902750,$$\
$$1066695, 147929,664621,100821, 739930, 1083027, 544916,467855,1126753,525698,$$\
$$1158417,1188860,435354)$$

3- The Prover calculates commitment by using of $$KZG$$ commitment scheme as following:

$$Com_{T}=\sum_{i=0}^{deg_T}a_ig\tau^i=\sum_{i=0}^{deg_T}a_ick(i)$$  where  $$a_i$$ is coefficient of $$x^i$$ in polynomial  $$T(x)$$.

4- The Prover sends\
$$Com_{AHP}^0=\sum_{i=0}^{5}\hat{row}_{AHP_{A_i}}\hspace{1.1mm}ck(i)=$$\


and similarly

$$Com_{AHP}^1=$$, $$Com_{AHP}^2=$$, $$Com_{AHP}^3=$$, $$Com_{AHP}^4=$$, $$Com_{AHP}^5=$$, $$Com_{AHP}^6=$$, $$Com_{AHP}^7=$$ and $$Com_{AHP}^8=$$.

## 2-3- PFR and AHP Commitment.json File Format

```
{
    "commitmentId": String,
    "deviceType": String,
    "deviceIdType": String,
    "deviceModel": String,
    "manufacturer": String,
    "softwareVersion": String,
    "class":2,
    "m": 8,
    "n": 37,
    "p": 1678321,
    "g": 11,   
        
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
    "row_AHP_A": [469905, 454730, 902750, 1066695, 147929, 664621, 100821, 739930]
    "col_AHP_A": [ 872505, 833805, 101801, 662128,246919, 490249, 1483132, 344425]
    "val_AHP_A": [1218943,1568354, 194896,201373, 1024786, 189189,870027, 1349736]
    "row_AHP_B": [718167,356449, 709275, 781197,1053454, 311204,1550888,745068]
    "col_AHP_B": [1137166, 781052, 1498879, 898965, 1041045, 941775, 1334841,757883]
    "val_AHP_B": [462292, 995621, 1249861,256156, 1612428, 1573426, 169676,1592245]
    "row_AHP_C": [469905, 454730,902750, 1066695,147929,664621,100821,739930]
    "col_AHP_C": [469905,454730, 902750,1066695, 147929,664621,100821, 739930]
    "val_AHP_C": [1083027, 544916,467855,1126753,525698, 1158417,1188860,435354]
    "Com_AHP0": 64-bit Integer,
    "Com_AHP1": 64-bit Integer,
    "Com_AHP2": 64-bit Integer,
    "Com_AHP3": 64-bit Integer,
    "Com_AHP4": 64-bit Integer,
    "Com_AHP5": 64-bit Integer,
    "Com_AHP6": 64-bit Integer,
    "Com_AHP7": 64-bit Integer,
    "Com_AHP8": 64-bit Integer,    
    
    "curve": String,
    "polynomial_commitment": String
}
```
