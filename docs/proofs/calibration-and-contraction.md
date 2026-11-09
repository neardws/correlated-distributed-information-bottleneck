# 相关二元分布式信息瓶颈：固定长度校准、集中收缩与局部全块效率（v0.3）

> 本文核心结果已经完成有限范围的非形式化数学审读。该审读不是形式化正确性认证、新颖性认证或完整区域认证。

状态摘要见 [证明索引](README.md)。台账条目见 [内界与外界台账](../bound-ledger.md)。

除明确标注自然底的推导外，全部对数以2为底。有限字母表，跨时间独立同分布（iid），无交互固定长度编码。全文保留原目标，不将相关观测的隐藏目标替换成条件独立潜变量。

## 0. 陈述与范围

**[标准结果／自包含重证]** 对任意有限源 $P_{XY}$，两终端都观察同一个 $Y^n$ 时，固定长度 block relevance 区域为
$$
\mathcal R_=\{(R_1,R_2,\Delta):R_i\ge0,\ 0\le\Delta\le F(R_1+R_2)\},\tag{0.1}
$$
$$
F(R)=\sup_{P_{U|Y}:I(Y;U)\le R}I(X;U),\qquad X-Y-U.\tag{0.2}
$$
这里允许所有有限aux；下文证明安全界 $|U|\le|\operatorname{supp}Y|+2$，从而sup可取到，不声称最紧界。

**[标准结果／自包含重证]** 令 $h_2^{-1}:[0,1]\to[0,1/2]$ 为指定分支，$a*b=a(1-b)+(1-a)b$。若X公平且共同观测是BSC(p)输出，$0\le p\le1/2$，则对全部 $R\ge0$，
$$
F_p(R)=1-h_2\!\left(p*h_2^{-1}\big(1-\min\{R,1\}\big)\right).\tag{0.3}
$$
逆覆盖任意块映射，而非只优化BSC测试通道。

**[已证明／核心数学经非形式化审读，非新颖认证]** 对相关噪声内点 $(p,q)=(1/4,1/8)$，令 $V=(Y_1,Y_2)$。**固定**参考输入分布 $P_V=(3,1,1,3)/8$（顺序00、01、10、11）及反向核 $K=P_{X|V}$，有
$$
\eta_{\rm MI}(P_V,K):=
\sup_{P_{U|V}:I(V;U)>0}\frac{I(X;U)}{I(V;U)}=\frac13.\tag{0.4}
$$
这是集中、固定reference的互信息收缩系数，不是允许任意参考输入分布的统一通道常数。最优是小扰动逼近的sup，不是正信息aux取等。它给原分布式操作外界
$$
\Delta\le\min\left\{\frac{R_1+R_2}{3},\frac34[1-h_2(1/6)]\right\}.\tag{0.5}
$$
这不是分布式紧界，也没有求出完整集中曲线或分布式区域。


**[局部全块结论／核心数学经非形式化审读]** 对§5的固定相关源，在一切有限块长及无交互局部固定长度编码下，本文证明
$$
I(X^m;J_1,J_2)\le\tfrac14[H(J_1)+H(J_2)]\le\tfrac14\log(M_1M_2),\tag{0.6}
$$
并以真实确定固定长度码族匹配其效率上确界：
$$
L=C_{\rm fin}=\tfrac14<\tfrac13.\tag{0.7}
$$
Mi是各端实际使用的消息字母表大小，熵仅为中间上界。相应操作外界为
$$
\Delta\le\min\{(R_1+R_2)/4,\ I(X;V)\}.\tag{0.8}
$$
该结论允许独立私有种子；合法源独立公共Q须条件化。集中固定reference系数1/3不变，因为集中编码不满足局部消息的条件独立结构。本结论不刻画完整正率区域。

## 1. 操作定义、块损失与随机性

### 1.1 固定长度定义

设 $(X^n,Y^n)\sim P_{XY}^{\otimes n}$。单终端确定编码 $J=f_n(Y^n)\in[M_n]$，率为 $\log M_n/n$，保留信息为 $I(X^n;J)/n$。规定 $(R,\Delta)$ 可达，若对每个 $\epsilon>0$，存在 $N_\epsilon$，使**所有** $n\ge N_\epsilon$ 都存在码满足
$$
\frac{\log M_n}{n}\le R+\epsilon,\qquad
\frac{I(X^n;J)}n\ge\Delta-\epsilon.\tag{1.1}
$$
两终端同观测时用 $J_i=f_{i,n}(Y^n)\in[M_{i,n}]$，分别要求率不超过 $R_i+\epsilon$，并将relevance换为 $I(X^n;J_1,J_2)/n$。一般分布式模型则编码器i仅见 $Y_i^n$。所有区域取非负参数及渐近闭包；此定义已经允许任意小松弛。闭包不改变可达性：给定极限点及epsilon，先取距其足够近的可达点，再用该点的充分大块长码。

消息集可删去不使用的字母；其对数是一次固定长度成本，不自动等于熵。有限块码重用、分割和拼接都按实际消息数计费。

最优块概率预测满足
$$
D_{\rm block}^*=\frac1nH(X^n|J)=H(X)-\frac1nI(X^n;J).
$$
逐符号预测的最优损失却是 $\sum_tH(X_t|J)/n$，一般更大。其差为后验条件总相关
$$
\frac1n\left[\sum_tH(X_t|J)-H(X^n|J)\right]\ge0.
$$
以下逆证明直接用块链式法则，不以逐坐标relevance冒充block relevance。

### 1.2 私有种子与公共Q

若 $S_1,S_2$ 彼此独立、与全源独立，且消息数上界对所有种子统一有效，令 $S=(S_1,S_2)$，则
$$
I(X^n;J_1,J_2)\le I(X^n;J_1,J_2,S)
=\mathbb E_s I(X^n;J_1,J_2|S=s).\tag{1.2}
$$
存在一个联合种子值使relevance不降且保留两条消息数上界；固定之得到合法确定局部映射。有限源与有限消息下，可把随机核表示为有限确定映射混合，所以取到问题无碍。不能分别选两个“最优”种子，也不能据此保证多个期望失真、泄漏或期望长度约束同时满足。

源独立公共 $Q$ 若对decoder可见，指标必须是 $I(X^n;J_1,J_2|Q)/n=I(X^n;J_1,J_2,Q)/n$。不允许免费源相关Q。统一消息数下可固定公共种子；若采用平均率时分，则用预先确定的子块长度和规则，乘积消息数与独立子块relevance按长度相加，不提供额外源信息。

## 2. 相同观测的双向归约

### 2.1 两终端到集中

集中编码器看Y全块，可计算 $(f_1(Y^n),f_2(Y^n))$，用至多 $M_1M_2$ 个索引注入表示，故
$$
\log M\le\log M_1+\log M_2,\quad
I(X^n;J)=I(X^n;J_1,J_2).\tag{2.1}
$$
给每端epsilon/2率松弛即可保证集中epsilon松弛。

### 2.2 集中到任意分率，包括零率与取整

给定 $R_i\ge0$ 及epsilon>0，令 $R=R_1+R_2$。取充分大n的集中码使
$\log M\le n(R+\epsilon/3)$、relevance至少 $\Delta-\epsilon$。将索引J−1写成 $L=\lceil\log M\rceil$ 位，M=1时L=0。令
$$
\ell_1=\min\{L,\lfloor n(R_1+\epsilon/3)\rfloor\},\quad
\ell_2=L-\ell_1.\tag{2.2}
$$
两终端都能算出完整集中索引，各发送指定前/后分量。拼接精确恢复，relevance不变，每端消息数至多 $2^{\ell_i}$。若未在 $\ell_1=L$ 截断，则
$$
\ell_2\le n(R+\epsilon/3)+1-[n(R_1+\epsilon/3)-1]=nR_2+2.\tag{2.3}
$$
截断时 $\ell_2=0$。所以 $n\ge2/\epsilon$ 足够保证两端rate均不超过 $R_i+\epsilon$。

若 $R_1=0$ 且要求该端严格常数，直接取 $\ell_1=0,\ell_2=L$，另一端率至多 $R_2+\epsilon/3+1/n$；对称端点同理。两率均0时，消息数界迫使 $\Delta=0$，常数码实现。这里没有声称每个有限块都能在无松弛整数容量下任意拆分；只用明确epsilon松弛与闭包。由两方向得(0.1)，待§3核定F。

在二元噪声族 $P_N=(1-2p+q,p-q,p-q,q)$ 中，q=p给 $N_1=N_2$ 几乎处处，故确是本节同观测模型。不同观测时一般无法各自计算同一集中索引，本归约失效；只知H(J)而非消息数也不足以一次固定长度分割。

## 3. 单终端有限源 block IB

### 3.1 任意块编码的逆

对 $J=f(Y^n)$ 定义 $U_t=(J,Y^{t-1})$。联合律为
$\prod_sP_Y(y_s)P_{X|Y}(x_s|y_s)1\{j=f(y^n)\}$，所以
$$
X_t-Y_t-(J,Y^{t-1}),\qquad X_t-(J,Y^{t-1})-X^{t-1}.\tag{3.1}
$$
第二链来自给定Y过去后，过去target仍通过 $\prod_{s<t}P_{X|Y}(x_s|y_s)$ 产生，不因条件J而改变。具体熵链为
$$
H(X_t|J,X^{t-1})\ge H(X_t|J,X^{t-1},Y^{t-1})
=H(X_t|J,Y^{t-1}).
$$
从块链式法则及iid target，
$$
I(X^n;J)\le\sum_t I(X_t;J,Y^{t-1}).\tag{3.2}
$$
而由iid observation，
$$
\sum_t I(Y_t;J,Y^{t-1})
=\sum_tI(Y_t;J|Y^{t-1})=I(Y^n;J)\le\log M.\tag{3.3}
$$
取独立均匀T，置 $(X,Y)=(X_T,Y_T)$、$U=(T,J,Y^{T-1})$。有 $X-Y-U$，两种单字母信息恰是以上坐标信息的平均，故
$$
\frac1n I(X^n;J)\le I(X;U)\le F(\log M/n),\quad
I(Y;U)\le\log M/n.\tag{3.4}
$$
这覆盖所有有限块映射及源独立随机核；不是错误的 $I(X^n;J)\le\sum_tI(X_t;J)$。源有记忆或消息偷看target时(3.1)未必成立。

### 3.2 固定长度可达：量词、双容差、支持取整与统一覆盖

**[标准结果／固定长度可达证明]** 固定一个有限测试核 $W(u|y)=P_{U|Y}(u|y)$，记 $P=P_{YU}$、$r=I(Y;U)$。删去边缘零概率字母，令 $a=|\mathcal Y|,b=|\mathcal U|$，两个边缘均满支持。给定任意目标 $\epsilon>0$，以下所有参数先于块长固定：

1. 先固定rate裕量 $\delta=\epsilon/4>0$。
2. 选 $0<\alpha<1$，使 $-\log_2(1-\alpha)<\epsilon/4$。令
$$
q_\alpha(x|u)=(1-\alpha)P_{X|U}(x|u)+\alpha/|\mathcal X|,
\quad L_\alpha=\log_2(|\mathcal X|/\alpha).\tag{3.5}
$$
3. 定义联合概率单纯形上的连续函数
$$
E(T)=-H_T(U|Y)-\sum_uT_U(u)\log_2P_U(u)
=D_2(T\|T_Y P_U).\tag{3.6}
$$
因 $P_U$ 满支持，E在整个有限单纯形连续（条件熵按联合熵减边缘熵定义），且E(P)=r。选联合容差 $\tau_{YU}>0$，使 $ab\tau_{YU}L_\alpha<\epsilon/4$，且所有 $\|T-P\|_\infty\le\tau_{YU}$ 的联合分布均满足 $|E(T)-r|<\delta/4$。可以先取连续性半径，再严格缩小以满足闭球要求。
4. 选输入容差
$$
0<\tau_Y<\min\{\tau_{YU}/4,\ \tfrac12\min_yP_Y(y)\}.\tag{3.7}
$$
输入典型指 $\|\hat P_{y^n}-P_Y\|_\infty\le\tau_Y$；联合典型指逐元素偏差至多 $\tau_{YU}$，并禁止P(y,u)=0的组合。两容差明确不同且有严格余量。

现在对**任意**输入典型 $y^n$，令 $n_y$ 为y出现次数。按每行支持 $\mathcal S_y=\{u:W(u|y)>0\}$ 给数 $n_yW(u|y)$ 取整：先取floor，再把不足整数按余数分配给支持内字母，使行总数恰为 $n_y$，每个支持内格误差至多1；支持外计数始终0。由(3.7)，输入典型行均有正次数（充分大n），即使某行为0也可直接置全行0。得到条件型联合T满足
$$
|T(y,u)-P(y,u)|\le |\hat P_Y(y)-P_Y(y)|W(u|y)+1/n
\le\tau_Y+1/n.\tag{3.8}
$$
要求 $1/n<\tau_{YU}/4$ 后，右侧严格小于 $\tau_{YU}/2$；所以构造的型类全部联合典型，没有引入任何零概率组合。

固定该 $y^n$，每个该条件型的 $u^n$ 在 $P_U^{\otimes n}$ 下概率为
$2^{n\sum_uT_U(u)\log_2P_U(u)}$。逐行应用有限多项式型类计数界
$$
(n+1)^{-ab}2^{nH_T(U|Y)}\le |\mathcal T(T_{U|Y}|y^n)|\le2^{nH_T(U|Y)}
$$
（即多项式系数的标准有限型界，逐行代入各 $n_y$，再用 $n_y+1\le n+1$），得到单条随机码字匹配概率统一下界
$$
\Pr_{P_U^{\otimes n}}\{(y^n,U^n)\text{联合典型}\}
\ge(n+1)^{-ab}2^{-nE(T)}
\ge(n+1)^{-ab}2^{-n(r+\delta/4)}.\tag{3.9}
$$
只要再令 $ab\log_2(n+1)/n\le\delta/4$，便得到 $2^{-n(r+\delta/2)}$。所有阈值只依赖固定P、核、epsilon及预选参数，**不依赖所取的典型输入序列**；多项式因子已显式吸收进delta。

生成 $K_n=\lceil2^{n(r+\delta)}\rceil$ 条独立 $P_U^{\otimes n}$ 码字。编码器发最小联合典型索引，没有则发1。非典型输入也发1。对每个典型输入，未覆盖概率至多
$$
(1-2^{-n(r+\delta/2)})^{K_n}\le\exp[-2^{n\delta/2}].\tag{3.10}
$$
平均坏事件概率不超过
$$
\bar e_n=P\{Y^n\text{非输入典型}\}+\exp[-2^{n\delta/2}]\longrightarrow0.
$$
因此对每个充分大n都存在一份确定码本，使坏事件概率 $e_n\le\bar e_n$。固定它及最小索引规则，运行时无随机编码。坏事件只用于分析，decoder不需要识别真实失败，始终使用同一平滑预测规则。

### 3.3 平滑损失与最终epsilon预算

令 $c_\alpha(y,u)=\sum_xP_{X|Y}(x|y)[-\log_2q_\alpha(x|u)]\in[0,L_\alpha]$。对任一已固定码本，选码仅依赖Y，故精确有
$$
\mathbb E\left[\frac1n\sum_t-\log_2q_\alpha(X_t|u_t(J))\ \middle|\ Y^n=y^n\right]
=\frac1n\sum_tc_\alpha(y_t,u_t(J)).\tag{3.11}
$$
成功时经验代价偏差至多 $ab\tau_{YU}L_\alpha$，坏事件代价至多 $L_\alpha$。并且
$$
\mathbb Ec_\alpha(Y,U)\le H(X|U)-\log_2(1-\alpha)
$$
因为在设计分布支持上 $q_\alpha\ge(1-\alpha)P_{X|U}$。所以整体预测损失至多
$$
H(X|U)-\log_2(1-\alpha)+ab\tau_{YU}L_\alpha+\bar e_nL_\alpha.\tag{3.12}
$$
由块后验的条件KL最优性，$H(X^n|J)/n$ 不超过该乘积预测器损失。最终选一个统一 $N_\epsilon$，使**每个** $n\ge N_\epsilon$ 同时满足：

- $1/n<\tau_{YU}/4$，输入行正次数所需阈值；
- $ab\log_2(n+1)/n\le\delta/4$；
- $1/n\le\epsilon/4$，从而 $\log K_n/n\le r+\delta+1/n\le r+\epsilon/2$；
- 输入非典型概率乘 $L_\alpha\le\epsilon/8$，且 $\exp[-2^{n\delta/2}]L_\alpha\le\epsilon/8$。

则坏事件项至多epsilon/4，平滑及成功项分别严格小于epsilon/4，故
$$
\frac1nI(X^n;J)\ge I(X;U)-3\epsilon/4\ge I(X;U)-\epsilon.\tag{3.13}
$$
这给定任意epsilon后，先delta、再alpha、再双容差、最后n的完整依赖顺序；n选定后不再改delta。消息是实际 $K_n$ 个索引，不是把随机U的信息量当一次码长。无界loss由全事件平滑控制，未假定运行码的块后验为设计核乘积。至此每个有限测试核对应点可达。

### 3.4 安全aux界、最大值、凹性和连续性

删去P_Y零字母，令 $m=|\operatorname{supp}Y|$。对aux的每个使用字母j，记后验向量 $w_j=P_{Y|U=j}$，权重 $\lambda_j=P_U(j)>0$，定义 $Aw=P_{X|Y}w$。保留特征点
$$
z_j=(w_j(1),\ldots,w_j(m-1),H(w_j),H(Aw_j))\in\mathbb R^{m+1}.\tag{3.14}
$$
若点数大于m+2，$(1,z_j)$ 线性相关，存在非零 $c_j$ 满足 $\sum_jc_j=0,\sum_jc_jz_j=0$。c有正负项。取
$$
t=\min_{c_j>0}\frac{\lambda_j}{c_j}>0,\qquad
\lambda'_j=\lambda_j-tc_j.\tag{3.15}
$$
正c项非负且至少一项变0；负c项增加；零c项不变。总重仍1、平均特征点不变，后验向量 $w_j$ 不动。删去零权重，反复得到至多m+2点。保持均值P_Y及两个平均熵，就保持两个信息量；由 $P(j|y)=\lambda_jw_j(y)/P_Y(y)$ 重建核。

固定m+2个aux字母、允许零权重时，随机核空间紧、互信息连续、约束闭非空，故(0.2)最大值存在。F非减，数据处理给
$$
0\le F(R)\le\min\{R,I(X;Y)\}.\tag{3.16}
$$
独立标签B混合两个核并取aux=(B,U_B)，两个信息量均按权重平均，故F凹；再缩减基数不损失信息。有限凹函数内部连续；F≤R给0右连续，F(0)=0。R≥H(Y)时取U=Y，F=I(X;Y)。从左以概率theta使用Y、否则常数的aux给 $F(\theta H(Y))\ge\theta I(X;Y)$，保证饱和端点左连续。H(Y)=0时F恒0。于是(3.4)可对渐近码取极限，结合可达得到(0.2)的操作区域。

依赖与失败条件：本节只用有限型计数、大数律、KL非负、线性代数和有限熵连续性；不需分布式BT精确性。若不平滑、选码偷看X、源有记忆或有额外源相关decoder信息，必须重做相应步骤。

## 4. 公平BSC共同观测：MGL的完整所需重证

### 4.1 反向噪声独立

X公平，$Y=X\oplus N$，$N\sim\operatorname{Bern}(p)\perp X$。有 $P(Y=y,N=e)=P(N=e)/2$，所以Y公平，N也独立Y。反向 $X=Y\oplus N$ 可使用相同独立噪声；iid向量 $N^n$ 独立于 $(Y^n,J)$，只要J仅由Y和源独立种子产生。非公平X一般没有此性质。

### 4.2 标量凸性

令 $g_p(v)=h_2(p*h_2^{-1}(v))$，$v\in[0,1]$。先用自然熵H，在 $u\in(0,\ln2)$ 令 $f(u)=H^{-1}(u)\in(0,1/2)$，有 $f'>0,f''>0$。固定u、置 $z=p+(1-2p)f(u)$，则
$$
[H(z)]''=-\frac{(1-2p)^2f'^2}{z(1-z)}+(1-2p)f''\ln\frac{1-z}{z}.\tag{4.1}
$$
p<1/2时，其非负等价于
$$
A(p)=-(1-2p)f'^2+z(1-z)f''\ln\frac{1-z}{z}\ge0.
$$
对 $k(z)=z(1-z)\ln[(1-z)/z]$，
$$
k''(z)=-2\ln\frac{1-z}{z}-\frac{1-2z}{z(1-z)}\le0\quad(0<z\le1/2).\tag{4.2}
$$
所以A关于p凹。由 $H(f(u))=u$ 二次求导得A(0)=0；p=1/2时z=1/2，A=0。故A在两端之间非负，p=1/2对应常函数；对u端点连续延拓。换底
$$
g_p(v)=\frac1{\ln2}H\!\left(p*H^{-1}((\ln2)v)\right)\tag{4.3}
$$
保凸。p≤1/2时 $p*x\in[p,1/2]$ 随x非减，故g也非减。

### 4.3 标量条件版与向量条件版

若比特B、侧信息W任意，E∼Bern(p)独立于(B,W)，逐w的后验参数b即使大于1/2也因熵对称性满足 $h_2(p*b)=g_p(h_2(b))$。Jensen给
$$
H(B\oplus E|W)\ge g_p(H(B|W)).\tag{4.4}
$$
令任意二元向量B^n、任意W，E^n是iid Bern(p)且独立整个(B^n,W)，C^n=B^n⊕E^n。链式法则得
$$
\begin{aligned}
H(C^n|W)&=\sum_tH(C_t|C^{t-1},W)\\
&\ge\sum_tH(C_t|C^{t-1},B^{t-1},W)\\
&=\sum_tH(C_t|B^{t-1},W)\\
&\ge\sum_tg_p(H(B_t|B^{t-1},W))\\
&\ge n g_p(H(B^n|W)/n).\tag{4.5}
\end{aligned}
$$
等号处：给定B过去后C过去只揭示E过去，后者独立整个B、W和当前E。随后先用(4.4)，再用凸性与链式法则。B坐标可相关，W可依赖整个B；真正独立条件是整个添加噪声向量。噪声若与W相关，此推导不成立。

### 4.4 全块逆、固定长度可达与端点

用B=Y、C=X、W=J，且 $H(Y^n|J)/n\ge\max\{0,1-\log M/n\}$，有
$$
\frac1nI(X^n;J)\le1-g_p(\max\{0,1-\log M/n\}).\tag{4.6}
$$
同观测两端取J=(J1,J2)、M≤M1M2即可。此逆覆盖所有块映射、全部aux和时分。

对0≤R≤1，取独立 $Z\sim\operatorname{Bern}(\beta)$，$U=Y\oplus Z$、$\beta=h_2^{-1}(1-R)$，则
$$
I(Y;U)=1-h_2(\beta)=R,\quad I(X;U)=1-h_2(p*\beta).\tag{4.7}
$$
§3.2–3.3将测试核转为确定固定长度码，§2再拆分任意分率，匹配(4.6)。R≥1取U=Y。得到(0.3)。R=0给F=0；R=1及以上饱和于1−h₂(p)；p=0给min{R,1}；p=1/2给恒0。p>1/2时翻转共同观测，变为噪声1−p而保持target和编码问题不变。凹性由§3.4或1−g_p(1−R)可见。

这是标准校准，不是新定理。自然底MGL区间应是[0,ln2]；bit换底后才是[0,1]。没有依赖未读的1973历史原证明。

## 5. 固定参考内点的集中1/3收缩及分布式外界

### 5.1 源、反向核与精确命名

令X公平，$(N_1,N_2)\perp X$，$P_N=(5,1,1,1)/8$，$Y_i=X\oplus N_i$。这对应p=1/4、q=1/8，四噪声概率均正且q≠p²，不是条件独立CEO边界。定义V=(Y1,Y2)，则
$$
P_V=(3,1,1,3)/8,\quad
m(v)=\mathbb E[(-1)^X|V=v]=(2/3,0,0,-2/3).\tag{5.1}
$$
例如00下P(X=0)=5/6，11下为1/6，异号下为1/2。固定这个P_V与 $K=P_{X|V}$，P_VK=P_X是公平分布。

以下还证明固定reference的KL系数
$$
\eta_{\rm KL}(P_V,K)=\sup_{Q\ne P_V}
\frac{D(QK\|P_VK)}{D(Q\|P_V)}=1/3.\tag{5.2}
$$
Q可遍历所有V上的分布，但分母的reference始终是上述固定P_V；不允许把它换成任意reference后仍宣称同常数。互信息系数定义见(0.4)。

### 5.2 mgf与KL共轭

本小节用自然底KL $D_e$。对实s，
$$
Z_s=\mathbb E_{P_V}e^{sm(V)}=\frac14+\frac34\cosh(2s/3)
\le\cosh(s/3)^3.\tag{5.3}
$$
令c=cosh(s/3)≥1，则差为
$$
c^3-\tfrac32c^2+\tfrac12=(c-1)^2(c+\tfrac12)\ge0,\tag{5.4}
$$
s≠0时严格。任取Q，记b=E_Qm∈[−2/3,2/3]，令 $P_s=P_Ve^{sm}/Z_s$。KL非负给
$$
D_e(Q\|P_V)=D_e(Q\|P_s)+sb-\ln Z_s
\ge sb-3\ln\cosh(s/3).\tag{5.5}
$$
置s=3t并取sup，
$$
D_e(Q\|P_V)\ge3d_e(b),\quad
d_e(b)=\frac{1+b}{2}\ln(1+b)+\frac{1-b}{2}\ln(1-b).\tag{5.6}
$$
因为 $\sup_t\{tb-\ln\cosh t\}$ 的唯一最大点是 $t=\operatorname{atanh}b$，代回即d_e(b)。QK对target的符号均值为b，故d_e(b)=D_e(QK∥P_X)。这证明固定reference KL上界。

对任意X−V−U，逐u令Q=P(V|u)并平均，得到
$$
I(V;U)\ge3I(X;U).\tag{5.7}
$$
全部有限aux与独立时分标签均被覆盖。这里未限制aux为局部product核；集中放宽将用于outer。

### 5.3 最优是sup逼近，非正信息取等

取u∈{−1,+1}，定义集中核
$$
P(U=u|v)=\frac{1+u\zeta m(v)}2,\quad0<\zeta<1.\tag{5.8}
$$
因E_Pm=0，U公平，$P(v|u)=P_V(v)(1+u\zeta m(v))$，且E_Pm²=1/3给target后验符号均值uζ/3。因此
$$
I(X;U)=d_e(\zeta/3)/\ln2,\quad
I(V;U)=\mathbb E_Pd_e(\zeta m(V))/\ln2.\tag{5.9}
$$
由d_e(z)=z²/2+O(z⁴)，分子为ζ²/(18ln2)+O(ζ⁴)、分母为ζ²/(6ln2)+O(ζ⁴)，比值趋于1/3。对单一 $Q_\zeta=P_V(1+\zeta m)$，同样的二次展开给KL比趋于1/3，故(0.4)、(5.2)的sup均精确。

若Q≠P且b≠0，在(5.5)取s=3atanh b≠0，mgf严格性给 $D_e(Q\|P)>3d_e(b)$。若b=0而Q≠P，左侧正而右侧0，也严格。因此任何有限aux且I(V;U)>0时，比值严格小于1/3；最优常数只由趋零扰动逼近。**逐个严格不等式并不推出统一严格间隙。** 集中核(5.8)也不是原两端局部可实现码的声明。

### 5.4 全block外界

原模型任意局部固定长度码 $J_i=f_i(Y_i^n)$，令J=(J1,J2)。集中观察V^n能计算J；§3.1的两条Markov关系适用（将观测Y换为V）。逐坐标使用(5.7)，得
$$
\begin{aligned}
I(X^n;J)&\le\sum_t I(X_t;J,V^{t-1})\\
&\le\tfrac13\sum_tI(V_t;J,V^{t-1})
=\tfrac13 I(V^n;J)\le\tfrac13\log(M_1M_2).\tag{5.10}
\end{aligned}
$$
等号只用V跨时iid，不要求Y1与Y2给定X条件独立。再由DPI及后验
$$
I(X;V)=1-\left[\tfrac34h_2(1/6)+\tfrac14\right]
=\tfrac34[1-h_2(1/6)],
$$
得到(0.5)。统一消息数下的私有随机化可直接按Markov证明或固定种子处理；合法公共Q须逐Q条件化。这是已证明并经非形式化数学审读的有效outer，不是分布式tightness或新颖性认证。换pmf、换target或提供未计费相关公共信息时不得直接套用。

### 5.5 G的操作凹性、burst与全块效率关卡

**[操作拼接与效率等价]** 令
$$
G(r)=\sup\{\Delta:(R_1,R_2,\Delta)\text{原分布式操作可达},\ R_1+R_2\le r\}.
$$
先证凹性：取两可达点，按预定theta∈(0,1)，在总长N的前 $n_a=\lfloor\theta N\rfloor$ 块及余下 $n_b=N-n_a$ 分别运行两组码。给定目标epsilon，先选各点的rate/relevance松弛足够小，再取N大使两子块均超过各自阈值；每端发送两索引对，消息数至多两子码字母表之积。独立源子块及分别编码使relevance**精确相加**，率按子块长度加权，取整误差O(1/N)。由(1.1)所有充分大N都可用，闭包消掉松弛。对G的sup用任意逼近点再让逼近误差趋零，得
$$
G(\theta r_a+(1-\theta)r_b)\ge\theta G(r_a)+(1-\theta)G(r_b).\tag{5.11}
$$
theta=0、1平凡。G非减，(0.5)给G(0)=0及G(r)≤r/3。因此0<a<b时，和零码时分得到G(a)≥(a/b)G(b)，即G(r)/r非增。故
$$
L:=\lim_{r\downarrow0}\frac{G(r)}r
=\sup_{r>0}\frac{G(r)}r\in[1/4,1/3].\tag{5.12}
$$
下界来自只使用一个终端的BSC(p=1/4)曲线：由 $h_2(1/2-z)=1-2z^2/\ln2+O(z^4)$，其零率斜率为(1−2p)²=1/4。

进一步定义，Mi是每端在正概率源支持上**实际使用的消息字母表大小**，
$$
C_{\rm fin}:=\sup_{m,f_1,f_2:\ \log(M_1M_2)>0}
\frac{I(X^m;J_1,J_2)}{\log(M_1M_2)}.\tag{5.13}
$$
不用H(Ji)代替分母。若M1M2=1，两消息恒定、信息为0，排除0/0不损失任何正效率；分母正而信息0的码比值记0。

**有限码到操作点／burst。** 固定任意m块码，记 $a_i=\log M_i$、$\rho_i=a_i/m$、$\rho=\rho_1+\rho_2>0$、$d=I(X^m;J_1,J_2)/m$。给定任意固定theta∈(0,1]，在总长N的预定 $k_N=\lfloor\theta N/m\rfloor$ 个独立m块上重复该码，剩下全部静默（含不足一个活动块的尾部）。两端每端使用字母表大小 $M_i^{k_N}$，因各源块独立且每个使用消息有正概率，确实能实现此乘积范围；联合消息对的可达范围不必是两端全笛卡尔积，但不影响逐端计费。于是
$$
\frac{\log M_{i,N}}N=\frac{k_Na_i}N\le\theta\rho_i,
\quad \frac1NI(X^N;J_{1,N},J_{2,N})=\frac{k_Nm}{N}d
\ge\theta d-\frac{md}{N}.\tag{5.14}
$$
给定epsilon，取N≥md/epsilon（d=0时无此要求）及其它平凡取整阈值，就对**所有**充分大N满足操作定义。因此(θρ1,θρ2,θd)可达。theta=1已给该有限码的正率操作点；theta任意小则将任意正率高效码稀释到零率而保持d/ρ效率。若d=0，结论仍成立只是效率0。

于是 $\sup_{r>0}G(r)/r\ge d/\rho$，再对有限码取sup得到L≥C_fin。反方向，由定义每个有限码有
$I(X^n;J_1,J_2)\le C_{\rm fin}\log(M_1M_2)$；分母0时也成立。对任一可达点和epsilon>0取充分大n，
$$
\Delta-\epsilon\le C_{\rm fin}(R_1+R_2+2\epsilon).
$$
这里C_fin≤1/3由(5.10)，故可安全令epsilon↓0，得 $G(r)\le C_{\rm fin}r$。因此
$$
\boxed{L=C_{\rm fin}=\sup_{r>0}G(r)/r}.\tag{5.15}
$$
这个等价只是操作拼接与消息数定义的推论，不是原问题的单字母化。

### 5.6 严格间隙的全局含义

由(5.15)，命题 $L<1/3$ 等价于存在同一个 $c<1/3$，使所有有限块长、所有合法局部固定长度码满足
$$
I(X^m;J_1,J_2)\le c\log(M_1M_2).\tag{5.17}
$$
也等价于所有r>0均有G(r)≤cr；分母0时信息0。因任意正率高效有限码都能按(5.14)稀释到零率，单字母弱扰动分析、逐个aux严格不等式或数值未逼近，都不足以证明该统一命题。下一节利用局部结构直接证明全块1/4界；结合(5.15)得到L=1/4。这没有将(5.11)–(5.15)的操作等价误作单字母化，也没有将局部构造类假定为完整可行类。

## 6. 固定相关内点的局部全块加强逆与匹配效率

本节只处理§5的固定源：X公平，$(N_1,N_2)\perp X$，噪声概率按00、01、10、11顺序为(5,1,1,1)/8，跨时iid，$Y_i=X\oplus N_i$。终端i仅见自己的整个观测块，无交互，decoder只收到两个消息。结论覆盖任意有限块映射，而不限于一字母量化核。

### 6.1 精确耦合与反向独立性

置
$$
\lambda=\frac{1-1/\sqrt2}{2},\qquad
1-2\lambda=1/\sqrt2,\qquad \lambda(1-\lambda)=1/8.\tag{6.1}
$$
取A、B1、B2彼此独立、各为Bern(lambda)，并独立于公平X，定义
$$
Z=X\oplus A,\qquad Y_i=Z\oplus B_i,\qquad N_i=A\oplus B_i.\tag{6.2}
$$
于是X→Z→(Y1,Y2)，两观测给定Z条件独立。逐项核源分布：
$$
\begin{aligned}
P(N_1=N_2=1)&=(1-\lambda)\lambda^2+\lambda(1-\lambda)^2=1/8,\\
P(N_1=0,N_2=1)&=(1-\lambda)^2\lambda+\lambda^2(1-\lambda)=1/8,\\
P(N_1=1,N_2=0)&=1/8,\\
P(N_1=N_2=0)&=(1-\lambda)^3+\lambda^3=1-3\lambda(1-\lambda)=5/8.
\end{aligned}\tag{6.3}
$$
所有噪声独立X，因此精确匹配整个P_XY1Y2，不只是观测边缘；独立重复即匹配每个m块的原源律。任意原局部映射的信息量在此耦合下不变。

公平性还给
$$
P(Z=z,A=a,B_1=b_1,B_2=b_2)
=\tfrac12 P_A(a)P_{B_1}(b_1)P_{B_2}(b_2).\tag{6.4}
$$
故A独立整个(Z,B1,B2)。反向X=Z⊕A的噪声独立于Z及两观测，向量A^m也独立于(Z^m,Y1^m,Y2^m)和源独立随机编码所产消息。对每支，Z公平且Bi独立Z，所以Yi公平，反向Z=Yi⊕Bi中Bi独立Yi，进而Bi^m独立于(Yi^m,Ji)。这里不要求Bi独立另一端消息；后续支路收缩仅使用Ji，绝不条件化另一个消息后套用同一个固定reference系数。

Z只在分析中耦合，没有给编码器或decoder任何额外侧信息，也不收费或传输Z。目标始终是原X；下面第一步保留I(X^m;J)，并明确保留外层收缩损失。原观测给定X仍相关，故本证明不是将条件独立CEO定理直接套给原X。

### 6.2 公平BSC的标量和全块线性收缩

设D公平，C=D⊕E，E∼Bern(e)独立D，0≤e≤1/2，且C−D−U。暂用自然底，定义
$$
d(b)=\frac{1+b}{2}\ln(1+b)+\frac{1-b}{2}\ln(1-b),\quad |b|\le1.
$$
由d'(b)=atanh b展开并积分，
$$
d(b)=\sum_{k=1}^{\infty}\frac{b^{2k}}{(2k)(2k-1)},\qquad |b|<1.\tag{6.5}
$$
两端由连续性及非负项极限延拓。对0≤t≤1逐项有t^(2k)≤t²，故d(tb)≤t²d(b)。给定U=u，令b_u=E[(-1)^D|u]；C后验均值为(1−2e)b_u，两边先验均公平。逐u平均并换底得到
$$
I(C;U)\le(1-2e)^2I(D;U).\tag{6.6}
$$
这是固定公平reference的标准收缩，不声称任意偏置reference均有相同常数。

若(C_t,D_t)为该对的iid重复，C^m−D^m−W，则取U_t=(W,D^{t−1})。由§3.1两条Markov及块熵链（随机核W同样适用），
$$
\begin{aligned}
I(C^m;W)&\le\sum_tI(C_t;W,D^{t-1})\\
&\le(1-2e)^2\sum_tI(D_t;W,D^{t-1})\\
&=(1-2e)^2I(D^m;W).\tag{6.7}
\end{aligned}
$$
第一步没有以ΣI(C_t;W)替换块信息，最后一步用D跨时iid。此处e=lambda，每层系数为1/2。

### 6.3 全块局部消息的条件独立

给定Z^m，Y1^m与Y2^m独立；对任意确定Ji=fi(Yi^m)，
$$
\begin{aligned}
P(j_1,j_2|z^m)
&=\sum_{y_1^m,y_2^m}\prod_tP(y_{1,t}|z_t)P(y_{2,t}|z_t)
1\{j_1=f_1(y_1^m)\}1\{j_2=f_2(y_2^m)\}\\
&=P(j_1|z^m)P(j_2|z^m).\tag{6.8}
\end{aligned}
$$
独立私有种子只是将指标换为各自局部随机核，同样分解。所以I(J1;J2|Z^m)=0，而不必有无条件独立。熵恒等式给
$$
\begin{aligned}
I(Z^m;J_1,J_2)
&=I(Z^m;J_1)+I(Z^m;J_2)-I(J_1;J_2)+I(J_1;J_2|Z^m)\\
&=I(Z^m;J_1)+I(Z^m;J_2)-I(J_1;J_2).\tag{6.9}
\end{aligned}
$$
这正是集中编码不具有的局部信息合并约束。任意集中W=g(Y1^m,Y2^m)一般不能拆为满足(6.8)的局部消息对，故不能把下一节的1/4推给集中编码。集中固定reference系数1/3与局部1/4界相容。

### 6.4 双层合成及实际率账

令J=(J1,J2)。外层X^m−Z^m−J及(6.4)、(6.7)给
$$
I(X^m;J)\le\tfrac12 I(Z^m;J).\tag{6.10}
$$
每条支路Z^m−Yi^m−Ji的反向公平BSC(lambda)给
$$
I(Z^m;J_i)\le\tfrac12 I(Y_i^m;J_i).\tag{6.11}
$$
结合(6.9)，
$$
\begin{aligned}
I(X^m;J_1,J_2)
&\le\tfrac14\sum_iI(Y_i^m;J_i)-\tfrac12 I(J_1;J_2)\\
&\le\tfrac14\sum_iH(J_i)
\le\tfrac14\sum_i\log M_i.\tag{6.12}
\end{aligned}
$$
确定码I(Yi^m;Ji)=H(Ji)，局部随机核只需≤。主界(0.6)丢弃非负冗余扣除量，因而较弱；这与(6.12)不冲突。这里只利用已审合成链保留的扣除项，不据此声称新的紧区域。

信息衰减因子1/2×1/2不是重复收费；每端log Mi仅在末端出现一次，熵只是中间上界。所有m、所有率、所有合法局部块映射均适用。M1M2=1时信息0。

源独立公共Q对decoder可见时，逐q条件化应用上述证明，条件源律仍相同，得到条件relevance的对应上界；若用统一消息数，上界沿用同一Mi。确定时分按子块平均保持。未条件化的共同种子可能破坏(6.8)，有交互或非局部编码也可能破坏它，不得照搬本证明。

对操作epsilon码，$\Delta-\epsilon\le(R_1+R_2+2\epsilon)/4$。epsilon↓0给Δ≤(R1+R2)/4；DPI另给Δ≤I(X;V)，于是得到(0.8)，仍为外界而非精确区域。

### 6.5 匹配的确定固定长度码族与量词

终端2恒定，仅用终端1的原BSC(1/4)观测。对0<t<1取设计测试核U=Y1⊕E_t，E_t独立、Bern((1−t)/2)，定义
$$
R(t)=1-h_2((1-t)/2),\qquad
D(t)=1-h_2((1-t/2)/2).\tag{6.13}
$$
D(t)在此表示设计relevance，不是失真。由§4公式，I(Y1;U)=R(t)、I(X;U)=D(t)。设计比
$$
\frac{D(t)}{R(t)}=\frac{d(t/2)}{d(t)}\longrightarrow\frac14\quad(t\downarrow0),\tag{6.14}
$$
来自(6.5)二次项。这不是一次随机U的消息长度结论，必须落实到固定长度码。

令t_k=1/k，k≥2，R_k=R(t_k)>0、D_k=D(t_k)>0，先固定
$$
\varepsilon_k=\min\{R_k^2,D_k/2\}>0.\tag{6.15}
$$
对每个固定k，应用§3.2–3.3：先固定目标epsilon_k及rate裕量，再选平滑与双典型容差，最后取所有充分大块长中的某个m_k≥k，得到确定单端码，实际使用字母表满足
$$
\frac{\log M_{1,k}}{m_k}\le R_k+\varepsilon_k,\quad
\frac{I(X^{m_k};J_{1,k})}{m_k}\ge D_k-\varepsilon_k>0,
\quad M_{2,k}=1.\tag{6.16}
$$
于是分母非零且
$$
\frac{D_k-\varepsilon_k}{R_k+\varepsilon_k}
\le\frac{I(X^{m_k};J_{1,k},J_{2,k})}{\log(M_{1,k}M_{2,k})}
\le\frac14.\tag{6.17}
$$
因epsilon_k/R_k≤R_k→0且D_k/R_k→1/4，下界趋于1/4。正信息确保消息非常数；删去未用索引只减消息数，不损下界。该序列是实际有限确定码族，不只是测试核比值；单端测试核仅用于下界，未假设它覆盖全部分布式可行类。

(6.15)只是充分的对角选择而非唯一选择；任何epsilon_k>0满足epsilon_k/R_k→0、epsilon_k=o(D_k)，并逐k取足够大m_k，都可作同样落实。所展示选择最终也满足epsilon_k/D_k→0，因为D_k/R_k→1/4。

### 6.6 最优效率与严格间隙

由全块上界(6.12)得C_fin≤1/4，(6.17)得C_fin≥1/4，结合(5.15)，
$$
\boxed{L=C_{\rm fin}=1/4<1/3.}\tag{6.18}
$$
如需选择严格在(1/4,1/3)内的统一常数，c=7/24即满足(5.17)。效率趋于1/3的合法原模型分布式码族被全块界排除，而不是因局部扫描或未找到候选而排除。

这只确定最优效率上确界及线性外界，不证明G(r)=r/4在全部正r成立，不证明完整(R1,R2,Δ)区域。集中最优扰动核仍有1/3，其不满足局部消息CI，因此没有矛盾。

## 7. 文献与适用限制

- Estella Aguerri–Zaidi, *Distributed Variational Representation Learning*, arXiv:1807.04193v3（2019-03-31），物理 p8 式 (12)–(13)：[arXiv:1807.04193](https://arxiv.org/abs/1807.04193)。其 CEO 定理依赖条件独立，不能用于本相关内点的逆。
- Goldfeld–Polyanskiy, *The Information Bottleneck Problem and Its Applications in Machine Learning*, arXiv:2004.14941v2（2020-05-01），§III 式 (11)–(16)：[arXiv:2004.14941](https://arxiv.org/abs/2004.14941)。该综述的操作损失为逐符号 log-loss；本文另给直接 block converse，不以逐符号逆替代。
- Fan Cheng, *Generalization of Mrs. Gerber’s lemma*, Communications in Information and Systems 14(2):79–86（2014），Lemma 1 及相应微积分论证：[DOI 10.4310/cis.2014.v14.n2.a1](https://doi.org/10.4310/cis.2014.v14.n2.a1)。本文完整重证所需特例，并明确自然底、bit 换底、逆熵分支与参数区间。
- 历史出处：[Dobrushin and Tsybakov, Information transmission with additional noise (1962)](https://doi.org/10.1109/TIT.1962.1057738)；[Wyner and Ziv, A theorem on the entropy of certain binary sequences and applications—I (1973)](https://doi.org/10.1109/TIT.1973.1055107)。两篇历史原始全文尚未核实，不以其未核定理编号或证明作为本文逻辑依赖。

### 未解决事项与适用边界

1. **文献归属与新颖性未认证。** 两层公平BSC收缩与局部CI组合可能已有相应结论；本文不作优先权判断。
2. **相关2026文献全文仍有获取限制。** 全文及假设尚未核齐，见 [参考文献](../references.md) 中仍未读全文的条目，不能据此确认覆盖、排除或领域空白；本稿不作任何该文覆盖结论。
3. **不是完整区域。** 已确定固定内点L=C_fin=1/4和全块线性外界，但未证明完整G(r)、所有正率紧性或非平凡Ψ张量化。
4. **扣除项与主界。** (6.12)保留−I(J1;J2)/2，主界(0.6)使用丢弃该非负扣除量后的较弱形式。两者一致，不代表另得完整区域。
5. **对角松弛非唯一。** (6.15)为充分选择，替代选择须保持相对于R_k和D_k的误差消失，并在每个固定k之后选择充分大块长；不能先取块长再改变设计裕量。
6. **不自动推广参数。** 其他(p,q)、非公平X、源有记忆、交互、非局部编码或源相关公共信息可能破坏精确耦合、反向独立或消息CI；未证明同λ表示或同1/4系数。合法独立私有随机性和条件化公共Q的范围见§1与§6。

相同观测、单端IB、MGL/BSC部分是标准校准；固定reference的集中1/3和局部全块1/4及匹配效率均给出可逐式检查的证明，核心结果经非形式化数学审读。这不构成形式化正确性、新颖性或完整区域认证。本文不附第三方 PDF。
