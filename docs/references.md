# 主要文献

BibTeX 收录下面的文献。字段以 2026-11-09 核对过的 arXiv API、Crossref 和 DataCite 记录为准。作者电子邮件、通信地址和单位不录入。本仓库不保存论文全文。DataCite 的 creator 字段不转写成 editor。

机器可读题录：[primary.bib](../references/primary.bib)。

## 1. Estella Aguerri 与 Zaidi，分布式变分表示学习

Iñaki Estella Aguerri，Abdellatif Zaidi。*Distributed Variational Representation Learning*。

- 期刊：IEEE Transactions on Pattern Analysis and Machine Intelligence，43(1):120–138。Crossref 的出版日期是 2021-01-01。
- DOI：[10.1109/TPAMI.2019.2928806](https://doi.org/10.1109/TPAMI.2019.2928806)。DOI 字符串中的年份是 2019，与期刊卷期年 2021 同时保留，不合并成一个年份。
- arXiv:1807.04193。API 给出的最新版本是 v3，首次提交 2018-07-11，v3 更新于 2019-03-31。版本记录：[abs/1807.04193](https://arxiv.org/abs/1807.04193)。核对用的 HTML：[html/1807.04193v3](https://arxiv.org/html/1807.04193v3)。
- 第一作者的论文署名是 Iñaki Estella Aguerri。Crossref 把该名字拆成 given name “Inaki Estella”、family name “Aguerri”。ORCID [0000-0001-5110-6858](https://orcid.org/0000-0001-5110-6858) 用来固定这个作者，不在 BibTeX 里改写姓氏。

阅读位置均指 arXiv v3 HTML。

- Section II：操作模型和条件独立假设。
- Theorem 1：条件独立时的相关度–复杂度区域。
- Remark 4：去掉条件独立后与长期未决的对数损失分布式信源编码的联系。
- Section VII-A：与对数损失 CEO 问题的连接。
- Section VII-B：和速率消去。

算法驻点的保证不作为全局最优或 converse。

## 2. Courtade 与 Weissman，对数损失多终端信源编码

Thomas A. Courtade，Tsachy Weissman。*Multiterminal Source Coding Under Logarithmic Loss*。

- 期刊：IEEE Transactions on Information Theory，60(1):740–761，2014 年 1 月。
- DOI：[10.1109/TIT.2013.2288257](https://doi.org/10.1109/TIT.2013.2288257)。
- arXiv:1110.3069。API 给出的最新版本是 v3，首次提交 2011-10-13，v3 更新于 2012-07-11。版本记录：[abs/1110.3069](https://arxiv.org/abs/1110.3069)。核对用的 HTML：[html/1110.3069v3](https://arxiv.org/html/1110.3069v3)。
- arXiv 摘要页的作者字符串是 Thomas Courtade；期刊与 arXiv HTML 的署名是 Thomas A. Courtade。BibTeX 采用带中间名首字母的期刊形式。
- arXiv 评论写有一篇 ISIT 2012 的部分版本。这里没有为该会议论文单列题录，因为本次没有核对会议页码。

定理编号来自 arXiv v3，不是期刊 PDF。

- Section 3 与 Theorem 3：两个编码器、条件独立观测的对数损失 CEO 区域。
- Theorem 10 与 Theorem 11：$m$ 编码器 CEO 的内界和严格意义外界。联合分布带有 $\prod_i p(y_i\mid x)$。
- Section 3.3：在该 CEO 假设下，把乘积重构放宽到整块分布不扩大区域。
- Theorem 6 与 Appendix E：重构两个被观测信源本身，源可以任意相关；这不是隐藏目标加相关噪声的定理。

## 3. Estella Aguerri 与 Zaidi，离散与高斯源的分布式信息瓶颈

Iñaki Estella Aguerri，Abdellatif Zaidi。*Distributed Information Bottleneck Method for Discrete and Gaussian Sources*。

- arXiv:1709.09082v3，首次提交 2017-09-26，v3 更新于 2017-10-03。arXiv 评论写明投稿 2018 International Zurich Seminar on Information and Communication。版本记录：[abs/1709.09082](https://arxiv.org/abs/1709.09082)。核对用的 HTML：[html/1709.09082v3](https://arxiv.org/html/1709.09082v3)。
- 会议页面 [IZS 2018](https://www.izs.ethz.ch/2018/) 写明会期为 2018 年 2 月 21–23 日。程序页 [Program.html](https://www.izs.ethz.ch/2018/Program.html) 列出该报告及两位作者。
- 论文 DOI：[10.3929/ethz-b-000245048](https://doi.org/10.3929/ethz-b-000245048)。DataCite 记录的出版者是 ETH Zurich，日期类型 Available 为 2018-02，资源类型为 Conference Paper。
- 论文集 DOI：[10.3929/ethz-b-000242151](https://doi.org/10.3929/ethz-b-000242151)。DataCite 题名为 *International Zurich Seminar on Information and Communication (IZS 2018): Proceedings*，Available 日期为 2018-02-21。该记录有 creator 字段。没有标题页证明这些人是编辑，所以 BibTeX 不设 `editor`。
- 论文 DataCite 记录没有页码。后来文献中出现过的页码不写入 BibTeX。

这篇是记号和定理范围的短前驱。它假设条件独立。它不是“相关噪声特例此后仍然开放”的独立证据。方程 (4) 的符号差异写在 [已知结果](known-results.md)。

## 4. Yuan、Wu 与 Zhou，面向任务的分布式跨模态信源编码

Zhe Yuan，Dan Wu，Liang Zhou。*Rate–Distortion Theory for Task-Oriented Distributed Cross-Modal Source Coding*。

- 期刊：IEEE Transactions on Communications，74:5366–5381，2026。Crossref 没有期号。
- DOI：[10.1109/TCOMM.2026.3666617](https://doi.org/10.1109/TCOMM.2026.3666617)。2026-11-09 的 Crossref 记录确认标题、三位作者、期刊、卷、页码和年份。同日该 DOI 返回 202，跳转到 `https://ieeexplore.ieee.org/document/11404184/`。
- arXiv API 用题名和作者检索，`totalResults` 为 0。没有可用的 arXiv 全文。
- 公开页面上能看到摘要，摘要把模型说成带语义先验的对数损失 CEO 型多终端信源编码。摘要不是全文。定理假设、辅助变量和是否包含 $p=1/4$、$q=1/8$ 都没有核对。
- 因此这篇文献只作为需要继续核对的邻近工作列入。它不证明该测试点已被覆盖，也不证明该测试点仍开放，更不构成 2026 年的新颖性证书。证明笔记使用这条限制，不把它的全文当作已审核材料。

## 5. Goldfeld 与 Polyanskiy，信息瓶颈及其机器学习应用

Ziv Goldfeld，Yury Polyanskiy。*The Information Bottleneck Problem and Its Applications in Machine Learning*。

- arXiv:2004.14941。2026-11-09 的 arXiv API 给出的最新版本是 v2，更新于 2020-05-01。版本记录：[abs/2004.14941](https://arxiv.org/abs/2004.14941)。
- 证明笔记沿用原稿对 §III 式 (11)–(16) 的指向，并说明该综述的操作损失是逐符号 log-loss。本次没有对照 PDF 重核这些公式编号。笔记中的 block converse 是自包含的，不依赖这次未做的对照。

## 6. Cheng，Mrs. Gerber 引理的推广

Fan Cheng。*Generalization of Mrs. Gerber’s lemma*。

- 期刊：Communications in Information and Systems，14(2):79–86，2014。
- DOI：[10.4310/cis.2014.v14.n2.a1](https://doi.org/10.4310/cis.2014.v14.n2.a1)。2026-11-09 的 Crossref 记录确认标题、作者、期刊、卷 14、期 2 和页码 79–86。
- 证明笔记引用 Lemma 1 的凸性陈述，并自包含地重证所需特例。期刊 PDF 没有收入仓库，公式编号没有用 PDF 再核一遍。

## 7. Dobrushin 与 Tsybakov，带附加噪声的信息传输

R. Dobrushin，B. Tsybakov。*Information transmission with additional noise*。

- 期刊：IEEE Transactions on Information Theory，8(5):293–304，1962 年 9 月。
- DOI：[10.1109/TIT.1962.1057738](https://doi.org/10.1109/TIT.1962.1057738)。2026-11-09 的 Crossref 记录确认标题、作者姓名的首字母形式、期刊、卷、期、页码和日期。
- 原始全文尚未核实。证明笔记不把未核的定理编号或证明当作逻辑依赖。BibTeX 不把首字母展开成未核对的全名。

## 8. Wyner 与 Ziv，某些二元序列的熵

A. Wyner，J. Ziv。*A theorem on the entropy of certain binary sequences and applications—I*。

- 期刊：IEEE Transactions on Information Theory，19(6):769–772，1973 年 11 月。
- DOI：[10.1109/TIT.1973.1055107](https://doi.org/10.1109/TIT.1973.1055107)。2026-11-09 的 Crossref 记录确认标题、作者姓名的首字母形式、期刊、卷、期、页码和日期。
- 原始全文尚未核实。自然底与 bit 换底后的参数区间由证明笔记自行写明，不依赖这篇未读全文。

## 元数据核对

2026-11-09 做了下列检查。

| 对象 | 结果 |
| --- | --- |
| arXiv API `1807.04193,1110.3069,1709.09082` | 三篇均返回 v3，标题、作者和更新日期与上表一致 |
| Crossref `10.1109/TPAMI.2019.2928806` | 卷 43、期 1、页 120–138、出版日期 2021-01-01 |
| Crossref `10.1109/TIT.2013.2288257` | 卷 60、期 1、页 740–761、2014 年 1 月 |
| DataCite `10.3929/ethz-b-000245048` | 标题、两位作者、ETH Zurich、2018 |
| DataCite `10.3929/ethz-b-000242151` | 论文集标题、Available 日期 2018-02-21。creator 字段不记为 editor |
| Crossref `10.1109/TCOMM.2026.3666617` | 卷 74、页 5366–5381、2026；无期号。全文未核对 |
| arXiv API `2004.14941` | 最新版本 v2，更新于 2020-05-01；作者 Ziv Goldfeld、Yury Polyanskiy。§III 公式编号未对照 PDF |
| Crossref `10.4310/cis.2014.v14.n2.a1` | 卷 14、期 2、页 79–86、2014；作者 Fan Cheng。全文未收入仓库 |
| Crossref `10.1109/TIT.1962.1057738` | 卷 8、期 5、页 293–304、1962 年 9 月。全文未核实 |
| Crossref `10.1109/TIT.1973.1055107` | 卷 19、期 6、页 769–772、1973 年 11 月。全文未核实 |
| HTML 与 DOI 链接 | 见下方链接检查。两个 ETH DOI 在同日既出现过 200，也出现过 HTTP 500；题录以同日返回 200 的 DataCite API 为准 |

链接检查时各 URL 的状态：

- `https://arxiv.org/abs/1807.04193`、`https://arxiv.org/html/1807.04193`、`https://arxiv.org/html/1807.04193v3`：200。
- `https://arxiv.org/abs/1110.3069`、`https://arxiv.org/html/1110.3069`、`https://arxiv.org/html/1110.3069v3`：200。
- `https://arxiv.org/abs/1709.09082`、`https://arxiv.org/html/1709.09082v3`：200。
- `https://doi.org/10.1109/TPAMI.2019.2928806`：202，跳转到 `https://ieeexplore.ieee.org/document/8766879/`。
- `https://doi.org/10.1109/TIT.2013.2288257`：202，跳转到 `https://ieeexplore.ieee.org/document/6651793/`。
- `https://doi.org/10.3929/ethz-b-000245048` 与 `https://doi.org/10.3929/ethz-b-000242151`：同日的访问里既有 200，也有 HTTP 500 或超时。论文 DOI 的一次成功访问跳到 ETH Research Collection 条目。两个 DOI 的 DataCite API 记录同日返回 200。旧 handle `http://hdl.handle.net/20.500.11850/245048` 返回 500，所以正文使用 DOI，不使用该 handle。
- `https://www.izs.ethz.ch/2018/` 与 `https://www.izs.ethz.ch/2018/Program.html`：200。
- `https://doi.org/10.1109/TCOMM.2026.3666617`：202，跳转到 `https://ieeexplore.ieee.org/document/11404184/`。页面提供摘要，不提供已核对的全文。

期刊 PDF 上的定理编号和页内公式没有重新核对。若期刊排版与 arXiv v3 不同，以以后对照期刊 PDF 的结果改正编号，不在未对照时改写上表。
