# Exam Guide — 全卷通用考试技巧

> 跨单元通用的内容放在这里：指令词、Mark Scheme 黑话、全卷失分点、复习计划、资源。
> 各单元专属的考点和陷阱见对应单元笔记。

---

## 🧭 指令词（Command Words）——决定你的答案长什么样

| 指令词 | 中文 | 你要写什么 | 典型分值 |
|--------|------|-----------|---------|
| **State / Give / Identify** | 说出 / 给出 / 指出 | **只要术语或事实**，一句话，不解释 | 1 |
| **Name** | 命名 | **只要名字** | 1 |
| **Describe** | 描述 | **说清楚是什么 / 会发生什么** —— 完整句子，点出特征 | 2–4 |
| **Explain** | 解释 | **Describe + why** —— 必须有因果（because / this means that / so that） | 2–6 |
| **Discuss** | 讨论 | **正反两面**，每个点都要展开 | 4–8 |
| **Compare** | 比较 | **相似点 + 差异点都写**，差异要成对 | 2–6 |
| **Tick / Circle** | 打勾 / 圈出 | 只标记，**不要多写** | 1–3 |
| **Draw and annotate** | 画图并标注 | **每一段标注都是得分点**，画完一定写英文标签 | 4–6 |
| **Complete the table** | 完成表格 | 按行给分，**拼写必须能辨认** | 4–6 |

### Describe vs Explain
> **Describe** = what happens｜**Explain** = why / how it works
>
> 例：*Explain how the firewall protects the network*
> ❌ "It blocks hackers."（这是 describe，而且是 **TV**）
> ✅ "It **examines incoming traffic** and **checks it against set criteria** such as a blacklist；if the traffic **does not meet the criteria it is rejected**, so unauthorised data cannot enter the network."

---

## 🔍 Mark Scheme 黑话表

| 缩写 | 全称 | 意思 |
|------|------|------|
| **TV** | Too Vague | **太笼统，不给分**。例："different access levels"、"best path" |
| **NE** | No Evidence | **没有答到问题** |
| **NAQ** | Not Answering the Question | **答非所问** |
| **BOD** | Benefit of the Doubt | **存疑但给分** |
| **Mark the first answer given** | — | **只改第一个答案** |
| **Mark whole answer** | — | **整体判分**，必须写成配对（HLL vs LLL 就是这种） |
| **"Any N from"** | — | 给分点比总分多，**任选 N 个**即可 |
| **"MAX N if no expansion"** | — | **不展开最多给 N 分** —— "必须解释"的信号 |
| **"Do not accept…"** | — | 明确排除项，**写了也不算分** |

### ⚖️ 三条铁律

**① 品牌名不得分** —— 试卷封面印着：*"No marks will be awarded for using brand names of software packages or hardware."*
❌ "Google Chrome" / "Microsoft Word"　✅ "web browser" / "word processor"

**② Repeat 的答案不得分** —— 题目已给的词再写不算分。题目说 "One example of primary storage is **cache**, give one **other**" → 写 cache = 0 分。

**③ 不结合情境的通用答案不得分** —— ✅ **把题干里的数字、传感器名、设备名抄进答案。**

---

## ⚡ 全卷通用失分点 Top 18

| # | 失分点 | 正确做法 |
|---|--------|---------|
| 1 | **不看指令词** —— Explain 题只写 Describe 的内容 | 看到 **Explain** 就必须出现 **because / this means / so that** |
| 2 | **不结合题干情境** | 抄题干的名词和数字进答案 |
| 3 | **只写点不解释** | 每个点后面必须接一句"所以…" |
| 4 | **单位搞错（1024 vs 1000）** | 存储单位一律 **1024**（**1000 已不在考纲内**）|
| 5 | **方向搞反** | 证书 server→browser；请求 browser→web server；地址 PC→MAR |
| 6 | **把 actuator 当成能显示屏幕内容** | Actuator 只引起**物理运动** |
| 7 | **把 ALU 当成 register** | 组件 ≠ 寄存器。寄存器只有 **PC / MAR / MDR / CIR / ACC** |
| 8 | **把 HDD 当成 optical storage** | **HDD = magnetic** |
| 9 | **性能题不说"增加还是减少"** | 必须写 "**if the clock speed is INCREASED**" |
| 10 | **写"encryption 能阻止黑客"** | 数据仍被窃取，只是变得 **meaningless** |
| 11 | **Compare 题只写一边** | A 怎样 + **whereas** + B 怎样 |
| 12 | **答案里出现品牌名** | 用通用词 |
| 13 | **二进制加法用"转十进制加完再转回来"** | 必须写**二进制竖式 + 进位**；**"show all working" 本身就是得分点** |
| 14 | **二补码在正数最前面加个 1** | 必须 **flip and add 1**；最高位权重是 **−128** |
| 15 | **写 "cable" / "path" / "best path"** | 用 **wire**；路由器题必须写 "the **router determines/assigns** the route" |
| 16 | **压缩题写文件格式（JPEG / MP4 / ZIP）** | 方法只有 **lossy** 和 **lossless** 两类 |
| 17 | **"fast" / "better" 没有比较对象** | **"Fast/faster alone is NE"** |
| 18 | **混淆 check digit 和 checksum** | **check digit = 数据输入**；**parity / checksum / echo / ARQ = 数据传输** |

---

## 🎯 投入产出比

### ⛔ 整份题库（2020–2026）**从未考过**的

| 内容 | 说明 |
|---|---|
| **RLE 单独出题** | **从未**独立出现。只是无损压缩的**举例**（判分写 "e.g. RLE"）。**不要练 RLE 编码/解码**，只要会写「无损压缩的一个例子是 RLE，它把重复数据**识别、分组并记录重复次数**」 |
| **ISBN-10 / ISBN-13 算法** | **从未**出现。校验位题考的是「算出 → 附末尾 → 扫描重算 → 比对」**流程**，不是加权算法 |
| **触摸屏类型 / 打印机 / 投影仪 / 2D–3D 扫描仪 / QR 码** | 2022 年后**从未考过**（Unit 3）|
| **输入输出设备如何工作** | **已从考纲删除** —— 写了**直接 0 分** |

### ✅ 性价比最高的（几乎每场必考）

1. **Unit 1**：进制转换 · 二进制加法 + overflow · 二补码 · 有损/无损压缩
2. **Unit 1**：存储单位换算（一律 **1024**）—— 常作**卷首 1 分题**
3. **Unit 2**：串行/并行 + 单工/半双工/全双工 —— **得分结构 = 特征（1 分）+ 展开后果（1 分）**
4. **Unit 2**：查错方法（parity / checksum / echo check / ARQ）
5. **Unit 2**：加密**术语定义**（encryption key / cipher text / symmetric / asymmetric）
6. **Unit 3**：寄存器 · FDE 周期 · cores–cache–clock 性能对比
7. **Unit 6**：sensor → microprocessor → actuator 五步链

### 📈 2026 的新趋势：题目变碎了

> - June 2026 **P11 Q3** = **五个独立**的 1 分进制换算
> - June 2026 **P12 Q1(c)** = **三个独立**的 1 分题（数制 + 两个二补码）
> - June 2026 **P12 Q4(c)** = **三个独立**的 1 分加密题
>
> → **定义和单步运算的性价比上升**。把每个核心术语当「**1 分题**」准备：一句话，措辞标准，不多写。

---

## 🗓️ 冲刺复习计划

**距考试 2 周以上** —— 按单元过正文 → 做完 📋 考纲对照清单 → 做该单元真题 → 回看陷阱表

**距考试 3–7 天** —— 只刷各单元 **🧠 一页纸速记** + **⚠️ 高频失分点汇总**；重点补 **Unit 3**（分值最高）和 **Unit 6**（模板最固定）

**考前一晚 / 当天早上** —— 只看三样：
1. 本页的**指令词表**和 **Mark Scheme 黑话表**
2. Unit 3 的 **🧠 一页纸速记**
3. Unit 6 的 **sensor → microprocessor → actuator 五步模板**

**考试中**
- **先读指令词**，再读题目内容
- **算分**：题目给几分就写几个点（3 分题写 3 个独立点，宁多勿少）
- **画图题**：每一段都标英文，标签就是分
- **不要空题**：写对方向的一部分也比留白强

---

## 🔗 资源

**题库**（按题目组织方式排序）

| 网站 | 特点 | 费用 |
|------|------|------|
| [Save My Exams — CIE IGCSE CS](https://www.savemyexams.com/igcse/computer-science/cie/23/topic-questions/1-data-representation/number-systems/exam-questions/) | **按考纲章节组织**，和本笔记单元划分**一一对应** | 部分免费 |
| [PapersDaddy — 0478 Topical](https://www.papersdaddy.com/cambridge/igcse/computer-science-0478/resources/topical-past-papers/paper-1) | Paper 1 按考纲领域分类 | **免费下载** |
| [Exam Papers Practice — 0478](https://www.exampaperspractice.co.uk/igcse-cie-computer-science-topic-questions/) | 已更新到 2026 考纲，带 mark scheme | 有免费样章 |
| [Educate A Change — 0478 Topical](https://educateachange.com/past-papers/topical/igcse/computer-science-0478/) | **1957 道**主题分类题（2015–2025） | 部分免费 |
| [Smart Exam Resources — 0478/0984](https://www.smartexamresources.com/course/caie-igcse-computer-science-0478-0984-9-1) | 主题分卷 + 主题 mark scheme | 付费 |
| [Physics and Maths Tutor](https://www.physicsandmathstutor.com/computer-science-revision/igcse-cie/) | 历年真题 + 分类题 | 免费 |

> 💡 **推荐组合**：本笔记每单元 → 配 **Save My Exams** 对应章节；需要更多同类题用 **PapersDaddy**（免费）或 **Educate A Change**。

**资料来源**：学校课件（Unit 1–5，⚠️ Unit 6 无课件）· *Cambridge IGCSE Computer Science* 教材 · *Hodder Study & Revision Guide* · **2020–2026 真题 QP / MS / Examiner Report（138 份）**

> ⚠️ 本笔记所有"官方答案"和"失分点"均来自真题 Mark Scheme 和 Examiner Report **原文**，不是推测。考纲每三年更新，使用前确认你的考试年份对应 **2026–2028** 考纲。
