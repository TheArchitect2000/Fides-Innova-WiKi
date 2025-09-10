---
description: >-
  The commitment phase contains two parts; AHP commitment and PFR commitment.
  After reviewing the algorithm, we will provide an example to clarify each
  parts.
---

# 2- Commitment Phase

Let $`\textit{M}_f`$ be a functional set which contains triple matrices  $`m_f=(A,B,C)\in (\mathbb{F}^{n\times n})^3`$ such that for each input vector $`X`$, there is a unique output vector $`Y`$ as well as a witness (intermediate) $`W`$ where $`Az\hspace{1mm} o\hspace{1mm} Bz=Cz`$ considering $`z=(1,X,W,Y)`$. 

The triplet  $`(A,B,C)\in (\mathbb{F}^{n\times n})^3`$  is a functional set if and only if $`A`$ and $`B`$ are $`t-`$ strictly lower triangular matrices $`(t-SLT)`$ and $`C`$ is $`t-`$ diagonal matrix $`(t-Diag)`$ \[1]. Here, $`t=|X|+1`$. 

The Prover obtains $`t-SLT`$  matrices $`A`$, $`B`$ and  $`t-Diag`$ matrix $`C`$ for the arithmetic circuit that is a directed acyclic graph of gates and wire inputs. Wires carry values from $`\mathbb{F}`$ and gates are add or multiplication. This work is done based on the two steps of the following construction:

* &#x20;Initialize three zero square matrices $`A, B, C`$ over $`\mathbb{F}`$ of order $`n=n_g +n_i + 1`$ where $`n_g`$ is the number of gates and $`n_i`$ is the number of inputs. Rows and columns of matrices are indexed on &lcub; $`0,1,...,n_g+n_i`$ &rcub;. Also, Gate $`i`$ with two left L and right R inputs and a selector S. We show the Gate  $`i`$ with a tuple $`(l_i, r_i, s_i)`$ where $`l_i`$ and $`r_i`$ are the left and right inputs' indexes in $`z`$, respectively.  Note that $`z`$ is indexed on  $`\{0,1,..,n_g+n_i\}`$. Hence,   $`l_i`$ and $`r_i`$ are between $`0`$ and $`n_g+n_i`$. Also, $`s_i`$ is "Addition", "Subtraction", "Multiplication" or "Division".  Note, if the left input is a value $`v`$, then $`l_i=0`$ or if the right input is a value $`v`$, then $`r_i=0`$.
* For $`i=0.., n_g-1:`$\
  &#x20;                 
  &#x20;                     If $`s_i`$ is "Addition" \
                              $`\hspace{1cm}`$ $`a)`$ Set $`C_{1+n_i+i, 1+n_i+i}=1`$\
                               $`\hspace{1cm}`$ $`b)`$\
  &#x20;                         $`\hspace{1.5cm}`$    $`A_{1+n_i+i,\hspace{1mm}0}=1`$\
  &#x20;                         $`\hspace{1.5cm}`$$`B_{1+n_i+i,\hspace{1mm}l_i}=\begin{cases}\text{left input}\hspace{1cm}l_i=0\\1\hspace{2.2cm}\text{otherwise}\end{cases}`$\
  &#x20;                         \
  &#x20;                         \
  &#x20;                         $`\hspace{1.5cm}`$ $`B_{1+n_i+i,\hspace{1mm}r_i}=\begin{cases}\text{right input}\hspace{1cm}r_i=0\\1\hspace{2.2cm}\text{otherwise}\end{cases}`$ \
  &#x20;                     \
  &#x20;                     If $`s_i`$ is "Subtraction" \
                                $`\hspace{1cm}`$ $`a)`$ Set $`C_{1+n_i+i, 1+n_i+i}=1`$\
                                $`\hspace{1cm}`$ $`b)`$\
 &#x20;                          $`\hspace{1.5cm}`$ $`A_{1+n_i+i,\hspace{1mm}0}=1`$\
  &#x20;                         $`\hspace{1.5cm}`$ $`B_{1+n_i+i,\hspace{1mm}l_i}=\begin{cases}\text{left input}\hspace{1cm}l_i=0\\1\hspace{2.2cm}\text{otherwise}\end{cases}`$\
  &#x20;                         \
  &#x20;                         \
  &#x20;                         $`\hspace{1.5cm}`$$`B_{1+n_i+i,\hspace{1mm}r_i}=\begin{cases}(p-1)\times\text{right input}\hspace{1cm}r_i=0\\p-1\hspace{3.6cm}\text{otherwise}\end{cases}`$ \
  &#x20;                     \
  &#x20;                     If $`s_i`$ is "Multiplication" \
                                 $`\hspace{1cm}`$ $`a)`$ Set $`C_{1+n_i+i, 1+n_i+i}=1`$\
                                  $`\hspace{1cm}`$ $`b)`$\
  &#x20;                           $`\hspace{1.5cm}`$$`A_{1+n_i+i,\hspace{1mm}l_i}=\begin{cases}\text{left input}\hspace{1cm}l_i=0\\1\hspace{2.2cm}\text{otherwise}\end{cases}`$\
  &#x20;                         \
  &#x20;                         $`\hspace{1.5cm}`$ $`B_{1+n_i+i,\hspace{1mm}r_i}=\begin{cases}\text{right input}\hspace{1cm}r_i=0\\1\hspace{2.2cm}\text{otherwise}\end{cases}`$\
  &#x20;                     If $`s_i`$ is "Division" \
                                  $`\hspace{1cm}`$ $`a)`$ Set $`C_{1+n_i+i, l_i}=1`$\
                                  $`\hspace{1cm}`$ $`b)`$\
  &#x20;                         $`\hspace{1.5cm}`$$`A_{1+n_i+i,\hspace{1mm}o_i}=1`$\
  &#x20;                         $`\hspace{1.5cm}`$$`B_{1+n_i+i,\hspace{1mm}r_i}=\begin{cases}\text{right input}\hspace{1cm}r_i=0\\1\hspace{2.2cm}\text{otherwise}\end{cases}`$
                               

If our processing machine has 32 registers, then the size of the input vector $`X`$ will be 32. Therefore, $`n_i=32`$ and $`X=(x_1,x_2,...,x_{32})`$ where $`x_i`$ corresponds to $`i^{th}`$ register, $`R_i`$. Also, $`z=(1,x_1,x_2,..x_{32},w_1,..,w_{n_g-n_r},y_1,..,y_{n_r})`$ where $`n_r`$ is the number of registers that change during a program execution. For example, assume the first gate in a computation is the instruction "add $`R_1`$ , $`R_1`$, 5", which means $`R_1^{(2)}=R_1^{(1)}+5`$ . In the above "for" loop in step $`i=0`$, $`s_0`$="Addition", $`l_0=1`$, and $`r_0=0`$, hence $`C_{1+32,\hspace{1mm}1+32}=1`$ , $`A_{1+32,\hspace{1mm}0}=1`$, , and $`B_{{1+32},\hspace{1mm}0}=5`$.

## 2-1- PFR Commitment

PFR aims to prove the target program is a function with mentioned characteristics in $`A, B, C`$. PFR function will be edited later.&#x20;
$`Commit(ck,m_f=(A,B,C)\in \textit{M}_f,s\in R)`$:  This function outputs &#x20;
$`Com_{PFR}=(Com_{PFR}^0,Com_{PFR}^1,Com_{PFR}^2,Com_{PFR}^3,Com_{PFR}^4,Com_{PFR}^5,Com_{PFR}^6,Com_{PFR}^7,Com_{PFR}^8)`$&#x20;

as following:

&#x20;1 - The Prover selects randomness $`s=(s_1,...,s_{s_{AHP}(0)})`$ of randomness space $`R`$.

&#x20; 2- The Prover calculates $`\overrightarrow{O}_{PFR}=Enc(m_f=(A,B,C))`$ as encoded index as following:

The Prover encodes each matrix $`A, B`$ and $`C`$ by three polynomials. The matrix $`N`$, $`N\in\{A, B, C\}`$, is encoded by polynomials $`row_{PFR_N}(x)`$, $`col_{PFR_N}(x)`$ and $`val_{PFR_N}(x)`$ so that $`row_{PFR_N}(\gamma^i)=\omega^{r_i}`$, $`col_{PFR_N}(\gamma^i)=\omega^{c_i}`$ and $`val_{PFR_N}(\gamma^i)=v_i`$ for $`i\in\{0,1,2,..,m-1\}`$ where  $`m=2n_g`$ is maximum of the number of nonzero entries in the  matrix $`N`$, The value of  $`n=n_g+n_i+1`$ is the order of the matrix.  Also, $`\gamma`$ is a generator of  multiplicative subgroup $`\mathbb{K}`$ of  $`\mathbb{F}`$ of order $`m`$ ($`\mathbb{K}=<\gamma>`$ and $`|\mathbb{K}|=m`$) and  $`\omega`$ is a generator of multiplicative subgroup $`\mathbb{H}`$ of $`\mathbb{F}`$ of order $`n`$ ($`\mathbb{H}=<\omega>`$ and $`|\mathbb{H}|=n`$).  Also $`r_i,c_i\in \{0,1,...,n-1\}`$ and $`v_i\in \mathbb{F}`$ are row number, column number and value of $`i^{th}`$ nonzero entry, respectively. Then, lets   $`O_{PFR}=(row_{PFR_{A_0}},....,row_{PFR_{A_{m-1}}},col_{PFR_{A_0}},...,col_{PFR_{A_{m-1}}},val_{PFR_{A_0}},...,val_{PFR_{A_{m-1}}},`$ $`row_{PFR_{B_0}},...,row_{PFR_{B_{m-1}}},col_{PFR_{B_0}},...,col_{PFR_{B_{m-1}}},val_{PFR_{B_0}},....,val_{PFR_{C_{m-1}}},`$ 
$`row_{PFR_{C_0}},...,row_{PFR_{C_{m-1}}},col_{PFR_{C_0}},...col_{PFR_{C_{m-1}}},val_{PFR_{C_0}},...,val_{PFR_{C_{m-1}}})`$

where $`row_{PFR_{N_i}}`$, $`col_{PFR_{N_i}}`$ and  $`val_{PFR_{N_i}}`$ are coefficient of $`x^i`$ of polynomials $`row_{PFR_N}(x)`$, $`col_{PFR_N}(x)`$ and $`val_{PFR_N}(x)`$ , respectively. The vector $`O_{PFR}`$ is called as  encoded index.

3- The Prover calculates $`Com_{PFR_T}=PC.Commit(ck,T,d_{AHP}(N,0,i)=m,r_{T})`$ for each polynomial $`T(x)`$. Note that $`T\in\{row_{PFR_N},col_{PFR_N},val_{PFR_N}\hspace{2mm}|\hspace{2mm}N\in \{A,B,C\}\}`$.

For example, if the polynomial commitment scheme $`KZG`$ is used, then \
$`Com_{T}=\sum_{i=0}^{deg_T}a_ig\tau^i=\sum_{i=0}^{deg_T}a_ick(i)`$  where  $`a_i`$ is coefficient of $`x^i`$ in polynomial $`T(x)`$.&#x20;

Size of Commitment: $`|Com_{PFR}|=9`$.

4- The Prover sends $`Com_{PFR}`$ to the Verifier.

CommitmentId= (SHA256(deviceType + deviceIdType + deviceModel + manufacturer + softwareVersion + creationTime))

## 2-2- AHP Commitment &#x20;

As mentioned before AHP phase aims, without revealing any information about function $`f`$, to prove that $`y=f(x)`$ for public $`x`$ and $`y`$. Now, we create a commitment for Algebraic Holographic Proof (AHP), $`AHP\hspace{1mm}Com`$ , in this section.&#x20;

$`Commit(ck',m_f=(A,B,C)\in \textit{M}_f,s\in R)`$: This function outputs 

$`Com_{AHP}=(Com_{AHP}^0,Com_{AHP}^1,Com_{AHP}^2,Com_{AHP}^3,Com_{AHP}^4,Com_{AHP}^5,Com_{AHP}^6,Com_{AHP}^7,Com_{AHP}^8)`$&#x20;
, here $`ck'(i)=ck(i )\hspace{1mm}r'^i`$ with random $`r'`$. &#x20;

&#x20;1 - The Prover selects random $`s=(s_1,...s_{s_{AHP}(0)})`$ from random space $`R`$. Note that $`s_{AHP}(0)=9`$ as explained in the setup phase. &#x20;2- The Prover calculates $`\overrightarrow{O}_{AHP}=Enc(m_f=(A,B,C))`$ as encoded index as following:

* Considering $`\gamma`$ as a generator of  multiplicative subgroup $`\mathbb{K}`$ of $`\mathbb{F}`$ of order $`m`$ (i.e., $`\mathbb{K}=<\gamma>`$ and $`|\mathbb{K}|=m`$), $`\omega`$ as a generator of multiplicative subgroup $`\mathbb{H}`$ of $`\mathbb{F}`$ of order $`n`$ (i.e., $`\mathbb{H}=<\omega>`$ and $`|\mathbb{H}|=n`$), for each matrix $`N\in \{A,B,C\}`$, we generate 3 polynomials $`row_{AHP_N}(x)`$,  $`col_{AHP_N}(x)`$, and  $`val_{AHP_N}(x)`$ as described in the following steps:
* The polynomial $`row_{AHP_N}:\mathbb{K}\to\mathbb{H}`$ is constructed by $`row_{AHP_N}(k=\gamma^i)=\omega^{r_i}`$ for $`0\leq i\leq ||N||-1`$ where $`||N||`$ is the number of nonzero entries in $`N`$, and $`r_i\in \{0,1,...,n-1\}`$ is the row number of  $`i^{th}`$ nonzero entry and otherwise, $`row_{AHP_N}(k)`$ is an arbitrary element in $`\mathbb{H}`$. Note that $`i`$ starts from zero. This step generate 3 polynomials; $`row_{AHP_A}(x)`$, $`row_{AHP_B}(x)`$, $`row_{AHP_C}(x)`$.
* The polynomial $`col_{AHP_N}:\mathbb{K}\to\mathbb{H}`$ is constructed by $`col_{AHP_N}(k=\gamma^i)=\omega^{c_i}`$ for $`0\leq i\leq ||N||-1`$ and $`c_i\in \{0,1,...,n-1\}`$ is column number of  $`i^{th}`$ nonzero entry and otherwise $`col_{AHP_N}(k)`$ returns an arbitrary element in $`\mathbb{H}`$.  This step generate 3 polynomials; $`col_{AHP_A}(x)`$, $`col_{AHP_B}(x)`$, $`col_{AHP_C}(x)`$.
* The polynomial $`val_{AHP_N}:\mathbb{K}\to\mathbb{H}`$ is constructed by $`val_{AHP_N}(k=\gamma^i)=\frac{v_i}{u_{\mathbb{H}}(row_{AHP_N}(k),row_{AHP_N}(k))u_{\mathbb{H}}(col_{AHP_N}(k),col_{AHP_N}(k))}`$ for $`0\leq i\leq ||N||-1`$ where $`v_i`$ is value of  $`i^{th}`$ nonzero entry and otherwise $`val_{AHP_N}(k)`$ returns zero where for each $`x \in \mathbb{H}`$, $`u_{\mathbb{H}}(x,x)=|\mathbb{H}|x^{|\mathbb{H}|-1}`$.

Now, we define $`\hat{row}_{AHP_N}`$, $`\hat{col}_{AHP_N}`$ and $`\hat{val}_{AHP_N}`$ as domain-extend of polynomials $`row_{AHP_N}`$, $`col_{AHP_N}`$ and $`val_{AHP_N}`$ where their domains are extended from subgroup $`\mathbb{K}`$ to filed  $`\mathbb{F}`$. Therefore, $`\forall k \in \mathbb{K}`$, $`row_{AHP_N}(k) = \hat{row}_{AHP_N}(k)`$, $`col_{AHP_N}(k) = \hat{col}_{AHP_N}(k)`$, and $`val_{AHP_N}(k) = \hat{val}_{AHP_N}(k)`$.

$`\overrightarrow{O}_{AHP}`$=  
$`(\hat{row}_{AHP_{A_0}},...,\hat{row}_{AHP_{A_{m-1}}},\hat{col}_{AHP_{A_0}},...,\hat{col}_{AHP_{A_{m-1}}},\hat{val}_{AHP_{A_0}},...,\hat{val}_{AHP_{A_{m-1}}},\hat{row}_{AHP_{B_0}},...,\hat{row}_{AHP_{B_{m-1}}},\hat{col}_{AHP_{B_0}},....`$ 

$`,\hat{col}_{AHP_{B_{m-1}}},\hat{val}_{AHP_{B_0}},...,\hat{val}_{AHP_{B_{m-1}}},\hat{row}_{AHP_{C_0}},...,\hat{row}_{AHP_{C_{m-1}}},\hat{col}_{AHP_{C_0}},...,\hat{col}_{AHP_{C_{m-1}}},\hat{val}_{AHP_{C_0}},....,\hat{val}_{AHP_{C_{m-1}}})`$

where $`\hat{row}_{AHP_{N_i}}`$, $`\hat{col}_{AHP_{N_i}}`$ and $`\hat{val}_{AHP_{N_i}}`$ are coefficient of $`x^i`$ of polynomials $`\hat{row}_{AHP_N}(x)`$, $`\hat{col}_{AHP_N}(x)`$ and $`\hat{val}_{AHP_N}(x)`$, respectively. The vector $`\overrightarrow{O}_{AHP}`$ is called the **encoded index**.&#x20;

3- The Prover calculates commitment for polynomial $`T\in`$ &lcub; $`\hat{row}_{AHP_N},\hat{col}_{AHP_N},\hat{val}_{AHP_N}\hspace{2mm}|\hspace{2mm}N\in\{A,B,C\}`$ &rcub; as $`Com_{AHP_T}=PC.Commit(ck',T,d_{AHP}(N,0,i)=m,s_i)`$.

For example, if the polynomial commitment scheme $`KZG`$ is used, then\
$`Com_{AHP_T}=\sum_{i=0}^{deg_T}a_ick'(i)`$ where $`a_i`$ is coefficient of $`x^i`$ in polynomial $`T(x)`$ are calculated by the Prover as follows: \
$`Com_{AHP}^0=\sum_{i=0}^{deg_{\hat{row}_{AHP_A}(x)}}\hat{row}_{AHP_{A_i}}\hspace{1.1mm}ck'(i)`$,  \
&#x20;$`Com_{AHP}^1=\sum_{i=0}^{deg_{\hat{col}0_{AHP_A}(x)}}\hat{col}_{AHP_{A_i}}\hspace{1.1mm}ck'(i)`$,  \
&#x20;$`Com_{AHP}^2=\sum_{i=0}^{deg_{\hat{val}_{AHP_A}(x)}}\hat{val}_{AHP_{A_i}}\hspace{1.1mm}ck'(i)`$,\
$`Com_{AHP}^3=\sum_{i=0}^{deg_{\hat{row}_{AHP_B}(x)}}\hat{row}_{AHP_{B_i}}\hspace{1.1mm}ck'(i)`$,  \
$`Com_{AHP}^4=\sum_{i=0}^{deg_{\hat{col}_{AHP_B}}(x)}\hat{col}_{AHP_{B_i}}\hspace{1.1mm}ck'(i)`$,   \
$`Com_{AHP}^5=\sum_{i=0}^{deg_{\hat{val}_{AHP_B}(x)}}\hat{val}_{AHP_{B_i}}\hspace{1.1mm}ck'(i)`$, \
$`Com_{AHP}^6=\sum_{i=0}^{deg_{\hat{row}_{AHP_C}(x)}}\hat{row}_{AHP_{C_i}}\hspace{1.1mm}ck'(i)`$,  \
&#x20;$`Com_{AHP}^7=\sum_{i=0}^{deg_{\hat{col}_{AHP_C}(x)}}\hat{col}_{AHP_{C_i}}\hspace{1.1mm}ck'(i)`$,   \
$`Com_{AHP}^8=\sum_{i=0}^{deg_{\hat{val}_{AHP_C}(x)}}\hat{val}_{AHP_{C_i}}\hspace{1.1mm}ck'(i)`$.

4- The prover send the calculated commitment values to the Verifier.

## 2-3- PFR and AHP Commitment.json File Format
A publicly accessible file to be published on a public repository, such as a blockchain.
```
{
    "commitmentId": String,
    "deviceType": String,
    "deviceIdType": String,
    "deviceModel": String,
    "manufacturer": String,
    "softwareVersion": String,
    "class": 32-bit Integer,
    "m": 64-bit Integer,
    "n": 64-bit Integer,
    "p": 64-bit Integer,
    "g": 64-bit Integer,   
        
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
    "row_AHP_A": 64-bit Array,
    "col_AHP_A": 64-bit Array,
    "val_AHP_A": 64-bit Array,
    "row_AHP_B": 64-bit Array,
    "col_AHP_B": 64-bit Array,
    "val_AHP_B": 64-bit Array,
    "row_AHP_C": 64-bit Array,
    "col_AHP_C": 64-bit Array,
    "val_AHP_C": 64-bit Array,
    
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
    "polynomialCommitment": String
}
```
* **`commitmentId`**: Unique identifier for the commitment.
* **`deviceType`**: Type of the IoT device (e.g., 'Sensor', 'Actuator', Car).
* **`deviceIdType`**: Type of the device identifier (e.g., 'MAC', 'VIN').
* **`deviceModel`**: Model of the IoT device.
* **`manufacturer`**: Manufacturer of the IoT device (e.g., 'Siemens', 'Tesla').
* **`softwareVersion`**: Software or firmware version of the device.

## Param.json File Format


# 2- Commitment Phase (for logical operation "and")


