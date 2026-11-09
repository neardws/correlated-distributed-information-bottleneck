# 主要文献

BibTeX 只收录下面三篇。字段以 2026-11-09 核对过的 arXiv API、Crossref 和 DataCite 记录为准。作者电子邮件和通信地址不录入。本仓库不保存论文全文。

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
- 论文集 DOI：[10.3929/ethz-b-000242151](https://doi.org/10.3929/ethz-b-000242151)。DataCite 题名为 *International Zurich Seminar on Information and Communication (IZS 2018): Proceedings*，创建者是 Amos Lapidoth 与 Stefan M. Moser，Available 日期为 2018-02-21。BibTeX 的 `editor` 取自这一论文集记录。论文自己的 DataCite 记录没有编辑者字段。
- 论文 DataCite 记录没有页码。后来文献中出现过的页码不写入 BibTeX。

这篇是记号和定理范围的短前驱。它假设条件独立。它不是“相关噪声特例此后仍然开放”的独立证据。方程 (4) 的符号差异写在 [已知结果](known-results.md)。

## 元数据核对

2026-11-09 做了下列检查。

| 对象 | 结果 |
| --- | --- |
| arXiv API `1807.04193,1110.3069,1709.09082` | 三篇均返回 v3，标题、作者和更新日期与上表一致 |
| Crossref `10.1109/TPAMI.2019.2928806` | 卷 43、期 1、页 120–138、出版日期 2021-01-01 |
| Crossref `10.1109/TIT.2013.2288257` | 卷 60、期 1、页 740–761、2014 年 1 月 |
| DataCite `10.3929/ethz-b-000245048` | 标题、两位作者、ETH Zurich、2018 |
| DataCite `10.3929/ethz-b-000242151` | 论文集标题、两位编辑、Available 日期 2018-02-21 |
| HTML 与 DOI 链接 | 见下方链接检查。两个 ETH DOI 在同日既出现过 200，也出现过 HTTP 500；题录以同日返回 200 的 DataCite API 为准 |

链接检查时各 URL 的状态：

- `https://arxiv.org/abs/1807.04193`、`https://arxiv.org/html/1807.04193`、`https://arxiv.org/html/1807.04193v3`：200。
- `https://arxiv.org/abs/1110.3069`、`https://arxiv.org/html/1110.3069`、`https://arxiv.org/html/1110.3069v3`：200。
- `https://arxiv.org/abs/1709.09082`、`https://arxiv.org/html/1709.09082v3`：200。
- `https://doi.org/10.1109/TPAMI.2019.2928806`：202，跳转到 `https://ieeexplore.ieee.org/document/8766879/`。
- `https://doi.org/10.1109/TIT.2013.2288257`：202，跳转到 `https://ieeexplore.ieee.org/document/6651793/`。
- `https://doi.org/10.3929/ethz-b-000245048` 与 `https://doi.org/10.3929/ethz-b-000242151`：同日的访问里既有 200，也有 HTTP 500 或超时。论文 DOI 的一次成功访问跳到 ETH Research Collection 条目。两个 DOI 的 DataCite API 记录同日返回 200。旧 handle `http://hdl.handle.net/20.500.11850/245048` 返回 500，所以正文使用 DOI，不使用该 handle。
- `https://www.izs.ethz.ch/2018/` 与 `https://www.izs.ethz.ch/2018/Program.html`：200。

期刊 PDF 上的定理编号和页内公式没有重新核对。若期刊排版与 arXiv v3 不同，以以后对照期刊 PDF 的结果改正编号，不在未对照时改写上表。
