# Exam Guide — 全卷通用考试技巧

> 跨单元通用的内容放在这里：指令词、Mark Scheme 黑话、全卷失分点、复习计划、资源。
> 各单元专属的考点和陷阱见对应单元笔记。

---

## 📄 两张卷子的结构

| | **Paper 1** Computer Systems | **Paper 2** Algorithms, Programming and Logic |
|---|---|---|
| 时长 | 1 小时 45 分 | 1 小时 45 分 |
| 分值 | **75 分** | **75 分** |
| 占比 | **50%** | **50%** |
| 考纲范围 | Topic 1–6 | Topic 7–10 |
| 题型 | 简答 + 结构化 | 简答 + 结构化 + **写算法** |
| 计算器 | ❌ 不允许 | ❌ 不允许 |
| 对应笔记 | Unit 1–6 | Unit 7–10 + [Pseudocode Reference](Pseudocode%20Reference.md) |

### ⚠️ Paper 2 的三条铁规

**① 必须用伪代码作答**
> 考纲原文：*"Where the solution to a problem involves coding, candidates are required to write solutions in **pseudocode**. Solutions written in **programming code will not be awarded marks**."*
> → 用 Python / Java / VB 语法写答案 = **0 分**

**② 唯一例外：最后一道 15 分 scenario 题**
> 可以用伪代码，**或** Python / Visual Basic / Java 之一（其他语言不给分）
> 题目基于 Topic 7–10 的**未见过**情境；考纲建议在这道题上花 **30 分钟**

**③ 评分看逻辑不看语法，但格式还是得守**
> 考纲原文：*"Knowledge of programming language syntax is **not** examined; in all cases the **logic is more important than the syntax**."*
> → 变量名可以不同、小语法错可能不扣分；但**官方伪代码的格式**（`←`、THEN 缩进 2 格、`MOD(a,b)`）是"逻辑的表达方式"，照自己习惯写会丢分。详见 [Pseudocode Reference](Pseudocode%20Reference.md)

---

## ⚠️ 只做 2023 年以后的 Paper 2 卷子

**2023 年考纲改革把 Paper 2 整个换掉了**。用老卷练手会练错方向。

| | **2015–2022**（老卷，44 份）| **2023–2025**（新卷，21 份）| **2026+（你考的）** |
|---|---|---|---|
| 卷名 | Problem-solving and Programming | Algorithms, Programming and Logic | 同左 |
| 总分 | 50 | **75** | **75** |
| 结构 | **Section A（Q1 = 20 分场景大题）+ Section B** | **没有 Section A/B**，Q1…Q11 平铺 | 同左 |
| 最后一题 | Section B 数据库题 | **固定 15 分 scenario 题** | 同左 |
| 数据库 | **query-by-example (QBE) 网格** | **SQL**（`SELECT/FROM/WHERE`）| 同左 |
| 逻辑门 / 真值表 | **完全没有** | **每份卷子都有** | 同左 |

### 🚫 老卷里已经作废、别练的

| 内容 | 为什么 |
|---|---|
| **QBE 网格题**（画表格写条件）| 新卷 **21/21 全用 SQL**，QBE 完全消失 |
| **Section A 的 pre-release 场景题** | 新卷没有这个结构了；15 分题是**当场给的未见过情境** |
| **"Identify three loop structures" 这类列举题** | 新卷改成了 tick / 连线选择题 |

### 🆕 老卷里**根本没有**、2023 才加的（只做老卷会完全没准备）

| 新增内容 | 证据 |
|---|---|
| **程序开发生命周期 PDLC** | `life cycle` 出现 10 次，**全部在 2023+**；老卷 44 份一次没考 |
| **decomposition / abstraction** | 出现 6 次，**全部在 2023+** |
| **2D 数组** | `two-dimensional (2D)` 首次出现于 2023-21-O/N |
| **`ROUND` / `RANDOM` / `SUBSTRING` / `LENGTH` / `UCASE` / `LCASE`** | 出现 12 次，**全部在 2023+**（老卷只有 `MOD` 和 `DIV`）|
| **文件处理**（`OPENFILE`/`READFILE`/`WRITEFILE`/`CLOSEFILE`）| 出现 5 次，**全部在 2023+** |
| **可维护性**作为独立小题 | 出现 6 次，**全部在 2023+** |
| **arithmetic / Boolean / logical operators** 分类 | 仅 2024-22-M/J、2025-23-M/J |
| **bubble sort / linear search** 明文点名 | 仅 2024-22-F/M、2024-22-O/N、2025-22-F/M、2025-23-M/J |
| **逻辑门 + 真值表** | 新卷 **21/21 全有**，老卷**完全没有**（2023 才把 Logic 并入 Paper 2）|

> 💡 **练手优先级**：2023–2025 的 21 份 → 2026 年的 → 老卷只挑 trace table / flowchart / 找错改错 / validation / test data 这几个**没变的题型**练。

### 🔁 贯穿 12 年、唯一没变的题型

| 题型 | 覆盖率 | 典型分值 |
|---|---|---|
| **trace table 填表** | **61 / 65 份** | 4–5 |
| **flowchart 流程图题** | 43 / 65 份 | 4–6 |
| **找错并改正** | 43 / 65 份 | 4 |
| **写算法 / 写程序** | **65 / 65 份** | 老卷 5–6 / 新卷 15 |
| **validation + test data** | 各 37 / 65 份 | 4 |

> ⚠️ **这五类怎么变都要考** —— 不管练新卷老卷，这几块都要练熟。

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

## 📝 Paper 2 判分规则（和 Paper 1 不一样）

### ① 伪代码题按「**逻辑点**」给分，不按行数

| 情况 | 结果 |
|---|---|
| 用了正确的结构（循环/判断/过程）但变量名不同 | ✅ 给分 |
| 语法有小错但逻辑对 | ✅ 可能给分（*logic is more important than syntax*）|
| 逻辑对但写成 Python / Java 语法 | ❌ **0 分**（非 scenario 题）|
| 用自然语言 "if the score is higher than the maximum" | ❌ **0 分**（*"`x > y` is acceptable but `x is greater than y` is not"*）|

### ② 写算法题的六个固定给分点

| 给分点 | 说明 |
|---|---|
| **变量声明** | 用了 `DECLARE` 且类型正确 |
| **初始化** | 累加/计数变量在循环前归零；最值用 `Array[1]` 初始化 |
| **循环边界** | 不越界（冒泡排序到 N−1） |
| **输入提示** | 每个 `INPUT` 前有 `OUTPUT "Enter..."` |
| **正确输出** | 最后有 `OUTPUT` 结果 |
| **结构正确** | 用了该用的循环/判断类型（FOR / WHILE / REPEAT） |

> 💡 **一行代码往往值 1 分** —— 写不出完整答案就写你能写的部分，**部分分很容易拿**。

### ③ 「找错改错」题必须**两栏都写**

> | Error | Correction |
> |---|---|
> | The loop goes up to 8 but the array has only 8 elements | Change `FOR Index ← 1 TO 8` to `FOR Index ← 1 TO 7` |
>
> ⚠️ 只写 Error 不写 Correction = **一半分没了**
> ⚠️ "the loop is wrong" = **0 分** —— 必须**引用具体代码**

### ④ 三种错误类型（题目问 "State the type of error" 时只能从这三个里选）

| 类型 | 特征 |
|---|---|
| **Syntax error** | 程序**跑不起来**（忘 `ENDIF`、`MOD x y`）|
| **Logic error** | 程序**跑得起来但结果错**（用了 `>` 应该是 `<`）|
| **Runtime error** | 运行时**崩溃**（除以 0、数组越界）|

### ⑤ Trace table 题按**每一格**给分

> - 每个变量**单独一列**
> - **OUTPUT 单独一列**（忘了就丢分）
> - 数组元素**逐个开列**（`A[1] | A[2] | A[3]`）
> - 循环变量**每一轮都要记**

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
| **RLE 单独出题** | 近年**没有单独大题**，但 2026–2028 考纲明确把 RLE 作为 lossless compression 的例子。**至少掌握 RLE 的编码/解码原理**，不要只背名字；考纲要求的是“理解如何压缩”，不是只认术语 |
| **ISBN-10 / ISBN-13 算法** | 近年**没有单独考具体加权算法**。重点掌握 check digit 的「计算 → 附在末尾 → 重新计算 → 比对」流程；具体 ISBN 权重不必死记 |
| **触摸屏类型 / 打印机 / 投影仪 / 2D–3D 扫描仪 / QR 码** | 近年**少考**，但 2026–2028 考纲**仍明确列出**（Unit 3）。至少掌握**用途和适用场景**，不要完全跳过 |
| **输入输出设备如何工作** | 当前考纲的重点是“**是什么 / 为什么需要 / 在情境中选择**”，不要求逐设备背内部工作原理；但答到相关原理通常不扣分，不要被“写了 0 分”吓住 |

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

**距考试 3–7 天** —— 只刷各单元 **🧠 一页纸速记** + **⚠️ 高频失分点汇总**
- **Paper 1**：重点补 **Unit 3**（分值最高）和 **Unit 6**（模板最固定）
- **Paper 2**：**默写** [Pseudocode Reference](Pseudocode%20Reference.md) 的「⚡ 十条最容易丢分的硬性规定」+ Unit 7 的「六大方法速查表」+ Unit 9 的 SQL 模板 + Unit 10 的六个真值表

**考前一晚 / 当天早上**
- **两卷都看**：本页的**指令词表**、**Mark Scheme 黑话表**、**两张卷子结构**
- **Paper 1**：Unit 3 的 🧠 一页纸速记 + Unit 6 的 sensor → microprocessor → actuator 五步模板
- **Paper 2**：[Pseudocode Reference](Pseudocode%20Reference.md) 的 **⚡ 十条** + **🧠 一页纸速记**

**考试中（两卷通用）**
- **先读指令词**，再读题目内容
- **算分**：题目给几分就写几个点（3 分题写 3 个独立点，宁多勿少）
- **画图题**：每一段都标英文，标签就是分
- **不要空题**：写对方向的一部分也比留白强

**考试中（Paper 2 专属）**
- ⏱️ **时间分配**：前面所有小题 ≈ **75 分钟**，最后 15 分 scenario 题 ≈ **30 分钟**（考纲官方建议）
- ✍️ **写算法前先在草稿区列变量清单** —— 漏声明变量是最大面积失分
- 🔁 **写完检查这四样**：变量都 `DECLARE` 了吗？累加变量初始化了吗？循环会越界吗？用 `←` 了吗？
- 🚫 **非 scenario 题千万别写 Python/Java 语法** —— 不给分

---

## 🔗 资源

**题库**（按题目组织方式排序）

| 网站 | 特点 | 费用 |
|------|------|------|
| [Save My Exams — CIE IGCSE CS](https://www.savemyexams.com/igcse/computer-science/cie/23/topic-questions/1-data-representation/number-systems/exam-questions/) | **按考纲章节组织**，和本笔记单元划分**一一对应** | 部分免费 |
| [PapersDaddy — 0478 Topical Paper 1](https://www.papersdaddy.com/cambridge/igcse/computer-science-0478/resources/topical-past-papers/paper-1) | Paper 1 按考纲领域分类 | **免费下载** |
| [PapersDaddy — 0478 Topical Paper 2](https://www.papersdaddy.com/cambridge/igcse/computer-science-0478/resources/topical-past-papers/paper-2) | Paper 2 按考纲领域分类 | **免费下载** |
| [Exam Papers Practice — 0478](https://www.exampaperspractice.co.uk/igcse-cie-computer-science-topic-questions/) | 已更新到 2026 考纲，带 mark scheme | 有免费样章 |
| [Educate A Change — 0478 Topical](https://educateachange.com/past-papers/topical/igcse/computer-science-0478/) | **1957 道**主题分类题（2015–2025） | 部分免费 |
| [Smart Exam Resources — 0478/0984](https://www.smartexamresources.com/course/caie-igcse-computer-science-0478-0984-9-1) | 主题分卷 + 主题 mark scheme | 付费 |
| [Physics and Maths Tutor](https://www.physicsandmathstutor.com/computer-science-revision/igcse-cie/) | 历年真题 + 分类题 | 免费 |

> 💡 **推荐组合**：本笔记每单元 → 配 **Save My Exams** 对应章节；需要更多同类题用 **PapersDaddy**（免费）或 **Educate A Change**。

**本校最新资料（`../csresource/new/`）**

| 资料 | 用途 |
|---|---|
| [2026–2028 考纲](../csresource/new/2026_10_19_PPT/Syllabus/0478%20Computer%20Science%202026-2028%20Syllabus%20document%20.pdf) | 核对知识点范围和 pseudocode 规范 |
| [按单元真题 + Answer Key](../csresource/new/Past%20Exam%20Papers/Questions%20by%20Unit/) | Unit 1–10 + Big Programming Question，适合学完一单元就刷 |
| [June 2026 Paper 2 官方 Mark Scheme](../csresource/new/Past%20Exam%20Papers/Questions%20by%20Year/) | 核对 Paper 2 答案，替代旧笔记里的“推断” |
| [Paper 2 Homework Booklet 答案](../csresource/new/2026_10_19_PPT/Homework%20Booklet/) | 学校作业本对照；注意个别答案本身有 bug（见 Unit 8） |
| [Practice Paper 1 / 2 - CT1](../csresource/new/) | 考前套卷练习 |
| [Unit 4 Common Test 反馈](../csresource/new/2026_10_19_Common%20Test%20U4%20-%20feedback%20v2/) | 看真实评分标准和示例答案 |
| [Chapter 7 / 8 PPT](../csresource/new/2026_10_19_PPT/PPT/) | Paper 2 算法与编程课件 |

**资料来源**：学校课件（Unit 1–5 slides；Unit 3/4/5 另有 PPT/Chapter 4）· 学校按单元整理的 QP / Answer Key · *Cambridge IGCSE Computer Science* 教材 · *Hodder Study & Revision Guide* · **2020–2026 真题 QP / MS / Examiner Report（138 份）**

> ⚠️ 本笔记中标注「官方」的答案来自真题 **Mark Scheme / Examiner Report 原文**；标注「推断」的答案是按考纲和评分规范推得的，**不是官方原文**。考纲每三年更新，使用前确认你的考试年份对应 **2026–2028** 考纲。
