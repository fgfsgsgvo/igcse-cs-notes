# Unit 2 — Data Transmission 数据传输

> **考纲**：0478 Syllabus 2026–2028 · Section 2.1–2.3
> **试卷**：Paper 1 Computer Systems（75 分 / 1 小时 45 分）
> **本单元特点**：**概念解释题为主**，几乎没有计算。大量 "Describe / Explain" 题，需要写出**完整的流程链**而不是零散关键词。

---

## 📋 考纲对照清单

| 考纲 | 内容 | 出题形式 | 掌握 |
|---|---|---|---|
| 2.1.1 | 数据包结构 + 包交换 | 描述流程 | ☐ |
| 2.1.2 | 串行/并行、单工/半双工/全双工 | 描述 + 判断适用场景 | ☐ |
| 2.1.3 | USB 接口 | 优缺点 | ☐ |
| 2.2.1 | 为什么需要查错 | 解释 | ☐ |
| 2.2.2 | 奇偶校验、校验和、回送校验 | 描述流程 + 计算 | ☐ |
| 2.2.3 | 校验位（ISBN、条形码）| 描述 + 举例 | ☐ |
| 2.2.4 | ARQ | 描述流程 | ☐ |
| 2.3.1–2 | 对称/非对称加密 | 解释 + 比较 | ☐ |

---

# 2.1 Types and Methods of Data Transmission 数据传输的类型与方法

## 2.1.1 Data Packets 数据包

### 为什么要分包
> When data is sent over long distances, it is **broken down into packets**. Packets tend to be quite small (e.g. **64 KiB**). This allows data to be sent in **manageable chunks** that can be sent along the **most efficient route**.

### 📦 数据包的三部分结构 ⭐（必背）

```
┌────────────────────┬─────────────────┬──────────────────┐
│   PACKET HEADER    │    PAYLOAD      │    TRAILER       │
│   （包头）           │   （有效载荷）    │    （包尾）        │
├────────────────────┼─────────────────┼──────────────────┤
│ • Destination      │                 │ • Cyclic         │
│   address 目的地址  │   The actual    │   Redundancy     │
│ • Originator's     │   data being    │   Check (CRC)    │
│   (sender's)       │   transmitted   │   错误校验码      │
│   address 源地址    │   实际传输的数据  │ • Method of      │
│ • Packet number    │                 │   identifying    │
│   包序号            │                 │   the end of the │
│                    │                 │   packet 结束标志 │
└────────────────────┴─────────────────┴──────────────────┘
```

> ⚠️ **考纲明确只要求这三项 header 信息**：**destination address（目的地址）、packet number（包序号）、originator's address（发送方地址）**。
> 超出考纲但可加分的：source/destination MAC address、hop / time-to-live 字段、checksum。

### 🔄 包交换 Packet Switching 五步流程 ⭐

**English（背这五步，Describe 题按步给分）**
> 1. **Data is broken down into packets.**（数据被拆分成数据包）
> 2. **Each packet is assigned a sequence number.**（每个包分配序号）
> 3. **Each packet can take its own route based on congestion.**（每个包可根据网络拥塞走不同路线）
> 4. **Routers control the route each packet takes.**（路由器负责决定/控制每个包的路由）
> 5. **Packets may arrive out of order; once the final packet has arrived, they are reordered.**（包可能乱序到达，最后一个包到达后重新排序）

**中文理解**：就像把一本书拆成很多信封分别寄出，每个信封走不同路线，到收件人那里再按编号拼回原书。

### 包交换的优缺点

| ✅ Advantages | ❌ Disadvantages |
|---|---|
| No need to tie up a single communication line（不必独占一条线路） | Packets can be lost and need to be re-sent（包可能丢失需重发） |
| Can overcome failed/busy/faulty lines by re-routing（可绕开故障线路） | Doesn't work well with **real-time streaming**（不适合实时直播） |
| Easy to expand usage（易于扩展） | **Delay at the destination** whilst packets are being re-ordered（终点需等待重排序，有延迟）|
| High data transmission rate possible（可实现高速传输） | |

### ⚠️ 场景题高频：为什么视频会议/直播质量差？

**答题模板**
> ① 音视频数据被拆成数据包 → 每个包**可能走不同路线**
> ② 因此包的**到达时间不同**，甚至**丢失**
> ③ 到达后还需要**重新排序**，产生延迟
> ④ 结果：画面卡顿/冻结、声音断续、**音画不同步（out of synchronisation）**
>
> **解决方案**：使用**专用通信链路（dedicated communication link）**让所有包走同一条路径，消除时间差。
> （超出考纲但会被给分的说法：**circuit switching 电路交换**）

---

## 2.1.2 Data Transmission 传输方式

### 两个维度 ⭐ 别混淆

| 维度 | 分类 | 判断"什么" |
|---|---|---|
| **方向 Direction** | Simplex / Half-duplex / Full-duplex | 数据能不能双向、能不能同时 |
| **方式 Method** | Serial / Parallel | 一次传几位、用几根线 |

> 💡 这两组词**可以组合**使用：`full-duplex serial transmission`、`half-duplex parallel transmission`。
> **考试常考「看描述选分类」的表格题。**

### ① 传输方向

| 模式 | 英文定义 | 中文 | 例子 |
|---|---|---|---|
| **Simplex** 单工 | Data can be sent in **one direction only** | 只能单向 | 数据发送到打印机、键盘→电脑、电视广播 |
| **Half-duplex** 半双工 | Data can be sent in **both directions, but not at the same time** | 双向但**不能同时** | **对讲机（walkie-talkie）** |
| **Full-duplex** 全双工 | Data can be sent in **both directions at the same time** | 双向**同时** | 宽带上网、电话通话 |

> ⚠️ 描述全双工时强调 **at the same time**；半双工强调 **not at the same time**。这两个词是唯一的分界，必须写出来。

### ② 串行 vs 并行 ⭐

| | **Serial** 串行 | **Parallel** 并行 |
|---|---|---|
| **原理** | 数据**一次 1 位**，沿**单根**线/通道传输 | **多位同时**沿**多根**线/通道传输（每位一根线） |
| **速度** | 相对慢 | **更快**（适合大量数据、时间敏感的任务） |
| **干扰** | External interference 风险**小** | 干扰风险**大** |
| **距离** | **适合长距离**，更可靠 | **只适合很短距离**（如计算机内部电路） |
| **成本** | **更便宜**（硬件少） | **更贵**（需要更多硬件/接口） |
| **数据倾斜 Skew** | ✅ 不存在 skew | ❌ **会产生 skew** |
| **例子** | **USB** 连接 | 计算机**内部总线**传输 |

**🔑 Skew（数据倾斜）—— 高频考点**
> **English**: In parallel transmission, separate bits may travel at **different speeds** along the various wires, causing the bits to **arrive out of sync**. This is called **skew**.
> **中文**：并行传输中，各根线上传输速度有微小差异，导致各位到达时间不再同步。

→ **这就是并行线只能用于极短距离的原因。**

### 场景选择题速查

| 场景 | 答案 | 理由 |
|---|---|---|
| 计算机内部组件之间传输 | **Parallel** | 距离极短、追求速度、无 skew 风险 |
| 连接打印机/外置硬盘/长距离 | **Serial** | 距离长、干扰小、便宜 |
| 对讲机 | **Half-duplex** | 双向但不能同时 |
| 电视广播 | **Simplex** | 只能单向 |
| 视频通话/宽带 | **Full-duplex** | 双向同时 |

---

## 2.1.3 Universal Serial Bus (USB) 通用串行总线

**English（背定义）**
> USB is a form of **serial data transmission**. It has become the **industry standard** method of transferring data between devices. USB supports both **half-duplex and full-duplex** transmission.

**连接时的自动流程**
> When a USB device is connected: the computer **automatically detects** the device, and the appropriate **device driver is automatically loaded**.

### ✅ 优点 / ❌ 缺点

| ✅ Benefits | ❌ Drawbacks |
|---|---|
| Devices are **automatically detected** and **device drivers automatically loaded** | Standard USB only supports a maximum cable length of **about 5 m**（需 USB hub 延长）|
| Connections **only fit one way**, preventing incorrect connections | Even though USB is backwards compatible, **very early standards (V1) may not be supported** by the latest computers |
| Has become an **industry standard**（兼容性极好）| Newer versions **(V3/V4 USB-C) still have slower data transfer rates** compared with e.g. **Ethernet** |
| Can support **different data transmission rates** | |
| **No need for an external power source** — the cable supplies **+5 V** power | |
| **USB protocol notifies the transmitter to re-transmit** data if errors are detected | |
| Relatively easy to add more ports using a **USB hub** | |
| **Backward compatible** | |

### USB-C（超出考纲，但可能出比较题）
- **对称 24-pin 连接器**，正反面都能插（no up or down orientation）
- 更小更薄
- 提供 **100 W / 20 V** 电力 → 可为大型设备充电
- 数据传输速率 **10 Gbps** → 支持 4K 视频
- 向后兼容 USB 2.0 / 3.0（需转接头）

> ⚠️ **比较题（Compare）陷阱**：题目要求 compare 就必须**两边都提到**。只写 "USB-C 更快" 不算比较，要写 **"USB-C is faster than USB-A"**。
> 另外：**是 data *transfer* faster，不是 data *access***；**是连接器对称（fits either way round），不是线缆两端相同**。这些细节写错不给分。

---

# 2.2 Methods of Error Detection 错误检测方法

## 2.2.1 为什么需要查错

**English（背）**
> Errors can occur during data transmission due to:
> - **electrical interference** — can corrupt data（数据损坏）
> - **packet switching** — can lead to data being lost or out of synchronisation
> - **skewing of data** — bits arrive no longer synchronised
>
> Errors can take the form of **data loss（丢数据）, data gain（多数据） or data change（数据被改变）**.

---

## 2.2.2 Parity Check / Checksum / Echo Check

### ① Parity Check 奇偶校验 ⭐

**原理**
> A parity check checks whether data has been **changed or corrupted** after transmission. The **left-most bit (the parity bit)** is reserved and set so that the total number of 1-bits is either **even (even parity)** or **odd (odd parity)**.

| 类型 | 规则 |
|---|---|
| **Even parity** | 该字节（含校验位）中 1 的总数必须是**偶数** |
| **Odd parity** | 1 的总数必须是**奇数** |

**例子**（7 位数据 + 1 位校验位）
```
数据     1001001   →  已有 3 个 1（奇数）
偶校验： 11001001  →  补一个 1，共 4 个 1（偶数）✅
奇校验： 01001001  →  补一个 0，共 3 个 1（奇数）✅
```

**⚠️ 奇偶校验的局限（高频考点）**
> If **two bits** change during transmission, the parity may **stay the same**, so the error would **not be detected**.
> （一个位出错一定能查出；**两个位同时出错则查不出**。）

### ② Parity Block / Parity Byte 奇偶校验块 ⭐

**用途**：不仅能发现错误，还能**定位出错的具体位置**。

**原理**：把 8 个数据字节排成一列，**每行（每个字节）**做水平奇偶校验，**每列**再做垂直奇偶校验，把所有垂直校验位组成额外的第 9 个字节 = **parity byte**。

```
        Parity  B2  B3  B4  B5  B6  B7  B8
Byte 1    1     1   1   1   0   1   1   0
Byte 2
Byte 3    1     0   0   1   0   1   0   1
...
Byte 8    ...
Parity    1     0   0   0   1   0   0   0     ← 垂直校验汇总
byte
```

**定位方法**：
1. 逐行检查 → 发现**第 8 行**的 1 的个数不符合偶校验
2. 逐列检查 → 发现**第 5 列**的 1 的个数不符合偶校验
3. **行与列的交点**就是出错的那一位 → 把它翻转即可修复

> **答案模板**：*"Byte 8 (row 8) now has incorrect parity; bit 5 (column 5) also has incorrect parity. The intersection of row 8 and column 5 identifies the position of the corrupted bit."*

### ③ Checksum 校验和

**原理**
> A checksum is **calculated by the sending computer** from the block of data using an **agreed algorithm**. The data is sent as a block **together with the checksum**. The **receiving computer re-calculates** the checksum using the **same algorithm**. **Any difference indicates an error.**

**步骤模板**
1. 发送方用约定算法算出校验和
2. 校验和随数据一起发送
3. 接收方用**同一算法**重新计算
4. 两者**不一致 → 说明传输出错**

### ④ Echo Check 回送校验

**原理**
> The received data is **sent back to the sending computer**, where it is **compared with the original data**. If they differ, the data is re-sent.

**⚠️ 为什么不可靠（必考）**
> If the two sets of data are different, **it is not known whether the error occurred when sending the data originally or when sending it back for checking.**
> 中文：无法判断错误是发生在**去程**还是**回程**，所以不能确定哪一份是对的。

---

## 2.2.3 Check Digits 校验位 ⭐

**English（背定义）**
> A **check digit** is a value **calculated from the digits** of a number (using methods such as **ISBN-13** or **modulo-11**), and **added to the end (right-hand side)** of the number. It is used to **detect errors following data entry**.

**能检测出的错误类型（4 种，必背）**
> - **incorrect digits entered**（输入了错误的数字）
> - **transposition errors**（**数字顺序颠倒**，如 1234 输成 1324）
> - **omitted or extra digits**（漏输或多输一位）
> - **phonetic errors**（谐音错误，如把 13 "thirteen" 听成 30 "thirty"）

**典型应用**
| 应用 | 说明 |
|---|---|
| **ISBN**（国际标准书号）| 书号最后一位是校验位 |
| **Barcodes**（条形码）| 超市商品条码，确保条码被**正确读取** |

> ⚠️ **区分 check digit 和 parity check**：
> - **Check digit** 用于**数据输入（data entry）**阶段防人为输错
> - **Parity check / checksum** 用于**数据传输（data transmission）**阶段防干扰致错

---

## 2.2.4 Automatic Repeat Request (ARQ) 自动重传请求 ⭐

**English（背完整流程）**
> ARQ is a method of checking data after transmission. It uses **positive and negative acknowledgements** and **timeout**.

**流程模板（一定要写全链路）**
1. 接收设备收到数据时，同时收到一个**错误检测码**（通常是 **CRC — cyclic redundancy check**）
2. 用这个码判断接收到的数据**是否包含传输错误**
3. **如果没有检测到错误** → 接收方向发送方送回 **positive acknowledgement（肯定应答）**
4. **如果检测到错误** → 接收方向发送方送回 **negative acknowledgement（否定应答）**，并**请求重新传输数据**
5. 发送方使用 **timeout（超时）**：等待一个**预设的时间长度**
6. 如果在此时间内**没有收到任何应答** → 发送方**自动重发数据**
7. 重复以上过程，**直到收到 positive acknowledgement**，或**达到预设的最大重传次数**

**应用**：常用于移动电话网络，以保证数据完整性（data integrity）。

---

# 2.3 Encryption 加密

## 2.3.1 为什么需要加密

**English（背）**
> When data is transmitted over **public networks**, there is always the risk of it being **intercepted**. Encryption turns the data into a form that is **unreadable** to anybody for whom the data is not intended.
>
> **Encryption cannot stop data being intercepted**, but it **prevents it from making any sense** if it is intercepted.

**术语**
| 术语 | 定义 |
|---|---|
| **Plaintext** 明文 | The original, unencrypted data |
| **Ciphertext** 密文 | Data that has been encrypted |
| **Encryption key** 密钥 | The value used to encrypt/decrypt |

---

## 2.3.2 Symmetric vs Asymmetric ⭐⭐（本单元最高频）

| | **Symmetric** 对称加密 | **Asymmetric** 非对称加密 |
|---|---|---|
| **密钥数量** | **1 个**（single key） | **2 个**（a matching pair） |
| **密钥类型** | 同一把密钥既加密又解密 | **Public key**（公开，任何人可见）+ **Private key**（私密，仅一人持有） |
| **密钥关系** | — | 两把密钥**数学上相关，但无法由一把推导出另一把** |
| **安全性** | 较低 —— **密钥必须双方共享**，传输密钥的过程可能被截获 | **更高** |
| **加密强度** | 对称密钥常用 **128/256-bit**（如 AES） | 非对称密钥通常**更长**（如 RSA 常用 **2048-bit 以上**）；考试不考具体位数 |

### 📨 非对称加密的完整流程（必考 4 分题）

**场景**：A 要给 B 发送机密文件。

```
① B 生成一对匹配的密钥（public key + private key）
② B 把 自己的 PUBLIC key 发送给 A
③ A 用 B 的 public key 加密文件
④ A 把加密后的文件发送给 B
⑤ B 用 自己的 PRIVATE key 解密文件
```

> 🔑 **记忆要点**：**用对方的公钥加密，用自己的私钥解密。**（public key 加密 → private key 解密）

### ❓ "为什么非对称比对称更安全？" 答题模板

> ① 对称加密**只有一把密钥**，发送方和接收方**必须共享同一把密钥**
> ② 传递这把密钥的过程（如通过邮件/短信发送）**本身可能被截获** → 密钥一旦泄露，**全部数据都不安全**
> ③ 非对称加密使用**公钥和私钥一对**，**只有公钥需要公开传输**，私钥**始终不离开持有者**
> ④ 公钥和私钥**数学相关但无法互相推导** → 即使公钥被截获，**也无法解密密文**
> ⑤ 因此非对称加密**明显更安全**

> ⚠️ **失分警告**：只写 "asymmetric uses two keys" **拿 0 分**。必须写出 **public key / private key 分别做什么**，才算解释。

---

# 📝 考试怎么考（Exam Focus）

## 各题型的答题模板

### 1️⃣ "Describe the process of packet switching"（4–6 分）
按 **五步流程** 顺序写，一步一分。不要写成一段废话。

### 2️⃣ "Explain the suitability of each method for a given scenario"（高频）⭐
考纲明确要求 **explain suitability for a given scenario**。

**答题结构**：
> ① 说出该场景的特点（距离长/短？需要双向同时吗？数据量大吗？）
> ② 匹配传输方式
> ③ 说出理由

**示例**：*"Video is being streamed to a large screen 2 metres away."*
> → **Serial, full-duplex**。理由：距离虽短但需**双向同时**通信（控制信号 + 视频流）；serial 抗干扰强。

**示例**：*"Data is transferred between components inside a computer."*
> → **Parallel**。理由：距离**极短**，不会有 **skew** 问题；parallel **传输速度快**，适合内部高速传输。

### 3️⃣ "Explain how ARQ detects errors"（3–4 分）
按上面 7 步流程写。**必须包含**：CRC → positive/negative acknowledgement → timeout → re-send。

### 4️⃣ 表格判断题（Tick the appropriate column）⭐
考纲和真题都爱出这种题。**看清题目说 "more than one column, or none"**。

**速查表**

| 描述 | 答案 |
|---|---|
| An extra bit is sent with each byte of data | **Parity check** |
| Makes use of positive and negative acknowledgement | **ARQ** |
| Uses timeout to determine if data needs to be re-sent | **ARQ** |
| If an error is found, a request is made to re-send the data | **ARQ** |
| Re-calculation is made on any additional data values sent with the main data block | **Checksum** |
| Method used to determine **which bit** in a data block has been altered | **Parity check**（parity block）|
| Additional value sent at the end of a block of data used to check if a transmission error occurred | **Checksum** |
| Number of 1-bits are counted before and after a data block has been sent | **Parity check / Checksum** |
| Value used as part of a data packet **trailer** to check if any data corruption has occurred | **CRC** |

### 5️⃣ "Compare" 题
必须**双向对比**：`X is ___ , whereas Y is ___`。单方面陈述不得分。

### 6️⃣ "Explain why … is not reliable"（echo check 必考）
必须写出**具体原因（无法确定错误发生在去程还是回程）**，不能只写 "it is not reliable"。

---

## ⚠️ 高频失分点汇总

| # | 陷阱 | 正确做法 |
|---|---|---|
| 1 | 用 "cable" 代替 "wire" | 用 **wire / channel**（评分明确提到这点）|
| 2 | 混淆 **direction**（simplex/half/full）和 **method**（serial/parallel）| 这是**两个独立维度**，可组合 |
| 3 | 把包交换写成"数据直接传送" | 必须写 **broken down into packets** + 每包**独立路由** |
| 4 | 奇偶校验只说"检查错误" | 要写清 **parity bit 设在最左位** + **odd/even 的 1 的个数规则** |
| 5 | 忘记奇偶校验**查不出 2 位同时出错** | 这是必考的局限 |
| 6 | 混淆 **checksum** 和 **check digit** | checksum = 传输阶段；check digit = **数据输入**阶段 |
| 7 | 非对称加密只说 "uses two keys" | 必须说明 **public key 加密、private key 解密** |
| 8 | 对比题只写一边 | 必须 **both similarities and differences** |
| 9 | ARQ 漏掉 **timeout** | timeout 是 ARQ 三大要素之一（+/- acknowledgement + timeout）|
| 10 | 把校验位用途说成"检测传输错误" | 校验位检测的是**数据输入错误**（transposition、phonetic 等）|
| 11 | 写 **cable** 或 **path** 代替 **wire** | 用 **wire / channel / line**（判分明确 **TV**）|
| 12 | 路由器题只说"每个包走不同路线" | 必须写 **router determines/assigns the route**；"best path" 单独写不给分 |
| 13 | "it is faster" / "it is better" 没有比较对象 | 必须写清**跟什么比**或**用来做什么**（"fast alone is NE"）|
| 14 | USB 写"可以长距离传输" | 2026 判分**明确拒绝**这一条 |
| 15 | 加密说成"防止数据被偷 / 被读" | 数据**仍可能被截获**，只是变得 **meaningless** |
| 16 | 问"为什么选这个方法"却答"这个方法是什么" | 问 why 答**理由**；问 how 才答**流程** |
| 17 | ARQ 题把正应答和负应答混着写 | 题目说 positive 就**只写 positive 路径** |
| 18 | 对称加密只说 "uses a key" | 必须写 **the same key**（加密解密用同一把）|
| 19 | echo check 写"要求重发" | 重发是 **ARQ**；echo check 是**发回比对** |
| 20 | 选方法的题把力气花在"选择"上 | **"No mark for choice"** —— 分数只给**匹配的理由** |
| 21 | 包结构把 **payload** 写进 header | header 只有**地址 + 包序号**；payload 是数据本身 |
| 22 | 奇偶校验说"校验位告诉接收方应该是奇还是偶" | 校验位是**按 1 的个数算出来设的**，不是指示器 |

---

## 📊 真题实证（2020–2026 考频与官方答案）

### 考频表

| 考纲点 | 出现频率 | 典型分值 | 优先级 |
|---|---|---|---|
| **2.1.2 serial/parallel + simplex/half/full** | **每场必考**（2025/2026 每套卷） | 2–6 | ★★★ |
| **2.2.2 查错方法（parity/checksum/echo）** | **每场必考**（2020–2026 无例外） | 1–6 | ★★★ |
| **2.3.2 对称 vs 非对称加密** | 多数场次；**2025 起重心转向非对称 + "密钥/密文"定义** | 1–8 | ★★★ |
| **2.1.1 数据包与包交换** | 2023 起多数场次（2020–2022 完全没有） | 1–6 | ★★★ |
| 2.2.4 ARQ | 多数场次 | 3–6 | ★★☆ |
| 2.2.3 校验位 | 多数场次 | 3–4 | ★★☆ |
| 2.1.3 USB | **2022/2023 完全没考**，2024 只作干扰项，2026 回归 | 1–3 | ★★☆ |
| **ISBN 算法** | **整份题库 0 次** | — | ☆☆☆ |

> ⚠️ **USB 的 IP 定位**：它是 Unit 2 里唯一「时有时无」的考点。**别把时间花在 USB-C 的 100W/10Gbps 这些数字上**，考的是 **serial + 不能长距离 + 自动检测/防插反** 这几条。

---

### 官方判分答案（背英文原文）

**① 传输方式的得分分解 —— 这是本单元最关键的结构认识 ⭐⭐**

| 写法 | 得分点（**一个点一分**） |
|---|---|
| **Serial** | "Data is sent **one bit at a time**" + "down a **single wire**" |
| **Parallel** | "uses **multiple wires**" + "sends **multiple bits** of data at a time" |
| **Simplex** | "Data is sent in **one direction only**" |
| **Half-duplex** | "in **both directions**" + "**not at the same time**" |
| **Full-duplex** | "in **both directions**" + "**at the same time**" |

**2026 June Q2(c) 的 6 分答案原文**：
> Any six from (**one mark for benefit (MAX 3), one mark for expansion (MAX 3)**):
> - Data is sent **one bit at a time** … so bits are **less likely to be skewed** … so it can be safely sent across a **longer distance**
> - Data is sent along a **single wire** … so **less chance of interference/crosstalk** … so bits are less likely to be lost
> - Data is sent in **both directions at the same time** … so there is **no delay** between computers sending and receiving data

→ **得分结构 = 说特征（1 分）+ 展开后果（1 分）**。只写特征最多拿一半。

判分：*"**MP2 – cable/path is TV**"* → 写 **cable** 或 **path** **不给分**，必须是 **wire**。*"MP1 – **BOD** bit by bit"*。

**② 数据包三部分**（2025 Nov P13 的 6 分题官方答案）
> - **Header** — originator's/sender's (IP) address, destination/receiver's (IP) address, **packet number**
> - **Payload** — the data itself
> - **Trailer** — **end of packet notification**, error checking data

判分宽容：*"**BOD** head for header and trail for trailer."*

**③ 路由器的角色**（3 分，0478/12 June 2026 官方答案）
> - **examines/searches the packet** to find the destination IP address
> - **sends/forwards** the packet towards its destination
> - **determines/assigns the route**
> - fastest/shortest/**least-traffic** route
> - uses/updates a **routing table**
> - checks/updates **hop count / TTL**

⚠️ 判分：*"Do not accept generic statement like 'each packet takes a different path' **if there is no reference to the router determining/assigning the path**."*
⚠️ *"**best path is TV**"* —— "best path" 单独写不给分。

**④ 为什么需要重排**（2025 Summer P11 官方答案）
> - The packets **arrive in the wrong order** // Each packet could take a different route
> - Some packets may **take longer than others** to be transmitted
> - Some packets may **not arrive / be corrupted** and need to be requested again

**⑤ 偶校验如何检测错误**（4 分，2025 Summer P12 官方答案）
> - A parity bit is added to each byte … **to make the number of 1s/0s even**
> - that will be **1 if the number of 1s/0s is odd**
> - The number of 1s/0s in each byte is **counted after transmission**
> - If any bytes have an **odd** number of 1s/0s **an error is detected**

**⑥ 为什么奇偶校验查不出错**（2 分，0478/12 June 2026 官方答案）
> - A **transposition error** has occurred // Bits have been **interchanged/changed places**
> - **Even number of bits** has flipped/changed
> - … doesn't record the location of bits … so the **count/total of the 1s/0s is still the same** … so it will still meet the parity set

⚠️ 两条判分：*"MP1 – **Even number of errors is TV**"*（必须写 even number of **bits**）；*"MP2 – **number of 1s is correct is NE**"*。

**⑦ checksum 的 3 分答案**（0478/13 June 2026 官方答案）
> - The checksum value is **sent with the data**
> - The receiving device uses the **same algorithm** to calculate the checksum value // **recalculated by the receiver**
> - The checksum values are **compared**
> - If the same **no error** has occurred // If different **an error** has occurred

**⑧ echo check 的 3 分答案**（2025 Nov P11 官方答案）
> - (Data being sent to the receiver) and a **copy sent back** from the receiver to the sender
> - Sending device **comparing** the original data and the copy
> - If original data and copy **don't match** an error is detected

**⑨ ARQ + 肯定应答（positive acknowledgement）**（2023 Winter P13 官方答案）
> - **Timer is started** when the sending device transmits a data packet to receiver
> - Receiving device **checks the data packet for errors**
> - Once the receiving device knows the packet is **error free** it sends an **acknowledgement** back to the sending device … and the **next packet is sent**
> - If the sending device **does not receive an acknowledgement before the timer ends** … a **timeout** occurs
> - … the data packet is **resent** … **until acknowledgement received** // until max number of attempts reached

**⑩ 密钥（encryption key）的定义**（2 分，0478/13 June 2026 官方答案）
> - A **string of characters/numbers** used to encrypt data
> - Used by an **algorithm/cipher** (to encrypt/decrypt the data)

判分：*"MP2 – **Accept 'It is an algorithm/cipher'**"*

**⑪ 加密的两种类型**（1 分题，2026 官方答案）
> **Symmetric // synchronous** 或 **Asymmetric // asynchronous**
> **BOD**：Single key encryption / public key and private key encryption
> ❌ **"Do not allow protocols that use encryption e.g. SSL"**

**⑫ 密文的名字**：`Cipher / cypher text`（**BOD** "cipher" 或 "cipher data" 单独写也认）

**⑬ 非对称加密的 8 分填空**（2025 Summer P11 Q6(a) 官方答案顺序）
> `algorithm → plain text → cipher text → meaningless → public/private → private/public → public → private`

⚠️ 判分：**第 6 空必须是第 5 空的相反顺序** —— 公钥/私钥的配对必须**内部自洽**，不能两空写同一个。

**⑭ 为什么用非对称而不是对称**（1 分）
> - The process is **more secure**
> - Do not need to worry about **key exchange**

**⑮ 对称加密 4 分答案**（2022 Winter P11 官方答案）
> - 先拿 1 分：Data is encrypted and decrypted using the **same key/algorithm**
> - 再拿 3 分：Data before encryption is known as **plain text**；Data after encryption is known as **cypher text**；Key is sent to receiver (to allow data to be decrypted)

---

### 官方判分规则（这几条决定你拿不拿到分）

| 规则 | 官方原文 |
|---|---|
| **cable / path 不给分** | **"MP2 – cable/path is TV"** —— 必须写 **wire**（或 channel / line）|
| **"best path" 太笼统** | "Do not accept generic statement like 'each packet takes a different path' if there is no reference to the router determining/assigning the path"；**"MP4 – best path is TV"** |
| **"fast" 单独写不给分** | **"Fast/faster alone is NE"** —— 必须写出**跟什么比**或**用来做什么** |
| **USB 不能写"可以长距离"** | 2026 June 判分明确 **"Do not accept 'can be used over long distance'"** |
| **check digit 不用于传输** | **"Do not accept check digit. This is for data entry and not for transmission."** |
| **偶数是修饰 bit 的** | **"Even number of errors is TV"** —— 必须写 even number of **bits** |
| **加密题不能答协议** | **"Do not allow protocols that use encryption e.g. SSL"** |
| **选方法的题，选择本身不给分** | **"No mark for choice."** —— 分数只给**与所选方法匹配的理由** |

---

### 三条 Unit 2 独有的死穴

**① 加密不是"防止数据被偷"，而是"被偷了也看不懂"。**
这条错误在 **2020 March → 2025 Nov 连续 8 份考官报告**里出现。官方用词是 **meaningless**，**不是 "unreadable"**（2025 Summer 明确指出 unreadable 不给分）。
正确框架：**数据仍然可能被截获 / 被偷，但它已经变得毫无意义。**

**② check digit 属于数据输入（data entry），不属于数据传输（transmission）。**
2026 June 判分直接写进 Guidelines。凡是问"传输过程中如何查错"，答案只能从 **parity / checksum / echo check / ARQ** 里选，**写 check digit 直接 0 分**。

**③ USB 连接 ≠ USB 设备。**
考官报告从 2020 Nov 到 2022 Nov 点了 **5 次**：问 USB **传输**，考生答 U 盘**存储**。另外 **"USB" 单独出现太笼统，不给分**。

---

## 🧠 一页纸速记

```
数据包 = HEADER(目的地址+源地址+包序号) + PAYLOAD(数据) + TRAILER(CRC+结束标志)

包交换 = 拆包 → 编号 → 各自选路 → 路由器转发 → 乱序到达后重排

方向：Simplex 单向 | Half-duplex 双向不同时 | Full-duplex 双向同时
方式：Serial 一位一线(远/稳/便宜/无skew) | Parallel 多位多线(快/短距/会skew)

查错：
  Parity       → 加 1 位，1 的个数奇/偶（查不出 2 位错）
  Parity block → 行+列，能定位出错位
  Checksum     → 发送方算，接收方重算，不一致=出错
  Echo check   → 发回比对（不可靠：不知错在去程还是回程）
  Check digit  → 数据输入防错（ISBN、条形码）
  ARQ          → CRC + 正/负应答 + timeout 重传

加密：Symmetric 1 把钥匙（需共享，不安全）
      Asymmetric 2 把（公钥加密 → 私钥解密，安全）
```

---

## 🔗 延伸资源

- 学校课件：`csresource/…/Slides/1 Computer Systems/2 Data transmission/`
- 真题练习：`csresource/…/Past Exam Papers/Questions by Unit/Unit 2 - Data transmission (188 pts)/`
- Revision Guide 第 2 章（含大量 sample Q&A 与评分老师点评）
- 在线练习（按考纲章节分类）：[Save My Exams — 2. Data Transmission](https://www.savemyexams.com/igcse/computer-science/cie/23/topic-questions/) ｜ [PapersDaddy — 0478 Topical Paper 1](https://www.papersdaddy.com/cambridge/igcse/computer-science-0478/resources/topical-past-papers/paper-1)（免费）

---

**上一单元**：[Unit 1 - Data representation](Unit 1 - Data representation.md) | **下一单元**：[Unit 3 - Hardware](Unit 3 - Hardware.md)
