# Pseudocode Reference 伪代码规范速查

> **来源**：0478 Syllabus 2026–2028 · Section 4 "Details of the assessment" → Pseudocode
> **为什么这份文件最重要**：Paper 2 占**总成绩的 50%**，而且**必须用伪代码作答**。
> 考纲原文：*"Where the solution to a problem involves coding, candidates are required to write solutions in **pseudocode**. Solutions written in **programming code will not be awarded marks**."*
> 唯一例外：**最后那道 15 分 scenario 题**，可以用 pseudocode 或 **Python / Visual Basic / Java**。
> 官方规定了精确格式——**照自己写 Python 的习惯写，会丢分。**

---

## ⚡ 十条最容易丢分的硬性规定（先背这个）

| # | ❌ 常见写法 | ✅ 官方要求 |
|---|---|---|
| 1 | 用 `=` 赋值 | 用 **`←`**（`Counter ← 0`）|
| 2 | THEN / ELSE 缩进 4 格 | **只缩进 2 格**（CASE 的 case 也是 2 格）|
| 3 | `X MOD Y` / `X DIV Y` | **函数形式**：`MOD(X, Y)` / `DIV(X, Y)` |
| 4 | `SUBSTRING(s, 0, 3)` | 下标**从 1 开始**：`SUBSTRING(s, 1, 3)` |
| 5 | 以为 `REPEAT...UNTIL` 条件为 FALSE 时结束 | **条件为 TRUE 时结束**（UNTIL = "直到…为止"）|
| 6 | 用 `CALL MyFunction(...)` | **函数不能用 CALL**，只能作为**表达式的一部分** |
| 7 | 标识符用下划线 `Total_Score` | **不允许下划线**，用 Pascal case：`TotalScore` |
| 8 | 标识符以数字开头 `1stPlace` | **必须以大写字母开头** |
| 9 | REAL 写成 `.5` 或 `5.` | 小数点**两边都至少有一位数字**：`0.5`、`5.0` |
| 10 | 数组写 `Grid[2][3]` | **每个维度只用一个下标值**：`Grid[2, 3]` |

---

## 1️⃣ 排版与书写规范

### 缩进
> Lines are indented by **four spaces** to indicate that they are contained within a statement in a previous line.

★ **例外（最容易错）**：*"the THEN and ELSE clauses of an IF statement are indented by only **two spaces**. Cases in CASE statements are also indented by only **two spaces**."*

```
IF Score > 50
   THEN                          ← 2 格
       OUTPUT "Pass"             ← 语句本身再 4 格
   ELSE                          ← 2 格
       OUTPUT "Fail"
ENDIF
```

### 大小写
| 对象 | 规则 | 例子 |
|---|---|---|
| **关键字** | 全大写 | `IF` `REPEAT` `PROCEDURE` `DECLARE` |
| **标识符** | Pascal case（每个单词首字母大写）| `NumberOfPlayers` |
| **meta-variable** | 尖括号包围 | `<Condition>` `<Statements>` |

### 注释
```
// This procedure swaps
// values of X and Y
PROCEDURE Swap(X : INTEGER, Y : INTEGER)
```
- 用 **`//`**，到行尾结束
- **多行注释每一行都要写 `//`**
- 惯例：放在**被注释代码的上一行**，**保持相同缩进**
- 短注释可以跟在语句行尾

---

## 2️⃣ 数据类型与字面量

### 五种基本数据类型（必须背）

| 类型 | 含义 | 字面量写法 |
|---|---|---|
| **INTEGER** | 整数 | `5`、`-3` |
| **REAL** | 可含小数的数 | `4.7`、`0.3`、`-4.0`、`0.0` |
| **CHAR** | 单个字符 | `'x'`、`'c'`、`'@'` ← **单引号** |
| **STRING** | 零个或多个字符 | `"This is a string"`、`""` ← **双引号** |
| **BOOLEAN** | 逻辑值 | `TRUE`、`FALSE` |

> ⚠️ **REAL 的陷阱**：*"always written with at least one digit on either side of the decimal point"*
> ✅ `0.3`　✅ `4.0`　✅ `0.0`　❌ `.3`　❌ `4.`

> ⚠️ **空字符串 `""` 是合法的 STRING**，常在初始化数组时用到。

---

## 3️⃣ 标识符命名规则

**English（原文）**
> Identifiers are in mixed case using **Pascal case**, e.g. `FirstName`. They can only contain **letters (A–Z, a–z) and digits (0–9)**. They must **start with a capital letter** and not a digit. **Accented letters and other characters, including the underscore, should not be used.**

**四条硬规则**
1. 只能用**字母 + 数字**
2. **必须以大写字母开头**，不能以数字开头
3. **不能用下划线**、重音字母或其他符号
4. **关键字不能当标识符**（`IF`、`Total` 这类不能用）

> ⚠️ **大小写不敏感**：*"Countdown and CountDown should **not** be used as separate variables."*

> 💡 **单字母什么时候可以**：*"Single letters may be used where these are conventional (such as `i` and `j` when dealing with array indices, or `X` and `Y` when dealing with coordinates)."*
> → 数组下标用 `i`/`j`、坐标用 `X`/`Y` 是**被认可的**。

---

## 4️⃣ 变量与常量

### 声明变量
```
DECLARE <identifier> : <data type>
```
```
DECLARE Counter : INTEGER
DECLARE TotalToPay : REAL
DECLARE GameOver : BOOLEAN
```

### 声明常量
```
CONSTANT <identifier> ← <value>
```
```
CONSTANT HourlyRate ← 6.50
CONSTANT DefaultText ← "N/A"
```

> ⚠️ **常量的值只能是字面量（literal）**，考纲原文：
> *"**Only literals** can be used as the value of a constant. A variable, another constant or an expression **must never** be used."*
> ❌ `CONSTANT Tax ← BaseRate * 2`　❌ `CONSTANT Limit ← MaxValue`

### 赋值
```
<identifier> ← <value>
```
```
Counter ← 0
Counter ← Counter + 1
TotalToPay ← NumberOfHours * HourlyRate
```

> 💡 **为什么用常量**：*"It is good practice to use constants if this makes the pseudocode more readable, and easier to update if the value of the constant changes."* —— 考纲 7 的"可维护性"考点就考这个。

---

## 5️⃣ 输入输出

```
INPUT <identifier>
OUTPUT <value(s)>
```
```
INPUT Answer
OUTPUT Score
OUTPUT "You have ", Lives, " lives left"
```

> 💡 `OUTPUT` 可以用**逗号分隔多个值**，字符串加引号，变量不加。

---

## 6️⃣ 运算符

### 算术运算符

| 符号 | 含义 |
|---|---|
| `+` | 加 |
| `-` | 减 |
| `*` | 乘 |
| `/` | 除 |
| `^` | 乘方（raised to the power of）|

```
Answer ← Score * 100 / MaxMark
Answer ← Pi * Radius ^ 2
```

> ⚠️ **乘除优先级高于加减**（正常数学规则），但**建议加括号明确顺序**。

### MOD 与 DIV —— 是**函数**不是运算符 ⭐

```
DIV(<identifier1>, <identifier2>)   // 返回商，舍去小数部分
MOD(<identifier1>, <identifier2>)   // 返回余数
```
```
DIV(10, 3) returns 3
MOD(10, 3) returns 1
```

> ⚠️ **这是最好认的"照习惯写就丢分"点**。Python 里是 `10 // 3`、`10 % 3`，VB 里是 `\`、`Mod`，但**0478 的伪代码一律写成函数形式 `DIV(10, 3)`**。

### 逻辑（比较）运算符
| 符号 | 含义 |
|---|---|
| `=` | 等于 |
| `<` | 小于 |
| `<=` | 小于或等于 |
| `>` | 大于 |
| `>=` | 大于或等于 |
| `<>` | **不等于**（不是 `!=`）|

> 这些运算的结果**永远是 BOOLEAN**。

### 布尔运算符
**只有三个：`AND`、`OR`、`NOT`**（没有 XOR、没有 `&&`、`||`）

```
IF Answer < 0 OR Answer > 100
   THEN
       Correct ← FALSE
   ELSE
       Correct ← TRUE
ENDIF
```

---

## 7️⃣ 字符串处理（库例程）

| 函数 | 作用 | 参数类型 |
|---|---|---|
| `LENGTH(<identifier>)` | 字符串长度 | STRING → INTEGER |
| `LCASE(<identifier>)` | 全部转小写 | STRING 或 CHAR |
| `UCASE(<identifier>)` | 全部转大写 | STRING 或 CHAR |
| `SUBSTRING(<identifier>, <start>, <length>)` | 从 start 开始取 length 个字符 | start、length 为正整数 |

```
LENGTH("Happy Days")              returns 10
LCASE('W')                        returns 'w'
UCASE("Happy")                    returns "HAPPY"
SUBSTRING("Happy Days", 1, 5)     returns "Happy"
```

> ⚠️ **SUBSTRING 的下标从 1 开始**：*"Generally, a start position of 1 is the first character in the string."*
> ⚠️ **参数顺序是 (字符串, 起点, 长度)** —— 不是 (起点, 终点)！取第 1 到第 5 个字符写 `SUBSTRING(s, 1, 5)`。

---

## 8️⃣ 其他库例程

| 函数 | 作用 |
|---|---|
| `ROUND(<identifier>, <places>)` | 四舍五入到 `places` 位小数 |
| `RANDOM()` | 返回 0 到 1 之间（含）的随机数 |

> `ROUND` 的 identifier 是 **REAL**，places 是 **INTEGER**。

```
Value ← ROUND(RANDOM() * 6, 0)    // 返回 0 到 6 之间的整数
```

> 💡 **生成 1–6 的骰子**：`ROUND(RANDOM() * 5, 0) + 1` —— 这种"范围转换"题很常见。

---

## 9️⃣ 选择（Selection）

### IF 语句（无 ELSE）
```
IF <condition>
   THEN
       <statements>

ENDIF
```

### IF 语句（有 ELSE）
```
IF <condition>
   THEN
       <statements>
   ELSE
       <statements>
ENDIF
```

> ⚠️ **THEN 和 ELSE 只缩进 2 格**。考纲原文：*"(They are, in a sense, a continuation of the IF statement rather than separate statements.)"*

### 嵌套 IF

```
IF ChallengerScore > ChampionScore
   THEN
       IF ChallengerScore > HighestScore
          THEN
              OUTPUT ChallengerName, " is champion and highest scorer"
          ELSE
              OUTPUT Player1Name, " is the new champion"
       ENDIF
   ELSE
       OUTPUT ChampionName, " is still the champion"
       IF ChampionScore > HighestScore
          THEN
              OUTPUT ChampionName, " is also the highest scorer"
       ENDIF
ENDIF
```

> ⚠️ 考纲限制：**嵌套最多三层**（*"Candidates will not be required to write more than three levels of nested statements"*）

### CASE 语句
```
CASE OF <identifier>
   <value 1> : <statement>
   <value 2> : <statement>
   ...
   OTHERWISE <statement>
ENDCASE
```
```
INPUT Move
CASE OF Move
   'W' : Position ← Position - 10
   'E' : Position ← Position + 10
   'A' : Position ← Position - 1
   'D' : Position ← Position + 1
   OTHERWISE OUTPUT "Beep"
ENDCASE
```

**三条规则**
1. **按顺序测试** —— 找到匹配就执行并跳出，**剩下的 case 不再测试**
2. **OTHERWISE 必须放最后**，前面的都不匹配时才执行
3. 每个分支**只写一条语句**、每个 case **只用单个值**；复杂的话应该改用 IF

---

## 🔟 迭代（Iteration）

### FOR —— 计数控制循环（count-controlled）
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

> ⚠️ **三个必须记住的边界行为**（考纲原文明确写了，**trace table 题必考**）：
> - 变量取 value1 到 value2，**两端都包含**
> - **value1 = value2 → 循环体执行 1 次**
> - **value1 > value2 → 循环体一次都不执行**
> - `STEP` 的增量可以是**负数**
> - 循环变量必须是 **INTEGER**

**嵌套 FOR（二维数组的标配写法）**
```
Total ← 0
FOR Row ← 1 TO MaxRow

   RowTotal ← 0
   FOR Column ← 1 TO 10

       RowTotal ← RowTotal + Amount[Row, Column]
   NEXT Column
   OUTPUT "Total for Row ", Row, " is ", RowTotal
   Total ← Total + RowTotal
NEXT Row
OUTPUT "The grand total is ", Total
```

### REPEAT —— 后置条件循环（post-condition）
```
REPEAT

   <statements>
UNTIL <condition>
```

> ⚠️⚠️ **最易搞反的地方**：
> - 循环体**至少执行一次**（先执行后判断）
> - **条件为 `TRUE` 时终止**（UNTIL 读作"直到…为止"）
> - 条件为 FALSE 时**再执行一遍**

```
REPEAT
   OUTPUT "Please enter the password"
   INPUT Password

UNTIL Password = "Secret"
```

### WHILE —— 前置条件循环（pre-condition）
```
WHILE <condition> DO

   <statements>
ENDWHILE
```

> - 条件**为 TRUE 才执行**（先判断后执行）
> - 第一次判断就是 FALSE → 循环体**一次都不执行**
> - 条件**为 FALSE 时终止**

```
WHILE Number > 9 DO
   Number ← Number - 9

ENDWHILE
```

### 🔑 WHILE vs REPEAT 一句话区分

| | 判断时机 | 最少执行次数 | 终止条件 |
|---|---|---|---|
| **WHILE** | **之前** | **0 次** | 条件 = FALSE |
| **REPEAT UNTIL** | **之后** | **1 次** | 条件 = **TRUE** |

> 💡 题目说"**the code must run at least once**"或"keep asking until the user enters valid data" → 用 **REPEAT**。

---

## 1️⃣1️⃣ 过程与函数

### 过程 PROCEDURE

**无参数**
```
PROCEDURE <identifier>

   <statements>
ENDPROCEDURE
```

**带参数**
```
PROCEDURE <identifier>(<param1>:<datatype>, <param2>:<datatype>...)

   <statements>
ENDPROCEDURE
```

**调用**
```
CALL <identifier>
CALL <identifier>(Value1, Value2...)
```

> ⚠️ **`CALL` 是完整语句**，可以单独占一行。
> ⚠️ **参数最多两个**（*"Procedures and functions may have up to **two parameters**"*）
> ⚠️ 传入的值**数据类型必须匹配**定义。

```
PROCEDURE DefaultLine
   CALL Line(60)

ENDPROCEDURE

PROCEDURE Line(Size : INTEGER)
   DECLARE Length : INTEGER
   FOR Length ← 1 TO Size
       OUTPUT '-'
   NEXT Length

ENDPROCEDURE

IF MySize = Default
   THEN
       CALL DefaultLine
   ELSE
       CALL Line(MySize)

ENDIF
```

### 函数 FUNCTION

与过程的区别：**函数会返回一个值**，所以定义时要写返回类型。

```
FUNCTION <identifier> RETURNS <data type>

   <statements>
ENDFUNCTION
```
```
FUNCTION <identifier>(<param1>:<datatype>, ...) RETURNS <data type>

   <statements>
ENDFUNCTION
```

用 **`RETURN`** 指定返回的值，通常是函数体的**最后一条语句**。

```
FUNCTION SumSquare(Number1 : INTEGER, Number2 : INTEGER) RETURNS INTEGER
   RETURN Number1 * Number1 + Number2 * Number2

ENDFUNCTION

OUTPUT "Sum of squares = ", SumSquare(10, 20)
```

### ⚠️⚠️ 过程 vs 函数的调用方式（高频失分点）

> 考纲原文：*"Because a function returns a value that is used when the function is called, **function calls are not complete program statements**. The keyword **CALL should not be used when calling a function**. Functions should only be called as **part of an expression**."*

| | PROCEDURE | FUNCTION |
|---|---|---|
| 返回值 | ❌ 无 | ✅ 返回一个值 |
| 定义时写返回类型 | ❌ | ✅ `RETURNS INTEGER` |
| 调用方式 | `CALL MyProc(5)` | 用在**表达式里** |
| 能否单独占一行 | ✅ 可以 | ❌ **不可以** |

```
CALL DisplayResult(Total)          ✅ 过程
Result ← SumSquare(10, 20)         ✅ 函数（用在表达式里）
CALL SumSquare(10, 20)             ❌ 函数不能用 CALL
```

### 局部变量 vs 全局变量
- **全局变量**：在所有过程/函数**之外**声明，整个程序都能访问
- **局部变量**：在过程/函数**内部**声明，只有该过程/函数能用

> 💡 **为什么优先用局部变量**（答题模板）：
> - avoids naming conflicts（避免命名冲突）
> - the variable cannot be changed by other parts of the program（不会被程序其他部分意外修改）
> - easier to debug / more maintainable（更易调试和维护）
> - frees up memory when the procedure ends（过程结束后释放内存）

---

## 1️⃣2️⃣ 数组（Arrays）

### 声明
```
DECLARE <identifier> : ARRAY[<l>:<u>] OF <data type>
DECLARE <identifier> : ARRAY[<l1>:<u1>, <l2>:<u2>] OF <data type>
```
```
DECLARE StudentNames : ARRAY[1:30] OF STRING
DECLARE NoughtsAndCrosses : ARRAY[1:3, 1:3] OF CHAR
```

> ⚠️ **一定要显式写上下界**（`[1:30]` 而不是 `[30]`）。考纲原文：
> *"It is good practice to explicitly state what the lower bound of the array (i.e. the index of the first element) is because this **defaults to either 0 or 1 in different systems**. Generally, a lower bound of **1** will be used."*

### 使用
```
StudentNames[1] ← "Ali"
NoughtsAndCrosses[2, 3] ← 'X'
StudentNames[n + 1] ← StudentNames[n]
```

> ⚠️ **每个维度只用一个下标值**，用**逗号**分隔：`Grid[2, 3]`，**不是** `Grid[2][3]`。
> ✅ 下标**可以用变量**（*"Including the use of variables as indexes in arrays"*）

### 用循环操作数组
```
FOR Index ← 1 TO 30

   StudentNames[Index] ← ""
NEXT Index
```

**二维数组用嵌套循环**
```
FOR Row ← 1 TO 3
   FOR Column ← 1 TO 3

       NoughtsAndCrosses[Row, Column] ← ' '
   NEXT Column
NEXT Row
```

---

## 1️⃣3️⃣ 文件处理（File Handling）

### 四个命令

```
OPENFILE <File identifier> FOR <File mode>
READFILE <File identifier>, <Variable>
WRITEFILE <File identifier>, <Variable>
CLOSEFILE <File identifier>
```

| 模式 | 含义 |
|---|---|
| **READ** | 从文件读数据 |
| **WRITE** | 往文件写数据 —— **会创建新文件，原文件里的数据全部丢失** |

> ⚠️ **三条铁规**
> 1. **WRITE 模式会毁掉原文件内容**（*"A new file will be created and any existing data in the file will be lost."*）
> 2. **同一个文件同一时间只能以一种模式打开**
> 3. **用完必须 CLOSEFILE**（*"Files should be closed when they are no longer needed"*）

### 标准范例：逐行读一个文件并写进另一个文件

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

> 💡 **读文件的固定套路**：`OPENFILE` → `WHILE NOT EOF(...)` → `READFILE` → 处理 → `ENDWHILE` → `CLOSEFILE`

---

## 🚫 官方规范里**没有**的东西（别用！）

> ⚠️⚠️ **这一节救分**。你的课本、作业本、网上教程大量混入 **A-Level (9618)** 的内容 —— **0478 根本没有这些**。写了不加分，还可能被判为"没按伪代码作答"。

| ❌ 不在 0478 规范里 | 怎么来的 | 0478 该怎么写 |
|---|---|---|
| **`ELSE IF`** / `ELSIF` / `elif` | Python / VB / A-Level | **必须嵌套 IF**，每个 IF 配一个 `ENDIF` |
| **`&` 拼接字符串** | VB / A-Level | 用 `OUTPUT` 的**逗号分隔**，或多条 OUTPUT |
| **`+` 拼接字符串** | Python / Java | 同上 |
| **`%`**（取余）| Python / C | **`MOD(a, b)`** |
| **`//`**（整除）| Python | **`DIV(a, b)`** |
| **`!=`** | Python / C | **`<>`** |
| **`==`** | Python / C / Java | **`=`** |
| **`&&` / `\|\|` / `!`** | C / Java | **`AND` / `OR` / `NOT`** |
| **`APPEND` 文件模式** | A-Level | 0478 只有 **READ / WRITE** |
| **`BYVAL` / `BYREF`** | A-Level / VB | 0478 不涉及 |
| **`DATE` 数据类型**、`TODAY()`、`DAY()` | A-Level | 0478 只有 **5 种**基本类型 |
| **`ASC()` / `CHR()`** | A-Level | 0478 字符串只有 LENGTH / LCASE / UCASE / SUBSTRING |
| **`LEFT()` / `RIGHT()` / `MID()`** | VB / A-Level | 用 **`SUBSTRING()`** |
| **`TO_LOWER()` / `TO_UPPER()`** | Python / A-Level | 用 **`LCASE()` / `UCASE()`** |
| **`STR_TO_NUM()` / `NUM_TO_STR()` / `IS_NUM()`** | A-Level | 0478 不涉及（题目会给做法）|
| **`INT()`**（取整） | 很多语言 | **`DIV(a, b)`** 或 **`ROUND(x, 0)`** |
| **`OUTPUT MyArray`**（整个数组）| Python | **非法！** 必须用循环**逐元素**输出 |
| **`DECLARE a, b : INTEGER`** | 作业本 / A-Level | 规范是**一行一个标识符**：`DECLARE a : INTEGER` |
| **`STEP 0.01`**（非整数步长）| 作业本示例 | **STEP 必须求值为整数** |
| **`ROUND(x)`** 单参数 | 作业本示例 | **`ROUND(x, places)`** 两参数 |
| **`CONSTANT X = 5`**（用等号）| 作业本 | **`CONSTANT X ← 5`** |
| **`CONSTANT X ← Y * 2`**（表达式）| 作业本 | **只能是字面量** |

> 💡 **一句话**：**能加分的只有考纲 Section 4 里列出的那些语法**。看到陌生的"高级"写法，先问自己"考纲里有吗"。

### ⚠️ 关于 `EOF()` 的诚实说明

> **`EOF()` 不在考纲规范的语法清单里**，但它是**历年教材和答案普遍使用的读文件写法**（你的作业本答案、学校练习都在用）。
> **两条路**：
> 1. 用 `WHILE NOT EOF("file.txt") DO` —— 通用做法，风险很低
> 2. 用**结束标记（sentinel）** —— 更保险，完全用规范内的语法：
> ```
> READFILE "data.txt", Line
> WHILE Line <> "END" DO
>     OUTPUT Line
>     READFILE "data.txt", Line
> ENDWHILE
> ```
> ⚠️ 注意哨兵写法的顺序：**先在循环外读一次**，循环体内**最后再读一次**。

---

## 📋 完整模板：一份满分的 Paper 2 答案长什么样

```pseudocode
// ---- 1. 先声明所有变量和常量 ----
CONSTANT MaxStudents ← 30
DECLARE StudentNames : ARRAY[1:MaxStudents] OF STRING
DECLARE StudentMarks : ARRAY[1:MaxStudents] OF INTEGER
DECLARE Index : INTEGER
DECLARE Total : INTEGER
DECLARE Average : REAL

// ---- 2. 再定义过程/函数 ----
PROCEDURE InputData(Position : INTEGER)
   OUTPUT "Enter the student name"
   INPUT StudentNames[Position]
   OUTPUT "Enter the student mark"
   INPUT StudentMarks[Position]
ENDPROCEDURE

// ---- 3. 主程序 ----
Total ← 0
FOR Index ← 1 TO MaxStudents
   CALL InputData(Index)
   Total ← Total + StudentMarks[Index]
NEXT Index

Average ← ROUND(Total / MaxStudents, 2)
OUTPUT "The average mark is ", Average
```

> ⚠️ **顺序很重要**：考纲明确说 *"Procedures and functions are **defined at the start of the code**."*

---

## ⚠️ 高频失分点汇总

| # | 陷阱 | 正确做法 |
|---|---|---|
| 1 | 用 `=` 赋值 | 用 **`←`** |
| 2 | THEN / ELSE / CASE 的 case 缩进 4 格 | **只缩进 2 格** |
| 3 | `10 MOD 3` | **`MOD(10, 3)`** —— 函数形式 |
| 4 | `10 DIV 3` | **`DIV(10, 3)`** —— 函数形式 |
| 5 | `SUBSTRING(s, 0, 5)` | 下标**从 1** 开始 |
| 6 | `SUBSTRING(s, 1, 5)` 以为是"第 1 到第 5 位" | 第三个参数是**长度**不是终点，恰巧结果一样但概念要清楚 |
| 7 | 以为 `REPEAT...UNTIL` 条件为 FALSE 时结束 | **条件为 TRUE 时结束** |
| 8 | `CALL MyFunction(x)` | 函数**不能**用 CALL，只能用在表达式里 |
| 9 | 函数定义时忘写 `RETURNS <type>` | 必须有返回类型 |
| 10 | 标识符用下划线 | 用 Pascal case |
| 11 | 标识符以数字开头 | 以**大写字母**开头 |
| 12 | 关键字当变量名 | 换一个名字 |
| 13 | `Countdown` 和 `CountDown` 当两个变量 | **大小写不敏感**，是同一个 |
| 14 | `CONSTANT X ← Y * 2` | 常量的值**只能是字面量** |
| 15 | REAL 写 `.5` / `5.` | 小数点两边都要有数字 |
| 16 | CHAR 用双引号 | CHAR 用**单引号** |
| 17 | `Grid[2][3]` | `Grid[2, 3]` |
| 18 | 数组只写 `ARRAY[30]` | 写全上下界 `ARRAY[1:30]` |
| 19 | 以为 FOR 循环不含末端 | **两端都包含** |
| 20 | `OPENFILE` 用 WRITE 模式却不想要文件被清空 | **WRITE 会创建新文件，原数据全丢** |
| 21 | 打开文件后忘记 `CLOSEFILE` | 必须关闭 |
| 22 | 过程和函数写在主程序**后面** | 定义在**代码开头** |
| 23 | 用 `!=` | 用 **`<>`** |
| 24 | 用 `&&` / `||` | 用 **`AND`** / **`OR`** |
| 25 | 过程/函数参数超过 2 个 | 考纲限制**最多 2 个参数** |
| 26 | 嵌套语句超过 3 层 | 考纲限制**最多 3 层** |
| 27 | 用 Python / Java 语法作答 | **除最后 15 分大题外，写编程语言代码不得分** |

---

## 🧠 一页纸速记

```
赋值 ←       不等于 <>      乘方 ^      取整除 DIV(a,b)   取余 MOD(a,b)
布尔只有 AND / OR / NOT

DECLARE Name : INTEGER
CONSTANT Rate ← 6.50          // 值只能是字面量
DECLARE A : ARRAY[1:10] OF STRING
DECLARE B : ARRAY[1:3, 1:3] OF CHAR      // 用 [行, 列]

INPUT X                       OUTPUT "text ", X, " more"

IF c THEN ... ELSE ... ENDIF          // THEN/ELSE 缩进 2 格
CASE OF x
   'A' : ...                  // case 也缩进 2 格
   OTHERWISE ...
ENDCASE

FOR i ← 1 TO 10 ... NEXT i            // 含两端；1>10 时执行 0 次
FOR i ← 10 TO 1 STEP -1 ... NEXT i    // 步长可为负
WHILE c DO ... ENDWHILE               // 先判断，可能 0 次
REPEAT ... UNTIL c                    // 后判断，至少 1 次；c 为 TRUE 时停

PROCEDURE P(a : INTEGER) ... ENDPROCEDURE     CALL P(5)
FUNCTION F(a : INTEGER) RETURNS INTEGER ... RETURN x ... ENDFUNCTION
                                              y ← F(5)      // 不能 CALL

LENGTH(s)  LCASE(s)  UCASE(s)  SUBSTRING(s, 起始, 长度)   // 下标从 1
ROUND(x, 2)   RANDOM()

OPENFILE "f.txt" FOR READ      // 或 WRITE（会清空原文件）
READFILE "f.txt", Line
WRITEFILE "f.txt", Line
CLOSEFILE "f.txt"
```

**上一单元**：[Unit 6 - Automated and emerging technologies](Unit 6 - Automated and emerging technologies.md)
