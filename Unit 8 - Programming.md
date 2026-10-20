# Unit 8 — Programming 程序设计

> **考纲**：0478/0984 · Topic 8
> **试卷**：Paper 2 — Algorithms, Programming and Logic
> **分值**：Paper 2 = **75 分 / 1 小时 45 分 / 占总成绩 50%**
> **计算器：不允许**
> **本单元特点**：Unit 8 是**Paper 2 分值最大、最拉分**的单元，也是唯一"必须动手写"的单元。
> 前面 Unit 7 教你**怎么想**，Unit 8 教你**怎么写**。两者的分在一道题里通常连着给。
> ⚠️ **必须用官方伪代码作答**，写 Python/Java 语法**不给分**（唯一例外见下）。
> 📖 逐条语法 → [Pseudocode Reference.md](Pseudocode%20Reference.md)（**这份文件是本单元的字典，边做边查**）

---

## 📋 考纲对照清单

| ✓ | 考纲点 | 内容 | 在笔记里 |
|---|---|---|---|
| ☐ | 8.1.1 | 声明和使用变量与常量 | [↓](#811-变量与常量--variables-and-constants) |
| ☐ | 8.1.2 | 基本数据类型：integer / real / char / string / Boolean | [↓](#812-数据类型--data-types) |
| ☐ | 8.1.3 | 输入与输出 | [↓](#813-输入输出--input-and-output) |
| ☐ | 8.1.4 (a) | **顺序** sequence | [↓](#814a-顺序--sequence) |
| ☐ | 8.1.4 (b) | **选择** selection（IF / CASE）| [↓](#814b-选择--selection) |
| ☐ | 8.1.4 (c) | **迭代** iteration（计数控制 / 前置 / 后置）| [↓](#814c-迭代--iteration) |
| ☐ | 8.1.4 (d) | **求和与计数** totalling and counting | [↓](#814d-求和与计数--totalling-and-counting) |
| ☐ | 8.1.4 (e) | **字符串处理** length / substring / upper / lower | [↓](#814e-字符串处理--string-handling) |
| ☐ | 8.1.4 (f) | 算术、逻辑、布尔运算符 | [↓](#814f-运算符--operators) |
| ☐ | 8.1.5 | 嵌套语句（**最多三层**）| [↓](#815-嵌套语句--nested-statements) |
| ☐ | 8.1.6 | 过程、函数、参数（**最多两个参数**）| [↓](#816-过程与函数--procedures-and-functions) |
| ☐ | 8.1.6 (c) | 局部变量与全局变量 | [↓](#816c-局部变量与全局变量--local-and-global-variables) |
| ☐ | 8.1.7 | 库例程 MOD / DIV / ROUND / RANDOM | [↓](#817-库例程--library-routines) |
| ☐ | 8.1.8 | 可维护的程序 | [↓](#818-可维护的程序--maintainable-programs) |
| ☐ | 8.2.1 | 声明并使用 1D 和 2D 数组 | [↓](#821-数组--arrays) |
| ☐ | 8.2.2 | 理解数组的用途 | [↓](#821-数组--arrays) |
| ☐ | 8.2.3 | 用迭代向数组写入/读取值 | [↓](#82-3-用迭代操作数组--using-iteration-with-arrays) |
| ☐ | 8.3.1 | 把数据存进文件供程序使用的目的 | [↓](#831-为什么要用文件--purpose-of-file-storage) |
| ☐ | 8.3.2 | 打开、关闭并对文件进行读写 | [↓](#832-文件操作--open-close-read-write) |

---

# 8.1 变量与常量 — Variables and Constants

## 变量 Variable

**English（背这句）**
> A **variable** is a named **store / location in memory** whose **value can change** while the program is running.

**四个要点（答 Define 题时挑相关的写）**
1. It has a **name / identifier**
2. It holds a **value**
3. The value is stored in a **memory location**
4. The value **can change** during execution

## 常量 Constant

**English（背这句）**
> A **constant** is a named value that **cannot change** while the program is running.

> ⚠️ **考纲硬性规定：常量的值只能是字面量（literal）**
> *"Only literals can be used as the value of a constant. A variable, another constant or an expression must never be used."*
> ✅ `CONSTANT HourlyRate ← 6.50`
> ❌ `CONSTANT Tax ← BaseRate * 2`（含表达式）
> ❌ `CONSTANT Limit ← MaxValue`（引用了变量）

## 🔧 为什么用常量？（高频 2–4 分题）

**English（背这句）**
> Using constants makes the program **more readable** and **easier to maintain / update**, because the value only needs to be changed in **one place** and it cannot be changed accidentally while the program is running.

**分点答（每点 1 分）**
| 理由 | English |
|---|---|
| 更易读 | It makes the program **more readable** / easier to understand |
| 更易改 | If the value changes, it only needs updating in **one place** |
| 防误改 | The value **cannot be changed accidentally** while the program runs |
| 防错 | It reduces the risk of **typing errors** if the value is used many times |
| 有意义的名字 | A meaningful identifier explains what the number means |

> 💡 **典型例子**：税率、最大学生数、π、每小时的工资率 —— 这些"不变但会改"的值就该用常量。

---

# 8.1.2 数据类型 — Data Types

**五种，必须能背定义 + 举例 + 能判断什么时候用哪个。**

| 类型 | English 定义 | 例子 | 占多少字节 |
|---|---|---|---|
| **INTEGER** | a **whole number** (positive or negative) | `42`、`-7`、`0` | 通常 4 |
| **REAL** | a number with a **fractional part / decimal point** | `3.14`、`-0.5`、`2.0` | 通常 8 |
| **CHAR** | a **single character** | `'A'`、`'7'`、`'@'` | 通常 1 |
| **STRING** | **zero or more characters** | `"Hello"`、`""` | 每字符 1 |
| **BOOLEAN** | one of two values: **TRUE or FALSE** | `TRUE` | 通常 1 |

## ⚠️ 选错类型就丢分（判断题常见）

| 数据 | 正确类型 | 为什么会错 |
|---|---|---|
| 年龄 | **INTEGER** | 没人 15.5 岁（除非题目要求）|
| 价格 | **REAL** | 有小数 |
| 姓名 | **STRING** | 多个字符 |
| 性别 | **CHAR** | 单字符 `'M'` / `'F'` |
| 是否会员 | **BOOLEAN** | 只有 是/否 |
| 电话号码 | **STRING** | ★ 不参与计算，且**可能有前导零**或 `+` 号 |
| 邮编 | **STRING** | 含字母和空格 |
| 学生人数 | **INTEGER** | 人数是整数 |
| 平均分 | **REAL** | 除法会产生小数 |

> ⚠️⚠️ **电话号码 / 邮编 / 身份证号必须是 STRING 不是 INTEGER** —— 这是经典考点：
> - 前导零会丢失（`01234` → `1234`）
> - 含字母/空格/`+` 的存不成数字
> - 不需要做数学运算

> ⚠️ **CHAR 用单引号 `'A'`，STRING 用双引号 `"A"`** —— 这是伪代码的硬规定。
> ⚠️ **BOOLEAN 只有 TRUE / FALSE** —— 不要写 `0` / `1`（那是别的语言）。

## 🔧 答题模板

**题目**："State a suitable data type for each of the following."
**格式**：一行一个，**直接写类型名**，不要写句子。

> - StudentName : **STRING**
> - NumberOfStudents : **INTEGER**
> - AverageMark : **REAL**
> - IsRegistered : **BOOLEAN**
> - Initial : **CHAR**

---

# 8.1.3 输入输出 — Input and Output

```
INPUT <identifier>
OUTPUT <value(s)>
```

```
INPUT StudentName
OUTPUT "Hello ", StudentName
OUTPUT "Your score is ", Score, " out of ", MaxScore
```

## 规则
- `INPUT` 后面**只能跟变量**（因为要把输入存进去）
- `OUTPUT` 后面可以跟**变量、字面量、多个用逗号分隔的值**
- **字符串要加引号**，变量不加

## ⚠️ 陷阱

| 错误 | 正确 |
|---|---|
| `INPUT "Enter your name"` | ❌ 不能给 INPUT 加提示语字符串 → 应写成 `OUTPUT "Enter your name"` 然后 `INPUT Name` |
| `OUTPUT StudentName` 但想显示引号 | 要显示引号就写 `OUTPUT "\"", StudentName, "\""`（一般不会考）|
| `INPUT Name, Age` | ❌ 一行只输入一个变量（要分行写）|

> ⚠️ **用户提示语（user prompt）是拿分点**：考纲明确要求算法里要写清楚 *"user prompts"*。
> 每次 `INPUT` 前面都要有 `OUTPUT "Enter ..."`。

---

# 8.1.4 (a) 顺序 — Sequence

**English（背这句）**
> **Sequence** means that the statements are executed **one after another, in the order they are written**.

> 💡 顺序是三种基本控制结构里最简单的一种 —— 没有判断、没有循环，从上到下一条条执行。
> **考点**：三种控制结构是 **sequence / selection / iteration**，必须能说出名字和区别。

---

# 8.1.4 (b) 选择 — Selection

## 两种选择结构

| 结构 | 什么时候用 |
|---|---|
| **IF** | 条件是**范围/比较**的时候；分支多的时候也可以嵌套 |
| **CASE** | 条件是**一组具体的值**的时候（尤其是单字符菜单）|

> ⚠️ **IF 和 CASE 是 selection，不是 iteration** —— iteration 只有 `FOR` / `WHILE` / `REPEAT` 三种。

## IF 语句

```
IF <condition>
   THEN
       <statements>
   ELSE
       <statements>
ENDIF
```

**三种形态**
| 形态 | 写法 |
|---|---|
| 单分支 | `IF...THEN...ENDIF`（无 ELSE）|
| 双分支 | `IF...THEN...ELSE...ENDIF` |
| 多分支 | 嵌套 IF（最多三层）|

> ⚠️ **THEN 和 ELSE 只缩进 2 格**（考纲硬规定，见 [Pseudocode Reference](Pseudocode%20Reference.md)）
> ⚠️ **`IF` 里必须有 `THEN`** —— 漏掉是经典语法错误

## CASE 语句

```
CASE OF <identifier>
   <value 1> : <statement>
   <value 2> : <statement>
   OTHERWISE <statement>
ENDCASE
```

**什么时候必须用 CASE 而不能用 IF**
> ✅ 当**同一个变量的多个离散值**要分别处理时
> ✅ 尤其是**单字符菜单**（`'A'` / `'B'` / `'C'` / `'Q'`）

```
INPUT Choice
CASE OF Choice
   'A' : CALL AddRecord
   'D' : CALL DeleteRecord
   'S' : CALL ShowRecords
   'Q' : OUTPUT "Goodbye"
   OTHERWISE OUTPUT "Invalid choice"
ENDCASE
```

## ⚠️ CASE 的三条硬规则（考点）

1. **按顺序测试**：找到匹配的就执行并跳出，**后面的 case 不再测试**
2. **OTHERWISE 必须放最后**，前面的都不匹配才执行
3. 每个分支**只写一条语句**、每个 case **只用单个值**；复杂了就该用 IF

> ⚠️ **考点**：*"Explain why a CASE statement is more suitable than an IF statement"*
> → **CASE is more readable / easier to understand when comparing one variable against many different values.**

> 💡 **考纲外但阅卷接受的扩展用法**（历年试卷答案里出现过，可用来简化答案）：
> - **逗号列表**：`0, 1 : OUTPUT "..."`（两个值走同一分支）
> - **范围**：`'A' TO 'Z' : OUTPUT "uppercase"`
> - **`OTHERWISE` 后不加冒号** —— 规范示例是 `OTHERWISE OUTPUT "Beep"`（没冒号），但两种写法都见过
>
> ⚠️ 但**官方规范的建议仍是"每个 case 单个值"** —— 如果题目明确要求按规范写，就用单个值。

---

# 8.1.4 (c) 迭代 — Iteration

**三种循环，必须能"看题目选循环"。**

| 循环 | 类型 | 判断时机 | 最少次数 | 什么时候用 |
|---|---|---|---|---|
| **FOR** | count-controlled 计数控制 | 循环开始前就知道次数 | 0 或 1 | **次数已知/固定** |
| **WHILE** | pre-condition 前置条件 | **循环体之前**判断 | **0 次** | 次数**未知**，可能一次都不做 |
| **REPEAT** | post-condition 后置条件 | **循环体之后**判断 | **1 次** | **至少要执行一次** |

## FOR 循环

```
FOR <identifier> ← <value1> TO <value2>

   <statements>
NEXT <identifier>
```
带步长：
```
FOR <identifier> ← <value1> TO <value2> STEP <increment>

   <statements>
NEXT <identifier>
```

> ⚠️ **四个硬规则（trace table/循环次数题必考）**
> - **两端都包含**
> - **value1 = value2 → 执行 1 次**
> - **value1 > value2 → 执行 0 次**（★ 最容易忘）
> - 循环变量必须是 **INTEGER**
> - ⚠️ **`STEP` 的值必须求值为整数** —— 写 `FOR x ← 0 TO 1 STEP 0.01` **违反规范**（有教材这么写，别照抄）。步长为负时可以，越过 value2 就结束。

## WHILE 循环（前置条件）

```
WHILE <condition> DO

   <statements>
ENDWHILE
```
> - 条件为 **TRUE** 才执行
> - 第一次判断就是 FALSE → **一次都不执行**
> - 条件变为 **FALSE** 时终止

## REPEAT 循环（后置条件）

```
REPEAT

   <statements>
UNTIL <condition>
```
> - **至少执行一次**
> - 条件为 **TRUE** 时**终止**（★ 最容易搞反）

## 🔧 怎么选？看题目关键词

| 题目说 | 用 |
|---|---|
| "for each of the 10 students" / "repeat 5 times" | **FOR** |
| "until the user enters ..." / "**at least once**" / 输入验证 | **REPEAT** |
| "while there are still ..." / "**as long as**" / 可能一次都不做 | **WHILE** |

## 🔧 经典用途：输入验证（REPEAT 的标准场景）

```
REPEAT
   OUTPUT "Enter a mark between 0 and 100"
   INPUT Mark

UNTIL Mark >= 0 AND Mark <= 100
```

> 💡 **为什么必须用 REPEAT 而不是 WHILE**：因为**至少要问一次**，WHILE 有可能一次都不问。

## 🔧 经典用途：重复输入直到有效 + 存入数组

**场景**：只要有效值，无效就重问；收满 N 个有效值后停止。

```
Count ← 0
REPEAT
   OUTPUT "Enter a value"
   INPUT Value

   IF <validation passes>
      THEN
          Count ← Count + 1
          Accepted[Count] ← Value
      ELSE
          OUTPUT "Invalid - please try again"
   ENDIF

UNTIL Count = 15

OUTPUT "Done"
```

> ⚠️ **计数器只在值通过验证、真正存进数组时才 +1** —— 放进 ELSE 分支就永远存不满。
> 💡 判定整数：`MOD(Value, 1) = 0`；`DIV(Value, 1) = Value`、`ROUND(Value, 0) = Value` 等价。
> 💡 题目说 "do not declare variables" 就**不要写 `DECLARE`**。

## 🔧 经典用途：读文件（WHILE 的标准场景）

```
WHILE NOT EOF("data.txt") DO
   READFILE "data.txt", Line
   OUTPUT Line

ENDWHILE
```

> ⚠️ **循环变量在循环体内被改动 = 危险信号**
> 如果 `FOR` 循环里改了循环变量（比如 `FOR i ← 1 TO 10` 里面写 `i ← i + 1`），会导致**跳过值或提前结束** —— 这是改错题的常客。

---

# 8.1.4 (d) 求和与计数 — Totalling and Counting

（方法本身见 [Unit 7 - 标准解题方法](Unit%207%20-%20Algorithm%20design%20and%20problem%20solving.md#75-标准解题方法--standard-methods-of-solution)，这里讲编程实现要点）

## 求和 Totalling

```
Total ← 0                          ← ★ 必须在循环外初始化
FOR Index ← 1 TO 10

   Total ← Total + Numbers[Index]
NEXT Index
```

## 计数 Counting

```
Count ← 0                          ← ★ 必须在循环外初始化
FOR Index ← 1 TO 10
   IF Numbers[Index] > 50
      THEN
          Count ← Count + 1
   ENDIF
NEXT Index
```

## 同时求和 + 计数（算平均数）

```
Total ← 0
Count ← 0
FOR Index ← 1 TO 10
   IF Numbers[Index] > 50
      THEN
          Total ← Total + Numbers[Index]      ← 求和
          Count ← Count + 1                   ← 计数
   ENDIF
NEXT Index

IF Count > 0
   THEN
       Average ← Total / Count                ← ★ 除以 Count 而不是 10！
   ELSE
       OUTPUT "No values to average"
ENDIF
```

> ⚠️⚠️ **除以 `Count` 不是除以数组长度** —— 如果只对满足条件的值求平均，分母是**计数结果**。
> ⚠️ **防止除以 0**：如果 `Count = 0` 会运行错误，所以要加 `IF Count > 0` 保护。

## 常见的多条件计数

```
Count ← 0
FOR Index ← 1 TO 10
   IF Numbers[Index] > 50 AND Numbers[Index] < 80
      THEN
          Count ← Count + 1
   ENDIF
NEXT Index
```

---

# 8.1.4 (e) 字符串处理 — String Handling

**考纲限定四个：length / substring / upper / lower**

| 函数 | 作用 | 返回值类型 |
|---|---|---|
| `LENGTH(<string>)` | 字符串的**字符个数** | INTEGER |
| `SUBSTRING(<string>, <start>, <length>)` | 从 start 开始取 length 个字符 | STRING |
| `UCASE(<string>)` | 全部转**大写** | STRING |
| `LCASE(<string>)` | 全部转**小写** | STRING |

```
LENGTH("Computer")                  returns 8
SUBSTRING("Computer", 1, 4)         returns "Comp"
SUBSTRING("Computer", 5, 4)         returns "uter"
UCASE("Computer")                   returns "COMPUTER"
LCASE("Computer")                   returns "computer"
```

## ⚠️⚠️ SUBSTRING 的下标问题（超高频）

> **考纲原文**：*"The first character of the string can be position **zero or one**."*
> **但官方伪代码规范用 1**：*"Generally, a start position of **1** is the first character in the string."*
> ✅ **考试一律按 1 来数**（除非题目明确说从 0 开始）。

**三个参数是 `(字符串, 起始位置, 长度)`**
- 不是 `(字符串, 起始位置, 结束位置)`！
- `SUBSTRING(s, 5, 4)` = 从第 5 个字符开始，取 **4 个**字符 → 第 5、6、7、8 位

## 🔧 实用技巧（考试常考）

| 想做的事 | 怎么写 |
|---|---|
| 取第一个字符 | `SUBSTRING(Name, 1, 1)` |
| 取最后一个字符 | `SUBSTRING(Name, LENGTH(Name), 1)` |
| 取前 3 个字符（首字母缩写）| `SUBSTRING(Name, 1, 3)` |
| 去掉第一个字符 | `SUBSTRING(Name, 2, LENGTH(Name) - 1)` |
| 不区分大小写地比较 | `IF UCASE(Answer) = "YES" THEN` |
| 逐个字符处理 | `FOR i ← 1 TO LENGTH(Word)` … `SUBSTRING(Word, i, 1)` |

## 🔧 字符串逐个字符处理的通用模板

```
DECLARE Word : STRING
DECLARE Letter : CHAR
DECLARE Count : INTEGER
DECLARE Index : INTEGER

INPUT Word
Count ← 0

FOR Index ← 1 TO LENGTH(Word)
   Letter ← SUBSTRING(Word, Index, 1)
   IF Letter = 'a' OR Letter = 'e' OR Letter = 'i' OR Letter = 'o' OR Letter = 'u'
      THEN
          Count ← Count + 1
   ENDIF
NEXT Index

OUTPUT "There are ", Count, " vowels"
```

> ⚠️ **`LENGTH()` 在 FOR 循环里是允许的**，但更严谨的写法是先存起来：
> `WordLength ← LENGTH(Word)` 然后 `FOR Index ← 1 TO WordLength`

## ⚠️ 字符串连接（concatenation）—— 0478 里**没有**专门的运算符

> ⚠️ **`&` 和 `+` 都不是 0478 考纲里的语法** —— 网上教程常用 `&`，那是 **A-Level (9618) 的习惯**。写成 `FullName ← FirstName & " " & LastName` 在 0478 里**没有依据**。

**✅ 0478 推荐做法：用 `OUTPUT` 的逗号分隔**
```
OUTPUT "Hello ", FirstName, " ", LastName
```

> 逗号会把多个输出项依次显示，不需要先拼成一个字符串。

**⚠️ 如果题目坚持要求把拼接结果存进变量**
> 0478 伪代码**没有官方的字符串拼接运算符**。不要写 `FullName ← LastName`（这只是复制，不是拼接），也不要写 `FullName ← FirstName & LastName`。优先把答案改写成 `OUTPUT` 逗号分隔；若老师明确教过某种写法，按老师要求，但要知道它不属于 0478 规范。

---

## 🔑 字符串函数速查（考纲限定只有这四个）

| 想做的事 | 写法 |
|---|---|
| 取长度 | `LENGTH(s)` |
| 取一段 | `SUBSTRING(s, 起始, 长度)` |
| 转大写 | `UCASE(s)` |
| 转小写 | `LCASE(s)` |
| 取首字符 | `SUBSTRING(s, 1, 1)` |
| 取末字符 | `SUBSTRING(s, LENGTH(s), 1)` |

> ⚠️ **没有 `LEFT` / `RIGHT` / `MID` / `TO_UPPER` / `TO_LOWER`** —— 那些是别的语言。

---

# 8.1.4 (f) 运算符 — Operators

## 三类运算符（考纲限定，必须全背）

### ① 算术运算符 Arithmetic

| 符号 | 含义 |
|---|---|
| `+` | 加 |
| `-` | 减 |
| `*` | 乘 |
| `/` | 除 |
| `^` | 乘方（raised to the power of）|

### ② 逻辑（比较）运算符 Logical / Comparison

| 符号 | 含义 | ⚠️ |
|---|---|---|
| `=` | 等于 | |
| `<` | 小于 | |
| `<=` | 小于或等于 | |
| `>` | 大于 | |
| `>=` | 大于或等于 | |
| `<>` | **不等于** | ★ 不是 `!=` |

> 结果**永远是 BOOLEAN**（TRUE / FALSE）

### ③ 布尔运算符 Boolean

**只有三个：`AND`、`OR`、`NOT`**（没有 XOR、没有 `&&`、没有 `||`）

## ⚠️ 运算符优先级

| 优先级 | 运算符 |
|---|---|
| 1（最高）| `^`、括号 `( )` |
| 2 | `*`、`/` |
| 3 | `+`、`-` |
| 4 | `=` `<` `<=` `>` `>=` `<>` |
| 5（最低）| `NOT` → `AND` → `OR` |

> 💡 **不确定就加括号** —— 加括号永远不扣分，算错才扣分。

## ⚠️ 高频陷阱

| 陷阱 | 说明 |
|---|---|
| 用 `!=` | 用 **`<>`** |
| 用 `&&` / `||` | 用 **`AND`** / **`OR`** |
| 用 `%` / `//` | 用 **`MOD(a,b)`** / **`DIV(a,b)`**（函数形式）|
| `AND` 和 `OR` 搞混 | `AND` = 两个都要满足；`OR` = 满足一个就行 |
| `NOT` 双重否定读不懂 | `NOT (A > B)` = `A <= B` |
| `2 ^ 3` 以为是 2×3 | 是 **2³ = 8** |

### 🔧 区间判断怎么写（高频）

| 想表达 | 写法 |
|---|---|
| 0 ≤ x ≤ 100 | `x >= 0 AND x <= 100` |
| x 在 0 到 100 之外 | `x < 0 OR x > 100` |
| x 不等于 0 且不等于 1 | `x <> 0 AND x <> 1` |

> ⚠️ **不能写 `0 <= x <= 100`** —— 伪代码不支持链式比较，必须用 `AND` 连接。

### 🔧 用 AND / OR / NOT 改写（真值表题）

| 表达式 | 等价写法 |
|---|---|
| `NOT (A = B)` | `A <> B` |
| `NOT (A > B)` | `A <= B` |
| `NOT (A AND B)` | `NOT A OR NOT B`（德摩根定律）|
| `NOT (A OR B)` | `NOT A AND NOT B`（德摩根定律）|

---

# 8.1.5 嵌套语句 — Nested Statements

**English（背这句）**
> A **nested statement** is a statement that is placed **inside another statement** of the same or a different type.

**常见嵌套**
- IF 里面套 IF（多重条件）
- IF 里面套 FOR（遍历时筛选）
- FOR 里面套 FOR（二维数组）
- FOR 里面套 IF 里面套 IF

> ⚠️ **考纲硬限制：不超过三层**
> *"Candidates will not be required to write more than **three levels** of nested statements."*
> → 你写的答案**最多三层缩进**就够了；超过三层要么是题目超纲，要么是你想复杂了。

## 🔧 判断怎么写更清晰（避免嵌套太深）

**❌ 深嵌套（难读）**
```
IF Age >= 18
   THEN
       IF HasTicket = TRUE
          THEN
              IF Paid = TRUE
                 THEN
                     OUTPUT "Entry allowed"
              ENDIF
          ENDIF
   ENDIF
ENDIF
```

**✅ 用 AND 合并（更清晰）**
```
IF Age >= 18 AND HasTicket = TRUE AND Paid = TRUE
   THEN
       OUTPUT "Entry allowed"
ENDIF
```

**✅ 用 OR 提前处理异常**
```
IF Age < 18 OR HasTicket = FALSE OR Paid = FALSE
   THEN
       OUTPUT "Entry denied"
   ELSE
       OUTPUT "Entry allowed"
ENDIF
```

> 💡 **答题技巧**：能用 `AND`/`OR` 合并的，就别嵌套 —— **可读性也是得分点**（见 8.1.8）。

---

# 8.1.6 过程与函数 — Procedures and Functions

## 核心区别（**必考**）

| | **PROCEDURE** | **FUNCTION** |
|---|---|---|
| 返回值 | ❌ 无 | ✅ **返回一个值** |
| 定义时 | 无返回类型 | 必须写 **`RETURNS <type>`** |
| 调用方式 | `CALL MyProc(...)` | **用在表达式里** |
| 能否单独一行 | ✅ 可以 | ❌ **不可以** |
| 有 `RETURN` 吗 | ❌ 没有 | ✅ 有 |

**English（背这句）**
> A **procedure** is a named block of code that performs a task but **does not return a value**.
> A **function** is a named block of code that **performs a task and returns a value**.

## 语法

### 过程
```
PROCEDURE <identifier>(<param1>:<datatype>, <param2>:<datatype>)

   <statements>
ENDPROCEDURE
```
```
CALL <identifier>(Value1, Value2)
```

### 函数
```
FUNCTION <identifier>(<param1>:<datatype>, ...) RETURNS <data type>

   <statements>
   RETURN <value>
ENDFUNCTION
```
```
Result ← <identifier>(Value1, Value2)
```

## ⚠️⚠️ 最容易失分的三点

1. **函数不能用 `CALL`！**
   > 考纲原文：*"function calls are **not complete program statements**. The keyword **CALL should not be used** when calling a function."*
   > ❌ `CALL SumSquare(10, 20)` → 0 分
   > ✅ `Result ← SumSquare(10, 20)`

2. **`RETURN` 通常是函数体的最后一条语句**，而且**必须返回值**

3. **参数最多两个**
   > 考纲原文：*"Procedures and functions may have up to **two parameters**."*

## 参数 Parameters

**English（背这句）**
> **Parameters** are the values that are **passed into** a procedure or function so that it can use them.

**为什么要用参数**（答题点）
- 让同一个过程/函数可以**处理不同的数据**（reusable 可重用）
- **不用**把数据存到全局变量里 → 更安全
- 让代码**更通用、更易维护**

**参数的类型必须匹配**：如果定义了 `(Size : INTEGER)`，传字符串进去就是错的。

## 🔧 什么时候用过程、什么时候用函数？

| 情况 | 用 |
|---|---|
| 只是**做一件事**（显示、保存、画图）| **PROCEDURE** |
| **需要拿一个结果回来**（计算、判断）| **FUNCTION** |
| 结果要**打印出来** | PROCEDURE（可以直接 `OUTPUT`）|
| 结果要**继续参与运算** | FUNCTION |

## 🔧 完整范例

```pseudocode
// ---- 函数：返回两个数的平方和 ----
FUNCTION SumSquare(Number1 : INTEGER, Number2 : INTEGER) RETURNS INTEGER
   RETURN Number1 * Number1 + Number2 * Number2

ENDFUNCTION

// ---- 函数：返回较大值 ----
FUNCTION MaxValue(Value1 : INTEGER, Value2 : INTEGER) RETURNS INTEGER
   IF Value1 > Value2
      THEN
          RETURN Value1
      ELSE
          RETURN Value2
   ENDIF

ENDFUNCTION

// ---- 过程：显示一行星号 ----
PROCEDURE DisplayLine(Size : INTEGER)
   DECLARE Count : INTEGER
   FOR Count ← 1 TO Size
       OUTPUT "*"
   NEXT Count

ENDPROCEDURE

// ---- 主程序 ----
DECLARE Answer : INTEGER
DECLARE Higher : INTEGER

Answer ← SumSquare(10, 20)                 ← 函数用在表达式里
Higher ← MaxValue(5, 12)
OUTPUT "The sum of squares is ", Answer
OUTPUT "The higher value is ", Higher
CALL DisplayLine(30)                       ← 过程用 CALL
```

> ⚠️ **注意 `MaxValue` 函数里两个分支都有 `RETURN`** —— 必须保证**所有路径都返回值**，否则是逻辑错误。

**布尔函数（BOOLEAN return）**

```
FUNCTION IsLuckyNumber(Num : INTEGER) RETURNS BOOLEAN
   IF Num = 7 OR Num = 4
      THEN
          RETURN TRUE
   ENDIF
   RETURN FALSE
ENDFUNCTION

FUNCTION IsEven(Num : INTEGER) RETURNS BOOLEAN
   RETURN MOD(Num, 2) = 0
ENDFUNCTION
```

> ⚠️ 函数头是 `RETURNS`（复数），函数体是 `RETURN`（单数）。
> ⚠️ **所有路径都要有返回值**：`RETURN FALSE` 必须放在 IF 外面，否则 `Num = 5` 时没有返回值。
> ✅ 函数用在表达式里：`OUTPUT IsLuckyNumber(7)`；❌ 不能写 `CALL IsLuckyNumber(7)`。

## ⚠️ 过程/函数为什么好（高频 Explain 题）

**English（背这句）**
> Using procedures and functions makes the program **more readable**, **easier to debug** and **easier to maintain**. The **same code can be reused** without being written out again, which **reduces the length of the program** and **reduces the chance of errors**.

**分点（每点 1 分）**
| 好处 | English |
|---|---|
| 可重用 | The code can be **reused** several times |
| 更短 | It **reduces the length** of the program |
| 更易读 | It makes the program **easier to understand** |
| 更易调试 | It is **easier to test / debug** each part separately |
| 更易维护 | A change only needs to be made in **one place** |
| 分工 | Different programmers can work on **different procedures** |

---

# 8.1.6 (c) 局部变量与全局变量 — Local and Global Variables

## 定义

| | **Global variable** | **Local variable** |
|---|---|---|
| 声明位置 | **所有过程/函数之外** | **过程/函数之内** |
| 谁能访问 | **整个程序**都能访问 | **只有该过程/函数**能访问 |
| 生命周期 | 程序运行期间一直存在 | 过程/函数结束时**被销毁** |

**English（背这句）**
> A **global variable** is declared **outside** all procedures and functions and can be accessed and changed by **any part** of the program.
> A **local variable** is declared **inside** a procedure or function and can only be used **within that procedure or function**.

## 🔧 为什么优先用局部变量（高频 Explain 题）

**English（背这句）**
> Local variables should be used wherever possible because they **cannot be changed by other parts of the program**, which **reduces the risk of errors**. They also **free up memory** when the procedure or function ends.

**分点**
| 理由 | English |
|---|---|
| 防冲突 | It avoids **naming conflicts** between different procedures |
| 防误改 | The variable **cannot be changed by another part** of the program |
| 好调试 | It is **easier to find errors** because the variable is only used in one place |
| 省内存 | The memory is **released** when the procedure ends |
| 可重用 | The procedure can be **reused** without side effects |

## ⚠️ 陷阱

| 陷阱 | 说明 |
|---|---|
| 在过程里用全局变量当参数 | 那是**坏习惯**，应该用参数传进去 |
| 局部变量和全局变量**同名** | ★ 局部会**遮蔽（shadow）**全局 —— 过程里改的是局部那个，全局不变！这是很阴的考点 |
| 以为局部变量在过程外还能用 | ❌ 过程一结束就没了 |

## 🔧 判断下面的代码输出什么（经典题）

```pseudocode
DECLARE Value : INTEGER        // 全局

PROCEDURE Change()
   DECLARE Value : INTEGER     // 局部，遮蔽了全局
   Value ← 100
ENDPROCEDURE

Value ← 5
CALL Change()
OUTPUT Value                   // 输出 5，不是 100！
```
> ⚠️ **因为过程里的 `Value` 是一个新的局部变量**，改它不会影响全局的 `Value`。
> 如果把过程里的 `DECLARE Value` 删掉，那改的就是全局，输出就变成 **100**。

---

# 8.1.7 库例程 — Library Routines

**English（背这句）**
> **Library routines** are sets of pre-written / built-in functions that can be used by a program without the programmer having to write the code.

**考纲限定四个：MOD、DIV、ROUND、RANDOM**

| 例程 | 作用 | 返回 |
|---|---|---|
| `MOD(a, b)` | 返回 a 除以 b 的**余数** | INTEGER |
| `DIV(a, b)` | 返回 a 除以 b 的**商**，舍去小数 | INTEGER |
| `ROUND(x, places)` | 把 x 四舍五入到 places 位小数 | REAL |
| `RANDOM()` | 返回 0 到 1 之间（含）的随机数 | REAL |

```
MOD(10, 3)          returns 1
DIV(10, 3)          returns 3
ROUND(3.14159, 2)   returns 3.14
ROUND(2.5, 0)       returns 3
RANDOM()            returns e.g. 0.7241
```

## ⚠️⚠️ MOD 和 DIV 是**函数**不是运算符

> 这是**最好认的"照 Python/VB 习惯写就丢分"点**！
> | 语言 | 取余 | 取整商 |
> |---|---|---|
> | Python | `%` | `//` |
> | Visual Basic | `Mod` | `\` |
> | **0478 伪代码** | **`MOD(a, b)`** | **`DIV(a, b)`** |
> ❌ `10 MOD 3` → ✅ `MOD(10, 3)`

## 🔧 MOD 的三大用途（超高频）

### ① 判断奇偶
```
IF MOD(Number, 2) = 0
   THEN
       OUTPUT "Even"
   ELSE
       OUTPUT "Odd"
ENDIF
```
> 💡 **`MOD(x, 2) = 0` 就是"偶数"的标准写法**，必背。

### ② 判断整除
```
IF MOD(Number, 5) = 0 THEN OUTPUT "Divisible by 5"
```

### ③ 循环中每 N 次做一件事
```
FOR Index ← 1 TO 100
   OUTPUT Numbers[Index]
   IF MOD(Index, 10) = 0
      THEN
          OUTPUT "----"          // 每 10 个输出一条分隔线
   ENDIF
NEXT Index
```

## 🔧 DIV 的用途

```
DIV(100, 60)      returns 1        // 100 分钟 = 1 小时
DIV(Seconds, 3600)                 // 秒转小时
DIV(TotalPence, 100)               // 便士转英镑
```
配合 MOD 做**单位转换**：
```
Hours   ← DIV(TotalMinutes, 60)
Minutes ← MOD(TotalMinutes, 60)
```

## 🔧 ROUND 的用途与陷阱

```
Average ← ROUND(Total / Count, 2)          // 保留 2 位小数
WholeNumber ← ROUND(RANDOM() * 6, 0)       // 0 到 6 的整数
```

> ⚠️ **ROUND 的第二个参数是"小数位数"**，不是"有效数字"。
> ⚠️ **`ROUND(x, 0)` 就是取整**。

## 🔧 RANDOM 的用途：生成指定范围

> ⚠️ **`RANDOM()` 只返回 0 到 1 之间的小数**，不能直接生成你要的范围。必须**缩放 + 平移**。

**公式：`ROUND(RANDOM() * (max - min), 0) + min`**

| 想要 | 写法 |
|---|---|
| 0–6 之间的整数 | `ROUND(RANDOM() * 6, 0)` |
| **1–6（骰子）** | `ROUND(RANDOM() * 5, 0) + 1` |
| 1–100 | `ROUND(RANDOM() * 99, 0) + 1` |
| 10–20 | `ROUND(RANDOM() * 10, 0) + 10` |

> ⚠️ **骰子题的经典错误**：写成 `ROUND(RANDOM() * 6, 0)` → 会得到 **0 到 6**（7 种结果），骰子只能是 1 到 6。

---

# 8.1.8 可维护的程序 — Maintainable Programs

**English（背这句）**
> A **maintainable** program is one that is **easy to understand, modify and update** by another programmer at a later date.

**考纲给的四个要素**
1. **Meaningful identifiers** 有意义的标识符
2. **Commenting** 注释
3. **Procedures and functions** 过程与函数（模块化）
4. **Appropriate commenting of syntax** 恰当注释语法

## ① Meaningful identifiers（有意义的名字）

| ❌ 差 | ✅ 好 |
|---|---|
| `x` | `StudentAge` |
| `arr1` | `StudentNames` |
| `t` | `TotalScore` |
| `n` | `NumberOfPlayers` |
| `Total_Score` | `TotalScore`（★ 不能有下划线）|

> 💡 **例外**：`i`、`j`（数组下标）和 `X`、`Y`（坐标）是**约定俗成**的，可以用。
> 💡 **命名技巧**：用 Pascal case，名字要**说明它是什么**，不是它是什么类型。

## ② Comments（注释）

```
// This function calculates the average
// of all the values in the array
FUNCTION CalculateAverage(Values : ARRAY[1:10] OF INTEGER) RETURNS REAL
   DECLARE Index : INTEGER
   DECLARE Total : INTEGER
   Total ← 0
   FOR Index ← 1 TO 10
       Total ← Total + Values[Index]       // add each value to the total
   NEXT Index
   RETURN Total / 10
ENDFUNCTION
```

> ⚠️ **注释的规则**（考纲原文）：
> - 用 `//`，到行尾结束
> - **多行注释每一行都要写 `//`**
> - 惯例放在被注释代码的**上一行**，**保持相同缩进**
> - 短注释可以跟在语句**行尾**

**🔧 注释该写什么？**
| ✅ 该写 | ❌ 别写 |
|---|---|
| 这段代码**为什么**这么做 | `// adds 1 to i`（废话）|
| 变量的**含义/单位** | `// this is an integer` |
| 复杂逻辑的**思路** | 把代码逐行翻译一遍 |
| 过程/函数的**用途**和**参数含义** | |

## ③ Procedures and functions（模块化）

把功能拆成过程/函数 → 主程序变短、可读、可重用（详见 [8.1.6](#816-过程与函数--procedures-and-functions)）

## 🔧 答题模板：Explain why the use of meaningful identifiers / comments makes a program more maintainable

> *"Meaningful identifiers / comments make the program **easier to understand** for another programmer. This means it is **easier to debug** and **easier to modify / update** the program at a later date, because the programmer can quickly see what each part of the code does."*

## ⚠️ 与 Unit 7 的关联

> Paper 2 里"可维护性"题经常和 Unit 7 的**分解**连起来考：
> **Decomposition → 拆成子程序 → 每个子程序用有意义的名字 + 注释 → 可维护**

---

# 8.2.1 数组 — Arrays

## 什么是数组

**English（背这句）**
> An **array** is a **data structure** that stores **multiple values of the same data type** under **one identifier**. Each value is accessed using an **index**.

**为什么用数组**（答题点）
- 用一个名字存**一组**数据，不用声明几十个变量
- 可以用**循环**批量处理
- 可以用**下标（index）**直接访问任意一个元素

## 一维数组 1D Array

**声明**
```
DECLARE <identifier> : ARRAY[<lower>:<upper>] OF <data type>
```
```
DECLARE StudentNames : ARRAY[1:30] OF STRING
DECLARE Scores : ARRAY[1:10] OF INTEGER
```

**使用**
```
Scores[1] ← 95
OUTPUT Scores[5]
Scores[Index] ← Scores[Index] + 1
```

## 二维数组 2D Array

**声明**
```
DECLARE <identifier> : ARRAY[<l1>:<u1>, <l2>:<u2>] OF <data type>
```
```
DECLARE Seats : ARRAY[1:5, 1:10] OF BOOLEAN
DECLARE Grid : ARRAY[1:3, 1:3] OF CHAR
```
> 💡 **二维数组可以想成"表格"**：第一个下标 = **行**，第二个下标 = **列**。
> `Seats[3, 7]` = 第 3 行第 7 列

**使用**
```
Seats[2, 5] ← TRUE
Grid[1, 1] ← 'X'
```

## ⚠️⚠️ 数组的三条硬规则

1. **必须显式写出下界** —— `ARRAY[1:30]` 不是 `ARRAY[30]`
   > 考纲原文：*"It is good practice to explicitly state what the lower bound of the array is because this **defaults to either 0 or 1 in different systems**. Generally, a lower bound of **1** will be used."*

2. **每个维度只用一个下标值，用逗号分隔**
   > ❌ `Grid[2][3]` → ✅ `Grid[2, 3]`

3. **下标可以用变量**（这是循环遍历数组的基础）
   > ✅ `Scores[Index]`、`Scores[Index + 1]`

## 🔧 数组的初始化（必须有）

```
FOR Index ← 1 TO 30

   StudentNames[Index] ← ""
NEXT Index
```

二维：
```
FOR Row ← 1 TO 5
   FOR Column ← 1 TO 10

       Seats[Row, Column] ← FALSE
   NEXT Column
NEXT Row
```

> ⚠️ **为什么必须初始化**：数组声明后里面可能是**垃圾值（残留数据）**，不初始化直接读会得到错误结果。

---

# 8.2.3 用迭代操作数组 — Using Iteration with Arrays

## ① 读入数据

```
FOR Index ← 1 TO 30
   OUTPUT "Enter student name ", Index
   INPUT StudentNames[Index]
NEXT Index
```

## ② 输出数据

```
FOR Index ← 1 TO 30
   OUTPUT StudentNames[Index]
NEXT Index
```

## ③ 处理数据（例：求和）

```
Total ← 0
FOR Index ← 1 TO 30
   Total ← Total + Scores[Index]
NEXT Index
```

## ④ 二维数组（嵌套循环）

```
Total ← 0
FOR Row ← 1 TO 5

   RowTotal ← 0
   FOR Column ← 1 TO 10

       RowTotal ← RowTotal + Values[Row, Column]
   NEXT Column
   OUTPUT "Total for row ", Row, " is ", RowTotal
   Total ← Total + RowTotal
NEXT Row

OUTPUT "The grand total is ", Total
```

> ⚠️ **嵌套循环的经典陷阱**：**累加变量初始化在循环外还是内？**
> - `Total`（总和）→ 初始化在**最外层外**
> - `RowTotal`（每行的和）→ 初始化在**外层循环内、内层循环外**（每一行都要重新归零）

## ⑤ 数组里存最大值/最小值

```
Highest ← Scores[1]
HighestName ← StudentNames[1]

FOR Index ← 2 TO 30
   IF Scores[Index] > Highest
      THEN
          Highest ← Scores[Index]
          HighestName ← StudentNames[Index]        ← ★ 别忘了同时更新对应的名字！
   ENDIF
NEXT Index
```

> ⚠️ **如果题目要"最高分的学生名字"**，你必须**同时**更新分数和名字 —— 只更新分数是常见失分。

## ⑦ 一趟遍历同时求 min / max / sum / mean

```
Min ← Nums[1]
Max ← Nums[1]
Sum ← 0

FOR Index ← 1 TO N
   Sum ← Sum + Nums[Index]
   IF Nums[Index] < Min THEN Min ← Nums[Index] ENDIF
   IF Nums[Index] > Max THEN Max ← Nums[Index] ENDIF
NEXT Index

Mean ← Sum / N
```

> ⚠️ **`Sum ← 0` 不能漏**；Min/Max 用**第一个元素**初始化，不要用 0。
> 💡 循环从 1 开始时，`Nums[1]` 会和自己比较一次，结果不受影响。

## ⑥ 数组的查找

```
Found ← FALSE
Index ← 1
WHILE Found = FALSE AND Index <= 30 DO
   IF StudentNames[Index] = SearchName
      THEN
          Found ← TRUE
      ELSE
          Index ← Index + 1
   ENDIF

ENDWHILE
```

## ⚠️ 数组相关的高频失分点

| # | 陷阱 | 正确 |
|---|---|---|
| 1 | `FOR Index ← 1 TO 30` 但访问 `[Index + 1]` | 改成 `TO 29` |
| 2 | 数组没初始化 | 循环赋初值 |
| 3 | 二维数组用 `[Row][Column]` | `[Row, Column]` |
| 4 | 只写 `ARRAY[30]` | `ARRAY[1:30]` |
| 5 | 每行的累加变量没重置 | 在内层循环前 `RowTotal ← 0` |
| 6 | 求最高分时忘了更新对应的名字 | 两个变量一起更新 |
| 7 | 下标从 0 开始写（伪代码默认 1）| 用 1 起（题目说了就按题目）|

---

# 8.3.1 为什么要用文件 — Purpose of File Storage

**English（背这句）**
> Storing data in a file allows the data to be **kept permanently / saved** so that it can be **used again by the program** at a later time, even after the program has been closed or the computer has been turned off.

**关键对比（高频）**

| | **变量/数组** | **文件** |
|---|---|---|
| 存储位置 | 内存（RAM）| 硬盘/固态盘（secondary storage）|
| 断电后 | **丢失** | **保留** |
| 速度 | 快 | 慢 |
| 容量 | 小 | 大 |
| 用途 | 程序运行时临时存 | **长期保存** |

**分点答（每点 1 分）**
| 理由 | English |
|---|---|
| 永久保存 | The data is stored **permanently** (not lost when the program closes)|
| 可重复使用 | The data can be **reused** the next time the program runs |
| 便于传输 | The file can be **transferred** to another computer / program |
| 数据量大 | Files can store **more data** than can be held in memory at once |
| 便于备份 | The file can be **backed up** |

---

# 8.3.2 文件操作 — Open, Close, Read, Write

## 四条命令（必须全背）

```
OPENFILE <File identifier> FOR <File mode>
READFILE <File identifier>, <Variable>
WRITEFILE <File identifier>, <Variable>
CLOSEFILE <File identifier>
```

| 模式 | 含义 | ⚠️ |
|---|---|---|
| **READ** | 从文件读数据 | 文件必须已存在 |
| **WRITE** | 往文件写数据 | ★ **会创建新文件，原文件里的数据全部丢失** |

## ⚠️⚠️ 三条铁规

1. **WRITE 模式会毁掉原文件内容**
   > 考纲原文：*"A new file will be created and **any existing data in the file will be lost**."*
   > → 如果想保留原数据，**不能**直接用 WRITE 打开原文件

2. **同一个文件同一时间只能以一种模式打开**

3. **用完必须 `CLOSEFILE`**
   > 考纲原文：*"Files should be **closed** when they are no longer needed."*

## 🔧 标准范例 ①：读一个文件，逐行显示

```
DECLARE LineOfText : STRING

OPENFILE "data.txt" FOR READ

WHILE NOT EOF("data.txt") DO
   READFILE "data.txt", LineOfText
   OUTPUT LineOfText

ENDWHILE

CLOSEFILE "data.txt"
```

> ⚠️ **官方伪代码规范里没有定义 `EOF()` 函数** —— 但它是读文件的**事实标准写法**，各教材和历年试卷的答案都在用。
> 更保险的替代写法是用一个**结束标记（sentinel）**：
> ```
> READFILE "data.txt", LineOfText
> WHILE LineOfText <> "END" DO
>     OUTPUT LineOfText
>     READFILE "data.txt", LineOfText
> ENDWHILE
> ```

## 🔧 标准范例 ②：把文件内容复制到另一个文件

```
DECLARE LineOfText : STRING

OPENFILE "FileA.txt" FOR READ
OPENFILE "FileB.txt" FOR WRITE

WHILE NOT EOF("FileA.txt") DO
   READFILE "FileA.txt", LineOfText
   WRITEFILE "FileB.txt", LineOfText

ENDWHILE

CLOSEFILE "FileA.txt"
CLOSEFILE "FileB.txt"
```

> ⚠️ **两个文件要分别 OPENFILE、分别 CLOSEFILE** —— 只关一个是最常见的失分。
> 💡 **跳过空行**：在 `READFILE` 后加 `IF LineOfText <> "" THEN WRITEFILE "FileB.txt", LineOfText ENDIF`；需要统计空行就再加一个 `EmptyLineCount ← EmptyLineCount + 1`。

## 🔧 标准范例 ③：把数组内容写进文件

```
DECLARE Names : ARRAY[1:10] OF STRING
DECLARE Index : INTEGER

OPENFILE "names.txt" FOR WRITE

FOR Index ← 1 TO 10
   WRITEFILE "names.txt", Names[Index]
NEXT Index

CLOSEFILE "names.txt"
```

## 🔧 标准范例 ④：输入一批数据存入数组，再写入文件

```pseudocode
DECLARE Names : ARRAY[1:10] OF STRING
DECLARE Index : INTEGER

// 输入
FOR Index ← 1 TO 10
   OUTPUT "Enter name ", Index
   INPUT Names[Index]
NEXT Index

// 写文件
OPENFILE "names.txt" FOR WRITE
FOR Index ← 1 TO 10
   WRITEFILE "names.txt", Names[Index]
NEXT Index
CLOSEFILE "names.txt"

// 读回来
OPENFILE "names.txt" FOR READ
WHILE NOT EOF("names.txt") DO
   READFILE "names.txt", Names[Index]
   OUTPUT Names[Index]

ENDWHILE
CLOSEFILE "names.txt"
```

## ⚠️ 文件操作高频失分点

| # | 陷阱 | 正确 |
|---|---|---|
| 1 | 忘了 `CLOSEFILE` | **每个打开的文件都要关** |
| 2 | 以为 WRITE 是追加 | **WRITE 会清空原文件** |
| 3 | 读文件没用循环 | 要 `WHILE NOT EOF` 逐行读 |
| 4 | 打开文件后忘记初始化变量 | 读之前变量要先声明 |
| 5 | 一个文件同时用两种模式打开 | 一次只能一种模式 |
| 6 | `READFILE` 的参数写成 `(变量, 文件)` | 顺序是 **`(文件, 变量)`** |
| 7 | 文件名忘加引号 | `"data.txt"` 要引号 |

---

## 📝 15 分大题的固定模板

```
N   <场景描述>（题面已给数组名 / 变量名）
    Write a program that meets the following requirements:
    ● ...（6–9 条 requirement）
    You must use pseudocode or program code and add comments to explain how your code works.
    You do not need to declare any arrays or variables; you may assume this has already been done.
    You do not need to initialise the data in the array Xxx[]
    All inputs and outputs must contain suitable messages.
                                                                    [15]
```

> ⚠️ **最后四句每份卷子都一样** —— 背熟，考场上不用花时间读。
> 💡 **"You do not need to declare …" 意味着那部分分值不在声明上**，全在逻辑和注释上。
> 💡 requirement 高频动词：**total**（求和）> **highest / maximum** > **average** > **lowest / minimum** > **count** > **sort**。求和 + 最值 + 平均必须能默写。

## 🧠 Unit 8 命题规律（精简）

> - **语法细节题占大头**：1 分选择（循环类型 / 数据类型）+ 找错题的四个点。
> - **数据类型几乎每份必考**。
> - **文件题固定** `OPENFILE → READFILE → CLOSEFILE` 三步；2023 新增，老卷练不到。
> - **2023 新增的库例程**：`ROUND / RANDOM / SUBSTRING / LENGTH / UCASE / LCASE` —— 必须单独背。
> - **`ROUND` 两参数形式必考**（rounded to 2/4 decimal places）。
> - **数组声明 + 初始化**是 15 分题的前两步。
> - **函数**：`RETURNS` vs `RETURN`；所有路径都要有返回值。
> - **嵌套语句**不作独立考点，但嵌套逻辑（2D 数组、IF 套 IF）到处是；最多 3 层。
> - **15 分题常见骨架**：1D 数组 + 并行 2D 数组；体育积分榜（按行求和 → 求最大 → 输出对应名字）；菜单驱动增删查。
> - 老卷 QBE / Section A 题型已作废；**Paper 2 只练 2023 年以后的卷子**。

---

## ⚠️ 高频失分点汇总

| # | 陷阱 | 正确做法 |
|---|---|---|
| 1 | 用 `=` 赋值 | 用 **`←`** |
| 2 | THEN / ELSE / CASE 的 case 缩进 4 格 | **只缩进 2 格** |
| 3 | `10 MOD 3` / `10 DIV 3` | **`MOD(10, 3)`** / **`DIV(10, 3)`** |
| 4 | 用 `CALL` 调用函数 | 函数只能**用在表达式里** |
| 5 | 函数定义忘写 `RETURNS <type>` | 必须写返回类型 |
| 6 | 函数不是所有路径都有 `RETURN` | 每个分支都要返回 |
| 7 | `SUBSTRING(s, 0, 3)` | 下标**从 1 开始** |
| 8 | `SUBSTRING(s, 1, 5)` 以为是"第 1 到 5 位" | 第三个参数是**长度** |
| 9 | 用 `!=` | 用 **`<>`** |
| 10 | 用 `&&` / `||` / `%` / `//` | 用 `AND` / `OR` / `MOD()` / `DIV()` |
| 11 | 写 `0 <= x <= 100` | `x >= 0 AND x <= 100` |
| 12 | 电话号码用 INTEGER | 用 **STRING** |
| 13 | CHAR 用双引号 | CHAR 用**单引号** |
| 14 | 累加/计数变量不初始化 | `Total ← 0` / `Count ← 0` |
| 15 | 数组只写 `ARRAY[30]` | `ARRAY[1:30]` 写全上下界 |
| 16 | 数组写 `Grid[2][3]` | `Grid[2, 3]` |
| 17 | 数组没初始化就用 | 先循环赋初值 |
| 18 | 嵌套循环里每行的累加变量没重置 | 放在内层循环**之前** |
| 19 | 求最高分只更新分数不更新名字 | 两个一起更新 |
| 20 | 骰子写 `ROUND(RANDOM() * 6, 0)` | 1–6 要写 `ROUND(RANDOM() * 5, 0) + 1` |
| 21 | 用常量存表达式 | 常量**只能是字面量** |
| 22 | 标识符用下划线 / 数字开头 | Pascal case，**大写字母开头** |
| 23 | 局部变量和全局变量同名还以为改的是全局 | 局部会**遮蔽**全局 |
| 24 | 以为 WRITE 是追加 | **WRITE 清空原文件** |
| 25 | 忘了 `CLOSEFILE` | 每个文件都要关 |
| 26 | 过程/函数参数超过 2 个 | 考纲限制**最多 2 个** |
| 27 | 嵌套超过 3 层 | 考纲限制**最多 3 层** |
| 28 | 用 Python / Java 语法作答 | **非 scenario 题写编程语言代码不得分** |
| 29 | 函数/过程定义写在调用之后 | 定义在**代码开头** |

---

## 🧠 一页纸速记

```
五种类型：INTEGER / REAL / CHAR('a') / STRING("abc") / BOOLEAN(TRUE)

变量值可变；常量值不可变 —— 常量只能是字面量
CONSTANT HourlyRate ← 6.50
DECLARE Score : INTEGER

DECLARE A : ARRAY[1:10] OF STRING        // 必须写下界
DECLARE B : ARRAY[1:3, 1:3] OF CHAR      // [行, 列]
A[i] ← 5        FOR i ← 1 TO 10 ... NEXT i

三种控制结构：sequence / selection / iteration
  IF c THEN ... ELSE ... ENDIF          // THEN/ELSE 缩进 2 格
  CASE OF x
     'A' : ...                          // case 也缩进 2 格
     OTHERWISE ...
  ENDCASE

  FOR i ← 1 TO 10 ... NEXT i            // 含两端；1>10 执行 0 次
  WHILE c DO ... ENDWHILE               // 先判断，可能 0 次
  REPEAT ... UNTIL c                    // 后判断，至少 1 次；c 为 TRUE 时停

求和 Total←0；计数 Count←0；最值 Max←A[1]（★不是0）

字符串：LENGTH(s)  SUBSTRING(s, 起始, 长度)  UCASE(s)  LCASE(s)
        下标从 1 开始

运算符：+ - * / ^    = < <= > >= <>    AND OR NOT
库例程：MOD(a,b) DIV(a,b) ROUND(x,2) RANDOM()
        奇偶 → MOD(n,2)=0
        骰子 → ROUND(RANDOM()*5, 0) + 1

PROCEDURE P(a : INTEGER) ... ENDPROCEDURE      CALL P(5)
FUNCTION F(a : INTEGER) RETURNS INTEGER ... RETURN x ... ENDFUNCTION
                                               y ← F(5)     // 不能 CALL
参数最多 2 个；嵌套最多 3 层

局部变量（过程内）> 全局变量（过程外）—— 局部更安全

可维护：有意义的名字 + 注释(//) + 过程函数

文件：OPENFILE "f.txt" FOR READ / WRITE      // WRITE 会清空原文件
      READFILE "f.txt", Line
      WRITEFILE "f.txt", Line
      CLOSEFILE "f.txt"                       // 必须关
```

---

## 🔗 延伸资源

**本地资源**
- 逐条语法规范 → [Pseudocode Reference.md](Pseudocode%20Reference.md)
- 设计方法与标准算法 → [Unit 7 - Algorithm design and problem solving.md](Unit%207%20-%20Algorithm%20design%20and%20problem%20solving.md)

**在线题库**
- [Cambridge IGCSE Computer Science 0478 Past Papers](https://www.cambridgeinternational.org/programmes-and-qualifications/cambridge-igcse-computer-science-0478/past-papers/)
- [Save My Exams — IGCSE Computer Science](https://www.savemyexams.com/igcse/computer-science/)
- [Physics and Maths Tutor — Computer Science](https://www.physicsandmathstutor.com/computer-science-revision/igcse/)

---

**上一单元**：[Unit 7 - Algorithm design and problem solving](Unit%207%20-%20Algorithm%20design%20and%20problem%20solving.md)
**下一单元**：[Unit 9 - Databases](Unit%209%20-%20Databases.md)
