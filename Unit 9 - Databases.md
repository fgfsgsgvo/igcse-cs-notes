# Unit 9 - Databases

> **Paper 2 · Topic 9**　数据库是 Paper 2 里**最容易拿满分的单元之一**：概念固定、SQL 语法有限、题型重复。核心只有四件事：**表/字段/记录、数据类型、主键、SQL 查询**。

---

# 9.1 数据库基础 — Database Basics

## 9.1.1 什么是数据库

**English（背这句）**
> A **database** is an organised collection of data stored electronically, allowing data to be **stored, searched, updated and retrieved** efficiently.

**中文理解**：数据库 = 有组织地存在计算机里的数据集合。重点不是“存”，而是**有组织、可查询、可更新、可共享**。

**Data vs Information**
| 术语 | 含义 | 例子 |
|---|---|---|
| **Data** 数据 | 未加工的原始事实/数值 | `18`、`A123`、`2026-10-19` |
| **Information** 信息 | 经过处理、有上下文和意义的数据 | “学生 A123 的年龄是 18 岁” |

> 💡 数据库存的是 **data**；查询结果、报表是 **information**。

## 9.1.2 表、记录、字段

| 术语 | English | 含义 |
|---|---|---|
| **Table** 表 | A collection of related records | 由行和列组成，一张表存一类数据 |
| **Record** 记录 | A collection of fields about one entity | **一行** = 一个完整对象（一个学生、一本书） |
| **Field** 字段 | A single item of data about an entity | **一列** = 一个属性（姓名、年龄、班级） |

**例子：Student 表**

| StudentID | Name | Age | Class | FeePaid |
|---|---|---|---|---|
| S001 | Alice | 16 | CS1 | TRUE |
| S002 | Ben | 17 | CS1 | FALSE |
| S003 | Chloe | 16 | CS2 | TRUE |

- 整张表 = **table**
- 每一行（S001 / Alice / 16 / CS1 / TRUE）= **record**
- 每一列（StudentID、Name、Age…）= **field**

> ⚠️ **字段 vs 记录不要写反**：field 是列，record 是行。

## 9.1.3 数据库的优点

**English（背这句）**
> Databases **reduce data duplication**, **improve data integrity**, allow **data sharing**, and make **searching, sorting and updating** data faster and easier.

**中文要点**：
1. **减少重复**（data redundancy）——同一数据只存一次
2. **提高完整性**（data integrity）——修改一处，所有使用者看到最新值
3. **方便共享**——多个程序/用户可同时访问
4. **方便查询/排序/更新**——SQL 一条语句就能完成
5. **安全性**——可设置访问权限（access rights）
6. **备份与恢复**——集中管理更容易备份

> ⚠️ 题目问 "advantage of using a database rather than a flat file"，最稳的两点是 **less data duplication** 和 **better data integrity**。

## 9.1.4 Flat-file vs Relational Database

| | **Flat-file database** | **Relational database** |
|---|---|---|
| 结构 | **一张表** | **多张相互关联的表** |
| 重复数据 | 多（同一数据反复出现） | 少（拆表后用键关联） |
| 数据一致性 | 差（改一处可能漏改其他处） | 好（只存一次） |
| 适合 | 简单、小规模数据 | 复杂、多实体数据 |
| 关联方式 | 无 | **primary key / foreign key** |

> 💡 2026–2028 考纲的 SQL 只要求**单表查询**，但理解 relational 结构有助于回答“为什么要用多张表”。

---

# 9.2 数据类型 — Data Types

## 9.2.1 考纲限定的六种类型

| 数据类型 | English | 用途 | 例子 |
|---|---|---|---|
| **Text / alphanumeric** | Text / alphanumeric | 字母、数字、符号的组合 | 姓名、地址、电话号码、邮编 |
| **Character** | Character | **单个**字符 | `'A'`、`'7'`、`'#'` |
| **Boolean** | Boolean | 只有两个值：TRUE / FALSE（或 Yes / No） | `FeePaid`、`IsMember` |
| **Integer** | Integer | 整数（无小数） | 年龄、数量、库存 |
| **Real** | Real | 可含小数 | 价格、身高、平均分 |
| **Date/Time** | Date/time | 日期或时间 | `2026-10-19`、`14:30` |

> ⚠️ **电话号码、邮编、学号通常存成 Text**，即使它们看起来像数字。原因：需要保留前导 0、可能有字母/符号、不需要做算术运算。
> ⚠️ **Boolean 只能有两个值**，不要用它存 “Yes / No / Maybe”。

## 9.2.2 怎么选数据类型（答题模板）

题目给一个字段和用途，按这三步选：

1. 会不会做**算术**？会 → Integer 或 Real；不会 → Text
2. 有没有**小数**？有 → Real；没有 → Integer
3. 是不是**单个字符 / 只有两个状态 / 日期时间**？分别 → Character / Boolean / Date-Time

**例子**

| 字段 | 最合适类型 | 理由 |
|---|---|---|
| `StudentID`（如 S001） | **Text** | 含字母，且不做算术 |
| `Age` | **Integer** | 整数，可能做比较/统计 |
| `Price` | **Real** | 有小数 |
| `Postcode` | **Text** | 可能含字母和空格，需保留格式 |
| `IsMember` | **Boolean** | 只有 TRUE/FALSE |
| `Initial` | **Character** | 单个字母 |
| `DateOfBirth` | **Date/time** | 日期 |

> ⚠️ 如果题目问 "field size"，指的是**最多能存多少个字符/数字范围**，例如 `Name` 最多 30 个字符、`Age` 0–120。字段大小要**够用但不过大**。

## 9.2.3 字段大小与验证

**Field size** 限制字段能存的数据量：
- Text：最大字符数（如 30）
- Integer：取值范围（如 0–120）
- Real：精度/范围
- Date/time：日期格式

**Validation（验证）**：数据库可以在输入时检查数据是否合理。考纲六种：

| 验证类型 | 检查什么 | 例子 |
|---|---|---|
| **Range check** | 数值是否在范围内 | Age 必须在 0–120 |
| **Length check** | 字符数是否合适 | Postcode 最多 8 个字符 |
| **Type check** | 数据类型是否正确 | Age 不能输入 `"abc"` |
| **Presence check** | 必填字段是否为空 | Name 不能留空 |
| **Format check** | 是否符合规定格式 | Date 必须是 `DD/MM/YYYY` |
| **Check digit** | 用算法验证一串数字 | ISBN、条形码 |

> 💡 数据库的 **validation rule** 和 Unit 7 的验证检查是同一套概念；Paper 2 可能问“给这个字段选一种验证并说明”。

---

# 9.3 主键与外键 — Keys

## 9.3.1 Primary Key 主键

**English（背这句）**
> A **primary key** is a field (or combination of fields) that **uniquely identifies each record** in a table. It **cannot be null** and **cannot contain duplicate values**.

**作用**：
1. **唯一标识**每条记录
2. 防止重复记录
3. 用于**连接**其他表（作为 foreign key 的参照）
4. 方便快速查找/更新特定记录

**怎么选主键**：
- 必须**每条记录都不同**
- 不能为空
- 通常是 ID 类字段：`StudentID`、`BookID`、`OrderID`、`ISBN`
- **不要选**可能重复或会变的字段：`Name`、`Age`、`Address`、`PhoneNumber`

**例子**

| 表 | 合适的主键 | 不合适的原因 |
|---|---|---|
| Student | `StudentID` | `Name` 可能重名 |
| Book | `ISBN` / `BookID` | `Title` 可能重复 |
| Order | `OrderID` | `Date` 同一天可能有多单 |

> ⚠️ **主键不能是 NULL**；如果题目问 "why is this field suitable as a primary key?"，答：**each record has a unique value / no duplicates / cannot be blank**。

## 9.3.2 Foreign Key 外键（理解即可）

**English**
> A **foreign key** is a field in one table that refers to the **primary key** in another table, creating a **link** between the two tables.

**例子**：
- `Student` 表主键：`StudentID`
- `Result` 表里有 `StudentID` 字段 → 它就是 foreign key，指向 `Student.StudentID`

**作用**：把两张表关联起来，避免重复存储学生信息；同时保证结果表中的学生必须存在（referential integrity）。

> 💡 2026–2028 考纲的 SQL 只考**单表**，但 foreign key 的概念常在选择/简答题里出现。

## 9.3.3 Composite Key 复合主键（了解）

当**单个字段**不能唯一标识记录时，可以用**两个或多个字段组合**作为主键。例如选课表：

| StudentID | CourseID | Grade |
|---|---|---|
| S001 | CS101 | A |
| S001 | CS102 | B |
| S002 | CS101 | A |

`StudentID` 单独会重复，`CourseID` 单独也会重复，但 **(`StudentID`, `CourseID`) 组合唯一** → 复合主键。

---

# 9.4 SQL — Structured Query Language

> 2026–2028 考纲只考这些：**SELECT、FROM、WHERE、ORDER BY ASC/DESC、SUM、COUNT、AND、OR**。不会考 JOIN、GROUP BY、INSERT、UPDATE、DELETE。

## 9.4.1 基本结构

```sql
SELECT 字段列表
FROM 表名
WHERE 条件
ORDER BY 字段 ASC|DESC;
```

**执行顺序（理解用）**：
1. `FROM` 找表
2. `WHERE` 筛选记录
3. `SELECT` 选出字段
4. `ORDER BY` 排序

> ⚠️ 书写顺序永远是 **SELECT → FROM → WHERE → ORDER BY**，不要按执行顺序写。

## 9.4.2 SELECT / FROM

**查全部字段**
```sql
SELECT *
FROM Student;
```

**查指定字段**
```sql
SELECT Name, Age
FROM Student;
```

**查多个字段（用逗号分隔）**
```sql
SELECT StudentID, Name, Class
FROM Student;
```

> ⚠️ 字段之间用**逗号**，最后一个字段后面**不要加逗号**。
> ⚠️ `SELECT *` 表示所有字段；题目若要求“只显示姓名”，就不要用 `*`。

## 9.4.3 WHERE 条件

**比较运算符**：`=`、`<>`（不等于）、`>`、`<`、`>=`、`<=`

```sql
SELECT Name
FROM Student
WHERE Age = 16;
```

```sql
SELECT Name
FROM Student
WHERE Age >= 16;
```

**字符串要加引号**（通常单引号）：
```sql
SELECT Name
FROM Student
WHERE Class = 'CS1';
```

**布尔值**：
```sql
SELECT Name
FROM Student
WHERE FeePaid = TRUE;
```

> ⚠️ 文本值必须加引号；数字不加引号。
> ⚠️ 0478 的“不等于”通常写 `<>`，不是 `!=`。

## 9.4.4 AND / OR

**AND**：两个条件都满足
```sql
SELECT Name
FROM Student
WHERE Age = 16 AND Class = 'CS1';
```

**OR**：至少一个条件满足
```sql
SELECT Name
FROM Student
WHERE Class = 'CS1' OR Class = 'CS2';
```

> ⚠️ **AND 优先级高于 OR**。如果题目混合使用，最稳妥是加括号：
> `WHERE (Class = 'CS1' OR Class = 'CS2') AND Age = 16`

## 9.4.5 ORDER BY 排序

**升序**（小到大 / A–Z）：
```sql
SELECT Name, Age
FROM Student
ORDER BY Age ASC;
```

**降序**（大到小 / Z–A）：
```sql
SELECT Name, Age
FROM Student
ORDER BY Age DESC;
```

> 💡 `ASC` 是默认值，但题目要求“升序”时写出来更清楚。
> ⚠️ `ORDER BY` 永远放在 `WHERE` 后面（如果有 WHERE）。

## 9.4.6 SUM / COUNT 聚合函数

**SUM**：求某列总和
```sql
SELECT SUM(Price)
FROM Product;
```

**COUNT**：数记录条数
```sql
SELECT COUNT(*)
FROM Student;
```

**带条件**：
```sql
SELECT COUNT(*)
FROM Student
WHERE Class = 'CS1';
```

> ⚠️ `SUM` 只能用于**数值**字段；`COUNT(*)` 数的是**记录数**，`COUNT(Field)` 数的是该字段**非空值**的个数。
> ⚠️ 题目问 "how many students" → 用 `COUNT`；问 "total price" → 用 `SUM`。

## 9.4.7 典型 SQL 题型

### 题型 1：写查询

**题目**：List the names of all students in class CS1, in alphabetical order.

```sql
SELECT Name
FROM Student
WHERE Class = 'CS1'
ORDER BY Name ASC;
```

**给分点**：
- `SELECT Name`（选对字段）
- `FROM Student`（选对表）
- `WHERE Class = 'CS1'`（条件 + 引号）
- `ORDER BY Name ASC`（排序）

### 题型 2：补全 SQL

题目给半句，补缺失部分：
```sql
SELECT Name, Age
FROM Student
WHERE Age > _____
ORDER BY Age DESC;
```
→ 填一个合理的数字；注意题目给的范围。

### 题型 3：解释输出

题目给 SQL 和表，问输出哪些记录/哪些列。做法：
1. 先看 `WHERE` 筛掉哪些行
2. 再看 `SELECT` 保留哪些列
3. 最后按 `ORDER BY` 排序
4. 逐行写出结果

**例子**：

| StudentID | Name | Age | Class |
|---|---|---|---|
| S001 | Alice | 16 | CS1 |
| S002 | Ben | 17 | CS1 |
| S003 | Chloe | 16 | CS2 |

```sql
SELECT Name
FROM Student
WHERE Age = 16
ORDER BY Name DESC;
```

输出：
```
Chloe
Alice
```

> ⚠️ 输出只包含 `SELECT` 指定的列；`ORDER BY Name DESC` 让 Chloe 排在 Alice 前面。

### 题型 4：找 SQL 错误

常见错误：
| 错误 | 改正 |
|---|---|
| `SELECT Name FROM Student WHERE Class = CS1;` | 字符串加引号：`'CS1'` |
| `SELECT Name, FROM Student;` | 去掉多余逗号 |
| `SELECT Name FROM Student ORDER BY Age WHERE Age > 10;` | `WHERE` 必须在 `ORDER BY` 前 |
| `SELECT Name FROM Student WHERE Age = '16';` | 数字不加引号（或按字段类型判断） |
| `SELECT Name FROM Student WHERE Class = 'CS1' AND OR Age = 16;` | `AND` / `OR` 不能连用 |
| `SELECT COUNT(Name) FROM Student WHERE ...` 想数人数 | 用 `COUNT(*)` 更稳妥 |

---

# 9.5 数据库设计题 — 从需求到表

## 9.5.1 题目长什么样

> "A school wants to store information about its students. Each student has a unique student ID, a name, a date of birth, a class and a fee-paid status. Design a single-table database..."

**答题步骤**：
1. **列出字段**：StudentID、Name、DateOfBirth、Class、FeePaid
2. **给每个字段选数据类型**
3. **选主键**：StudentID
4. **写字段大小/验证**（如果题目要求）
5. **画表**：字段名 + 数据类型（+ 主键标记）

**示例答案**

| Field name | Data type | Field size / validation | Key |
|---|---|---|---|
| StudentID | Text | 5 characters | **Primary key** |
| Name | Text | 30 characters, presence check | |
| DateOfBirth | Date/time | valid date format | |
| Class | Text | 3 characters | |
| FeePaid | Boolean | TRUE/FALSE | |

> ⚠️ 题目说 "single-table" 就**不要拆成多张表**；说 "unique" 的字段通常是主键候选。

## 9.5.2 常见失分点

| 失分点 | 正确做法 |
|---|---|
| 把 field 和 record 写反 | field = 列，record = 行 |
| 主键选了可能重复的字段 | 选 ID/ISBN 等唯一字段 |
| 电话号码存成 Integer | 存成 Text，保留前导 0 |
| 价格存成 Integer | 有小数 → Real |
| SQL 字符串不加引号 | `'CS1'` |
| SQL 子句顺序错 | SELECT → FROM → WHERE → ORDER BY |
| `COUNT` 和 `SUM` 混用 | 数条数用 COUNT，求和用 SUM |
| 输出题多写了未 SELECT 的列 | 只写 SELECT 指定的列 |

---

# 9.6 一页纸速记

```
Database = organised collection of data
Table = rows + columns
Record = one row (one entity)
Field = one column (one attribute)

Data types: Text / Character / Boolean / Integer / Real / Date-Time

Primary key:
  uniquely identifies each record
  no duplicates, cannot be NULL
  e.g. StudentID, ISBN, OrderID

Foreign key:
  field referring to primary key in another table
  links two tables

SQL:
  SELECT fields
  FROM table
  WHERE condition
  ORDER BY field ASC|DESC;

  AND = both conditions
  OR  = at least one condition
  SUM(field) = total
  COUNT(*)   = number of records

SQL order:
  SELECT → FROM → WHERE → ORDER BY
```

---

# 9.7 真题实证与练习方向

> 学校资料：`Past Exam Papers/Questions by Unit/Unit 9 - Databases (167 pts)/` 有 **Question Paper + Answer Key**，共 22 题、167 分。

**高频题型排序**：
1. **SQL 查询/补全/解释输出** —— 几乎每套都有，分值最大
2. **选择合适的数据类型** —— 1–3 分，送分题
3. **主键的作用/选择主键** —— 1–2 分
4. **数据库 vs flat-file 的优点** —— 2–4 分
5. **设计单表数据库** —— 4–6 分

**练习建议**：
- 先把 Unit 9 的 22 道题按题型分类，SQL 题全部手写一遍
- 每道 SQL 题都问自己：选对字段了吗？表名对吗？字符串加引号了吗？子句顺序对吗？
- 输出题不要只看答案，自己逐行画表筛选

---

**上一单元** ← [Unit 8 - Programming](Unit%208%20-%20Programming.md)
**下一单元** → [Unit 10 - Boolean logic](Unit%2010%20-%20Boolean%20logic.md)
