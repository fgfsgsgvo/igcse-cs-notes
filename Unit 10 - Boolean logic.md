# Unit 10 - Boolean logic

> **Paper 2 · Topic 10**　布尔逻辑是 Paper 2 里**最像“数学题”的单元**：规则少、题型固定、画图/真值表都能练。核心是六个逻辑门、真值表、逻辑表达式和逻辑电路之间的**四种互相转换**。

---

# 10.1 逻辑门 — Logic Gates

## 10.1.1 什么是逻辑门

**English（背这句）**
> A **logic gate** is a hardware component that takes one or more binary inputs and produces a single binary output, based on a **Boolean function**.

**中文理解**：逻辑门是数字电路的基本元件。输入和输出都只有 **0 / 1**（低/高电平）。考试只考 **6 种门**，而且除 NOT 外都**只有两个输入**。

## 10.1.2 六种逻辑门总表

| Gate | 名称 | 输入数 | 功能（一句话） | Boolean expression |
|---|---|---|---|---|
| **NOT** | 非门 | **1** | 输出与输入相反 | `NOT A` |
| **AND** | 与门 | 2 | **两个都为 1** 才输出 1 | `A AND B` |
| **OR** | 或门 | 2 | **至少一个为 1** 就输出 1 | `A OR B` |
| **NAND** | 与非门 | 2 | AND 的输出再取反 | `NOT (A AND B)` |
| **NOR** | 或非门 | 2 | OR 的输出再取反 | `NOT (A OR B)` |
| **XOR** | 异或门 | 2 | **两个输入不同**时输出 1 | `A XOR B` |

> ⚠️ **NOT 只有一个输入**；其余五个都是**两个输入**。画电路时不要给 NOT 画两个输入。
> ⚠️ **NAND / NOR 不是“先取反再 AND/OR”**，而是“先 AND/OR 再取反”；顺序不要搞反。

## 10.1.3 符号形状（考试要认）

| Gate | 符号特征 | 记忆 |
|---|---|---|
| **NOT** | 三角形 + 输出端一个小圆圈 | 三角尖朝输出，圆圈表示“取反” |
| **AND** | **D 形**（左边平直，右边半圆） | 平直输入边 + 圆头输出 |
| **OR** | 左边**弧形**，右边尖 | 弧形输入边 |
| **NAND** | **AND 形 + 输出小圆圈** | D 形带泡泡 |
| **NOR** | **OR 形 + 输出小圆圈** | 弧形带泡泡 |
| **XOR** | **OR 形 + 输入端多一条弧线** | “exclusive OR”，弧形输入边多一条线 |

> 💡 小圆圈（bubble）= **NOT / 取反**。看到输出端有圆圈，就是 NAND 或 NOR。
> 💡 XOR 和 OR 的区别：XOR 的输入边有**两条弧线**（或一条额外的弧线），OR 只有一条。

## 10.1.4 六个真值表（必须背）

### NOT
| A | NOT A |
|---|---|
| 0 | 1 |
| 1 | 0 |

### AND
| A | B | A AND B |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | **1** |

### OR
| A | B | A OR B |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | **1** |
| 1 | 0 | **1** |
| 1 | 1 | **1** |

### NAND
| A | B | A NAND B |
|---|---|---|
| 0 | 0 | **1** |
| 0 | 1 | **1** |
| 1 | 0 | **1** |
| 1 | 1 | 0 |

### NOR
| A | B | A NOR B |
|---|---|---|
| 0 | 0 | **1** |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |

### XOR
| A | B | A XOR B |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | **1** |
| 1 | 0 | **1** |
| 1 | 1 | 0 |

> ⚠️ **XOR 的口诀**：**不同为 1，相同为 0**。
> ⚠️ **NAND / NOR 的口诀**：先算 AND / OR，再把结果**全部取反**。

---

# 10.2 逻辑表达式 — Boolean Expressions

## 10.2.1 三种写法

0478 考试常用**关键字**写法；有些教材/题目也会用符号写法。两种都要认识。

| 运算 | 关键字写法 | 符号写法 | 备注 |
|---|---|---|---|
| NOT | `NOT A` | `¬A` 或 `A'` | 单输入 |
| AND | `A AND B` | `A · B` 或 `AB` | 两个都为 1 |
| OR | `A OR B` | `A + B` | 至少一个为 1 |
| NAND | `NOT (A AND B)` | `¬(A · B)` | AND 后取反 |
| NOR | `NOT (A OR B)` | `¬(A + B)` | OR 后取反 |
| XOR | `A XOR B` | `A ⊕ B` | 不同为 1 |

> ⚠️ **括号决定运算顺序**。`NOT A AND B` 通常理解为 `(NOT A) AND B`；如果不确定，**多加括号**最安全。
> ⚠️ 0478 的题目通常直接写 `AND` / `OR` / `NOT` / `XOR`，按题目给的记号写即可。

## 10.2.2 运算优先级

从高到低：

1. **NOT**（括号内先算）
2. **AND**
3. **OR / XOR**

**例子**：
```
NOT A AND B OR C
= ((NOT A) AND B) OR C
```

> 💡 不确定时加括号，阅卷不会因为括号多而扣分。

## 10.2.3 从文字描述写表达式

| 题目说法 | 逻辑关系 | 表达式 |
|---|---|---|
| “A **and** B must both be true” | AND | `A AND B` |
| “**either** A **or** B” | OR | `A OR B` |
| “A must **not** be true” | NOT | `NOT A` |
| “**either** A **or** B, **but not both**” | XOR | `A XOR B` |
| “**not both** A and B” | NAND | `NOT (A AND B)` |
| “**neither** A **nor** B” | NOR | `NOT (A OR B)` |
| “A and B, **but not** C” | AND + NOT | `A AND B AND (NOT C)` |

**例子 1**：
> “The alarm sounds if the door is open **or** the window is open, **and** the system is armed.”

```
Alarm = (DoorOpen OR WindowOpen) AND Armed
```

**例子 2**：
> “The fan turns on if the temperature is high **and** the switch is on, **or** if the manual override is on.”

```
Fan = (TempHigh AND SwitchOn) OR ManualOverride
```

**例子 3**：
> “The light is on if exactly one of the two switches is on.”

```
Light = A XOR B
```

> ⚠️ “exactly one” / “but not both” 是 **XOR** 的信号词。
> ⚠️ “neither … nor …” 是 **NOR** 的信号词。

---

# 10.3 真值表 — Truth Tables

## 10.3.1 怎么列输入组合

| 输入数 | 行数 | 顺序 |
|---|---|---|
| 1 | 2 | 0, 1 |
| 2 | 4 | 00, 01, 10, 11 |
| 3 | **8** | 000, 001, 010, 011, 100, 101, 110, 111 |

> ⚠️ **n 个输入 → 2ⁿ 行**。3 个输入必须写 **8 行**，少一行就丢分。
> 💡 推荐按**二进制计数顺序**写，不容易漏组合。

## 10.3.2 从逻辑表达式列真值表

**步骤**：
1. 列出所有输入组合
2. 先算括号内
3. 再算 NOT
4. 再算 AND
5. 最后算 OR / XOR
6. 把中间结果也写成列（方便检查，也方便拿过程分）

**例子**：`Q = (A AND B) OR (NOT C)`

| A | B | C | A AND B | NOT C | Q |
|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 1 | **1** |
| 0 | 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 1 | **1** |
| 0 | 1 | 1 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 | **1** |
| 1 | 0 | 1 | 0 | 0 | 0 |
| 1 | 1 | 0 | 1 | 1 | **1** |
| 1 | 1 | 1 | 1 | 0 | **1** |

> 💡 中间列（`A AND B`、`NOT C`）不是必须，但强烈建议写；既方便检查，也能让阅卷老师看到你的思路。

## 10.3.3 从逻辑电路列真值表

**步骤**：
1. 给每个门的输出起一个中间变量名（如 X、Y）
2. 按信号从左到右的顺序，逐列计算
3. 最后算输出列
4. 检查行数是否 = 2ⁿ

**例子**：电路 = `NOT (A AND B)`（即 NAND）

| A | B | A AND B | NOT (A AND B) |
|---|---|---|---|
| 0 | 0 | 0 | **1** |
| 0 | 1 | 0 | **1** |
| 1 | 0 | 0 | **1** |
| 1 | 1 | 1 | 0 |

## 10.3.4 从真值表写表达式

**方法：看输出为 1 的行，写“乘积项之和”（sum of products）**

对每一行输出为 1 的记录：
- 输入为 **1** → 写变量本身（如 `A`）
- 输入为 **0** → 写 `NOT 变量`（如 `NOT A`）
- 把这些条件用 **AND** 连起来
- 最后把所有行用 **OR** 连起来

**例子 1**：

| A | B | Q |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

输出为 1 的行：
- `A=0, B=1` → `(NOT A) AND B`
- `A=1, B=0` → `A AND (NOT B)`

所以：
```
Q = ((NOT A) AND B) OR (A AND NOT B)
```
这正是 **XOR**。

**例子 2**：

| A | B | Q |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |

只有 `A=0, B=0` 输出 1：
```
Q = (NOT A) AND (NOT B)
```
它其实等价于 **NOR**（`NOT (A OR B)`），因为两者真值表完全相同；题目没要求简化时，按 1 行写出的表达式即可。

> ⚠️ 题目说 "without simplification" 时，**不要化简**；按真值表直接写出的表达式即使冗长也给分。
> ⚠️ 如果输出为 1 的行很多，也可以看输出为 0 的行，写反表达式；但初学建议统一用“1 行写乘积项之和”。

---

# 10.4 逻辑电路 — Logic Circuits

## 10.4.1 画电路的规则

1. **NOT 一个输入**；AND/OR/NAND/NOR/XOR **两个输入**
2. 输入画在左边，输出画在右边
3. 按表达式**从左到右**画：先画括号内，再画外面的门
4. 每个门标清楚；输入标 A、B、C，输出标 Q
5. **不要简化**，题目要求“from the expression”就照表达式画
6. 电路最多 **3 个输入、1 个输出**（考纲限制）

## 10.4.2 从表达式画电路

**例子**：`Q = (A AND B) OR (NOT C)`

画法：
1. 画一个 **AND** 门，输入 A、B → 输出 X
2. 画一个 **NOT** 门，输入 C → 输出 Y
3. 画一个 **OR** 门，输入 X、Y → 输出 Q

```
A ──┐
    AND ── X ──┐
B ──┘           │
                OR ── Q
C ── NOT ── Y ──┘
```

> ⚠️ 先画最内层括号，再把结果接到外层门。不要一上来就画最外面的 OR。

**例子**：`Q = NOT (A OR B)`（NOR）
1. 画 **OR** 门，输入 A、B → 输出 X
2. 画 **NOT** 门，输入 X → 输出 Q

```
A ──┐
    OR ── X ── NOT ── Q
B ──┘
```

## 10.4.3 从电路写表达式

**步骤**：
1. 从最左边的门开始，给每个门输出起名
2. 写出每个门的表达式
3. 把中间变量代入下一级
4. 得到最终表达式

**例子**：

```
A ──┐
    AND ── X ──┐
B ──┘           │
                OR ── Q
C ──────────────┘
```

- `X = A AND B`
- `Q = X OR C`

代入：
```
Q = (A AND B) OR C
```

> ⚠️ 不要漏括号；`A AND B OR C` 有歧义，写成 `(A AND B) OR C` 更清楚。

## 10.4.4 从问题描述画电路

**步骤**：
1. 找出所有输入（传感器/开关/条件）
2. 找出输出
3. 把描述拆成 “AND / OR / NOT / XOR” 关系
4. 写表达式
5. 按表达式画电路

**例子**：
> “A security light turns on if the motion sensor detects movement **and** it is dark, **or** if the manual switch is on.”

- 输入：`Motion`、`Dark`、`Manual`
- 输出：`Light`
- 表达式：`Light = (Motion AND Dark) OR Manual`
- 电路：AND(Motion, Dark) → OR(..., Manual) → Light

## 10.4.5 从真值表画电路

**步骤**：
1. 从真值表写出表达式（看输出为 1 的行）
2. 按表达式画电路
3. 如果题目要求“from truth table”且不要求简化，直接照写出的表达式画

**例子**：

| A | B | Q |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

输出为 1 的行：01、10、11
```
Q = ((NOT A) AND B) OR (A AND (NOT B)) OR (A AND B)
```
电路按这个表达式画（即使它其实等价于 `A OR B`，题目没要求简化就不要化简）。

> 💡 如果题目明确说 "simplify"，才可以把 `A OR B` 写出来；否则按原式画。

---

# 10.5 常见题型与答题模板

## 10.5.1 题型 1：识别门 / 写名称

> "Name the logic gate that outputs 1 only when both inputs are 1."

**答案**：AND gate.

> "Name the logic gate that outputs 1 when the inputs are different."

**答案**：XOR gate.

**口诀**：
- both / all → AND
- either / at least one → OR
- not / inverted → NOT
- not both → NAND
- neither / nor → NOR
- different / exactly one → XOR

## 10.5.2 题型 2：补全真值表

**给分点**：
- 输入组合齐全（2ⁿ 行）
- 中间列正确
- 输出列正确

> ⚠️ 3 输入只写 4 行是**最常见的失分**。

## 10.5.3 题型 3：从表达式画电路

**给分点**：
- 门的类型正确
- 输入连接正确
- 门的数量/顺序正确
- 输出标清楚

> ⚠️ 题目说 "without simplification" 就不要化简；化简后可能和答案电路不一致。

## 10.5.4 题型 4：从电路写表达式

**给分点**：
- 每个门的表达式正确
- 中间变量代入正确
- 括号正确

> ⚠️ 先写中间变量，再代入，不要心算跳步。

## 10.5.5 题型 5：从真值表写表达式/画电路

**给分点**：
- 找出输出为 1 的行
- 每行写对乘积项（0 → NOT，1 → 原变量）
- 用 OR 连接
- 按表达式画电路

---

# 10.6 高频失分点

| 失分点 | 正确做法 |
|---|---|
| NOT 画成两个输入 | NOT 只有 **1 个输入** |
| NAND / NOR 顺序搞反 | 先 AND/OR，再取反 |
| XOR 和 OR 混淆 | XOR：不同为 1；OR：有 1 就 1 |
| 真值表行数不够 | n 个输入写 **2ⁿ 行** |
| 输入组合漏写/重复 | 按 000,001,010… 顺序写 |
| 表达式漏括号 | `(A AND B) OR C` 不要写成 `A AND B OR C` |
| 电路化简了但题目没要求 | 题目说 "without simplification" 就照原式画 |
| 从真值表写表达式时 0/1 写反 | 输出为 1 的行：输入 1 → 原变量，输入 0 → NOT |
| 画电路时输入线交叉混乱 | 输入放左、输出放右，门从左到右排 |

---

# 10.7 一页纸速记

```
Six gates:
  NOT  1 input   output opposite
  AND  2 inputs  both 1 → 1
  OR   2 inputs  at least one 1 → 1
  NAND 2 inputs  NOT (A AND B)
  NOR  2 inputs  NOT (A OR B)
  XOR  2 inputs  different → 1

Truth table rows:
  1 input  → 2
  2 inputs → 4
  3 inputs → 8

From expression to circuit:
  brackets first → NOT → AND → OR → output

From truth table to expression:
  rows with output 1
  input 1 → variable
  input 0 → NOT variable
  AND within a row, OR between rows

Signal words:
  both / all          → AND
  either / at least   → OR
  not both            → NAND
  neither / nor       → NOR
  different / exactly one → XOR
```

---

# 10.8 真题实证与练习方向

> 学校资料：`Past Exam Papers/Questions by Unit/Unit 10 - Boolean logic (154 pts)/` 有 **Question Paper + Answer Key**，共 29 页、154 分。

**高频题型排序**：
1. **真值表补全/绘制** —— 几乎每套都有
2. **从表达式/描述画电路** —— 高频
3. **从电路写表达式** —— 高频
4. **识别逻辑门** —— 1 分送分题
5. **从真值表写表达式/画电路** —— 稍难，但有固定套路

**练习建议**：
- 每个门的真值表默写一遍，直到不看笔记也能写
- 3 输入真值表至少练 5 道，确保 8 行不漏
- 画电路时用铅笔，先画括号内，再画外层
- 做完后把电路反推成表达式，检查是否和题目一致

---

**上一单元** ← [Unit 9 - Databases](Unit%209%20-%20Databases.md)
**下一单元** → [Pseudocode Reference](Pseudocode%20Reference.md)
