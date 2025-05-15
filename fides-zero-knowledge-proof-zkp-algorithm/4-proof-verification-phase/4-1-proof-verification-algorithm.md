---
description: >-
  In this section, we will review the proof verification phase of the protocol.
  This phase contains two parts; AHP and PFR. We also provide an example to
  clarify the method.
---

# 4- Proof Verification Phase

## 4-1- PFR Verify
$$Verify(\mathbb{F}, \mathbb{H}, \mathbb{K}, com_{PFR},\pi_{PFR})$$: This function outputs $$1$$, if the following equations satisfies.

$`1) h(\gamma^{p_i})=a_i`$ for $`i\in \{1,2,...,v\}`$ where $`\pi_{PFR_1}=h(x)`$\
$`2) M(\beta_2)-q_2(\beta_2)Z_{\mathbb{K}}(\beta_2)=0`$

## 4-2- AHP Verify

$$Verify(\mathbb{F}, \mathbb{H}, \mathbb{K}, Com_{AHP},\Pi_{AHP},X,Y)$$: This function outputs 1 if

1- The Verifier checks $`\hat{z}_C(\omega^{j})=Y(i)`$ for indices $`j`$ corresponding to $`Y`$ and $`i=1,...,n_r`$.  
   

2- The following four equations satisfies for random value  $$\beta_3\in\mathbb{F}$$ chosen by the Verifier.

$`h_3(\beta_3)v_{\mathbb{K}}(\beta_3)=a(\beta_3)-b(\beta_3)(\beta_3g_3(\beta_3)+\frac{\sigma_3}{|\mathbb{K}|})\hspace{1cm}(1)`$

$`r(\alpha,\beta_2)\sigma_3=h_2(\beta_2)v_{\mathbb{H}}(\beta_2)+\beta_2g_2(\beta_2)+\frac{\sigma_2}{|\mathbb{H}|}\hspace{1.3cm}(2)`$

$`s(\beta_1)+r(\alpha,\beta_1)(\sum_{M\in\{A,B,C\}}\eta_M\hat{z}_M(\beta_1))-\sigma_2\hat{z}(\beta_1)=h_1(\beta_1)v_{\mathbb{H}}(\beta_1)+\beta_1g_1(\beta_1)+\frac{\sigma_1}{|\mathbb{H}|}\hspace{2mm}(3)`$

$`\hat{z}_A(\beta_1)\hat{z}_B(\beta_1)-\hat{z}_C(\beta_1)=h_0(\beta_1)v_{\mathbb{H}}(\beta_1)\hspace{2cm}(4)`$

where $`a(x)=\sum_{M\in \{A,B,C\}} \eta_M v_{\mathbb{H}}(\beta_2)v_{\mathbb{H}}(\beta_1)\hat{val_{AHP_M}}(x)\prod_{N\in\{A,B,C\}-\{M\}}(\beta_2-\hat{row_{AHP_N}}(x))(\beta_1-\hat{col_{AHP_N}}(x))`$ and $`b(x)=\prod_{M\in\{A,B,C\}}(\beta_2-\hat{row_{AHP_M}}(x))(\beta_1-\hat{col_{AHP_M}}(x))`$.&#x20;

3- The output $$result$$ in following steps is $$1$$.

3-1- The Verifier chooses random values $`\eta_{row_{AHP_A}}`$ , $`\eta_{col_{AHP_A}}`$ , $`\eta_{val_{AHP_A}}`$ , $`\eta_{row_{AHP_B}}`$ , $`\eta_{col_{AHP_B}}`$ , $`\eta_{val_{AHP_B}}`$ ,\
&#x20; $`\eta_{row_{AHP_C}}`$ , $`\eta_{col_{AHP_C}}`$ , $`\eta_{val_{AHP_C}}`$ ,  $`\eta_{\hat{w}}`$, $`\eta_{\hat{z}_A}`$, $`\eta_{\hat{z}_B}`$, $`\eta_{\hat{z}_C}`$, $`\eta_{\hat{z}}`$, $`\eta_{h_0}`$, $`\eta_s`$, $`\eta_{g_1}`$, $`\eta_{h_1}`$, $`\eta_{g_2}`$, $`\eta_{h_2}`$, $`\eta_{g_3}`$ and $`\eta_{h_3}`$ of $`\mathbb{F}`$ The Verifier can choose as following:\
&#x20;$`\eta_{row_{AHP_A}}=hash(s(10))`$ , $`\eta_{col_{AHP_A}}=hash(s(11))`$ , $`\eta_{val_{AHP_A}}=hash(s(12))`$ , $`\eta_{row_{AHP_B}}=hash(s(13))`$ , $`\eta_{col_{AHP_B}}=hash(s(14))`$ , $`\eta_{val_{AHP_B}}=hash(s(15))`$ ,$`\eta_{row_{AHP_C}}=hash(s(16))`$ , $`\eta_{col_{AHP_C}}=hash(s(17))`$ , $`\eta_{val_{AHP_C}}=hash(s(18))`$ ,\
$`\eta_{\hat{w}}=hash(s(19))`$, $`\eta_{\hat{z}_A}=hash(s(20))`$, $`\eta_{\hat{z}_B}=hash(s(21))`$, $`\eta_{\hat{z}_C}=hash(s(22))`$,  $`\eta_{h_0}=hash(s(23))`$, $`\eta_{s}=hash(s(24))`$, $`\eta_{g_1}=hash(s(25))`$, $`\eta_{h_1}=hash(s(26))`$,  $`\eta_{g_2}=hash(s(27))`$, $`\eta_{h_2}=hash(s(28))`$, $`\eta_{g_3}=hash(s(29))`$, $`\eta_{h_3}=hash(s(30))`$.&#x20;

3-2- The Verifier derives commitment of $$p(x)$$, $$Com_p$$, by using polynomial commitment scheme homomorphism.
For example, if polynomial commitment scheme $$KZG$$  is used, then
$`Com_p=\eta_{row_{AHP_A}}Com_{AHP}^0+\eta_{col_{AHP_A}}Com_{AHP}^1+\eta_{val_{AHP_A}}Com_{AHP}^2+\eta_{row_{AHP_B}}Com_{AHP}^3+\eta_{col_{AHP_B}}Com_{AHP}^4+\eta_{val_{AHP_B}}Com_{AHP}^5+\eta_{row_{AHP_C}}Com_{AHP}^6+\eta_{col_{AHP_C}}Com_{AHP}^7+\eta_{val_{AHP_C}}Com_{AHP}^8+\eta_{\hat{w}}Com_{AHP_X}^2+\eta_{\hat{z}_A}Com_{AHP_X}^3+\eta_{\hat{z}_B}Com_{AHP_X}^4+\eta_{\hat{z}_C}Com_{AHP_X}^5+\eta_{h_0}Com_{AHP_X}^6+\eta_sCom_{AHP_X}^7+\eta_{g_1}Com_{AHP_X}^8+\eta_{h_1}Com_{AHP_X}^9+\eta_{g_2}Com_{AHP_X}^{10}+\eta_{h_2}Com_{AHP_X}^{11}+\eta_{g_3}Com_{AHP_X}^{12}+\eta_{h_3}Com_{AHP_X}^{13}`$ 


3-3- The Verifier chooses random $$x'\in\mathbb{F}$$ and queries $$p(x')$$.  Also, can select as $$x'=hash(s(22)))$$.

3-4- The Verifier computes $$result=PC.Check(vk,Com_p,x',y'=\pi_{AHP}^{16},\pi_{AHP}^{17})$$.\
&#x20;    \
For example, if polynomial commitment scheme $$KZG$$ is used, then the following equation checks:\
&#x20;     $$e(Com_p-gy',g)=e(\pi_{AHP}^{17},vk-gx')$$ \
&#x20;
