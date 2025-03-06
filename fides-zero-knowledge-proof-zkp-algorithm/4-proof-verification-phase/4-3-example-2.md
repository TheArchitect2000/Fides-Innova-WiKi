# Example 2

### AHP Verify

$$Verify(\mathbb{F}_{4767673}, \mathbb{H}, \mathbb{K}, Com_{AHP},\Pi_{AHP},X=(7,11,0,1,0,1,0,0,...,0),Y=(12,84))$$ :

Since $$h_3(\beta_3)=h_3(5)=$$ and $$v_{\mathbb{K}}(\beta_3)=v_{\mathbb{K}}(5)=$$, therefore, the left of equation $$(1)$$ is $$h_3(\beta_3)v_{\mathbb{K}}(\beta_3)=$$ . Also, since $$a(\beta_3)=a(5)=$$, $$b(\beta_3)=b(5)=$$ and $$\beta_3g_3(\beta_3)+\frac{\sigma_3}{|\mathbb{K}|}=$$, therefore, the right of the equation $$(1)$$ is $$a(\beta_3)-b(\beta_3)(\sigma_3g_3(\beta_3)+\frac{\sigma_3}{|\mathbb{K}|})=$$. So, the equation $$(1)$$ is established.

Since $$r(\alpha,\beta_2)=\frac{\alpha^{37}-\beta_2^{37}}{\alpha-\beta_2}=\frac{10^{37}-80^{37}}{10-80}=$$, $$\sigma_3=$$, therefore, the left of equation $$(2)$$  is $$r(\alpha,\beta_2)\sigma_3=$$ and since $$h_2(\beta_2)=h_2(80)=$$, $$v_{\mathbb{H}}(\beta_2)=v_{\mathbb{H}}(80)=$$, $$\beta_2g_2(\beta_2)+\frac{\sigma_2}{|\mathbb{H}|}=$$, therefore, the right of equation $$(2)$$ is $$h_2(\beta_2)v_{\mathbb{H}}+\beta_2g_2(\beta_2)+\frac{\sigma_2}{|\mathbb{H}|}=$$. So, equation $$(2)$$ is established.

Since $$s(\beta_1)=s(22)=$$, $$r(\alpha,\beta_1)=$$, $$\sum_{M\in\{A,B,C\}}\eta_M\hat{z}_M(\beta_1)=$$, $$\hat{z}(\beta_1)=$$, $$\sigma_2=$$, therefore, the left of the equation $$(3)$$ is $$s(\beta_1)+r(\alpha,\beta_1)(\sum_{M\in\{A,B,C\}}\eta_M\hat{z}_M(\beta_1))-\sigma_2\hat{z}(\beta_1)=$$. Also since $$h_1(\beta_1)=h_1(22)=$$, $$v_{\mathbb{H}}(\beta_1)=v_{\mathbb{H}}(22)=$$, $$g_1(\beta_1)=g_1(22)=$$, $$\sigma_1=$$, therefore the right of the equation $$(3)$$ is $$h_1(\beta_1)v_{\mathbb{H}}(\beta_1)+\beta_1g_1(\beta_1)+\frac{\sigma_1}{|\mathbb{H}|}=$$. So, the equation $$(3)$$ is established.

Since $$\hat{z}_A(\beta_1)=\hat{z}_A(22)=$$, $$\hat{z}_B(\beta_1)=\hat{z}_B(22)=$$,  $$\hat{z}_C(\beta_1)=\hat{z}_C(22)=$$, therefore, the left of the equation $$(4)$$ is  $$\hat{z}_A(\beta_1)\hat{z}_B(\beta_1)-\hat{z}_C(\beta_1)=$$. Also since $$h_0(\beta_1)=h_0(22)=$$ and $$v_{\mathbb{H}}(\beta_1)=v_{\mathbb{H}}(22)=$$, therefore the right of the equation $$(4)$$ is $$h_0(\beta_1)v_{\mathbb{H}}(\beta_1)=$$. So the equation $$(4)$$ is established.

2- The output $$result$$ in following steps is $$1$$.

2-1- The Verifier chooses random values $$\eta_{\hat{w}}$$, $$\eta_{\hat{z}_A}$$, $$\eta_{\hat{z}_B}$$, $$\eta_{\hat{z}_C}$$, $$\eta_{h_0}$$, $$\eta_s$$, $$\eta_{g_1}$$, $$\eta_{h_1}$$, $$\eta_{g_2}$$, $$\eta_{h_2}$$, $$\eta_{g_3}$$ and $$\eta_{h_3}$$ of $$\mathbb{F}$$ For example,  $$\eta_{\hat{w}}=1$$, $$\eta_{\hat{z}_A}=4$$, $$\eta_{\hat{z}_B}=10$$, $$\eta_{\hat{z}_C}=8$$,  $$\eta_{h_0}=32$$, $$\eta_s=45$$, $$\eta_{g_1}=92$$, $$\eta_{h_1}=11$$, $$\eta_{g_2}=1$$, $$\eta_{h_2}=5$$, $$\eta_{g_3}=25$$ and $$\eta_{h_3}=63$$.

2-2- The Verifier derives commitment of $$p(x)$$, $$Com_p$$, by using polynomial commitment scheme homomorphism.\
&#x20;       For example, if polynomial commitment scheme $$KZG$$  is used, then            $$Com_p=\eta_{\hat{w}}Com_{AHP_X}^1+\eta_{\hat{z}_A}Com_{AHP_X}^2+\eta_{\hat{z}_B}Com_{AHP_X}^3+\eta_{\hat{z}_C}Com_{AHP_X}^4+\eta_{h_0}Com_{AHP_X}^5+\eta_sCom_{AHP_X}^6+\eta_{g_1}Com_{AHP_X}^7+\eta_{h_1}Com_{AHP_X}^8+\eta_{g_2}Com_{AHP_X}^9+\eta_{h_2}Com_{AHP_X}^{10}+\eta_{g_3}Com_{AHP_X}^{11}+\eta_{h_3}Com_{AHP_X}^{12}=$$

2-3- The Verifier chooses random $$x'\in\mathbb{F}$$ and queries $$p(x')$$. For example, $$x'=2$$.

2-4- The Verifier computes $$result=PC.Check(vk,Com_p,x',y'=\pi_{AHP}^{16},\pi_{AHP}^{17})$$.\
&#x20;    \
For example, if polynomial commitment scheme $$KZG$$ is used, then the following equation checks:\
&#x20;     $$e(Com_p-gy',g)=e(\pi_{AHP}^{17},vk-gx')$$&#x20;

\
where $$e(Com_p-gy',g)$$ and $$e(\pi_{AHP}^{17},vk-gx')=$$\
&#x20;
