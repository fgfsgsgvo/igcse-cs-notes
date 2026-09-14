# Unit 1 — Data Representation 数据表示

> **考纲**：0478 Syllabus 2026–2028 · Section 1.1–1.3
> **试卷**：Paper 1 Computer Systems（75 分 / 1 小时 45 分 / **不可用计算器**）
> **本单元特点**：Paper 1 中考点数最密集的单元之一。**计算题 + 二进制运算题**必须拿满分（方法分），概念解释题靠背模板。

---

## 📋 考纲对照清单

| 考纲 | 内容 | 出题形式 | 掌握 |
|---|---|---|---|
| 1.1.1–2 | 三种数制 + 相互转换 | 计算/换算 | ☐ |
| 1.1.3 | 为什么用十六进制 | 描述 3 个用途 | ☐ |
| 1.1.4 | 8 位二进制加法 + overflow | 计算 + 解释 | ☐ |
| 1.1.5 | 逻辑移位 | 计算 + 评论 | ☐ |
| 1.1.6 | 二补码 | 转换 | ☐ |
| 1.2.1 | ASCII / Unicode | 解释 | ☐ |
| 1.2.2 | 声音采样 | 解释 + 计算 | ☐ |
| 1.2.3 | 位图图像 | 解释 + 计算 | ☐ |
| 1.3.1 | 存储单位 | 换算 | ☐ |
| 1.3.2 | 文件大小计算 | 计算 | ☐ |
| 1.3.3–4 | 有损/无损压缩、RLE | 解释 + 计算 | ☐ |

---

# 1.1 Number Systems 数制

## 1.1.1 为什么计算机使用二进制

**English（背这句）**
> Computers use binary because it only has two states, 0 and 1, which are easily represented by **on/off** electrical states in a circuit. All forms of data must be converted to binary to be processed by a computer.

**中文理解**
计算机内部是电路，只有「通电/断电」两种稳定状态 → 天然对应 `1`/`0`。任何数据（文字、图片、声音）**必须先转成二进制**才能被处理。电路用 **logic gates（逻辑门）** 运算，结果存在 **registers（寄存器）** 里。

> 💡 注意：三进制、十进制电路在技术上也能做，但**抗干扰差、成本高、易出错**。两个字态最稳定、最简单。答题时如果问 "why"，答 **two states / on and off** 即可得分。

---

## 1.1.2 三种数制与转换

### 三种数制对比

| 数制 | Base | 数字 | 说明 |
|---|---|---|---|
| **Denary** 十进制 | 10 | 0–9 | 人类日常使用 |
| **Binary** 二进制 | 2 | 0, 1 | 计算机使用；对应 on/off |
| **Hexadecimal** 十六进制 | 16 | 0–9, A–F | 二进制更短的写法，便于人类阅读 |

**十六进制字母表**（必背）：

| Denary | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **Hex** | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | **A** | **B** | **C** | **D** | **E** | **F** |
| **Binary** | 0000 | 0001 | 0010 | 0011 | 0100 | 0101 | 0110 | 0111 | 1000 | 1001 | 1010 | 1011 | 1100 | 1101 | 1110 | 1111 |

### 列标题（Heading values）—— 换算的核心

**8 位二进制**（考纲要求最大到 **16 位**）：

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|
| 2⁷ | 2⁶ | 2⁵ | 2⁴ | 2³ | 2² | 2¹ | 2⁰ |

**十六进制**：… 4096 | 256 | 16 | 1（即 16³, 16², 16¹, 16⁰）

---

### 🔧 四种转换方法（必须练成肌肉记忆）

#### ① Binary → Denary
把**所有是 1 的位的列标题相加**。

```
0 1 1 1 1 0 0 1  =  64 + 32 + 16 + 8 + 1  =  121
```

#### ② Denary → Binary（连除 2 取余）
**不断除以 2，余数从下往上读**。

```
2 | 142
2 |  71  余 0        ↑
2 |  35  余 1        |
2 |  17  余 1        | 从下往上读
2 |   8  余 1        |
2 |   4  余 0        |
2 |   2  余 0        |
2 |   1  余 0        |
    0   余 1
→ 10001110
```
> ⚠️ 若题目要求 **8 位**而结果是 `111011`（6 位），左边**补零** → `00111011`。

#### ③ Binary ↔ Hexadecimal（**4 位一组**）
二进制转十六进制：**从右往左**每 4 位一组，不足左边补 0。

```
1011 1111 0000 1001  →  B    F    0    9   →  BF09
1 0011 1110 0111
→ 先补成 0001 0011 1110 0111  →  1 3 E 7  →  13E7
```
十六进制转二进制：**每个十六进制位写成 4 位二进制**。

```
45A   →  0100 0101 1010
E48D  →  1110 0100 1000 1101
```

#### ④ Hexadecimal ↔ Denary
**Hex → Denary**：每位 × 列标题，相加。

```
1FD  = (1 × 256) + (15 × 16) + (12 × 1) = 256 + 240 + 12 = 508
4EB5 = (4 × 4096) + (14 × 256) + (11 × 16) + (5 × 1) = 20149
```
**Denary → Hex**：连除 16 取余，从下往上读。

```
16 | 2004
16 |  125  余 4         ↑ 从下往上
16 |    7  余 13 (=D)   |
     0    余 7
→ 7D4
```

> 💡 **考场最优策略**：Denary → Hex 若数字不大，**先转二进制再 4 位一组转 Hex**，比连除 16 更快且不易错。

---

## 1.1.3 为什么用十六进制（Why hexadecimal is used）

**English（考试直接背这三点）**
> 1. Hexadecimal is **easier for humans to read and understand** than binary, because it is a **shorter representation** — one hex digit represents 4 binary bits.
> 2. It is **quicker/less error-prone to write** and takes up less space on screen than long binary strings.
> 3. It is used in specific areas of computer science, e.g. **MAC addresses, IP addresses, HTML colour codes and error codes**.

**中文理解**
`1010111100000001`（16 位）写成 `AF01` 只要 4 个字符。人眼读长串 01 极易出错。

### 十六进制的四个典型用途（考纲 + 真题高频）

| 用途 | 说明 |
|---|---|
| **Error codes** 错误代码 | 计算机自动生成，指向出错的内存位置 |
| **MAC address** | 格式 `NN-NN-NN-DD-DD-DD`，前 6 位**厂商代码**，后 6 位**设备序列号** |
| **IP address** | IPv4 是 **32 位**，IPv6 是 **128 位** |
| **HTML colour codes** | 颜色由 **红绿蓝（RGB）** 组合，每色 0–255。`#FF0000` = 纯红，`#FF8000` = 橙色，`#B18904` = 棕褐色 |

> ⚠️ 题目问 "Describe **three** uses"（6 分）→ 一个用途 2 分：**写出用途 + 说明它是什么**。只写 "MAC address" 拿一半，要写 "MAC addresses are given to a NIC and are written in hex, made of the manufacturer code and the serial number"。

---

## 1.1.4 二进制加法与 Overflow

### 加法规则（必背表）

| 运算 | Carry | Sum |
|---|---|---|
| 0+0+0 | 0 | 0 |
| 0+0+1 | 0 | 1 |
| 0+1+0 | 0 | 1 |
| 0+1+1 | **1** | 0 |
| 1+0+0 | 0 | 1 |
| 1+0+1 | **1** | 0 |
| 1+1+0 | **1** | 0 |
| 1+1+1 | **1** | 1 |

**口诀**：1+1=0 进 1；1+1+1=1 进 1。

### 例题

```
  00100111      ← carry 行
+ 01001010
  ────────
  01110001
```
逐列（从右往左）：
- col1: 1+0 = 1，无进位
- col2: 1+1 = 0，进 1
- col3: 1+0+1 = 0，进 1
- col4: 0+1+1 = 0，进 1
- col5: 0+0+1 = 1，无进位
- col6: 1+0+1… 依次类推

### ⚠️ Overflow Error 溢出

**English（背）**
> An **overflow error** occurs when the result of a calculation is **too large to be stored** in the number of bits available (the register/word size).
> For an 8-bit register, the maximum value is **255 (2⁸ − 1)**. If the result exceeds this, a **ninth bit** is generated and the answer stored in the 8 bits is incorrect.

**例题**
```
  01101110   (= 110)
+ 11011110   (= 222)
  ────────
1) 01001100   ← 产生了第 9 位！
```
- 期望结果 110 + 222 = **332**
- 实际 8 位结果 `01001100` = **76** ← 明显错误
- **结论**：产生第 9 位 = overflow 的明确标志

**寄存器大小与最大值**

| 寄存器 | 最大值 | 公式 |
|---|---|---|
| 8-bit | 255 | 2⁸ − 1 |
| 16-bit | 65,535 | 2¹⁶ − 1 |
| 32-bit | 4,294,967,295 | 2³² − 1 |

> 💡 位数越多，能表示的数的范围越大。

---

## 1.1.5 逻辑移位（Logical Binary Shifts）

**规则**

| 方向 | 操作 | 效果 |
|---|---|---|
| **Left shift** 左移 | 每位左移，**右边补 0**，最左边（MSB）移出的位**丢失** | **× 2**（每移 1 位） |
| **Right shift** 右移 | 每位右移，**左边补 0**，最右边（LSB）移出的位**丢失** | **÷ 2**（每移 1 位） |

- **MSB** = Most Significant Bit（最左位，权重最大）
- **LSB** = Least Significant Bit（最右位，权重最小）
- 移 n 位 → × 2ⁿ 或 ÷ 2ⁿ

**例题**：54 = `00110110`

| 操作 | 结果 | 值 | 是否正确 |
|---|---|---|---|
| 左移 2 位 | `11011000` | 216 | ✅ 54 × 2² = 216 |
| 左移 4 位 | `01100000` | 96 | ❌ 应为 864，**丢失了 1 位 → error** |
| 右移 1 位 | `00011011` | 27 | ✅ 54 ÷ 2 = 27 |
| 右移 4 位 | `00000011` | 3 | ❌ 应为 3.375，**精度丢失 → error** |

> ⚠️ **一旦有 1 被移出寄存器，结果就是错的（error）**，因为数据丢失了。

---

## 1.1.6 二补码（Two's Complement）

用途：表示**负数**。8 位二补码中，**最左边一位的权重是 −128**（而不是 +128）。

```
−128  64  32  16  8  4  2  1
  ↓
  1    0   0   0  0  0  0  0   =  −128
  0    1   1   1  1  1  1  1   =  +127      ← 范围：−128 到 +127
```

**范围公式**：n 位二补码可表示 **−2ⁿ⁻¹ 到 +2ⁿ⁻¹ − 1**

### 🔧 正数 → 负数（三种方法）

**方法 A：直接按权重凑**
```
求 −67：
−128 + 32 + 16 + 8 + 4 + 1 = −67
  1   0  1  1  1  1  0   1
```

**方法 B：取反加一**（最通用）
```
67  =  01000011
取反 = 10111100
加 1 = 10111101   →  −67  ✅
```

**方法 C：从右往左，遇到第一个 1 为止照抄，之后全部取反**（课件教的速算法）
```
+12 = 0000 1100
从右往左：0 照抄，0 照抄，1 照抄（遇到第一个 1，停止照抄）
剩下高位全部取反：0000 → 1111
−12 = 1111 0100   ✅
```

### 负数 → Denary
把**最高位当 −128**，其余位按正常权重相加。
```
11100110 = −128 + 64 + 32 + 4 + 2 = −26
```

---

# 1.2 Text, Sound and Images 文字、声音与图像

## 1.2.1 Character Sets 字符集

**English（背）**
> A **character set** is a defined list of characters recognised by a computer. Each character is represented by a **unique binary number** (a code). When a key is pressed, the code is looked up in a stored table.

| 字符集 | 位数 | 字符数 | 特点 |
|---|---|---|---|
| **ASCII** | 7-bit | 2⁷ = **128** | 只覆盖英文、数字、标点、控制码 |
| **Extended ASCII** | 8-bit | 2⁸ = **256** | 增加了部分西欧/特殊符号 |
| **Unicode** | 变长（8/16/21/32 位） | **超过 100 万** | 支持所有语言（中文、日文、阿拉伯文）和 **emoji** |

### ASCII 的局限
> The main drawback of ASCII is that it **cannot represent non-Western languages** such as Chinese or Japanese characters.

### Unicode 的优势
> Unicode allows for a **greater range of characters and symbols** than ASCII, including different languages and emojis.

> ⚠️ **代价**：Unicode **requires more bits per character than ASCII**（考纲明确列出），因此同样内容用 Unicode 存储**文件更大**。
> 例：一份文本用 ASCII 编码 32 KB，用 Unicode 编码 64 KB。

> 💡 **易错点**：**Unicode 不是 ASCII 的子集**，两者是并列的不同字符集。ASCII 也不是 Unicode 的子集。

---

## 1.2.2 Representation of Sound 声音的表示

**English（背流程）**
> Sound is **analogue** data. To store sound on a computer, the sound wave must be **sampled at regular intervals** and converted to binary using an **ADC (analogue-to-digital converter)**. On playback, a **DAC** converts it back to analogue.

### 两个决定质量与大小的参数 ⭐

| 参数 | 英文定义 | 中文 | 提高的后果 |
|---|---|---|---|
| **Sample rate** | The **number of samples taken per second**, measured in **hertz (Hz)** | 每秒采样次数 | 音质↑ **和** 文件大小↑ |
| **Sample resolution** | The **number of bits used to store each sample** (bits per sample) | 每个采样点的位数 | 音质↑ **和** 文件大小↑ |

**常见值**
- 典型音频采样率：**44,100 Hz**（每秒 44,100 个采样点）
- CD 采样精度：**16-bit** → 每个采样占 2 bytes，可表示 2¹⁶ = **65,536** 个振幅等级

### 🔢 声音文件大小公式

```
Sound file size (bits) = Sample rate (Hz) × Sample resolution (bits) × Duration (seconds)
```

**例题**
```
采样率 6 Hz，时长 3 秒，精度 4 bits
6 × 3 × 4 = 72 bits = 9 bytes
```

**真题级例题**
```
60 分钟音频，采样率 44,100，精度 16 bits
44100 × 16 × (60 × 60) = 2,540,160,000 bits
÷ 8 = 317,520,000 bytes
÷ 1024 ÷ 1024 = 302.8 MiB
```

---

## 1.2.3 Representation of Bitmap Images 位图图像的表示

**English（背）**
> An image is made up of a series of **pixels** (picture elements) arranged in a **two-dimensional matrix**. Each pixel is converted to a **binary number**, which is processed by the computer.

| 术语 | 定义 | 中文 |
|---|---|---|
| **Pixel** | Picture element — the smallest addressable element of an image | 像素 |
| **Resolution** | The **number of pixels** in the image (e.g. 1024 × 1080) | 分辨率 |
| **Colour depth** | The **number of bits used to represent each pixel/colour** | 色深 |

### 色深与颜色数
**颜色数 = 2ⁿ**，n = 色深

| 色深 | 可表示颜色数 |
|---|---|
| 1 bit | 2（黑白） |
| 2 bits | 4（00, 01, 10, 11） |
| 3 bits | 8 |
| 8 bits | 256 |
| **24 bits** | **超过 1600 万**（≈人眼可分辨的极限） |

> 照片通常用 **24-bit colour**，每个像素由 24 位组成。

### 🔢 图像文件大小公式

```
Image file size (bits) = Resolution (width × height in pixels) × Colour depth (bits)
```

**例题**
```
宽 17 px，高 14 px，色深 2 bits
14 × 17 × 2 = 476 bits
÷ 8 = 59.5 → 60 bytes
```

**真题级例题**
```
2048 × 3072 像素，色深 32 bits
2048 × 3072 × 32 = 201,326,592 bits
÷ 8 = 25,165,824 bytes
```

> ⚠️ **分辨率↑ 或 色深↑ → 画质↑ 且 文件大小↑**（这是必考的一句话因果，两个方向都要写）

### Metadata 元数据（背景知识）
存储在图像文件中的附加数据，定义图像的 **width, height, colour depth, colour palette**。不属于计算范围，但解释题可能提到。

### Vector vs Bitmap（背景知识，非本考纲重点）
- **Bitmap**：由像素组成 → 适合照片、数字艺术；放大会 **pixelated（像素化）**
- **Vector**：存储绘制图形的**数学描述**（圆心坐标、半径、宽度、颜色）→ 适合 logo、简图；放大不失真

---

# 1.3 Data Storage and Compression 数据存储与压缩

## 1.3.1 存储单位（Measurement of Data Storage）

| 单位 | 符号 | 位数/字节数 | 数值 |
|---|---|---|---|
| **Bit** | b | 0 或 1 | 最小单位 |
| **Nibble** | — | **4 bits** | — |
| **Byte** | B | **8 bits** | 1 |
| **Kibibyte** | KiB | 1024 bytes = 2¹⁰ | 1,024 |
| **Mebibyte** | MiB | 1024² bytes = 2²⁰ | 1,048,576 |
| **Gibibyte** | GiB | 1024³ bytes = 2³⁰ | 1,073,741,824 |
| **Tebibyte** | TiB | 1024⁴ bytes = 2⁴⁰ | 1,099,511,627,776 |
| **Pebibyte** | PiB | 1024⁵ bytes = 2⁵⁰ | 1,125,899,906,842,624 |
| **Exbibyte** | EiB | 1024⁶ bytes = 2⁶⁰ | 1,152,921,504,606,846,976 |

### ⚠️⚠️ 本单元最大的送分/送命点

> **计算必须用 1024，不是 1000！**

考纲原文：
> *Calculations must use the measurement of **1024** and not 1000.*
> *Answers must be given in the **units specified in the question**.*

**换算流程**
```
bit  ⇄ byte        ：÷ 8 或 × 8
byte → KiB → MiB → GiB …  ：每级 ÷ 1024
```

**Windows 的陷阱**：你在 Windows 里看到的 `KB`、`MB` 其实是 JEDEC 标准的**十进制符号**，但用的是 **1024**。官方 SI 单位应写作 **KiB**（1024 bytes）。考试中**一律用 KiB/MiB/GiB 系列符号，且一律用 1024**。

---

## 1.3.2 文件大小计算（Calculation of File Size）

两个公式必须默写：

```
🖼  Image file size (bits) = Width (px) × Height (px) × Colour depth (bits)

🔊 Sound file size (bits) = Sample rate (Hz) × Sample resolution (bits) × Duration (s)
```

### ✅ 计算题答题模板（拿满方法分）

题目信息可能给的是：
- **图像**：resolution（width × height）和 colour depth
- **声音**：sample rate、sample resolution 和 length of track

**步骤（一定要写出来！）**
1. 写出公式（不写公式也至少要写代入过程）
2. 代入数值 → 得到 **bits**
3. **÷ 8** → bytes
4. **÷ 1024 多次** → 题目要求的单位（KiB / MiB / GiB）
5. 写上单位

> 💡 **评分老师原话**："If you make any errors in your calculation, by showing all steps, you could still gain a good mark even if your final answer is incorrect."
> → **每一步都要写，即使算错也有方法分。**

**综合例题**：相机有 64 GiB 内存，每张照片 2048 × 3072 像素、色深 32 bits，能存几张？
```
每张 bits   = 2048 × 3072 × 32 = 201,326,592 bits
每张 bytes  = ÷ 8 = 25,165,824 bytes
相机容量     = 64 × 1024 × 1024 × 1024 = 68,719,476,736 bytes
张数         = 68,719,476,736 ÷ 25,165,824 = 2730 张
```

> ⚠️ **单位一定要按题目要求**。题目说 "Give your answer in MiB" 就**必须**给 MiB，给 bits 会丢分。

---

## 1.3.3 为什么需要压缩（Purpose of Compression）

**English（背三个 "less"）**
> Compression reduces the size of a file, which means:
> - **less storage space** is required
> - **less bandwidth** is required
> - **shorter transmission time** (files download/upload faster)
> - potentially **lower cost** (e.g. cloud storage charges)

> ⚠️ **评分陷阱**：写 "uses up less **space**" **得 0 分**。必须写 **"less storage space"** 或 **"less memory space"** —— 只写 "space" 不算。

---

## 1.3.4 有损 vs 无损压缩 ⭐

| | **Lossy** 有损 | **Lossless** 无损 |
|---|---|---|
| **原理** | 永久删除部分数据（permanently removes data） | 不丢失任何数据，只是**重新编码** |
| **能还原吗** | ❌ 不能还原成原始文件 | ✅ 可**完整重建**原文件 |
| **压缩率** | 高（文件更小） | 较低 |
| **画质/音质** | 下降 | 不变 |
| **适用** | 图像、声音、视频 | **所有类型**，尤其**文本文档和可执行文件** |
| **例子** | **MP3, MP4, JPEG, MPEG** | **RLE (run length encoding)**, Huffman coding |

### 为什么文本/程序不能用有损压缩
> Text documents and executable code must be compressed **in their entirety** to avoid losing essential data — any lost character would corrupt the file.

### 有损压缩的两个经典例子

**MP3**（音频）
- 可把音乐文件缩小约 **90%**
- 算法移除人耳听不到的声音：
  - 移除**人耳听觉范围之外**的声音
  - 两个声音同时播放时，移除较安静的那个（**perceptual music shaping** 感知音乐整形）

**JPEG**（位图图像）
基于两个原理：
1. 人眼对**颜色深浅**的分辨力不如对**亮度**的分辨力
2. 把像素的**颜色与亮度分离**后，图像可切成 **8 × 8 像素的块**，丢弃部分信息也不会明显降低画质

### 无损压缩：RLE（Run Length Encoding）

**原理**：把**连续重复的相同数据**压缩成 **「次数 + 数据」的 data pair（频率/数据对）**。

**图像例子**（1 bit 色深：0 = 白，1 = 黑）
```
0000000000
0000000000
0011111100
0000001000
...
原始 = 100 bits

→  22W 6B 8W 1B 8W 1B … 
→  22 0   6 1   8 0   1 1   8 0   1 1 ...
   （次数 + 颜色代码，即 frequency/data pairs）
```

**文字例子**
```
aaaaaaa / bbbbbbbbbb / c / d / c / d / c / d / eeeeeeee
→  255 08 97 // 255 10 98 // 99 / 100 / 99 / 100 / 99 / 100 // 255 08 101
     ↑     ↑
     │     └── 重复字符的 ASCII 码
     └──────── 重复次数
255 是标志位，表示后面两个值分别是「重复次数」和「ASCII 码」
```

### RLE 的适用性 ⚠️
| ✅ 适合 | ❌ 不适合 |
|---|---|
| 有大片**连续同色**区域的图像 | 全彩照片（颜色变化频繁，压缩后可能**更大**） |

> ⚠️ **易错判断题**："RLE works effectively on any run of repeating units" —— **错误**。RLE 只对**连续、大量重复**的数据有效。

---

# 📝 考试怎么考（Exam Focus）

## 各题型的答题模板

### 1️⃣ 计算/换算题
- **Command word**：`Convert` / `Calculate` / `Give your answer in …`
- 换行写中间结果，**写公式 + 代数 + 单位**
- 二进制写够位数（题目说 8-bit 就写 8 位，不满**左边补 0**）

### 2️⃣ "Comment on your answer" 题（移位/加法进位必考）⭐
这是 IGCSE 的特色题型，**没写清楚会丢分**。

**模板**：
> ① 实际结果 = ___。
> ② 期望结果应该是 ___（原值 × 2ⁿ 或 ÷ 2ⁿ，或加法前的两数之和）。
> ③ 二者**相同 / 不同**，因为 **没有 / 有** 1 被移出寄存器（或产生了第 9 位）。
> ④ 因此发生了 **overflow error / loss of data**。

**范例（满分答法）**
> *Shifting two places left should give the result 44 × 2² = 176, which means the actual result is the same as the expected result.*
>
> *A ninth bit is generated following this binary addition. The expected result for this addition (220 + 44) is 264. However, the value 8 is generated. This is clearly incorrect and is due to the fact that the result of the sum exceeds the maximum value which can be represented by an 8-bit word (that is, 255). An **overflow error** has occurred.*

### 3️⃣ "Explain the term …" 题
- **Command word**：`Explain` / `Describe` / `State`
- `Explain` 要**展开因果**，`State` 只要一句话
- **Explain 题的标准结构**：定义 + 为什么 + 后果

**示例**
> *Explain sample resolution:* The sample resolution is the **number of bits** used to store **each sample**. A higher sample resolution means more distinct amplitude values can be represented, which gives **better sound quality** but a **larger file size**.

### 4️⃣ "Explain why the student's answer is incorrect" 题
必须写**两件事**：① 错在哪 ② 正确说法是什么。

**题库（高频错误说法）**

| 错误说法 | 正确说法 |
|---|---|
| 1 MiB = 1,000,000 bytes | 1 MiB = **1,048,576** bytes（1024²）|
| 有损压缩后文件可以随时还原 | 有损压缩**永久丢失数据，无法还原** |
| RLE 对任何重复数据都有效 | RLE 只对**连续大量重复**有效，全彩照片无效 |
| ASCII 是 Unicode 的子集 | 二者是**并列**的独立字符集，ASCII 不能表示中文等 |
| 播放声音要用 ADC | **播放**要用 **DAC**；**录制/采样**才用 ADC |

---

## 📊 真题实证（2020–2026 考频与官方答案）

### 考频表

| 考纲点 | 出现频率 | 典型分值 | 优先级 |
|---|---|---|---|
| **1.1.2 三数制转换** | **每场必考**（每套卷都有） | 1–6 | ★★★ |
| **1.3.4 有损/无损压缩** | **每场必考**（本单元最高频） | 1–4 | ★★★ |
| **1.1.4 二进制加法 + overflow** | 2023 起**每场**（2020–2022 完全没有） | 3–4 | ★★★ |
| **1.1.6 二补码** | 2023 起**每场** | 1–2 | ★★★ |
| **1.3.1 存储单位换算** | 2023 起**多数场次**，常作卷首 1 分题 | 1–4 | ★★★ |
| 1.2.3 位图图像 | 多数场次 | 1–5 | ★★☆ |
| 1.1.5 逻辑移位 | 2023 起**多数场次** | 1–3 | ★★☆ |
| 1.2.1 ASCII / Unicode | 2023 起（2020–2022 完全没有） | 1–4 | ★★☆ |
| 1.1.3 为什么用十六进制 | 多数场次 | 1–2 | ★★☆ |
| 1.2.2 声音采样 | 约一半场次（**2022 完全没有**） | 1–5 | ★★☆ |
| 1.3.2 文件大小计算 | 每年约一次 | 2–4 | ★★☆ |
| **RLE 单独出题** | **整份题库 0 次** | — | ★☆☆ |
| **ISBN 算法** | **整份题库 0 次** | — | ☆☆☆ |

> 📌 **2026 的题型变了**：从「describe X **[4]**」变成**一连串 1 分小题**。June 2026 P11 Q3 是**五个独立的 1 分换算**；P12 Q1(c) 是**三个独立的 1 分**（数制判断 + 两个二补码）；P12 Q4(c) 是**三个独立的 1 分**加密题。
> → **定义和单步运算的性价比大幅上升**，别再把时间全押在长篇 describe 上。

> ⚠️ **2019 前的旧考点已从考纲删除**：input/output devices、键盘如何工作。真题里给出这类答案**直接 0 分**（2025 Nov P11 考官报告原话："Candidates are reminded that the operation of input and output devices is **no longer listed in the syllabus and not assessed**."）

---

### 官方判分答案（背英文原文）

**① 为什么用十六进制** —— 多年逐字重复的给分点：
> - Easier/quicker for humans to **read/write/understand/remember**
> - Easier/quicker to **spot errors / debug**
> - **Shorter representation** // takes up less space **on screen/on the display**
> - Less likely for humans to **make a mistake**

⚠️ **2026 June Q3(a) 直接考 MCQ**：问哪一条**不正确** → 正确答案是 **"Hexadecimal uses less storage space"（D）**。
**"less screen space" ✅ 给分；"less storage space" ❌ 不给分** —— 因为它**仍然以二进制存储**。

**十六进制的用途清单**（多年逐字重复）：
> Represent colours in HTML // HTML colour codes; MAC address; Assembly language; Error messages/codes; IP address; URL; Memory dump; Memory locations

**② 二进制加法的给分点**（0478/11 June 2026 Q3(f) 官方原文）
> - One mark for **each correct nibble** (MAX 2)
> - One mark for the **three correct carries as working**
> - One mark for **one overflow bit**

判分补充：*"Carries can be shown above/below. **BOD 4 carries shown if the overflow is shown as a carry first, then as overflow.** Ignore the crossing out of carries."*

**③ overflow 解释**（2 分，官方答案）
> - The result is **greater than 255** // The result is **too large**
> - **Cannot be stored in 8 bits** // Cannot be stored in the number of bits available for the register

**④ 逻辑移位的"机制"描述**（3 分，Winter 2024 P12 官方答案）
> - Each/All/Every value/digit/**bit** in the binary number is **shifted/moved to the left**
> - The **left most/most significant bit is lost**
> - A **0 is added as the right most/least significant bit**

移位后的**数学效果**：*"Divide by 16 / 2⁴"*（右移 4 位）；*"The binary integer is **multiplied by 2**"*（左移 1 位）。→ **移 n 位 = ×2ⁿ 或 ÷2ⁿ**。

**⑤ 二补码**（2 分题的官方给分格式）
> - One mark for a correct **working method** e.g. **flip and add / flip and add 1**
> - One mark for the **correct answer**

**⑥ 文字如何变成二进制**（3 分，2025 Nov P11 / 2026 June 官方答案）
> - A **character set** is used … such as **ASCII/Unicode**
> - Each character has a **unique** binary value
> - It is **converted to** that binary value (and stored)

**⑦ 声音如何变成数字**（4 分，0478/13 June 2026 Q3(b) 官方答案）
> - The analogue sound is **sampled** / by measuring the **amplitude/height** (of each sound wave)
> - … at a set **sample rate** // by description
> - … at a set **sample resolution** // by description
> - The sample value is **converted to binary** / The binary for each sample is **stored in sequence**

**⑧ 图像如何变成二进制**（3 分，0478/12 June 2026 Q6(a) 官方答案）
> - Image is **broken down/divided into pixels**
> - Each pixel is a **single/one colour**
> - Each colour/pixel has a **binary value**

⚠️ 该题判分**明确禁止**：*"Do not accept reference to **resolution and colour depth**. They are not directly relevant."* —— 解释"图像怎么变二进制"时**不能提分辨率和色深**。
另有：*"Just any reference to the image having/consisting of pixels is **NE**."*

**⑨ 无损压缩如何工作**（3–4 分，2025 Summer P12 / 2026 June 官方答案）
> - A **compression algorithm** is used … such as **Run Length Encoding / RLE**
> - **Repeating pixels are grouped/identified** // Patterns are identified
> - … and stored with the **number of times they are repeated** // and **indexed**
> - The size of the file is reduced **without permanently removing any data**

判分补充：2026 明确 *"**Accept others that are correct for other lossless methods, for example Huffman encoding**."* → **RLE 是举例，不是唯一正确答案**。

**⑩ 有损压缩做了什么**（2021 March / 2025 Nov 官方答案）
> - Reduce the range of colours used / **colour depth** / bits per pixel
> - Reduce the number of pixels / **image resolution**
> - **Quality** // detail
> - **Metadata**

**⑪ 存储单位换算的确定答案**

| 题目 | 答案 |
|---|---|
| 3072 bytes = ? KiB | **3** |
| 2 PiB = ? TiB | **2048**（**只乘一次 1024**，不是 1048576） |
| 4 GiB = ? MiB | **4096** |
| 4096 MiB = ? GiB | **4** |
| 1 byte = ? nibbles | **2** |
| 1 KiB = ? bytes | **1024** |
| 8 bytes = ? nibbles | **16** |
| 512 KiB = ? MiB | **0.5** |

大小顺序：**EiB > PiB > TiB > GiB > MiB > KiB**（2026 两套卷各考一次 1 分单选，**一大一小两个方向**都考）。

---

### 官方判分规则（这几条决定你拿不拿到分）

| 规则 | 官方原文 |
|---|---|
| **前导零现在单独强调** | 2026 三套卷都写 **"Leading zeros must be present"**；P12 补充 **"Only penalise missing leading zeros once."** |
| **单位换算一律 1024** | *"**1000 was previously accepted for kilobyte, but this unit system is no longer part of this syllabus.**"*（2024 Summer P11）|
| **加法必须写二进制竖式** | 转十进制加完再转回来 = **方法分全丢**（2023–2025 八份报告反复警告）|
| **压缩题不能写文件格式** | 2026 判分明确 **"Do not accept file formats e.g. MP4, ZIP"** |
| **宽容度** | 二补码 **BOD** "flip and add" 即可；hex 填空 **BOD** 拼写 |

---

### 三条 Unit 1 独有的死穴

**① "十六进制省存储空间"是错的。** 它**仍然是二进制存储**，只是更好读。
2024 March 考官报告原话：*"Candidates had a common misconception that hexadecimal saves storage space. **This is not the case as it is still stored as binary.**"*

**② 二补码绝不能在正数前面加个 1。** 这是全卷最顽固的错误 —— 2024 Summer P11 一份报告里出现 3 次：
*"Some candidates gave an incorrect binary number of 10100000. It is likely that these candidates have converted the value 32 to binary **then added a 1 as the most significant bit to indicate it is negative**."*
→ 必须**取反加一**。另一个变体错误是把最高位当 **+128**（应作 **−128**）。

**③ 一个十六进制位不是一个十进制数。** `2A` 要**分别**转 `2` 和 `A(=10)`，**不是**把 `14` 转成二进制。2025 Summer 考官报告点名：*"Some candidates tried to convert the value 14 to binary, instead of converting the values 1 and 4 individually."*

---

## ⚠️ 高频失分点汇总

| # | 陷阱 | 正确做法 |
|---|---|---|
| 1 | 用 **1000** 而不是 **1024** 换算 | 一律 **1024** |
| 2 | 答案单位不是题目要求的 | **严格按题目要求单位** |
| 3 | 二进制没补齐到 8/16 位 | 左边**补 0** |
| 4 | 混淆 **sample rate** 和 **sample resolution** | rate = 每秒**多少次**；resolution = 每次**多少位** |
| 5 | 混淆 **resolution** 和 **colour depth**（图像）| resolution = **像素数量**；colour depth = **每像素位数** |
| 6 | "less space" 得 0 分 | 写 **"less storage space"** |
| 7 | 算 overflow 时只说"结果是错的" | 必须说明**产生了第 9 位 / 超过了 8 位最大值 255** |
| 8 | 十六进制转换时**分组方向搞错** | 从**右往左**每 4 位一组 |
| 9 | 二补码忘记最高位权值是 **−128** | 8 位二补码：−128 到 +127 |
| 10 | Unicode 说成"ASCII 的扩展/子集" | 说它是**独立的、更大范围的字符集，但每字符占用更多位** |
| 11 | 十六进制说成"能省存储空间" | 它**仍是二进制存储**，只是**更好读/更短/更少出错**；只有"省**屏幕**空间"给分 |
| 12 | 二补码用"正数前面加个 1" | 必须**取反加一（flip and add 1）**；最高位是 **−128** 不是 +128 |
| 13 | 把十六进制 `2A` 当成十进制 14 去转 | 每个 hex 位**分别**转：`2 → 0010`，`A(=10) → 1010` |
| 14 | 加法用"转十进制加完再转回来" | 必须写**二进制竖式 + 进位**；"show all working" **本身就是得分点** |
| 15 | 文件大小只乘了位数就收手 | 四步：宽×高 → ×色深 → **÷8** → **÷1024** |
| 16 | 解释"图像怎么变二进制"扯到分辨率和色深 | 2026 判分明确**不相关**；只写 pixel → 单色 → 二进制值 |
| 17 | 解释"文字怎么变二进制"写成键盘怎么工作 | 考纲已删，**0 分**；要写 character set + **unique** binary value |
| 18 | 比较 ASCII/Unicode 只写"位数不同" | 必须写出**好处**（能表示更多语言、emoji） |
| 19 | 压缩题不看场景（问图像却答文字的重复单词） | 题目给了 context 就**必须用这个 context** |
| 20 | 拿文件格式（JPEG / MP4 / ZIP）当压缩方法 | 方法只有 **lossy** 和 **lossless** 两类 |
| 21 | 位数/最大值记错：最小 8 位 = 1，最大 = 256，12 位最大 hex = F | 最小 = **0**，最大 = **255**，12 位最大 hex = **FFF**、denary = **4095**，**A = 10** |
| 22 | 移位方向搞反 / 移出的位补 **1** | 左移右补 0，右移左补 0；**一律补 0** |

---

## 🔗 延伸资源

- 学校课件：`csresource/…/Slides/1 Computer Systems/1 Data representation/`
- 真题练习：`csresource/…/Past Exam Papers/Questions by Unit/Unit 1 - Data representation (375 pts)/`
- 配套视频：见各课件同目录下的 `.webloc` 书签（YouTube 播放列表）
- 教材：`Books/IGCSE CIE/Textbook/` 第 1 章；`Study and Revision Guide` 第 1 章
- 在线练习（按考纲章节分类）：[Save My Exams — 1. Data Representation](https://www.savemyexams.com/igcse/computer-science/cie/23/topic-questions/1-data-representation/number-systems/exam-questions/) ｜ [PapersDaddy — 0478 Topical Paper 1](https://www.papersdaddy.com/cambridge/igcse/computer-science-0478/resources/topical-past-papers/paper-1)（免费）

---

**上一单元**：— | **下一单元**：[Unit 2 - Data transmission](Unit 2 - Data transmission.md)
