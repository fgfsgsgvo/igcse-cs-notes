# Unit 7 — Algorithm Design and Problem Solving 算法设计与问题求解

> **考纲**：0478/0984 · Topic 7
> **试卷**：Paper 2 — Algorithms, Programming and Logic
> **分值**：Paper 2 = **75 分 / 1 小时 45 分 / 占总成绩 50%**，考 Topic 7–10
> **计算器：不允许**
> **本单元特点**：Unit 7 是**方法论单元**（怎么设计、怎么查错、怎么测），Unit 8 是**语法单元**（怎么写）。
> 两者在 Paper 2 里**揉在一起考** —— 一道题可能前半段让你画结构图，后半段让你写伪代码。
> ⚠️ **Paper 2 必须用伪代码作答，写编程语言代码不给分**（唯一例外：最后 15 分 scenario 题可用 Python/VB/Java）。
> 📖 语法细节看 → [Pseudocode Reference.md](Pseudocode%20Reference.md)

---

## 📋 考纲对照清单

| ✓ | 考纲点 | 内容 | 在笔记里 |
|---|---|---|---|
| ☐ | 7.1 | 程序开发生命周期：analysis / design / coding / testing | [↓](#71-程序开发生命周期--the-program-development-life-cycle) |
| ☐ | 7.2 (a) | 系统由子系统构成，子系统又由更小的子系统构成 | [↓](#72-子系统与分解--sub-systems--decomposition) |
| ☐ | 7.2 (b) | 问题如何分解为组成部分 | [↓](#72-子系统与分解--sub-systems--decomposition) |
| ☐ | 7.2 (c) | 用不同方法设计并构造解决方案 | [↓](#73-三种设计工具--structure-diagrams--flowcharts--pseudocode) |
| ☐ | 7.3 | 说明给定算法的目的（inputs / processes / outputs / storage）| [↓](#74-说明算法的目的--purpose-of-an-algorithm) |
| ☐ | 7.4 | 标准解题方法：线性查找、冒泡排序、求和、计数、最大/最小/平均 | [↓](#75-标准解题方法--standard-methods-of-solution) |
| ☐ | 7.5 (a) | 验证检查（validation）的必要性与类型 | [↓](#76-验证--verification) |
| ☐ | 7.5 (b) | 核对检查（verification）的必要性与类型 | [↓](#76-验证--verification) |
| ☐ | 7.6 | 提出并应用合适的测试数据 | [↓](#77-测试数据--test-data) |
| ☐ | 7.7 | 完成 trace table 进行 dry run | [↓](#78-trace-table--dry-run) |
| ☐ | 7.8 | 找出算法中的错误并给出改正方法 | [↓](#79-找错与改错--identify-and-correct-errors) |
| ☐ | 7.9 | 用伪代码、程序代码、流程图编写和修改算法 | [↓](#710-写算法--write-and-amend-algorithms) |

---

# 7.1 程序开发生命周期 — The Program Development Life Cycle

## 四个阶段（必须按顺序背下来）

**English（背这句）**
> The program development life cycle consists of four stages: **analysis**, **design**, **coding** and **testing**.

| 阶段 | 中文 | 核心任务 |
|---|---|---|
| **Analysis** | 分析 | 弄清问题是什么、要求是什么 |
| **Design** | 设计 | 想清楚怎么解 |
| **Coding** | 编码 | 把设计写成代码 |
| **Testing** | 测试 | 用测试数据验证 |

---

### ① Analysis 分析

**English（背这句）**
> **Analysis** involves **abstraction**, **decomposition** of the problem and **identification of the problem and requirements**.

**三个动作**

| 动作 | 含义 |
|---|---|
| **Abstraction** 抽象 | 去掉与问题**无关的细节**，只保留**必要的信息** |
| **Decomposition** 分解 | 把大问题**拆成小问题** |
| **Identification of requirements** 确认需求 | 弄清程序**要做什么**、输入是什么、输出是什么 |

> 💡 **Abstraction 答题模板**（题目常问 "Explain what is meant by abstraction"）：
> *"Abstraction is removing / ignoring unnecessary details and keeping only the relevant / important features of a problem."*
> 例子：做一个"学生成绩系统"，不需要知道学生**住哪**、**父母是谁**——只需要姓名和分数。

---

### ② Design 设计

**English（背这句）**
> **Design** involves decomposition, **structure diagrams**, **flowcharts** and **pseudocode**.

**三种设计工具**（详见 [7.3](#73-三种设计工具--structure-diagrams--flowcharts--pseudocode)）

---

### ③ Coding 编码

**English（背这句）**
> **Coding** involves **writing program code** and **iterative testing**.

> ⚠️ **关键词是 iterative（迭代的）** —— 不是"写完再测一次"，而是**写一点、测一点、改一点**，不断重复。

---

### ④ Testing 测试

**English（背这句）**
> **Testing** involves testing the program code with the use of **test data**.

> 💡 **测试的目的是找错误，不是证明程序对** —— 这句在 Explain 题里很吃香。

---

## ⚠️ 陷阱

| 陷阱 | 说明 |
|---|---|
| 以为四个阶段是**线性一次性**的 | 实际是**循环的**：测试发现问题 → 回到设计 → 回到编码 |
| 把 abstraction 和 decomposition 搞混 | **Abstraction = 去掉细节**；**Decomposition = 拆成小块** |
| 写成 "planning" | 官方用词是 **design** |
| 忘写 "iterative" | coding 阶段是**迭代测试** |

---

## 🔧 答题模板：Explain the purpose of the analysis stage

> *"The analysis stage is used to **identify the problem and the requirements** of the solution. **Abstraction** is used to remove unnecessary details, and **decomposition** is used to break the problem down into smaller, more manageable sub-problems."*

---

# 7.2 子系统与分解 — Sub-systems & Decomposition

## 核心概念

**English（背这句）**
> Every computer system is made up of **sub-systems**, which are made up of **further sub-systems**.

> 💡 这就是**自顶向下（top-down）设计**的思想 —— 一层一层往下拆。
> 例：**学校** → 子系统：教务处、财务处、图书馆 → **图书馆** 的子系统：借书、还书、查询

**Decomposition 的定义**
**English（背这句）**
> **Decomposition** is breaking a problem down into **smaller, more manageable parts / sub-problems**.

**为什么要分解（This is a 3-mark question）**
1. **Easier to solve** —— 每个小问题更简单，更容易理解和解决
2. **Easier to test / debug** —— 可以单独测试每个部分
3. **Tasks can be shared** —— 不同的人/团队可以同时做不同的部分
4. **Easier to maintain and update** —— 改动只影响一个子系统

> ⚠️ **别只写 "it is easier"** —— 必须写**为什么容易**（easier to understand / test / share the work）。

---

# 7.3 三种设计工具 — Structure Diagrams, Flowcharts, Pseudocode

| 工具 | 形式 | 什么时候用 |
|---|---|---|
| **Structure diagram** 结构图 | **树状图**（自顶向下分层）| 展示**系统由哪些部分组成**，不展示逻辑顺序 |
| **Flowchart** 流程图 | 图形 + 箭头 | 展示**步骤和判断的流程**，有标准符号 |
| **Pseudocode** 伪代码 | 类代码文本 | 展示**具体逻辑**，最接近代码 |

---

## ① Structure Diagram 结构图

**English（背这句）**
> A **structure diagram** shows the **hierarchy** of a system, breaking it down into sub-systems from the top level downwards.

**例子：登录系统**

```
              Login System
                   │
      ┌────────────┼────────────┐
   Enter          Check        Show
   Details      Details       Result
                 │
        ┌────────┴────────┐
     Check            Check
   Username         Password
```

**规则**
- **最上面是整体系统**（Level 0）
- 每往下一层，就是**更小的子系统**
- **不显示顺序、不显示判断** —— 只显示"包含关系"
- 子系统的名字通常是**动词短语**（Check Password、Enter Details）

> ⚠️ **Structure diagram ≠ Flowchart**
> - Structure diagram：答"**由什么组成**"
> - Flowchart：答"**怎么做 / 什么顺序**"
> ⚠️ Structure diagram **没有箭头、没有判断框、没有起止符**。

---

## ② Flowchart 流程图

### 标准符号（考纲规定必须用这些，Section 4）

| 符号 | 名称 | 作用 |
|---|---|---|
| **箭头**（arrow）| **Flow line** | 表示控制从一个形状**传到另一个形状** |
| **矩形**（rectangle）| **Process** | 表示**执行某件事**（赋值、计算）|
| **两侧带竖线的矩形** | **Subroutine** | 表示**调用子程序**，会关联到一个独立的、不连线的流程图 |
| **平行四边形**（parallelogram）| **Input/Output** | 表示**输入或输出** |
| **菱形**（diamond）| **Decision** | 表示**判断**（Yes/No 或 True/False），有**两条**出口 |
| **椭圆/圆角矩形** | **Terminator** | 表示 **Start** 和 **Stop** |

> ⚠️ **Decision 必须有两条出口线，并且要标 Yes/No（或 True/False）** —— 忘了标是常见失分点。
> ⚠️ **Start 和 Stop 必须用 Terminator（圆角/椭圆）**，不能画成普通矩形。

### 例子：输入 10 个数求最大值

```
        ┌─────────┐
        │  Start  │  ← Terminator
        └────┬────┘
             ▼
    ╱─────────────────╲
   ╱  Enter a number   ╲   ← Input/Output（平行四边形）
   ╲                   ╱
    ╲─────────────────╱
             ▼
      ┌─────────────┐
      │ Max ← Num   │      ← Process（矩形）
      └──────┬──────┘
             ▼
      ┌─────────────┐
      │ Count ← 1   │
      └──────┬──────┘
             ▼
      ┌─────────────┐
   ┌─▶│ Count < 10? │      ← Decision（菱形）
   │  └──┬───────┬──┘
   │   No│       │Yes
   │     │       ▼
   │     │  ╱─────────────╲
   │     │ ╱ Enter a number ╲
   │     │ ╲                ╱
   │     │  ╲──────────────╱
   │     │       ▼
   │     │  ┌─────────────┐
   │     │  │ Num > Max?  │   ← Decision
   │     │  └──┬───────┬──┘
   │     │  No │       │ Yes
   │     │     │       ▼
   │     │     │  ┌──────────┐
   │     │     │  │ Max ← Num│
   │     │     │  └────┬─────┘
   │     │     │       │
   │     │     ▼◀──────┘
   │     │  ┌─────────────┐
   │     └─▶│ Count ← + 1 │
   │        └──────┬──────┘
   └───────────────┘
             │
             ▼
    ╱─────────────────╲
   ╱  Output Max       ╲
   ╲                   ╱
    ╲─────────────────╱
             ▼
        ┌─────────┐
        │  Stop   │
        └─────────┘
```

> 💡 Paper 2 画流程图的题通常只给**一小段**（比如一个判断或一个循环），不用画整题。

---

## ③ Pseudocode 伪代码

详见 **[Pseudocode Reference.md](Pseudocode%20Reference.md)** —— 那是 Paper 2 最核心的文件。

---

## ⚠️ 三选一的判断

| 题目说 | 用哪个 |
|---|---|
| "Show the **structure** / how the system is **broken down**" | **Structure diagram** |
| "Draw a **flowchart**" / 给了菱形+平行四边形 | **Flowchart** |
| "Write an **algorithm**" / "**pseudocode**" | **Pseudocode** |

> ⚠️ 题目**说哪个就写哪个**。让你画 flowchart 你写伪代码 = 0 分。

---

# 7.4 说明算法的目的 — Purpose of an Algorithm

**English（背这句）**
> The purpose of an algorithm can be described in terms of its **inputs**, **processes**, **outputs** and **storage**.

| 术语 | 中文 | 回答什么 |
|---|---|---|
| **Inputs** | 输入 | 算法**需要什么数据**（从用户/文件来的）|
| **Processes** | 处理 | 算法**对数据做了什么**（计算、比较、排序）|
| **Outputs** | 输出 | 算法**给出什么结果**（显示、写入文件）|
| **Storage** | 存储 | 算法**保存了什么**（变量、数组、文件）|

## 🔧 答题模板

**题目**："Explain the purpose of the algorithm shown in the pseudocode."

**答案结构（4 个点，每个 1 分）**
> - **Inputs**: the algorithm takes in ... *(e.g. the marks of each student)*
> - **Processes**: it then ... *(e.g. adds the marks together and divides by the number of students)*
> - **Outputs**: it outputs ... *(e.g. the average mark)*
> - **Storage**: ... is stored in ... *(e.g. the marks are stored in a 1D array)*

> ⚠️ **别只说 "it calculates the average"** —— 要**按 input → process → output 的顺序拆开说**，每步单独得分。

---

## 🔧 另一种问法："Describe the processes involved in an algorithm"

**答题技巧**：**逐行翻译成人话**，不要逐行照抄伪代码。

❌ *"Line 1 does DECLARE, line 2 does INPUT"*
✅ *"The algorithm asks the user to enter a number, then it checks whether that number is greater than the maximum so far; if it is, it updates the maximum."*

> ⚠️ **不要引用变量名当解释**，比如 "X becomes Y" —— 要说清楚**这个变量代表什么现实事物**。

---

# 7.5 标准解题方法 — Standard Methods of Solution

**考纲限定只有这 6 种 —— 背下来，Paper 2 一定考其中几个。**

| 方法 | 中文 | 典型问法 |
|---|---|---|
| **Linear search** | 线性查找 | "Write an algorithm to find whether X is in the list" |
| **Bubble sort** | 冒泡排序 | "Write an algorithm to sort the list into ascending order" |
| **Totalling** | 求和 | "Calculate the total..." |
| **Counting** | 计数 | "Count how many..." |
| **Finding maximum / minimum** | 求最值 | "Find the highest / lowest..." |
| **Finding average** | 求平均 | "Calculate the mean..." |

---

## ① Linear Search 线性查找

**English（背这句）**
> A **linear search** checks each item in turn, starting from the first, until the required item is found or the end of the list is reached.

**原理**：一个一个往下找，找到就停，找完没有就是"不存在"

**时间复杂度**：最坏情况要看全部 N 项 → 数据量大时**很慢**

```
DECLARE Names : ARRAY[1:10] OF STRING
DECLARE SearchName : STRING
DECLARE Found : BOOLEAN
DECLARE Index : INTEGER

Found ← FALSE
Index ← 1

INPUT SearchName

WHILE Found = FALSE AND Index <= 10 DO
   IF Names[Index] = SearchName
      THEN
          Found ← TRUE
      ELSE
          Index ← Index + 1
   ENDIF

ENDWHILE

IF Found = TRUE
   THEN
       OUTPUT "Found at position ", Index
   ELSE
       OUTPUT "Not found"
ENDIF
```

**关键点**
- **两个终止条件**：找到了 **OR** 查到头了 —— 两个都要写！
- **`Found` 标志变量（flag）是标准做法**
- 找到时 **Index 停在找到的位置**；没找到时 Index 会变成 11（越界了）—— 但因为你用 `Found` 判断，不会出错

> ⚠️ **常见错误**：只写 `WHILE Found = FALSE DO`，没写 `AND Index <= 10` → 找不到时会**死循环**
> ⚠️ **数组越界**：如果先加 Index 再比较，可能访问到 `Names[11]` 而报错

---

## ② Bubble Sort 冒泡排序

**English（背这句）**
> A **bubble sort** compares **adjacent items** and swaps them if they are in the wrong order. This is repeated until no more swaps are needed.

**原理**：相邻两个比大小，顺序不对就交换；一轮下来最大的会"冒"到最后

```
DECLARE Numbers : ARRAY[1:8] OF INTEGER
DECLARE Temp : INTEGER
DECLARE Swap : BOOLEAN
DECLARE Pass : INTEGER
DECLARE Index : INTEGER

REPEAT
   Swap ← FALSE
   FOR Index ← 1 TO 7
       IF Numbers[Index] > Numbers[Index + 1]
          THEN
              Temp ← Numbers[Index]
              Numbers[Index] ← Numbers[Index + 1]
              Numbers[Index + 1] ← Temp
              Swap ← TRUE
       ENDIF
   NEXT Index

UNTIL Swap = FALSE
```

**关键点（每题必答的）**
1. **循环变量上限是 N − 1**（8 个数的数组只能比 7 次）—— 因为要比 `[Index + 1]`，写到 N 会越界！
2. **交换三个步骤（swap）**：临时变量存第一个 → 第一个改成第二个 → 第二个改成临时变量
3. **`Swap` 标志**：一整轮没发生交换说明已排好，可以提前结束
4. 外层用 **REPEAT...UNTIL**（因为**至少要进行一轮**才能知道是否需要再排）

**升序 vs 降序**
- 升序（从小到大）：`IF Numbers[Index] > Numbers[Index + 1]` ← **大于就交换**
- 降序（从大到小）：`IF Numbers[Index] < Numbers[Index + 1]` ← **小于就交换**

### 另一种等价写法（作业本教的版本）

学校作业本用的是 **`WHILE IsSorted = FALSE` + `EndIndex` 逐轮递减** 的写法 —— **逻辑完全一样**，只是把"外层 REPEAT"换成"WHILE + 布尔标志"，并多加了一个"每轮少比一次"的优化：

```
EndIndex ← N - 1
IsSorted ← FALSE

WHILE IsSorted = FALSE DO
   IsSorted ← TRUE
   FOR Index ← 1 TO EndIndex
       IF Numbers[Index] > Numbers[Index + 1]
          THEN
              // 三步交换
              IsSorted ← FALSE
       ENDIF
   NEXT Index
   EndIndex ← EndIndex - 1
ENDWHILE
```

> ⚠️ **两种写法阅卷都接受**（看逻辑不看形式）。挑一种练熟就行。
> 💡 **`EndIndex` 递减的意义**：每跑完一轮，最后一个元素一定是最大的，下一轮就不用再比它了 —— 减少比较次数。
> ⚠️ 完整可运行版本（含并行数组同步交换）见 [Unit 8 的真题实证 ⑧](Unit%208%20-%20Programming.md)。

> ⚠️ **最常见错误**：`FOR Index ← 1 TO 8` → 当 Index = 8 时访问 `Numbers[9]` → **数组越界**
> ⚠️ **忘记用 Temp 变量**：直接 `A ← B` 然后 `B ← A` 会把两个值都变成 B

### 用 trace table 追踪冒泡排序（超高频）

对 `[3, 1, 2]` 做升序冒泡：

| Pass | Index | Numbers[Index] | Numbers[Index+1] | Swap? | 数组状态 |
|---|---|---|---|---|---|
| 1 | 1 | 3 | 1 | TRUE | [**1, 3**, 2] |
| 1 | 2 | 3 | 2 | TRUE | [1, **2, 3**] |
| — | — | — | — | Swap=TRUE → 再来一轮 | [1, 2, 3] |
| 2 | 1 | 1 | 2 | FALSE | [1, 2, 3] |
| 2 | 2 | 2 | 3 | FALSE | [1, 2, 3] |
| — | — | — | — | Swap=FALSE → 结束 | [1, 2, 3] |

---

## ③ Totalling 求和

**English（背这句）**
> **Totalling** keeps a **running total** by adding each new value to the total so far.

```
Total ← 0                          ← ★ 必须先初始化为 0
FOR Index ← 1 TO 10

   Total ← Total + Numbers[Index]
NEXT Index
```

> ⚠️ **忘了 `Total ← 0`** 是超高频失分点！循环前面**必须有初始化**。
> 💡 更严谨的写法用 `Total ← Total + Number`（单数），因为可能不是从数组读的。

---

## ④ Counting 计数

**English（背这句）**
> **Counting** keeps a **running count** of how many items meet a condition.

```
Count ← 0                          ← ★ 必须先初始化为 0
FOR Index ← 1 TO 10
   IF Numbers[Index] > 50
      THEN
          Count ← Count + 1
   ENDIF
NEXT Index
```

> ⚠️ **注意区分**：
> - `Count ← Count + 1` 是**计数**（加 1）
> - `Total ← Total + Value` 是**求和**（加值）

---

## ⑤ Finding Maximum / Minimum 求最值

**English（背这句）**
> To find the **maximum**, set the maximum to the **first value** and then compare each following value with it, replacing it if the new value is larger.

### ⭐ 关键：初始化成"第一个值"，不是 0！

```
Maximum ← Numbers[1]               ← ★ 不是 0！用第一个元素
FOR Index ← 2 TO 10                ← ★ 从 2 开始，因为 1 已经用过了

   IF Numbers[Index] > Maximum
      THEN
          Maximum ← Numbers[Index]
   ENDIF
NEXT Index
```

> ⚠️⚠️ **为什么不能用 0 初始化**：如果数组全是负数（比如 −5, −8, −3），初始化成 0 会得到错误答案 0。
> **考试就考这个** —— 题目很可能故意给全负数数组。
> ✅ 如果题目**保证是正数**，用 0 也可以；但**用 `Numbers[1]` 永远安全**，写成这样最稳。

**求最小值**：改成 `<` 即可
```
Minimum ← Numbers[1]
FOR Index ← 2 TO 10
   IF Numbers[Index] < Minimum
      THEN
          Minimum ← Numbers[Index]
   ENDIF
NEXT Index
```

### 同时求最大最小值

```
Maximum ← Numbers[1]
Minimum ← Numbers[1]
FOR Index ← 2 TO 10
   IF Numbers[Index] > Maximum
      THEN
          Maximum ← Numbers[Index]
   ENDIF
   IF Numbers[Index] < Minimum
      THEN
          Minimum ← Numbers[Index]
   ENDIF
NEXT Index
```

---

## ⑥ Finding Average 求平均

**English（背这句）**
> The **average** is found by **totalling** all the values and then **dividing** the total by the **number of values**.

```
Total ← 0
FOR Index ← 1 TO 10

   Total ← Total + Numbers[Index]
NEXT Index

Average ← Total / 10               ← ★ 除以个数
OUTPUT "The average is ", Average
```

> ⚠️ **除以的是"个数"不是"最大值"** —— `Total / 10` 不是 `Total / Numbers[10]`
> 💡 如果题目要求四舍五入 → `Average ← ROUND(Total / 10, 2)`
> 💡 小心**整除**：如果 Total 和 Count 都是 INTEGER，某些语言会得到整数结果；伪代码里 `/` 一般返回 REAL，但**保险起见可以 `ROUND` 明确**。

---

## 🔑 六大方法速查表

| 方法 | 初始化 | 循环范围 | 核心语句 |
|---|---|---|---|
| **线性查找** | `Found ← FALSE` | `WHILE Found = FALSE AND Index <= N` | `IF A[Index] = Target` |
| **冒泡排序** | `Swap ← FALSE` | `FOR Index ← 1 TO N-1` | 三步交换 + `Swap ← TRUE` |
| **求和** | `Total ← 0` | `FOR Index ← 1 TO N` | `Total ← Total + A[Index]` |
| **计数** | `Count ← 0` | `FOR Index ← 1 TO N` | `Count ← Count + 1` |
| **最大值** | `Max ← A[1]` | `FOR Index ← 2 TO N` | `IF A[Index] > Max THEN Max ← A[Index]` |
| **最小值** | `Min ← A[1]` | `FOR Index ← 2 TO N` | `IF A[Index] < Min THEN Min ← A[Index]` |

> 🧠 **一句话记忆**：**求和计数初始化 0，查最值初始化第一项，冒泡循环到 N−1，查找要两个终止条件。**

---

# 7.6 验证 — Validation

## 为什么需要验证

**English（背这句）**
> **Validation** is an automatic check performed by the computer to make sure that the data entered is **sensible / reasonable / acceptable**, before it is processed.

> ⚠️ **关键词是 "sensible / reasonable / acceptable"** —— 不是 "correct"！
> 验证**不能保证数据是对的**，只能保证**格式合理**。
> 例：输入生日 `31/02/2000`——格式对（合法日期格式），但日期不存在。验证**查不出来**。

## 七种验证检查（考纲限定）

| 类型 | English | 检查什么 | 例子 |
|---|---|---|---|
| **Range check** | 范围检查 | 值是否在允许的**范围**内 | 分数必须在 0–100 之间 |
| **Length check** | 长度检查 | 数据是否**太长/太短** | 密码至少 8 位；电话号码 11 位 |
| **Type check** | 类型检查 | 数据类型是否**正确** | 年龄字段输入 `"abc"` → 报错 |
| **Presence check** | 存在检查 | 必填字段**是否为空** | 姓名不能留空 |
| **Format check** | 格式检查 | 是否符合规定的**格式/模式** | 日期必须是 `DD/MM/YYYY`；邮编 `CB1 2AB` |
| **Check digit** | 校验位 | 用**算法计算出的额外数字**验证整串数字 | ISBN、条形码、身份证号 |
| **Visual check** | 目视检查 | **人眼**看一遍有没有错 | 手动输入后核对一遍 |

> ⚠️ **Check digit 是唯一"能查出错号"的检查** —— 因为它能检测**输入错误**（比如手抖打错一位）。
> ⚠️ **Range check vs Length check**：范围检查看**数值大小**，长度检查看**字符个数**。

## 🔧 答题模板

**题目**："Give a validation check that could be used for the field 'Age'."

> ✅ *"A **range check** — the age must be between 0 and 120."*
> ✅ *"A **type check** — the age must be an integer."*

**题目**："Explain why validation cannot prevent all errors."

> *"Validation only checks that the data is **sensible / reasonable**, it does not check that the data is **correct**. For example, a range check of 0–100 would accept a mark of 50 even if the student actually scored 60."*

---

# 7.6b 核对 — Verification

## 为什么需要核对

**English（背这句）**
> **Verification** is a check to make sure that the data has been **transferred / entered correctly** — that it **matches the original source**.

> 💡 **记忆对比**：
> - **Validation** = 数据**合理吗**？（机器自动检查）
> - **Verification** = 数据**和原稿一样吗**？（防止转录错误）

## 两种核对检查（考纲限定）

| 类型 | English | 怎么做 |
|---|---|---|
| **Visual check** | 目视核对 | **人眼**把输入的数据和原始文件对比一遍 |
| **Double entry check** | 双重录入核对 | **输入两次**，计算机比较两次是否相同，不同就报错 |

> ⚠️ **Visual check 同时出现在 validation 和 verification 里** —— 因为它是人工检查，既可以看"合不合理"，也可以看"对不对"。
> ⚠️ **双重录入（double entry）是最常考的一种**：比如设密码时输入两次、注册时输入两次邮箱。

## 🔧 答题模板

**题目**："Describe how a double entry check works."

> *"The data is **entered twice** by the user. The computer then **compares the two entries**; if they are **not the same**, an error message is displayed and the user is asked to re-enter the data."*

---

## ⚠️ Validation vs Verification 对比表（必背）

| | **Validation** | **Verification** |
|---|---|---|
| **目的** | 检查数据**是否合理** | 检查数据**是否准确/和原稿一致** |
| **执行者** | 计算机（自动）| 人（或人+机器）|
| **能查什么** | 格式、范围、类型错误 | 转录（抄写）错误 |
| **典型方法** | range / length / type / presence / format / check digit | visual / double entry |
| **例子** | 年龄输 −5 → 报错 | 输入密码两次防打错 |

---

# 7.7 测试数据 — Test Data

**考纲限定四种 —— 这题几乎每张卷子都有，而且很容易做错。**

## 四种测试数据的精确定义

| 类型 | English | 定义 |
|---|---|---|
| **Normal** | 正常数据 | 正常、**会被接受**的数据 |
| **Abnormal** | 异常数据 | 明显**不应该被接受**的数据（错误类型、超范围）|
| **Extreme** | 极值数据 | **可接受范围内**的**最大/最小值** |
| **Boundary** | 边界数据 | 可接受的**最大/最小值** **和** 对应的**刚被拒绝的**值 |

> ⚠️⚠️ **考纲原文的定义必须精确记住**：
> - *"**Extreme data** is the **largest / smallest acceptable value**."*
> - *"**Boundary data** is the **largest / smallest acceptable value** **and the corresponding smallest / largest rejected value**."*

## 举例：分数必须在 0–100 之间（含 0 和 100）

| 类型 | 数据 | 说明 |
|---|---|---|
| **Normal** | `55` | 范围内的普通值 |
| **Abnormal** | `"abc"` 或 `150` | 类型错误 / 超范围 |
| **Extreme** | `0` 和 `100` | **可接受**的最小和最大 |
| **Boundary** | `0`、`100`（接受）+ `-1`、`101`（拒绝）| **接受的最大最小 + 刚被拒绝的** |

> ⚠️ **最经典的失分**：把 `-1` 和 `101` 叫成 "extreme data"。
> ❌ 错：`-1` 和 `101` 是 extreme（因为 extreme 只在**可接受范围内**）
> ✅ 对：`-1` 和 `101` 是 **boundary**（"just rejected" values）
> ⚠️ **Boundary 必须成对**：只写 `0` 和 `100` 得一半分，还要写 `-1` 和 `101`。

## 🔧 答题模板：Suggest suitable test data

**必须写满 4 行，每行都要带类型的名字。**

> | Test data | Type | Reason |
> |---|---|---|
> | `55` | Normal | a typical value within the accepted range |
> | `150` | Abnormal | a value outside the accepted range, should be rejected |
> | `0` | Extreme | the smallest acceptable value |
> | `100` | Extreme | the largest acceptable value |
> | `-1` | Boundary | just below the smallest acceptable value, should be rejected |
> | `101` | Boundary | just above the largest acceptable value, should be rejected |

> 💡 **技巧**：看到"between X and Y"，答案就是 **X、Y（extreme）+ X−1、Y+1（boundary）**。

---

# 7.8 Trace Table — Dry Run

**English（背这句）**
> A **trace table** is used to **dry run** an algorithm, recording the value of each variable at each step to check whether the algorithm works correctly.

## Dry run 是什么
**English（背这句）**
> A **dry run** is working through an algorithm **manually / by hand**, without using a computer.

## 怎么做 trace table（关键技巧）

1. **先建一个表格**：左列写"step / line"，中间写**每一个变量**，最后一列写 **OUTPUT**
2. **从第一行开始，一行一行走**
3. **只记录发生了变化的值**（没变的留空或照抄上一次）
4. **遇到 OUTPUT 就把输出的内容写出来**（这是拿分点！）
5. **循环时要把循环变量每一轮都记下来**

**例子**

```
Total ← 0
FOR Index ← 1 TO 3
   INPUT Number
   Total ← Total + Number
NEXT Index
OUTPUT Total
```
输入依次为 `4`、`5`、`6`

| Step | Index | Number | Total | OUTPUT |
|---|---|---|---|---|
| 1 | | | 0 | |
| 2 | 1 | | | |
| 3 | | 4 | | |
| 4 | | | 4 | |
| 2 | 2 | | | |
| 3 | | 5 | | |
| 4 | | | 9 | |
| 2 | 3 | | | |
| 3 | | 6 | | |
| 4 | | | 15 | |
| 5 | | | | 15 |

## ⚠️ Trace table 的常见失分

| 陷阱 | 正确做法 |
|---|---|
| 只在变量变化时写，其他格留空 | ✅ **可以留空**（表示不变）—— 但**有些考官要求每格都填**，安全做法是把未变的值照抄 |
| **忘了写 OUTPUT 列** | ✅ OUTPUT 是**独立的一列**，必须写 |
| 循环变量没记录 | ✅ `Index` 每一轮的值都要写 |
| 直接写出最终答案 | ✅ 要**一步一步**记录过程，过程本身占分 |
| 数组元素更新时只写整体 | ✅ **数组的每个元素单独一列**（`A[1]`、`A[2]`…），或至少写清 `A[2]` 变了 |

> 💡 **数组在 trace table 里怎么处理**：给数组的**每个被用到的元素**单独开一列，例如 `A[1] | A[2] | A[3]`。

## ⚠️ 循环次数最容易数错（FOR 循环的边界规则）

> - **两端都包含** —— `FOR i ← 1 TO 3` 执行 **3 次**
> - **起点 = 终点** → 执行 **1 次**
> - **起点 > 终点** → 执行 **0 次**（这是最容易忘的！）
> - `STEP -1` 时从大到小

**例**：`FOR Index ← 1 TO 0` 循环体执行 **0 次**，直接跳到循环后面的语句。

---

# 7.9 找错与改错 — Identify and Correct Errors

## 三类错误（考试会问 "State the type of error"）

| 类型 | English | 含义 | 例子 |
|---|---|---|---|
| **Syntax error** | 语法错误 | **语法规则写错了**，程序无法运行 | 忘了 `ENDIF`；写成 `MOD x y` |
| **Logic error** | 逻辑错误 | 语法没问题，但**结果不对** | 用了 `>` 却应该是 `<`；循环上限少 1 |
| **Runtime error** | 运行错误 | 运行时**崩溃** | 除以 0；数组下标越界 |

> 💡 **区分技巧**：
> - 程序**跑不起来** → syntax error
> - 程序**能跑但答案错** → logic error
> - 程序**跑到一半崩了** → runtime error

## 🔧 答题模板（超高频，2 分题）

题目会给一段有错的伪代码，让你"Identify the error and suggest a correction."

**格式（必须两栏都写，只写一个只拿一半分）**

| Error | Correction |
|---|---|
| The loop goes up to 8 but the array only has 8 elements, so `Numbers[9]` is accessed | Change `FOR Index ← 1 TO 8` to `FOR Index ← 1 TO 7` |
| `Total` is not initialised before the loop | Add `Total ← 0` before the `FOR` statement |
| The maximum is initialised to 0 | Initialise `Maximum ← Numbers[1]` and start the loop from 2 |

> ⚠️ **必须引用具体代码**："the loop is wrong" 得 0 分；"the loop should go to 7 not 8" 得满分。
> ⚠️ **Correction 要写成可以直接替换的代码**，不要写"change it to something correct"。

## 常见错误清单（考前扫一眼）

| 错误 | 正确 |
|---|---|
| 求和/计数变量没初始化 | 加 `Total ← 0` / `Count ← 0` |
| 最大值初始化为 0 | 用 `Maximum ← Array[1]` |
| 数组越界（`TO N` 却访问 `[Index+1]`）| 改成 `TO N-1` |
| 用 `=` 做比较和赋值混淆 | 赋值用 `←`，比较用 `=` |
| `REPEAT...UNTIL` 条件写反 | UNTIL 后写**结束**的条件 |
| 循环里忘了递增计数变量 | 加 `Index ← Index + 1` |
| 交换变量时没用临时变量 | 用 `Temp` 三步交换 |
| 过程/函数定义在调用之后 | 定义移到**代码开头** |
| `CALL` 用在函数上 | 函数只能用在表达式里 |
| 字符串比较用了 `=` 却大小写不一致 | 先用 `UCASE()` 统一 |

---

# 7.10 写算法 — Write and Amend Algorithms

## 考试要求

**考纲原文**
> *"**Precision is required** when writing algorithms, e.g. **`x > y`** is acceptable but **`x is greater than y`** is **not** acceptable."*

> ⚠️⚠️ **这是 Paper 2 最容易白白丢分的地方**：**必须用伪代码符号，不能用自然语言描述**！
> ❌ `IF the score is higher than the maximum THEN` → 0 分
> ✅ `IF Score > Maximum THEN` → 得分

**另外两条考纲要求**
> - 要写清**每一步的变量**（variables）
> - 要写清**输出**（outputs）
> - 要写清**用户提示**（user prompts）

## 🔧 答题模板：Write an algorithm for the following problem

**标准结构（按这个顺序写，考官按这个给分）**

```pseudocode
// 1. 声明所有变量/常量/数组
DECLARE Count : INTEGER
DECLARE Total : INTEGER
DECLARE Average : REAL
DECLARE Scores : ARRAY[1:10] OF INTEGER

// 2. 定义过程/函数（如果题目要求）
PROCEDURE DisplayResult(Value : REAL)
   OUTPUT "The average score is ", Value

ENDPROCEDURE

// 3. 初始化
Total ← 0

// 4. 主逻辑：输入 → 处理 → 输出
FOR Count ← 1 TO 10
   OUTPUT "Enter a score"
   INPUT Scores[Count]
   Total ← Total + Scores[Count]
NEXT Count

Average ← Total / 10
CALL DisplayResult(Average)
```

## 📝 拿分要点清单（写的时候对照）

| ✓ | 要点 |
|---|---|
| ☐ | **所有变量都用 DECLARE 声明了**，并且写对了数据类型 |
| ☐ | **数组用 `ARRAY[1:N] OF <type>` 声明**，带上下界 |
| ☐ | **累加/计数变量初始化为 0** |
| ☐ | **循环边界正确**（不越界）|
| ☐ | **每个输入前有 OUTPUT 提示语**（"Enter a score"）|
| ☐ | **用 `←` 而不是 `=`** |
| ☐ | **缩进正确**（4 格；THEN/ELSE 2 格）|
| ☐ | **标识符是 Pascal case 且以大写开头** |
| ☐ | **过程/函数定义在代码开头** |
| ☐ | **算法是"精确的"——没有自然语言句子** |

## ⚠️ 时间分配（Paper 2 = 105 分钟，75 分）

| 部分 | 建议时间 |
|---|---|
| 前面所有小题 | **约 75 分钟** |
| **最后 15 分 scenario 题** | **约 30 分钟**（考纲官方建议）|

> 💡 **考纲原文**：*"It is expected that candidates should spend **30 minutes** answering this question."*

---

# 📊 真题实证（考频与真实题型）

> **数据来源**：June 2026 Paper 22（0478/22）真题原文 · 2015–2025 Paper 2 真题 **65 份 / 1079 题**
> ⚠️ **诚实说明**：我们手上**没有 Paper 2 的官方 mark scheme**，只有题目。
> → 下面标「官方」的是考纲规范明确规定的；标「推断」的是根据规范推出的答案，**不是官方判答案**。

## June 2026 Paper 22 完整拆解（最新一份，共 75 分）

| 题号 | 分值 | 考点 | Unit |
|---|---|---|---|
| Q1 | 1 | 三种循环的识别（选择）| **7 / 8** |
| Q2 | 1 | 数据类型（CHAR）| **8** |
| Q3 | 11 | validation（presence / checksum / format check）+ 写验证伪代码 | **7** |
| Q4 | 6 | PDLC 的 coding 与 testing 阶段 | **7** |
| Q5 | 10 | 2D 数组 + 线性查找：**找 4 个错并改正** + 命名算法 + 补写"未找到" | **7 / 8** |
| Q6 | 7 | **流程图 + trace table** | **7** |
| Q7 | 5 | 文件处理：为什么要用文件 + 写读文件伪代码 | **8** |
| Q8 | 9 | 逻辑门 / 真值表 | Unit 10 |
| Q9 | 10 | 数据库 + SQL | Unit 9 |
| Q10 | **15** | **scenario 题**：全年降雨统计 | **7 / 8** |

---

## 🎯 Unit 7 在 June 2026 的具体考法

### Q1 [1 分] 三种循环的识别
> *"Tick one box to complete the following sentence. Two types of pseudocode statements used for iteration are"*
> A. CASE and IF　B. FOR...NEXT and IF　C. **FOR...NEXT and WHILE...DO...ENDWHILE**　D. REPEAT...UNTIL and CASE

**答案：C**（推断）
> ⚠️ **A 和 D 是干扰项** —— CASE 和 IF 是 **selection** 不是 iteration。**把 IF 和 CASE 当成循环是经典错误**。
> 💡 **三种控制结构必须能一眼分清**：
> - **Sequence** = 顺次执行
> - **Selection** = **IF** / **CASE**
> - **Iteration** = **FOR...NEXT** / **WHILE...DO...ENDWHILE** / **REPEAT...UNTIL**

### Q3 [11 分] Validation 全考一遍
| 小问 | 分值 | 题目原文 / 考法 |
|---|---|---|
| (a)(i) | 1 | *"A check to make sure that data has been input and not left blank."* → **presence check**（推断）|
| (a)(ii) | 1 | *"A value placed at the end of a sequence of numbers in the code. The value is calculated from all the other values before it."* → **checksum**（推断）|
| (b) | 3 | *"Explain the purpose of a format check and give an example of where it could be used."* |
| (c) | **6** | **写伪代码**：逐个数输入，是整数就存进数组，不是就重新输入直到是整数；存满 15 个输出完成消息 |

**Q3(c) 题干原文**
> *Write the pseudocode for an algorithm to perform a validation check on each number as it is input, using the following criteria:*
> - Input one number at a time.
> - If the number is a whole number, store it in the current element of array Accepted[]
> - If the number is not a whole number, ask for it to be input again until it is a whole number.
> - When 15 whole numbers have been stored, output a message that states the check has been completed.
> *Use appropriate input prompts and output messages... **You do not need to declare any arrays or variables for this algorithm.***

> 💡 **命题趋势**：题目**明确说不用声明变量** —— 因为变量声明的分已经给过了，这 6 分全在**逻辑**上。
> ⚠️ 看到这种题，**别浪费时间写 DECLARE**，直接把循环和判断写对。

### Q4 [6 分] PDLC —— 背了就有分
> *"The program development life cycle is split into several stages. **Outline what happens during the coding and testing stages** of the program development life cycle."*

**答题要点（coding 3 分 + testing 3 分）**
| Coding | Testing |
|---|---|
| **writing program code** | **testing the code with test data** |
| **iterative testing** （边写边测）| using **normal / abnormal / extreme / boundary** data |
| following the design | comparing actual output with expected output |
| | finding and correcting errors |

### Q5 [10 分] 找错改错 —— **Paper 2 最典型的送分题**

题干给出的伪代码（原文照录，缩进和错误都是原文的）：
```
01  DECLARE Accounts : ARRAY[1:1000, 1:2] OF STRING
02  DECLARE Row : INTEGER
03  DECLARE AccountID : INTEGER
04  OUTPUT "Please enter an account ID "
05  OUTPUT AccountID
06  FOR Row ← 1 TO 1000
07      CASE OF AccountID = Accounts[Row, 1]
08          THEN
09              OUTPUT "The customer's name is ", Accounts[1, 2]
10          ENDIF
11  NEXT Row
```

**(a) [4 分] "Identify the line numbers of four errors in the pseudocode and suggest corrections."**

**四个错误（推断，非官方答案）**
| 行号 | 错误 | 改正 |
|---|---|---|
| **03** | `AccountID` 声明成 `INTEGER`，但题面说 account ID "contains letters and numbers" | `DECLARE AccountID : STRING` |
| **05** | `OUTPUT AccountID` 应该是输入 | 改成 `INPUT AccountID` |
| **07** | `CASE OF` 用法错误（CASE 不能带 `=` 条件）| 改成 `IF AccountID = Accounts[Row, 1]` |
| **09** | `Accounts[1, 2]` 写死了行号 | 改成 `Accounts[Row, 2]` |

> 💡 **答题格式**：题目问 "line numbers + corrections" → **必须写行号 + 改正代码**，只写一个不给分。
> 💡 **找错的四个方向**（考试就考这几类）：
> 1. **数据类型错**（第 03 行）
> 2. **INPUT / OUTPUT 搞反**（第 05 行）
> 3. **语句用错**（IF / CASE 混用，第 07 行）
> 4. **数组下标写死或写错**（第 09 行）

**(b) [1 分] "State the name given to this type of algorithm."** → **linear search**（推断）

**(c) [5 分] "The algorithm stops if the account number is not found... Write the pseudocode statements to change the algorithm to inform the user that the account number has not been found. Clearly state where in the original algorithm your new statements would be placed. Do not rewrite the whole algorithm."**

**推断答案（加分点）**
1. 在**第 02 行附近**加：`DECLARE Found : BOOLEAN`
2. 在**循环之前**加：`Found ← FALSE`
3. 在第 09 行附近找到时加：`Found ← TRUE`
4. 在 **`NEXT Row` 之后**加：
```
IF Found = FALSE
   THEN
       OUTPUT "Account number not found"
ENDIF
```

> ⚠️ **题目明确说 "Do not rewrite the whole algorithm" + "state where your new statements would be placed"** ——
> **只写新语句 + 写清插入位置**，重抄整段反而浪费时间且可能扣分。

### Q6 [7 分] 流程图 + Trace Table

> 流程图统计一个单词里"**相邻两个字符相同**"的次数，然后问用户是否继续（`Choice = 'Y'`）
> (a) [6] 用输入 `post, Y, committee, N, bookkeeper` 补全 trace table
> (b) [1] State the purpose of the algorithm

**表头**：`Word | WordLength | Count | NumLetter | Choice | OUTPUT`
> ⚠️ 题目给的 **Note: the first character of each word is in position 1** —— 这是**明示下标从 1 开始**。
> ⚠️ **`Choice` 也要记在 trace table 里**（因为 `Y` 和 `N` 会影响流程走向）。
> ⚠️ **OUTPUT 列只在真正输出时才填** —— 中间步骤留空。

### Q10 [15 分] Scenario 题 —— 全年降雨统计

**题干要求（原文摘要）**
> - Initialise the array `Rainfall[]` to zero.
> - Input the rainfall in mm for **each day** (365 days) and store it in the array.
> - Calculate:
>   - the **total** rainfall for the year in **centimetres** (1 cm = 10 mm), **rounded to two decimal places**
>   - the **mean average** daily rainfall in mm, **rounded to four decimal places**
>   - the **total number of days with no rainfall**
>   - the **longest number of consecutive days** with no rainfall
> - **Output all statistics with clear messaging.**
> - If the longest run of dry days is **15 or more**, output a drought message.
> - *"You must use pseudocode or program code and **add comments** to explain how your code works."*
> - *"All arrays, variables or constants used must be **declared**."*
> - *"All inputs and outputs must contain **suitable messages**."*

**这道题的六个给分点（对照检查）**
| # | 给分点 | 怎么写 |
|---|---|---|
| 1 | **数组声明** | `DECLARE Rainfall : ARRAY[1:365] OF REAL` |
| 2 | **数组初始化** | `FOR Day ← 1 TO 365 ... Rainfall[Day] ← 0 ... NEXT Day` |
| 3 | **两次循环**（输入 365 次 + 统计）| 或一次循环里全做 |
| 4 | **单位换算** | `TotalCm ← TotalMm / 10` |
| 5 | **ROUND 两参数** | `ROUND(TotalCm, 2)` 和 `ROUND(Mean, 4)` |
| 6 | **最长连续段** —— 这是**唯一的难点** | 见下方模板 |

**"最长连续无雨天数"的写法（核心难点）**
```
CurrentRun ← 0
LongestRun ← 0
FOR Day ← 1 TO 365
   IF Rainfall[Day] = 0
      THEN
          CurrentRun ← CurrentRun + 1
          IF CurrentRun > LongestRun
             THEN
                 LongestRun ← CurrentRun
          ENDIF
      ELSE
          CurrentRun ← 0                 ← ★ 一旦有雨就归零
   ENDIF
NEXT Day
```

> 💡 **模式**：**连续计数**题永远是"当前计数 + 最长记录"两个变量，遇到"断了"就把当前计数归零。
> ⚠️ 忘了 `CurrentRun ← 0` 是这道题最大的坑。

---

# 📈 历年考频（2015–2025，共 65 份卷子）

> **数据来源**：`ig1525.txt` —— 2015–2025 全部 Paper 2 题目原文，1079 题。
> 统计口径 = **含有该考点的卷子份数 / 65**。NEW = 2023–2025（21 份）· OLD = 2015–2022（44 份）。

## ⚠️ 先看懂这个：2023 年考纲改革把卷子改了

| 时期 | 卷名 | 份数 | 总分 | 结构 |
|---|---|---|---|---|
| 2015–2022 | Problem-solving and Programming | 44 | **50** | **Section A（Q1，20 分）+ Section B（30 分）** |
| 2023–2025 | Algorithms, Programming and Logic | 21 | **75** | **没有 Section A/B**，Q1…Q11 平铺，最后一题固定 15 分 |

> 💡 **这条决定了你该练什么**：
> - 老卷的 **Q1 = 20 分 pre-release scenario 大题**（44/44 份全部成立），是"声明变量 + 写算法 + 验证 + 解释"四段式
> - 新卷把它拆成了 **一道 15 分题 + 一堆 1–4 分的概念小题**（tick / 连线）
> - **你考的是新卷 —— 只做 2023 年及以后的卷子**。老卷的 Section A 题型已作废

## Unit 7 考点频次

| 考点 | ALL / NEW / OLD | 典型分值 | 题干原文 |
|---|---|---|---|
| **trace table 填表** | **61 / 18 / 43** | **4–5**（5 分 22 次、4 分 17 次）| *"Complete the trace table for the input data:"*（这一句在 51 份里逐字出现）|
| **flowchart 流程图题** | **43 / 19 / 24** | 4–6 | *"The flowchart represents an algorithm."* / *"Complete the flowchart for this algorithm."* / *"Describe the purpose of this flowchart."* |
| **找错并改正** | **43 / 20 / 23** | **4**（4 分 25 次；3 分 8 次）| *"Identify the line numbers of the four errors in the pseudocode and suggest a correction for each error."* |
| **validation 验证** | **37 / 15 / 22** | 4 | *"Give a validation check that you can perform on each of these fields. Each validation check must be different."* |
| **test data 测试数据** | **37 / 15 / 22** | **4** | *"Suggest suitable normal, abnormal, extreme and boundary test data to test if this validation check"* |
| **说明算法用途** | 17 / 9 / 8 | **固定 2 分** | *"State the purpose of this pseudocode algorithm."* / *"Describe the purpose of the algorithm."* |
| **PDLC 生命周期** | **10 / 10 / 0** | 1–4 | *"Tick one box to identify the first stage of the program development life cycle."*（**2023 才首次出现**）|
| **verification 核对** | 23 / 10 / 13 | 1 或 3–4 | *"Explain the difference between a validation check and a verification check."* |
| **structure diagram 结构图** | 8 / 6 / 2 | 2–4 | *"Complete the structure diagram for the given parts of the hotel booking system."* |
| **bubble sort 冒泡排序** | **8 / 8 / 0** | 4 | *"Write an algorithm in pseudocode to sort the array Values[1:50] into ascending order using a bubble sort."* |
| **分解 decomposition / 抽象 abstraction** | **6 / 6 / 0** | 1–4 | *"Identify three of the component parts when a problem has been decomposed at the analysis stage."*（**2023 才首次出现**）|
| **linear search 线性查找** | **2 / 2 / 0** | 4 | *"A linear search and a bubble sort are standard methods of solution."*（**全 65 份只被点名 2 次**）|
| **嵌套语句 nested** | **1 / 1 / 0** | — | 全文件仅 2019-23-O/N 提过一次 |

## 🔑 从频次得到的四个硬结论

1. **trace table + flowchart + 找错改错 = 三件套**，合计在新卷约占 **15–20 分**。这三个是"无论如何都会考"的题，必须练到条件反射。
2. **PDLC / decomposition / abstraction 是 2023 年新增**（10 次和 6 次出现**全部在 2023+**）—— 老卷 44 份一次没考过。**只做老卷的人会完全没准备这三块**。
3. **bubble sort 8 次全部在 2023+，linear search 只被点名 2 次**。所以：**冒泡排序必须能默写**；线性查找要会，但别以为它年年考。
4. **"说明算法用途"是固定 2 分题**（9 次 2 分 / 6 次 1 分）—— 送分题，但**答法有格式**，见上面 7.4 的答题模板。

## 📝 高频题干原文（一眼认出题型）

**Trace table**
- `Complete the trace table for the input data:` ← 最经典
- `Complete a trace table for each of the two sets of input data.`
- `Complete the headings for the trace table to show a dry-run for this algorithm.`

**Flowchart**
- `Complete this flowchart for the corrected algorithm:`
- `Identify a problem with this flowchart and explain how to correct it.`
- `Explain how the flowchart can be changed to produce the correct output.`
- `Draw the flowchart symbol for Decision and the flowchart symbol for Process.` ← 纯送分

**Purpose**
- `Identify and describe the function being performed by the algorithm.`

**Errors**
- `Find the four errors in the pseudocode and suggest a correction for each error.`
- `Identify four errors in the flowchart and suggest a correction for each error.` ← **流程图也会出找错题**

**Test data**
- `Name and describe the most appropriate programming data type for each of the examples of data given.`
- `Give two different sets of test data for this algorithm and state the purpose of each set.`

---

## 🧠 Unit 7 的命题规律（65 份卷子 + June 2026 汇总）

| 规律 | 说明 |
|---|---|
| **一道大题往往跨 Unit 7 和 8** | Q5 = 算法设计（找错）+ 编程语法（数组、IF）；Q10 = 两者全考 |
| **validation 年年考** | 而且形式固定：定义匹配 + Explain purpose + 写验证伪代码 |
| **PDLC 是"背了就有分"的题** | 6 分纯记忆，性价比最高；且**是 2023 新增，老卷练习题里练不到** |
| **找错题固定考 4 类错误** | 数据类型 / INPUT-OUTPUT / 语句用错 / 数组下标 |
| **找错题 2024 起要求写行号** | *"Identify the **line numbers** of the four errors"* —— 只写改正不给分 |
| **trace table 表格里一定有 OUTPUT 列** | 忘了就丢分 |
| **15 分 scenario 题一定有"难点子任务"** | 2026 是"最长连续无雨天"，通常要**两个变量 + 归零逻辑** |
| **"不用声明变量"这种话要看清** | 说了就是**真的不用写** —— 省时间 |

---

## ⚠️ 高频失分点汇总

| # | 陷阱 | 正确做法 |
|---|---|---|
| 1 | 用自然语言写算法 | 用伪代码符号（`x > y`）|
| 2 | 求和/计数变量不初始化 | `Total ← 0` / `Count ← 0` |
| 3 | 最大值初始化为 0 | `Maximum ← Array[1]` |
| 4 | 冒泡排序 `FOR Index ← 1 TO N` | `TO N-1`（防止越界）|
| 5 | 线性查找只写一个终止条件 | `Found = FALSE AND Index <= N` |
| 6 | 把 `-1`/`101` 叫 extreme data | 那是 **boundary data** |
| 7 | Boundary 只写接受端的值 | 要写**接受端 + 拒绝端**两对 |
| 8 | 说验证能保证数据正确 | 验证只保证**合理**，不保证**正确** |
| 9 | Validation 和 Verification 搞混 | Validation = 合理性；Verification = 一致性 |
| 10 | Trace table 忘了 OUTPUT 列 | OUTPUT 单独开一列 |
| 11 | FOR 循环边界数错 | 含两端；起>终 → 0 次 |
| 12 | 交换变量不用临时变量 | 用 `Temp` 三步交换 |
| 13 | 题目要 flowchart 却写伪代码 | 按题目要求选工具 |
| 14 | Structure diagram 画了箭头/判断框 | 结构图只有**层次**，没有顺序 |
| 15 | 算法里不写用户提示语 | 每个 INPUT 前加 OUTPUT "Enter..." |
| 16 | 忘了声明变量 | 所有变量先 DECLARE |
| 17 | 用编程语言语法（`for i in range`）| 用官方伪代码 `FOR i ← 1 TO n` |
| 18 | 在非 scenario 题里写 Python/Java | **写编程语言代码不得分** |

---

## 🧠 一页纸速记

```
PDLC  = Analysis → Design → Coding → Testing
        (abstraction 去细节 / decomposition 拆小块)

设计工具 = Structure diagram（层次，无箭头）
           Flowchart（有菱形判断，Yes/No 出口）
           Pseudocode（符号语言，不能写"x is greater than y"）

算法目的 = Inputs → Processes → Outputs → Storage

六大方法：
  线性查找  WHILE Found=FALSE AND Index<=N
  冒泡排序  REPEAT ... FOR Index←1 TO N-1 ... UNTIL Swap=FALSE
  求和      Total←0   Total←Total+A[i]
  计数      Count←0   Count←Count+1
  最值      Max←A[1]  FOR i←2 TO N
  平均      Total / 个数

Validation（合理）: range / length / type / presence / format / check digit
Verification（一致）: visual check / double entry check

测试数据：
  Normal    正常值
  Abnormal  明显错误值
  Extreme   可接受范围的最大/最小   ← "inside"
  Boundary  可接受的最大最小 + 刚被拒绝的  ← "inside + outside"

Trace table：每个变量一列，OUTPUT 单独一列，循环变量每轮都记

错误类型：Syntax（跑不起来）/ Logic（跑得起来结果错）/ Runtime（中途崩）
```

---

## 🔗 延伸资源

**本地资源**
- 伪代码完整语法 → [Pseudocode Reference.md](Pseudocode%20Reference.md)
- 历年题型与频率 → 见上方 **📊 真题实证**
- 下一单元 → [Unit 8 - Programming](Unit%208%20-%20Programming.md)

**在线题库**
- [Cambridge IGCSE Computer Science 0478 Past Papers](https://www.cambridgeinternational.org/programmes-and-qualifications/cambridge-igcse-computer-science-0478/past-papers/)
- [Save My Exams — IGCSE Computer Science](https://www.savemyexams.com/igcse/computer-science/)
- [Physics and Maths Tutor — Computer Science](https://www.physicsandmathstutor.com/computer-science-revision/igcse/)

---

**上一单元**：[Unit 6 - Automated and emerging technologies](Unit%206%20-%20Automated%20and%20emerging%20technologies.md)
**下一单元**：[Unit 8 - Programming](Unit%208%20-%20Programming.md)
