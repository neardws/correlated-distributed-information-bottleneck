# 内界与外界台账

本页登记相关观测模型上的界。每一条都标明状态。条件独立区域的公式只放在 [已知结果](known-results.md)，不转入本页的“已证明区域”栏。本页没有已证明的精确区域。

联合分布若没有写出 $p(y_1,y_2\mid x)=p(y_1\mid x)\,p(y_2\mid x)$，就不能使用依赖这条因子分解的速率消去。

## 可实现内界

**状态：内界。它不是区域的完整刻画。** 对每一个有限辅助字母上的

$$p(q)\,p(x,y_1,y_2)\,p(u_1\mid y_1,q)\,p(u_2\mid y_2,q),$$

源的联合分布 $p(x,y_1,y_2)$ 任意，不必因子分解成 $p(y_1\mid x)p(y_2\mid x)$。下列不等式描述一组可实现的码率与相关度阈值：

$$
\begin{aligned}
R_1&\ge I(Y_1;U_1\mid U_2,Q),\\
R_2&\ge I(Y_2;U_2\mid U_1,Q),\\
R_1+R_2&\ge I(Y_1,Y_2;U_1,U_2\mid Q),\\
\Delta&\le I(X;U_1,U_2\mid Q).
\end{aligned}
$$

内界是这些元组对所有有限 $\mathcal{U}_1,\mathcal{U}_2,\mathcal{Q}$ 取的并，再取闭包。写出这个并不需要一个统一的辅助基数上界。基数截止只在把并收成有限搜索时才需要；没有截止，内界仍然成立，只是不能被有限网格穷尽。

最后一行是可达到的相关度阈值，不是消息互信息的数据处理上界，也不是归一化消息互信息的极限值。$U_i$ 是参考设计中的辅助变量，$J_i$ 是块消息。下面只证明

$$\liminf_{n\to\infty}\frac1n I(X^n;J_1,J_2)\ge I_{P^\star}(X;U_1,U_2\mid Q).$$

因此任何不超过右边的 $\Delta$ 都可实现。不证明 $(1/n)I(X^n;J_1,J_2)$ 收敛到该单字母互信息。消息相关度的上界仍是后面的初等外界。

### 参考分布与固定码本

单字母量在参考分布

$$P^\star(q,x,y_1,y_2,u_1,u_2)=p(q)\,p(x,y_1,y_2)\,p(u_1\mid y_1,q)\,p(u_2\mid y_2,q)$$

下计算。乘积核

$$\prod_{t=1}^n p^\star(u_{1,t}\mid y_{1,t},q)\,p^\star(u_{2,t}\mid y_{2,t},q)$$

只描述参考律，不是固定码本之后编码器的实际条件输出分布。在 $P^\star$ 下有马尔可夫链 $U_i-(Y_i,Q)-(X,Y_{3-i},U_{3-i})$。随机码本按 $P^\star_{U_i\mid Q}$ 的边缘独立抽取。联合典型性引理和马尔可夫引理只在这个系综上使用：箱速率严格大于参考律中的 Berger–Tung 互信息时，系综的箱解码错误，以及 $(X^n,Y_1^n,Y_2^n,U_1^n,U_2^n)$ 偏离 $P^\star$ 的概率，都可以任意小。$X^n$ 出现在系综的联合典型事件里。译码器看不到 $X^n$。

码本的惩罚是源分布下的平均：箱解码失败，或选中码字与 $(X^n,Y_1^n,Y_2^n)$ 的联合型离 $P^\star$ 超过容差 $\tau$。系综平均惩罚小，就存在一组码本，其惩罚不超过该平均。固定这一组时只看该平均惩罚。这个选择不读取某一次源实现里译码是否成功。

固定之后，编码器 $i$ 只读 $Y_i^n$，在固定列表上按既定顺序取码字并发送箱索引。映射是确定性的，运行时不再抽取乘积核。编码器的实际条件输出是 $0$-$1$ 分布，一般不等于上面的参考乘积核。$Q$ 仍是 [编码模型](coding-model.md) 里事先固定的子块调度。

### 相关度下界

译码器对每个符号使用同一个预测，只依赖它自己的输出 $(\hat u_1,\hat u_2)$ 和已知的 $q$。取 $\alpha\in(0,1)$，

$$q_\alpha(x\mid \hat u_1,\hat u_2,q)=(1-\alpha)\,P^\star(x\mid \hat u_1,\hat u_2,q)+\frac{\alpha}{|\mathcal X|}.$$

若 $(\hat u_1,\hat u_2,q)$ 不在 $P^\star$ 的支撑上，或该条件概率没有定义，固定约定把 $P^\star(x\mid \hat u_1,\hat u_2,q)$ 换成 $1/|\mathcal X|$。于是恒有 $q_\alpha(x\mid \hat u_1,\hat u_2,q)\ge \alpha/|\mathcal X|$。译码器不根据真实成功或失败更换预测。箱里只剩一个候选时，它仍不知道该候选是不是发端码字。

块预测是乘积 $W(x^n\mid J)=\prod_t q_\alpha(x_t\mid \hat u_{1,t},\hat u_{2,t},q_t)$，由消息和已知调度确定。记 $\ell_\alpha=\log_2(1/W(X^n\mid J))$。后验 KL 不等式给出

$$\mathbb E[\ell_\alpha]=H(X^n\mid J)+D(P_{X^n\mid J}\,\|\,W)\ge H(X^n\mid J),$$

所以

$$\frac1n I(X^n;J)\ge H(X)-\frac1n\mathbb E[\ell_\alpha].$$

这是下界。不把 $I(X^n;J)$ 与 $I(X^n;\hat U_1^n,\hat U_2^n)$ 等同，也不把后者的归一化极限写成单字母互信息。

成功和错误只在分析里分开。设 $\mathcal E$ 为：箱解码失败，或 $(X^n,U_1^n,U_2^n,Q^n)$ 的联合型离 $P^\star$ 超过 $\tau$。每个实现都满足

$$0\le\ell_\alpha\le n\log_2\frac{|\mathcal X|}{\alpha},$$

因此

$$\frac1n\mathbb E[\ell_\alpha\mathbf{1}_{\mathcal E}]\le P(\mathcal E)\log_2\frac{|\mathcal X|}{\alpha}.$$

在 $\mathcal E^c$ 上，译出的码字等于编码器选中的码字，并且联合型在容差内。此时

$$q_\alpha(x\mid u_1,u_2,q)\ge(1-\alpha)\,P^\star(x\mid u_1,u_2,q).$$

故

$$\log_2\frac{1}{q_\alpha(x\mid u_1,u_2,q)}\le -\log_2(1-\alpha)+\log_2\frac{1}{P^\star(x\mid u_1,u_2,q)}.$$

$\tau$-典型序列的经验交叉熵不超过 $H_{P^\star}(X\mid U_1,U_2,Q)+\eta(\tau)$，其中 $\eta(\tau)\to 0$ 随 $\tau\to 0$。有限字母上，强典型性只用到 $P^\star$ 支撑内的原子，$\log_2(1/P^\star)$ 在这些原子上有界，交叉熵对联合型连续。成功代价非负，成功事件的概率不超过 $1$，所以成功部分对平均代价的贡献不超过

$$H_{P^\star}(X\mid U_1,U_2,Q)-\log_2(1-\alpha)+\eta(\tau).$$

两项相加，

$$\frac1n\mathbb E[\ell_\alpha]\le H_{P^\star}(X\mid U_1,U_2,Q)-\log_2(1-\alpha)+\eta(\tau)+P(\mathcal E)\log_2\frac{|\mathcal X|}{\alpha}.$$

于是

$$\frac1n I(X^n;J)\ge I_{P^\star}(X;U_1,U_2\mid Q)+\log_2(1-\alpha)-\eta(\tau)-P(\mathcal E)\log_2\frac{|\mathcal X|}{\alpha}.$$

先固定 $\alpha\in(0,1)$。对任意 $\delta>0$，选 $\tau$ 使 $\eta(\tau)<\delta/2$，再选严格的速率裕量，使系综中 $P(\mathcal E)\log_2(|\mathcal X|/\alpha)<\delta/2$。按不超过系综平均的总惩罚固定码本，并取足够大的块长，得到

$$\frac1n I(X^n;J)\ge I_{P^\star}(X;U_1,U_2\mid Q)+\log_2(1-\alpha)-\delta,$$

同时两个码率严格满足本节开头的三条 Berger–Tung 速率不等式，并带有该裕量。这三条是

$$
\begin{aligned}
R_1&\ge I(Y_1;U_1\mid U_2,Q),\\
R_2&\ge I(Y_2;U_2\mid U_1,Q),\\
R_1+R_2&\ge I(Y_1,Y_2;U_1,U_2\mid Q).
\end{aligned}
$$

它们不是两个条件互信息下界同时取等。[编码模型](coding-model.md) 的重复加尾部把这个有限块长变成一条序列。$\delta$ 任意，闭包去掉裕量，于是平滑阈值 $I_{P^\star}(X;U_1,U_2\mid Q)+\log_2(1-\alpha)$ 可实现。

再取整数 $k\ge 2$，令 $\alpha_k=1/k$。第 $k$ 个有限块长码的归一化相关度至少是 $I_{P^\star}(X;U_1,U_2\mid Q)+\log_2(1-\alpha_k)-1/k$，三条速率不等式都留有 $1/k$ 的裕量。$\log_2(1-\alpha_k)\to 0$。这些点的极限是满足上述三条速率不等式、相关度阈值等于 $I_{P^\star}(X;U_1,U_2\mid Q)$ 的元组。操作区域取闭包，所以该元组可实现：存在某条确定性码序列，满足

$$\liminf_{n\to\infty}\frac1n I(X^n;J)\ge I_{P^\star}(X;U_1,U_2\mid Q).$$

这条序列上的归一化消息互信息不必收敛。不能先把 $\alpha$ 送到 $0$ 再让块长增长，否则 $\log_2(|\mathcal X|/\alpha)$ 会在 $P(\mathcal E)$ 消失之前失控。速率的非严格边界由同一个闭包收入。论证不使用 $Y_1-X-Y_2$。

这是内界。它没有给出 converse，因此不是相关观测模型的精确区域。

### 三种更小的对象

下面三个对象是更窄的信道族，或是另一个优化。没有额外论证时，不能把它们换成上面对全部有限辅助字母取的并。

| 对象 | 它是什么 | 它不能代替什么 |
| --- | --- | --- |
| 全部有限乘积测试信道 | $p(u_i\mid y_i,q)$，字母有限但无统一基数截止 | 内界的取值范围；不是区域的完整刻画 |
| 二元对称信道限制 | 辅助信道或噪声被限制成 BSC | 全部乘积测试信道上的上确界 |
| 局部数值 | 固定字母、固定初始化或神经网络上的驻点 | 全局上确界，以及任何 converse |

否定一个 BSC 参数化，只否定这个参数化。它不否定未受 BSC 限制的乘积测试信道。一组局部搜索没有改进候选值，也不是不可能定理。

## 初等操作外界

**状态：初等恒等式加上数据处理，对相关观测成立。** 设 $J_i=f_i(Y_i^n)$ 且 $\log_2|\mathcal{J}_i|\le nR_i$。则

$$0\le\Delta_n\le\min\bigl\{I(X;Y_1,Y_2),\,R_1+R_2\bigr\}.$$

理由如下。非负性是互信息的非负性。消息对是 $(Y_1^n,Y_2^n)$ 的函数，所以

$$I(X^n;J_1,J_2)\le I(X^n;Y_1^n,Y_2^n).$$

独立副本给出 $I(X^n;Y_1^n,Y_2^n)=n\,I(X;Y_1,Y_2)$，这一步不需要 $Y_1-X-Y_2$。另一方面，

$$I(X^n;J_1,J_2)\le H(J_1,J_2)\le\log_2|\mathcal{J}_1|+\log_2|\mathcal{J}_2|\le n(R_1+R_2).$$

对使用 $\limsup$ 码率的序列，相应的极限陈述是

$$\liminf_{n\to\infty}\Delta_n\le\min\bigl\{I(X;Y_1,Y_2),\,R_1+R_2\bigr\}.$$

闭包保持这个外界。这些界有效，也通常很弱：它们没有处理两个编码器不能共享观测这一困难。

若码率定义改成极限松弛，上界里的 $R_1+R_2$ 随松弛一起变化。使用时要和 [编码模型](coding-model.md) 的同一套极限对齐，不能混用单块基数。

## 明确不移用的公式

下列对象依赖条件独立，或者重构的不是隐藏目标。它们不作为本模型的外界或精确区域进入台账。

- [已知结果](known-results.md) 中条件独立区域的四条子集不等式，以及 Section VII-B 消去 $R_1,R_2$ 之后的和速率公式。
- Courtade–Weissman Theorem 3 与 Theorem 10–11 的 CEO 区域。它们的联合分布含有 $\prod_i p(y_i\mid x)$。
- Courtade–Weissman Theorem 6。它重构的是两个被观测信源，失真是这两个信源上的对数损失。
- 任何把 $I(U_1;U_2\mid X)$ 直接删去之后得到的速率表达式。删除这一项的条件见 [已知结果](known-results.md)。

更强的集中式信息瓶颈外界或一般相关源上的多终端外界，仍须重新推导或给出适用的引用。下面只记录测试点上已经写明的一条外界。本页没有内界与外界重合的主张。

## 测试点上的全块外界

**状态：已证明的操作外界，仅 $(p,q)=(1/4,1/8)$，固定参考 $P_V=(3,1,1,3)/8$。不是紧界，也不是分布式可达性。** 证明见 [校准与收缩](proofs/calibration-and-contraction.md)。

$$
\Delta\le\min\left\{\frac{R_1+R_2}{3},\frac34\bigl[1-h_2(1/6)\bigr]\right\}.
$$

收缩系数 $\eta_{\rm MI}(P_V,K)=\eta_{\rm KL}(P_V,K)=1/3$ 是集中、固定参考的结果，再用于全部块长的局部编码。相同观测归约、有限单终端 block 信息瓶颈，以及公平 BSC 上 Mrs. Gerber 引理的所需特例，在同一笔记中作为标准结果重证。$L\in[1/4,1/3]$ 和 $L=C_{\rm fin}$ 是该笔记里的操作事实。统一严格间隙 $L<1/3$ 在该笔记中没有证明。这不是新颖性认证，也不是形式化认证。2026 年文献全文仍未审核。

## 台账摘要

| 编号 | 陈述 | 状态 | 还缺什么 |
| --- | --- | --- | --- |
| I0 | 有限辅助字母上的远程量化分箱 | 可实现内界 | 不是完备性；只证明相关度的 $\liminf$ 下界。$\Delta\le I(X;U_1,U_2\mid Q)$ 是可达到的阈值，不是消息互信息的上界，也不是它的极限值 |
| O0 | $0\le\Delta\le\min\{I(X;Y_1,Y_2),R_1+R_2\}$ | 初等操作外界 | 无；它不解决分布式困难 |
| O1 | $(p,q)=(1/4,1/8)$ 上 $\Delta\le\min\{(R_1+R_2)/3,\frac34[1-h_2(1/6)]\}$ | 已证明的全块外界 | 不是紧界或分布式可达性；严格间隙 $L<1/3$ 未在证明笔记中证明 |
| C0 | 条件独立区域及其和速率投影 | 文献事实，仅 $Y_1-X-Y_2$ | 基数需回到原文附录核对；不能用于相关噪声 |
| X0 | 内界与外界在相关二元族上重合 | 非结论 | 没有任何方向被证明匹配 |

$\Psi_\lambda$ 是和速率–相关度拉格朗日的候选支撑泛函，不是这张表里的操作区域。它的定义和二字母问题在 [未证明的问题](open-questions.md)。
