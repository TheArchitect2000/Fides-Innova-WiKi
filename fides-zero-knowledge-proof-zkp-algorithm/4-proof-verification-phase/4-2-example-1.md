# Example 1

### PFR Verify

$$Verify(\mathbb{F}, \mathbb{H}, \mathbb{K}, com_{PFR},\pi_{PFR})$$:&#x20;

$$1)$$ The Verifier checks $$h(\gamma^{p_1})=h(\gamma^0)=a_1=\omega^2$$ and $$h(\gamma^{p_2})=h(\gamma^3)=a_2=0$$.  Here, the Verifier  checks  $$h(1)=42$$ and $$h(48)=0$$.

$$2)$$ $$M(\beta_2)-q_2(\beta_2)Z_{\mathbb{K}}(\beta_2)=0$$ , that means $$36-30\times 146=36-36\equiv 0\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$, and $$F'(\beta_1)-q_1(\beta_1)Z_{\mathbb{K}}(\beta_1)=0$$, that means $$0-86\times 0\equiv 0\hspace{1mm}(\textrm{mod}\hspace{1mm}181)$$.

### AHP Verify

$`Verify(\mathbb{F}_{181}, \mathbb{H}, \mathbb{K}, Com_{AHP},\Pi_{AHP},x=4,y=82)`$ :

Since $$h_3(\beta_3)=h_3(5)=$$ and $$v_{\mathbb{K}}(\beta_3)=v_{\mathbb{K}}(5)=134$$, therefore, the left of equation $$(1)$$ is $$h_3(\beta_3)v_{\mathbb{K}}(\beta_3)=160$$ . Also, since $$a(\beta_3)=a(5)=$$, $$b(\beta_3)=b(5)=$$ and $$\beta_3g_3(\beta_3)+\frac{\sigma_3}{|\mathbb{K}|}=$$, therefore, the right of the equation $$(1)$$ is $$a(\beta_3)-b(\beta_3)(\sigma_3g_3(\beta_3)+\frac{\sigma_3}{|\mathbb{K}|})=160$$. So, the equation $$(1)$$ is established.

Since $$r(\alpha,\beta_2)=\frac{\alpha^5-\beta_2^5}{\alpha-\beta_2}=\frac{10^5-80^5}{10-80}=142$$, $$\sigma_3=84$$, therefore, the left of equation $$(2)$$  is $$r(\alpha,\beta_2)\sigma_3=163$$ and since $$h_2(\beta_2)=h_2(80)=42$$, $$v_{\mathbb{H}}(\beta_2)=v_{\mathbb{H}}(80)=72$$, $$\beta_2g_2(\beta_2)+\frac{\sigma_2}{|\mathbb{H}|}=35$$, therefore, the right of equation $$(2)$$ is $$h_2(\beta_2)v_{\mathbb{H}}+\beta_2g_2(\beta_2)+\frac{\sigma_2}{|\mathbb{H}|}=163$$. So, equation $$(2)$$ is established.

Since $`s(\beta_1)=s(22)=138`$, $`r(\alpha,\beta_1)=130`$, $`\sum_{M\in\{A,B,C\}}\eta_M\hat{z}_M(\beta_1)=121`$, $`\hat{z}(\beta_1)=53`$, $`\sigma_2=70`$, therefore, the left of the equation $`(3)`$ is $`s(\beta_1)+r(\alpha,\beta_1)(\sum_{M\in\{A,B,C\}}\eta_M\hat{z}_M(\beta_1))-\sigma_2\hat{z}(\beta_1)=31`$. Also since $`h_1(\beta_1)=h_1(22)=94`$, $`v_{\mathbb{H}}(\beta_1)=v_{\mathbb{H}}(22)=18`$, $`g_1(\beta_1)=g_1(22)=100`$, $`\sigma_1=62`$, therefore the right of the equation $`(3)`$ is $`h_1(\beta_1)v_{\mathbb{H}}(\beta_1)+\beta_1g_1(\beta_1)+\frac{\sigma_1}{|\mathbb{H}|}=31`$. So, the equation $`(3)`$ is established.

Since $`\hat{z}_A(\beta_1)=\hat{z}_A(22)=140`$, $`\hat{z}_B(\beta_1)=\hat{z}_B(22)=115`$,  $`\hat{z}_C(\beta_1)=\hat{z}_C(22)=125`$, therefore, the left of the equation $`(4)`$ is  $`\hat{z}_A(\beta_1)\hat{z}_B(\beta_1)-\hat{z}_C(\beta_1)=47`$. Also since $`h_0(\beta_1)=h_0(22)=73`$ and $`v_{\mathbb{H}}(\beta_1)=v_{\mathbb{H}}(22)=18`$, therefore the right of the equation $`(4)`$ is $`h_0(\beta_1)v_{\mathbb{H}}(\beta_1)=47`$. So the equation $`(4)`$ is established.

2- The output $`result`$ in following steps is $`1`$.

2-1- The Verifier chooses random values $`\eta_{\hat{w}}`$, $`\eta_{\hat{z}_A}`$, $`\eta_{\hat{z}_B}`$, $`\eta_{\hat{z}_C}`$, $`\eta_{h_0}`$, $`\eta_s`$, $`\eta_{g_1}`$, $`\eta_{h_1}`$, $`\eta_{g_2}`$, $`\eta_{h_2}`$, $`\eta_{g_3}`$ and $`\eta_{h_3}`$ of $`\mathbb{F}`$ For example, $`\eta_{\hat{w}}=1`$, $`\eta_{\hat{z}_A}=4`$, $`\eta_{\hat{z}_B}=10`$, $`\eta_{\hat{z}_C}=8`$,  $`\eta_{h_0}=32`$, $`\eta_s=45`$, $`\eta_{g_1}=92`$, $`\eta_{h_1}=11`$, $`\eta_{g_2}=1`$, $`\eta_{h_2}=5`$, $`\eta_{g_3}=25`$ and $`\eta_{h_3}=63`$.

2-2- The Verifier derives commitment of $`p(x)`$, $`Com_p`$, by using polynomial commitment scheme homomorphism.\
&#x20;       For example, if polynomial commitment scheme $`KZG`$  is used, then            $`Com_p=\eta_{\hat{w}}Com_{AHP_X}^2+\eta_{\hat{z}_A}Com_{AHP_X}^3+\eta_{\hat{z}_B}Com_{AHP_X}^4+\eta_{\hat{z}_C}Com_{AHP_X}^5+\eta_{h_0}Com_{AHP_X}^6+\eta_sCom_{AHP_X}^7+\eta_{g_1}Com_{AHP_X}^8+\eta_{h_1}Com_{AHP_X}^9+\eta_{g_2}Com_{AHP_X}^{10}+\eta_{h_2}Com_{AHP_X}^{11}+\eta_{g_3}Com_{AHP_X}^{12}+\eta_{h_3}Com_{AHP_X}^{13}=114`$

2-3- The Verifier chooses random $`x'\in\mathbb{F}`$ and queries $`p(x')`$. For example, $`x'=2`$.

2-4- The Verifier computes $`result=PC.Check(vk,Com_p,x',y'=\pi_{AHP}^{16},\pi_{AHP}^{17})`$.\
&#x20;    \
For example, if polynomial commitment scheme $`KZG`$ is used, then the following equation checks:\
&#x20;     $`e(Com_p-gy',g)=e(\pi_{AHP}^{17},vk-gx')`$ &#x20;

\
where $`e(Com_p-gy',g)=e(114-2\times 119,2)=e(57,2)=e(2\times 119,2)=119e(2,2)=119\times3=176`$ and $`e(\pi_{AHP}^{17},vk-gx')=e(149,57-2\times 2)=e(2\times 165,2\times 117)=119e(2,2)=119\times 3=176`$\
&#x20;
