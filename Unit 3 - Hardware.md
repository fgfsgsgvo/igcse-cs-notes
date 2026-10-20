# Unit 3 — Hardware 硬件

> **考纲**：Cambridge IGCSE Computer Science 0478 / 0984 (2026–2028) — Unit 3 Hardware
> **试卷**：Paper 1 Computer Systems — **75 分 / 1 小时 45 分钟 / 不允许使用计算器**
> **本单元特点**：**Paper 1 分值最高的单元**（历年真题累计约 505 分）。知识点最多最杂，但**套路最固定**——输入/输出设备、传感器、存储器几乎每年必考，且答案高度模板化。这是**最容易靠背诵拿满分的单元**。

---

## 📋 考纲对照清单

| # | 考纲条目 | 掌握 |
|---|---------|------|
| 3.1.1 | The central processing unit (CPU) / microprocessor | ☐ |
| 3.1.2 | Von Neumann architecture | ☐ |
| 3.1.2 | ALU, control unit (CU) and registers | ☐ |
| 3.1.2 | System buses — control bus, address bus, data bus | ☐ |
| 3.1.2 | Fetch–Decode–Execute cycle | ☐ |
| 3.1.3 | Cores, cache and system clock | ☐ |
| 3.1.4 | Instruction sets for a CPU | ☐ |
| 3.1.5 | Embedded systems | ☐ |
| 3.2.1 | Input devices: barcode scanners, QR code scanners, digital cameras, keyboards, microphones, mouse, 2D/3D scanners, touchscreens | ☐ |
| 3.2.2 | Output devices: actuators, light projectors, printers, 3D printers, LED and LCD screens, speakers | ☐ |
| 3.2.3 | Sensors | ☐ |
| 3.3.1 | Primary memory (RAM and ROM) | ☐ |
| 3.3.2 | Secondary storage | ☐ |
| 3.3.3 | Magnetic, optical and solid-state storage | ☐ |
| 3.3.4 | Virtual memory | ☐ |
| 3.3.5 | Cloud storage | ☐ |
| 3.4.1 | Network interface cards (NICs) | ☐ |
| 3.4.2 | MAC addresses | ☐ |
| 3.4.3 | IP addresses | ☐ |
| 3.4.4 | Routers | ☐ |

---

# 第一部分：计算机体系结构 Computer Architecture (3.1)

## 3.1.1 & 3.1.2 CPU 与冯·诺依曼结构

### CPU 的组成

**English（背这句）**
> The CPU is responsible for the execution and processing of all instructions and data in a computer. It consists of the control unit (CU), the arithmetic and logic unit (ALU), registers, buses, the system clock and primary memory.

**中文理解**

**A microprocessor（微处理器）** 是一块集成电路（microchip / integrated circuit），也叫 processor 或 CPU。它的作用是**解释并执行所有指令、完成算术运算**。

CPU 内部四大件：

| 部件 | 作用（English 背诵版） |
|------|----------------------|
| **Control Unit (CU)** 控制单元 | Reads instructions from memory, generates signals during the FDE cycle to control all components, and synchronises data flow and program instructions throughout the computer. |
| **Arithmetic and Logic Unit (ALU)** 算术逻辑单元 | Allows all arithmetic operations (such as +, −) and logic operations (such as AND, OR) to be carried out. It also allows multiplication and division using **shifting operators**. |
| **Registers** 寄存器 | High-speed areas of memory within the CPU used to store small amounts of data — the address of the next instruction, or the current instruction being decoded. |
| **System clock** 系统时钟 | Produces timing signals on the control bus to ensure all functions are synchronised. |

⚠️ **易错点**
- **Computers can have more than one ALU**（电脑可以有多个 ALU）——这是个冷门考点，出现过。
- ALU 做**乘除法是靠 shifting operators（移位）**实现的，不是"硬算"。
- 问 "role of the CU" 时，别只写 "controls the computer"——必须落到 **fetch instructions from memory** + **generate control signals** + **synchronise** 三个具体动作。

---

### 寄存器 Registers（高频考点，必背）

**English（背这句）** — 问 "describe the role of registers" [4] 时的满分答案骨架：

| 寄存器 | 全称 | 存什么 |
|--------|------|--------|
| **PC** | Program Counter | Stores the **address of the next instruction to be fetched** |
| **MAR** | Memory Address Register | Stores the **address of the memory location currently being read from or written to** |
| **MDR** | Memory Data Register（也叫 buffer register） | Stores the **data that has just been read from memory, or data about to be written to memory** |
| **CIR** | Current Instruction Register | Stores the **current instruction being decoded and executed** |
| **ACC** | Accumulator | Used when carrying out **ALU calculations** — stores data temporarily during the calculations |

**中文理解**

寄存器是 CPU 内部的**超高速小容量存储**，分**通用寄存器（general purpose）**和**专用寄存器（special purpose）**两种。上面 5 个都是专用寄存器。

**记忆口诀**：**PC 看下一条 → MAR 送地址 → MDR 搬数据 → CIR 译当前 → ACC 存结果**

🔧 **答题模板：Describe the role of registers** [4]
> Registers are data holding places which form part of the CPU. They can hold an instruction, an address or data. Registers can be general purpose or special purpose.
> - **Program counter (PC)** stores the address where the next instruction to be fetched can be found
> - **Memory address register (MAR)** stores the address of the memory location currently being read from or written to
> - **Memory data register (MDR)** stores data that has just been read from memory or data which is about to be written to memory
> - **Current instruction register (CIR)** stores the current instruction being decoded and executed
> - **Accumulator (ACC)** stores data temporarily during ALU calculations

💡 4 分 = 至少 4 个**展开说明**的事实。只写 "PC holds address" 而没说 address of what，**不给分**。

---

### 系统总线 System Buses（高频考点）

**English（背这句）**

| 总线 | 方向 | 作用 |
|------|------|------|
| **Address bus** 地址总线 | **Unidirectional** 单向 | Carries **addresses** throughout the system |
| **Data bus** 数据总线 | **Bidirectional** 双向 | Allows **data** to be carried to/from the CPU and memory, and to/from input/output devices |
| **Control bus** 控制总线 | **Bidirectional** 双向 | Carries **signals from the control unit** to all computer components |

**中文理解**

**Buses（总线）** 是在计算机内部传输数据和信号的通道。总线**使用并行传输（parallel data transfer）**，宽度（width）可以是 8 到 64 位。

⚠️ **三个必考细节**
1. **地址总线是单方向的**（只从 CPU 往外送地址），数据总线和控制总线是**双方向的**。这是选择题和连线题的常客。
2. **数据总线上传的数据可以是 address、instruction 或 numerical value**——不光是"数字"。
3. **总线宽度决定了字长（word length/size）和计算机性能**：16 位地址总线可寻址 2¹⁶ = 65536 个内存位置；64 位可寻址 2⁶⁴ 个。

🔧 **答题模板：Describe the role of buses** [3]
> System buses are used in computers to carry out three functions:
> - **address bus** carries addresses throughout the computer system
> - **data bus** carries data to and from the CPU, memory and I/O devices
> - **control bus** carries signals from the CPU to all other components to synchronise all operations

---

### 冯·诺依曼结构 Von Neumann Architecture

**English（背这句）**
> Von Neumann introduced the idea of the **stored program computer**. Its main features are: the concept of a central processing unit (CPU); the processor is able to access memory directly; computer memories can store **programs as well as data**; and stored programs are made up of instructions which can be executed in **sequential order**.

**中文理解**

冯·诺依曼结构的核心突破是**"存储程序"（stored program）**——程序和数据都存在同一块内存里，CPU 可以直接访问内存。这是 1940 年代中期之前所有计算机都没有的。

⚠️ **易错点**：别把 "Von Neumann architecture" 答成 "CPU 里有 ALU 和 CU"。得分点是 **stored program concept** + **programs and data stored in the same memory** + **instructions executed sequentially**。

---

### 取指-译码-执行周期 Fetch–Decode–Execute Cycle（年年考）

**English（背这句）**

**Fetch 取指阶段：**
> The PC contains the address of the next instruction to be executed. The address is copied from the PC to the MAR using the address bus. The contents of the memory location contained in the MAR are then copied into the MDR. The contents of the MDR are then copied to the CIR and the PC is incremented by one so the next instruction can be processed.

**Decode 译码阶段：**
> The instruction is now decoded so that it can be interpreted in the next part of the cycle.

**Execute 执行阶段：**
> The CPU passes the decoded instructions as a set of control signals to appropriate computer components. This allows each instruction to be carried out in a logical sequence.

**中文理解**

完整流程（背下来，按顺序写）：

```
PC 里有下一条指令的地址
  ↓ 用地址总线
地址从 PC 复制到 MAR
  ↓
MAR 中地址对应的内存内容 → 复制到 MDR
  ↓
MDR 的内容 → 复制到 CIR
  ↓
PC 加 1（指向下一条指令）
  ↓
CIR 中的指令被译码 (decode)
  ↓
CPU 把译码后的指令作为控制信号发给各部件 (execute)
```

⚠️ **反复出现的失分点**（Examiner Report 多次点名）：
- **必须写 "PC incremented by one"**——这是 Fetch 阶段独立的得分点，漏掉就丢分。
- 地址总线**只在 PC→MAR 这一步**用到；从内存取出内容到 MDR 用的是**数据总线**。写混不给分。
- 有考生写 "the instruction is fetched from the hard drive"——**错**，指令从**内存 (RAM)** 取，不是硬盘。

🔧 **答题模板：Describe three actions that take place during the FDE cycle** [3]
> 1. The address of the next instruction is copied from the **PC** to the **MAR** using the **address bus**
> 2. The contents of the memory location are copied into the **MDR**, then into the **CIR**, and the **PC is incremented**
> 3. The instruction is **decoded** and then **executed** as control signals sent to the appropriate components

---

### 3.1.3 核心数、缓存与时钟频率 Cores, Cache and Clock Speed

**English（背这句）**
> The system clock defines the clock cycle used to synchronise all computer operations. In general, **increasing the clock speed increases the processing speed of the CPU**, since it can carry out more processes per second. **Cache memory stores frequently used instructions and data**, and the larger the cache the better the CPU performance. **A quad core processor** is a microprocessor with four independently operating units (cores) that can read and execute CPU instructions.

🔧 **答题模板：Discuss four ways to improve the performance of a CPU** [4]
（这是**满分答案**，必须每条都带"为什么"）

| 方法 | 必须跟上的理由 |
|------|---------------|
| **Increase RAM size** | Since data is constantly moved into and out of RAM, the larger the RAM, the fewer data movements are needed, which increases operational speed |
| **Increase the width of the address bus and data bus** | A wider **address bus** allows more memory locations to be addressed; a wider **data bus** allows more data to be transferred per cycle. Both can improve performance |
| **Increase the clock speed** | It can carry out more processes per second; **however** this needs caution, since it can lead to overheating and potential computer crash as operations become out of synchronisation |
| **Use more cores (e.g. quad core)** | Allows multiple functions to be carried out simultaneously, which greatly improves CPU performance |

⚠️ **"Discuss" 类题目的铁律**：给方法**不加理由 = 0 分**。Examiner's comment 原话：
> "there is no mention of how the methods given would improve performance... The question asked for a **discussion**... this means it is necessary to explain why the methods mentioned would work."

❌ **反面教材**（0 分）："The performance of a computer can be improved by using more RAM, changing the clock speed and using bigger buses."
✅ **正确**："Increasing the clock speed means more FDE cycles can be carried out per second, **but** it risks overheating and out-of-synchronisation operations."

---

### Overclocking 超频

**English（背这句）**
> **Overclocking**, caused by changing the clock speed in the BIOS, can lead to **overheating** and to **non-synchronised instructions**, which can cause the computer to crash.

**中文理解**：超频 = 在 BIOS 里把时钟频率调高。好处是变快，坏处是**过热 + 指令不同步 → 死机**。

---

### Cache 缓存

**English（背这句）**
> Cache is **high-speed RAM that holds a copy of only the most frequently used data or instructions**. Cache is **first checked** when the CPU wants to access data/instructions from primary memory. The larger the cache memory size, the better the CPU performance.

**中文理解**：Cache 是 **CPU 与 RAM 之间的高速缓存**（现代 CPU 通常分为 L1/L2/L3 多级）。CPU 要数据时**先查 cache**，查到就直接用（快），查不到才去 RAM（慢）。Cache 越大，命中率越高，CPU 越快。

**连线题常考配对**：
- "Temporary storage space that stores frequently used data and instructions" → **Cache**
- "Can lead to overheating and non-synchronised operations in the CPU" → **Overclocking**
- "Can improve the performance of the CPU by increasing its width" → **Address/data bus**
- "Ensures correct synchronisation of all computer operations" → **System clock**
- "Part of the processing chip that does the processing work" → **Core**

---

### 3.1.4 指令集 Instruction Set

**English（背这句）**
> Instructions are a set of operations that need to be decoded in sequence; each operation is made up of an **opcode** and an **operand**. The **opcode** informs the CPU what operation needs to be done. The **operand** is the data which needs to be acted on, or refers to registers in memory. A number of allowed opcodes exist and these are referred to as the **instruction set**. Instruction sets are **low-level language instructions** that instruct the CPU how to carry out an operation.

**中文理解**

一条指令 = **操作码 (opcode)** + **操作数 (operand)**

举例：`ADD 5` → `ADD` 是 opcode（干什么），`5` 是 operand（对谁干）。

**Instruction set（指令集）** = 某个 CPU 能识别的**所有 opcode 的集合**。它是**低级语言指令**。

⚠️ 易错：instruction set 是**低级语言**，不是高级语言。ALU 乘除法用 **shifting operators**。

---

### 3.1.5 嵌入式系统 Embedded Systems

**English（背这句）**
> An **embedded system** is a combination of **hardware and software designed to carry out a specific task**. Hardware can be electronic, electrical or electro-mechanical. Embedded systems can be based on a **microcontroller**, **microprocessor** or **system on a chip (SoC)**.

**三种实现方式**：

| 类型 | English |
|------|---------|
| **Microcontroller** | A CPU with **RAM, ROM and peripherals all embedded on a single chip**, to carry out a specific task |
| **Microprocessor** | An integrated circuit consisting of **a CPU only** (no peripherals) |
| **System on a chip (SoC)** | Usually includes **a CPU, memory, I/O ports and secondary storage all on a single chip** |

🔧 **答题模板：Benefits and drawbacks of using embedded systems in household devices** [6]
（3 好处 + 3 坏处，每条一句）

**Benefits 好处**
| | English |
|---|---------|
| 1 | They are **small in size** and therefore easy to fit into devices |
| 2 | Compared to other systems, they are relatively **low cost to make** |
| 3 | They are usually **dedicated to one task**, making for simple interfaces and often **no requirement for an operating system** |
| 4 | They **consume very little power** |
| 5 | They can be **controlled remotely** using a mobile phone |
| 6 | **Very fast reaction to changing input** — they operate in real time and are feedback orientated; with mass production comes reliability |

**Drawbacks 坏处**
| | English |
|---|---------|
| 1 | It can be **difficult to upgrade** some devices to take advantage of new technology |
| 2 | **Troubleshooting faults** in the device is a **specialist task** |
| 3 | Although the interface can appear simple (such as a single knob), it can be **more confusing in reality** (changing the time on a cooker clock can require several steps) |
| 4 | Any device that can be accessed over the internet is **open to hackers, viruses and so on** |
| 5 | Due to the difficulty in upgrading and fault finding, devices are often **thrown away rather than repaired (very wasteful)** |
| 6 | Can lead to **environmental issues** created by an increase in the "throw away" society |

**常见例子**：security systems、set-top boxes、lighting applications、vending machines、washing machines、motor vehicles（fuel injection, GPS, ABS）。

---

# 第二部分：输入与输出设备 Input and Output Devices (3.2)

## 3.2.1 输入设备

### 条形码扫描器 Barcode Readers（高频）

**English（背这句）**
> Barcodes are a series of **dark and light parallel lines of varying thickness**. They are read by a scanner that uses a **red laser or red LED light source**. Reflected red light is read by **photoelectric cells (sensors)** that create a **digital sequence of dark and light**.

**工作原理（背）**：
1. 红光/红激光照到条形码上
2. 深色线条**吸收**红光，浅色线条**反射**红光
3. **光电元件 (photoelectric cells)** 检测反射光，产生**数字信号序列**（如 LDDDDLD = 0111101）
4. 条形码作为**主键 (key field)** 在**产品数据库**中唯一标识该商品
5. 读出商品详情（如价格），同时自动更新库存

**Advantages to the management 对商家的好处**
- Much easier and faster to change prices on stock items
- Much better, more up-to-date sales information / sales trends
- No need to price every stock item on the shelves（省时省钱）
- Allows for **automatic stock control**
- Possible to check customer buying habits more easily by linking barcodes to loyalty cards

**Advantages to the customers 对顾客的好处**
- **Faster checkout queues**（员工不用记/查价格）
- **Errors in charging customers is reduced**
- The customer is given an **itemised bill**
- Cost savings can be passed on to the customer
- Better track of "sell by dates" so food should be fresher

---

### 二维码 QR Codes（高频，与 barcode 对比是必考）

**English（背这句）**
> Quick response (QR) codes are another type of barcode made up of a **matrix of filled-in dark squares on a light background**. QR codes hold considerably more information than barcodes (**up to 7089 digits or 4296 characters**). **Three large squares at the corners** are used to align the QR code when it is being scanned.

**读取方法（4 步，背）**：
1. Camera on smartphone or tablet is pointed at the QR code
2. A **stored app processes the image** taken by the camera
3. The browser automatically reads the data generated by the app and **decodes any web addresses** embedded in the QR code
4. Any weblinks are then sent to the smartphone or tablet

🔧 **答题模板：Differences between the methods used to read barcodes and to read QR codes** [2]
> A barcode is read using a **red laser or LED light source** and **photoelectric cells** to detect reflected light, whereas a QR code is read by **a camera** which takes an image that is **processed by an app**.

🔧 **答题模板：Advantages of QR codes compared to barcodes** [2-3]
> - They can hold **much more information**
> - There will be **fewer errors**; the higher capacity allows the use of **built-in error-checking systems** (normal barcodes contain almost no data redundancy)
> - QR codes are **easier to read** — they don't need expensive laser or LED scanners, they can be read by the cameras on smartphones
> - It is easy to **transmit QR codes** as text messages or images
> - It is possible to **encrypt** QR codes, giving greater protection

⚠️ **Disadvantages of QR codes（必背，单独考过）**
- More than one QR format is available
- **QR codes can be used to transmit malicious code — known as attagging**（这个专有名词要记住！）since anyone can generate QR codes using free apps

---

### 数码相机 Digital Cameras

**English（背这句）**
> The image through the camera lens is captured on **photodiodes (charge coupled devices, CCD)** and converted into **pixels** which form an electronic matrix of the image which can be stored in memory. Microprocessors in the camera **automatically control many camera functions**, such as shutter speed, focus, aperture size, flash and "red eye" removal.

**传输方式**：USB port、Bluetooth（无线）、memory card reader。

---

### 键盘 Keyboards

**English（背这句）**
> Each character on a keyboard has an **ASCII value**. The computer is able to detect which key is pressed, which allows it to determine the character that was selected.

**缺点（必背）**：Entry of data via a keyboard is a **slow process** which is also **prone to error** and can lead to injuries such as **repetitive strain injury (RSI)**.

**两种形式**：physical keyboard（USB 或蓝牙连接）vs virtual keyboard（触摸屏上的）。

---

### 麦克风 Microphones

**English（背这句）**
> Microphones **convert sound into electric currents of varying amplitude**. A **diaphragm** in the microphone vibrates and a **copper coil and cone** attached to the diaphragm create an electric current as the coil vibrates back and forth. The electric current can be converted into **digital data** and then stored in computer memory.

**用途**：作为 sensor（防盗系统检测声音）、语音输入文字（对无法用键盘的残障人士特别有用）、配音。

---

### 光学鼠标 Optical Mouse

**English（背这句）**
> The optical mouse uses **tiny cameras and a red LED light source** to allow the exact position of the mouse to be calculated. Unlike a mechanical mouse, the optical mouse can work on **any surface** and has **no moving parts to wear out**.

🔧 **Advantages of an optical mouse compared to a mechanical mouse** [3]
> - No moving parts, therefore **more reliable**
> - **Dirt can't get trapped** in any components
> - **No need for special software**

🔧 **Advantages of a wired mouse (USB) compared to a wireless mouse** [3]
> - Unlike Bluetooth, wired connections have **no signal loss**
> - **Cheaper to use** (no need for batteries)
> - **Fewer environmental issues** (for example, disposal of batteries)

---

### 扫描仪 Scanners（2D / 3D）

**2D 扫描仪**

**English（背这句）**
> 2D scanners are used to scan in documents. The information on the document is converted into an **electronic format** that can be stored on computer memory.

**OCR 软件**：Computers equipped with **optical character recognition (OCR)** software allow the scanned text to be converted into a **text file format** which can then be imported into a word processor.

**用途**：机场读取护照实现自动边检——扫描护照照片并与边检摄像机拍到的图像比对，这叫 **facial recognition（人脸识别）**。

**扫描格式（三选一考点）**：

| 格式 | 用途 |
|------|------|
| **PDF** | Portable Document Format |
| **TIFF** | Tagged Image File Format — **recommended for uncompressed scanned images** |
| **JPEG** | Joint Photographic Experts Group — **standard format if a compressed image is required** |

**3D 扫描仪**

**English（背这句）**
> 3D scanners scan **solid objects** and produce a 3D image that can then be used in **computer-aided design (CAD)** software or even sent to a **3D printer** allowing the scanned object to be duplicated. 3D scanner technology uses **lasers, X-rays, magnetic resonance or white light**.

⚠️ **关键术语**：把人体解剖部位切成薄片来构建 3D 图像叫 **tomography（断层扫描）**；**Tomography uses X-rays**；**MRI scanners use radio frequencies**。

💡 记住这句对比：3D 扫描仪**effectively the reverse of what 3D printers do**（跟 3D 打印机正好相反）。

---

### 触摸屏 Touchscreens（三选一，考过多次）

**English（背这句）** — 三种技术对比表（背诵版）：

| | **Capacitive** 电容式 | **Infrared** 红外式 | **Resistive** 电阻式 |
|---|---|---|---|
| **原理** | Relies on fingers touching the screen causing a **change in the electrostatic field** (change in current flow) | Uses a glass screen and an array of **sensors and infrared transmitters**; where the **infrared beam is broken** by a finger, the signal to some sensors is broken or reduced | Made up of **two layers of polymer and glass**; a voltage is applied across the two surfaces; when the top layer is touched it makes contact with the bottom layer, **completing a circuit** |
| **定位** | Microprocessor calculates the point where the finger touches | Microprocessor calculates where the screen was touched | Detected where a **change in voltage** occurred; microprocessor calculates coordinates |
| **多点触控** | ✅ (projective type allows multi-touch — pinching and sliding) | ✅ **Allows multi-touch facility** | ❌ **Doesn't allow multi-touch** |
| **优点** | Good clarity in all lighting conditions; durable, tolerates scratches | **Good screen durability**; not severely affected by scratches or even cracked screens | **Good resistance to dust and water** |
| **缺点** | Technology can be **sensitive to magnetic fields or microwaves** | Can be **sensitive to moisture** on the screen; can be **sensitive to light interference** | **Low sensitivity**; doesn't allow multi-touch; **vulnerable to scratches and cracked layers** |

🔧 **答题模板：Advantages and disadvantages of [named] touchscreen technology** [5]
> 选一种，写 2 优 + 2 缺 + 1 原理/应用，凑 5 分。**别只写优缺点而不带理由**。

💡 触摸屏都支持：**bare fingers or a special stylus**（裸手指或专用触控笔）。

---

## 3.2.2 输出设备

### 执行器 Actuators（传感器题必配）

**English（背这句）**
> When a computer or microprocessor is used to control a process (such as a conveyor belt or a valve), it is usually necessary to use an **actuator** to start/stop the conveyor belt or open/close the valve. An actuator is a **mechanical or electro-mechanical device**, such as a **relay, solenoid or motor**.

⚠️ **Actuator 是输出设备**，不是输入设备——这是最容易搞混的点。传感器进、执行器出。

---

### 投影仪 Light Projectors

**English（背这句）**
> Light projectors are used to **project computer output onto a larger screen or interactive whiteboard**. The two most common types are **digital light projectors (DLP)** and **liquid crystal display (LCD)** projectors.

| | **DLP** | **LCD** |
|---|---|---|
| **原理** | Uses many **micro mirrors** arranged on a **DMD chip**; mirrors move according to data from the computer; produces a greyscale image (**1024 shades of grey**); a bright light passes through an **RGB filter** converting it into a full-colour image | A powerful beam of light is sent to a **chromatic-coated mirror** which splits the image into **red, green and blue components**; three versions of the image are produced and **recombined using a prism** |
| **优点** | Higher contrast ratios; higher reliability/longevity; **quieter running**; uses a single DMD chip (no issues lining up images); smaller and lighter; better suited to dusty or smoky atmospheres | **Gives a sharper image**; better colour saturation; **more efficient use of energy** — generates less heat |
| **缺点** | Image tends to suffer from **"shadows"** when showing a moving image; **greyscale/black-level reproduction can be less accurate**; colour definition frequently not as good | Contrast ratios not as good; **has a limited life**; LCD panels are organic and **degrade with time** (screens turn yellow) |

---

### 打印机 Printers

**喷墨打印机 Inkjet**
**English（背这句）**
> Inkjet printers rely on **spraying liquid ink droplets from a reservoir onto paper**. They use either **thermal bubble or piezoelectric technology** to create the ink bubbles and droplets. **Stepper motors** move paper up a line at a time and the **print head** moves across the page left to right. Ink cartridges and paper trays are only suitable for **relatively small print runs**.

**激光打印机 Laser**
**English（背这句）**
> Laser printers rely on using **dry powder ink (known as toner)**; this solid ink is **melted onto the paper using a fuser**. The position where text or images is to be printed is **charged negatively on a drum using a laser**. **Positively charged ink then sticks to the areas of negative charge** on the drum, which is then transferred to a sheet of paper as the drum rotates. **The whole page is produced in one go.** Toner cartridges and paper trays are much larger, so laser printers are more suitable for **large print runs**.

🔧 **答题模板：Choose a printer for [scenario]** — 判断标准：
- **一次一张 / 高质量彩色照片 / 少量** → **Inkjet**（便宜，初期成本低）
- **几百份传单 / 大批量 / 黑白为主 / 速度快** → **Laser**（单页成本低，快）

---

### 3D 打印机 3D Printers

**English（背这句）**
> 3D printers are used to produce **solid objects that actually work**; they are based on inkjet and laser printer technology. A solid object is **built up from very thin layers of material**; the printing medium can be **powdered resin, powdered metal, paper or ceramics**. 3D printing is an example of **additive printing** (an object is built up layer by layer).

**两种工艺**：
- **Direct 3D printing**：print head 左右上下移动，逐层堆积（typically **0.1mm thick**）
- **Binder 3D printing**：每层**两遍**——第一遍铺干粉，第二遍喷**binding agent（粘合剂）**把粉末层粘住

**用途**：medicine（prosthetic limbs、reconstructive surgery）、aerospace（light-weight parts）、fashion and art（one-off dresses、copies of rare paintings）、vintage car parts（no longer available）。

---

### LED 与 LCD 屏幕

**English（背这句）**
> An **LED screen** is made up of many tiny light emitting diodes. Each LED is **red, green or blue**. By varying the electric current to each diode, its brightness is controlled which results in millions of different colours. LED screens are used in **large outdoor advertising displays and large scoreboards**.
>
> **LCD screens** are made up of millions of tiny **liquid crystals arranged as a matrix (array) of pixels**. By varying the electric field to the liquid crystals their properties change. **Since LCDs do not produce any light, they need to be backlit** with a light source, such as LEDs.

**为什么用 LED 做 LCD 的背光（3 点）**：
1. They **reach maximum brightness immediately**
2. They produce a **very white light** which gives good colour definition
3. They **last almost indefinitely** and consume **very little power**

**OLED（有机发光二极管）**——LCD-LED 的替代品，因为它：
1. Allows **very thin screens (2mm or less)**, which means they can be formed into almost any shape
2. Provides **brighter colours** than LED backlit LCD screens
3. Allows for **true black**, unlike LCD
4. Consumes **very little power**

💡 冷知识考点：**Many televisions are advertised as LED when in fact they are LCD screens backlit with LEDs.**

---

### 扬声器 Speakers

**English（背这句）**
> Loudspeakers produce sound from **varying electric currents**. If sound is stored digitally on a computer, it needs to pass through a **digital to analogue converter (DAC)** first. Speakers are made up of a **paper/plastic cone, permanent magnet and a coil of wire wrapped around an iron core**. Varying electric currents cause the iron core to vibrate; this is connected to the cone which therefore also vibrates **producing sound**.

---

## 3.2.3 传感器 Sensors（年年考，模板最固定）

### 核心概念

**English（背这句）**
> Sensors are **input devices that read physical properties from their surroundings** (for example, temperature or light). Sensors **constantly send signals to a microprocessor**; they usually pass through an **analogue to digital converter (ADC)** first, since computers can only understand binary (digital) data.

⚠️⚠️ **最重要的失分点**（Examiner's comment 原文点名）：
> "there is the very common error of stating sensors only send data **when they detect a change in conditions** — **this is incorrect, since sensors constantly send data to the microprocessor**. They also incorrectly claim that **the sensors control the process**. Only one mark would be awarded for the whole part."

**记住两句话**：
1. Sensors **constantly** send data — **不是**"变化时才发"
2. Sensors **不控制**过程 —— **microprocessor 才控制**，传感器只提供数据

---

### 三种核心概念的区别（必考）

🔧 **答题模板：Explain the difference between monitoring and control** [2]
> **Monitoring** means the computer/microprocessor **compares the sensor data to stored data and produces a warning sound or screen output to alert the user** — but **takes no action**. Examples: monitoring a patient's vital signs in hospital, an intruder alarm system, pollution levels in a river.
>
> **Control** means the sensor data is again compared to stored/set data and **action is taken if the sensor data indicates the measured parameter is out of range**. Signals are sent out to **alter the process** until the sensor readings are back in range (for example, a valve may need to be opened, or a heater switched off). This is called **feedback**.

**关键差异**：monitoring 只"报警"，control 会"**采取行动改变过程**"。

---

### 传感器 + 执行器 + 微处理器协作（最高频 5 分题）

🔧 **答题模板：Describe how sensors, actuators and a microprocessor interact to control [process]** [5]

（这是历年反复出现的 5 分题，答案高度固定，直接背）

```
                    Sensors (温度/pH/湿度...)
                       ↓
                      ADC          ← 模拟信号转数字
                       ↓
                  Microprocessor   ← 与内存中的预设值比较
                       ↓
                      DAC          ← 数字信号转模拟（驱动执行器）
                       ↓
    Actuator (heater / valve / motor / air conditioning unit)
```

**5 个得分点（一一对应 5 分）**：
1. **[名传感器] sensors constantly collect data** and send it to the microprocessor (via an **ADC**)
2. The microprocessor **compares the incoming data with pre-set data values stored in memory**
3. If the reading is **out of range** (e.g. **temperature < 70°C** / **pH > 3.5**), the microprocessor **sends a signal** to the actuator
4. A **DAC may be needed** to convert the digital signal so it can operate the actuator
5. The actuator **switches on the heater / opens the valve** to bring the reading **back into range** (this is **feedback**)

💡 高分要点（Teacher's comments）：
> "The use of a **diagram of the control system is particularly helpful** in the explanation of how sensors, actuators and a microprocessor interact."

**画图能帮你拿分，也帮考官看懂——强烈建议画上面那个流程图。**

---

### 常见传感器速查表

| 传感器 Sensor | 测什么 | 典型应用（答题举例用） |
|--------------|--------|----------------------|
| **Temperature** 温度 | Measures temperature of the surroundings | control central heating system; control/monitor chemical processes; control temperature in a greenhouse |
| **Moisture** 湿度(土壤) | Measures water levels in, e.g., soil (based on **electrical resistance** of the sample) | control/monitor moisture levels in soil; monitor moisture in a food processing factory |
| **Humidity** 湿度(空气) | Measures the amount of **water vapour** in air (based on the fact that **conductivity of air changes** depending on water present) | monitor humidity levels in a building; monitor humidity in a factory manufacturing microchips; control humidity in a greenhouse |
| **Light** 光敏 | Use **photoelectrical cells** which produce an electric current depending on the **brightness of the light** | switch street lights on/off; switch on car headlights automatically when it gets dark |
| **Infrared (active)** 主动红外 | Uses an **invisible beam of infrared radiation** picked up by a detector; if the **beam is broken**, there is a change in the amount of IR reaching the detector | turn on car windscreen wipers automatically when it detects rain; security alarm system (intruder breaks the beam) |
| **Infrared (passive)** 被动红外 | Measures the **heat radiation given off by an object** | security alarm system (detects body heat); monitor temperature inside an industrial freezer |
| **Pressure** 压力 | A **transducer** that generates different electric currents depending on the pressure applied | weigh lorries at a weigh station; measure gas pressure in a nuclear reactor |
| **Acoustic / sound** 声波 | Basically **microphones** that convert detected sound into electric signals/pulses | pick up the noise of footsteps in a security system; detect sound of liquids dripping at a faulty pipe joint |
| **Gas** 气体 | Most common are **oxygen or carbon dioxide** sensors | monitor pollution levels in the air at an airport; monitor O₂/CO₂ in a greenhouse; monitor oxygen levels in a car exhaust |
| **pH** 酸碱度 | Measure **change in voltages** depending on how acidic the sample is | monitor/control acidity levels in soil; control acidity in a chemical process |
| **Magnetic field** 磁场 | Measure **changes in magnetic fields** — the signal output depends on how the field changes | detect magnetic field changes (mobile phones, CD players); **anti-lock braking systems (ABS)** in cars |
| **Accelerometer** 加速度计 | Measure **acceleration and motion** of an application, i.e. the change in velocity (a **piezoelectric cell** is used) | measure rapid deceleration in cars, and apply **airbags** in a crash; change between portrait and landscape mode in mobile phones |
| **Proximity** 接近 | Detect the **presence of a nearby object** | detect when a face is close to a mobile phone screen and switch off the screen when held to the ear |
| **Flow (rate)** 流量 | Measure the **flow rate of a moving liquid or gas** | respiratory devices and inhalers in hospitals; measure gas flows in pipes (natural gas) |
| **Level** 液位 | Use **ultrasonics** or **capacitance/conductivity** to measure static levels | monitor levels in a petrol tank in a car; pharmaceutical process monitoring powder levels in tablet production; leak detection in refrigerant |

🔧 **答题模板：Describe an application that uses [type] sensor** [3]
**结构 = what + why + how**（Teacher's comments 明确说要这三点）
> **What**: An application of **magnetic field** sensors is in **anti-lock brakes (ABS)** used in vehicles.
> **Why**: To detect when a wheel **locks up**.
> **How**: When a wheel locks up, this is detected by the microprocessor (which is constantly monitoring the sensor readings). The rotational speed of each wheel is carefully controlled by applying braking force wherever necessary to prevent locking up.

❌ **只写 "magnetic sensors are used in mobile phones" = 部分分，丢了 why 和 how**

---

# 第三部分：数据存储 Data Storage (3.3)

## 存储层级总览

```
┌─────────────────────────────────────────────┐
│  PRIMARY MEMORY 主存（CPU 可直接寻址）        │
│   Cache（L1，最快）/ RAM / ROM               │
├─────────────────────────────────────────────┤
│  SECONDARY STORAGE 辅存（CPU 不能直接寻址）   │
│   内部：HDD / SSD                            │
│   外部：DVD/CD、Blu-ray、USB 闪存盘、移动硬盘 │
└─────────────────────────────────────────────┘
```

**容量参考（常考数字）**：ROM chips typically **4 to 8 MiB**；RAM chips typically **1 to 256 GiB**；Secondary storage typically **2 TiB or larger**。

⚠️ **核心区别**：
> Unlike secondary storage, primary memory is **directly addressable by the CPU**. If data on secondary storage is needed by the CPU, it **must first be loaded into RAM** before the CPU can use the data.
> Secondary storage devices are **not directly addressable by the CPU** and are **non-volatile**.

---

## 3.3.1 主存 Primary Memory — RAM vs ROM（必考对比题）

**English（背这句）**（对比表，直接背）

| **RAM** | **ROM** |
|---------|---------|
| **Temporary** memory device | **Permanent** memory device |
| **Volatile** memory | **Non-volatile** memory device |
| Can be **written to and read from** | Data stored **cannot be altered** |
| Used to store **data, files, programs, and the part of the operating system currently in use** | Always used to store the **BIOS** and other data needed at **start-up** |
| **Can be increased in size** to improve operational speed | — |
| Also known as the **Immediate Access Store (IAS)** | — |

🔧 **答题模板：Describe the main differences between RAM and ROM** [3]
> - RAM is a **volatile/temporary** memory device, whereas ROM is **non-volatile/permanent**
> - RAM **can be written to and read from**, whereas data stored in ROM **cannot be altered**
> - RAM stores **data, files, programs and the part of the OS currently in use**, whereas ROM stores the **BIOS and start-up routines**

---

### SRAM vs DRAM

**English（背这句）**

| **DRAM** (Dynamic RAM) | **SRAM** (Static RAM) |
|---|---|
| Consists of a number of **transistors and capacitors** | Uses **flip flops** to hold each bit of memory |
| **Needs to be constantly refreshed** | **Doesn't need to be constantly refreshed** |
| **Less expensive** to manufacture than SRAM | **Has a faster data access time** than DRAM |
| Has a **higher memory capacity** than SRAM | **CPU memory cache makes use of SRAM** |
| **Main memory is constructed from DRAM** | — |
| Consumes **less power** than SRAM | — |

**记忆**：**D**RAM = **D**esktop main memory（便宜、大、要刷新）；**S**RAM = **S**peed cache（快、贵、不用刷新）。

---

## 3.3.3 磁存储 / 光存储 / 固态存储

### 磁存储 Magnetic Storage（HDD）

**English（背这句）**
> Data is stored on **platters** made from aluminium, glass or ceramic, and each surface is **coated in a magnetisable material**. The platters spin at about **7000 revolutions per minute (RPM)** — roughly 117 revolutions per second — and **read/write (electromagnetic) heads** float a fraction of a millimetre above the surface. Disk drives can have several platters; **both sides of the platter are used** and **each surface has its own read/write head**.
>
> Blocks of data are stored in **sectors and tracks**. The time it takes to find and access the required data block is known as **latency**. Once the sector containing the required data block is found, the data in a sector is read **sequentially**; however, actual data access is **direct**.
>
> After a lot of use, data on an HDD can suffer from **fragmentation**, which can seriously affect performance.

---

### 固态存储 Solid-State Storage（SSD / 闪存）

**English（背这句）**
> SSDs operate by controlling the **movement of electrons within NAND or NOR chips**. The data is stored as 0s or 1s in millions of tiny transistors. At each junction in a solid-state **NAND matrix**, there is one transistor called a **floating gate** and another called a **control gate**; this forms a **non-volatile rewritable** memory store.
>
> When a voltage is applied to the **control gate**, **electrons** from an electron source are attracted to it. The control gate is coated in a **dielectric material** causing electrons to be **trapped in the floating gate**, which gives control of the **bit value** stored at each junction.

⚠️ **填空高频词**（做完形填空型题目的关键词表）：
`electrons` / `NAND` / `matrix` / `intersection` / `floating gate` / `control gate` / `bit value` / `leak away` / `moving parts`

**标准填空题答案顺序**：
> Solid-state devices control the movement of **electrons** within a **NAND** chip. The device is made up of a **matrix** and at each **intersection** there is a **floating gate** and a **control gate** transistor. **Electrons** are attracted towards the **control gate** when a voltage is applied. This gives control over the **bit value** stored at each intersection. After 12 months, the charge can **leak away** which means the device needs to be used at least once a year. One of the main advantages of solid-state devices is there are no **moving parts** to wear out.

**SSD 格式**：Memory sticks、flash memory、SD cards、SSDs 都用固态技术。**micro SD cards** 约是普通 SD 卡的一半大小（用于 dashcams、drones）。

🔧 **答题模板：Benefits and drawbacks of SSDs compared to HDDs** [4-6]

**Benefits 好处**
> - **More reliable** (no moving parts)
> - **Much lighter weight**
> - **No need to "get up to speed"** before data access
> - **Less power consumption**
> - **Run much cooler**
> - **Very thin** due to solid-state technology
> - **Much faster data access**

**Drawbacks 坏处**
> - **Longevity (SSD endurance)** is still an issue
> - The memory chips have a **limited number of write cycles** — this can lead to **unrecoverable data loss**
> - If the **controller chip, memory cache, or one of the NAND memory chips** has been damaged, it may be **impossible to recover the data**

---

### 光存储 Optical Media

**English（背这句）**
> CDs and DVDs are optical storage devices that use **red laser light** to read and write data on the disk surface. They have **one spiral track** and data is stored in **pits and lands**, which can be read by an optical head. DVDs often use **dual-layering** to increase capacity.
>
> Blu-ray discs use **blue laser light**. Since the **wavelength of blue light is much shorter** than that of red light, this **increases the storage capacity**, making Blu-ray suitable for **4K high-definition movies**. Blu-ray discs have **built-in encryption** and a **much faster data transfer rate** than DVDs. They can also **automatically search for empty space** on the disk surface, preventing over-recording. Blu-ray discs allow for **greater interactivity** than DVDs.

**对比表（背数字）**：

| Disk type | Laser colour | Wavelength (nm) | Disk construction | Track pitch (µm) |
|-----------|--------------|-----------------|-------------------|------------------|
| **CD** | red | **780** | single 1.2 mm polycarbonate layer | **1.60** |
| **DVD (dual-layer)** | red | **650** | two 0.6 mm polycarbonate layers | **0.74** |
| **Blu-ray (single layer)** | blue | **405** | single 1.2 mm polycarbonate layer | **0.30** |
| **Blu-ray (dual-layer)** | blue | **405** | two 0.6 mm polycarbonate layers | **0.30** |

**逻辑链（不用背数字也能推）**：**波长越短 → track pitch 越小 → 单位面积能存的数据越多 → 容量越大**

---

## 3.3.4 虚拟内存 Virtual Memory（高频）

**English（背这句）**
> **Virtual memory** is the **RAM plus swap space** (which is allocated storage space on an HDD or SSD). RAM is known as the **physical memory**. New data is loaded into RAM from the HDD/SSD whenever required and "old" data is moved out to HDD/SSD as and when required. **Memory mapping** is used to keep track of where data is. Part of memory mapping is called **paging**, which is used by memory management to store and retrieve data (a **page** is a fixed length contiguous block of data).
>
> Virtual memory gives the **illusion of unlimited RAM**; even when RAM is "full", pages of data can be moved to and from HDD/SSD.

**Benefits 好处**
> - Programs **can be larger than physical RAM** and still be executed
> - **Reduces the need to buy and install extra RAM** (which is expensive)

**关键术语**：
- **Swap space** = HDD/SSD 上分配出来专门当"假 RAM"用的空间
- **Paging** = 把数据分成固定长度的 page 来回搬运
- **Disk thrashing** = 页面在 HDD 和 RAM 之间**频繁来回搬运**，导致读写头疯狂移动，**实际执行的计算很少**
- **Thrash point** = 系统忙于搬运数据以至于几乎不执行任何实际运算的状态

⚠️ **易错**：SSD **不会**出现同样的 thrashing 问题，因为它**没有移动部件**。

---

## 3.3.5 云存储 Cloud Storage

**English（背这句）**
> Cloud storage is the storing of vast quantities of data on **remote physical servers**. When using cloud storage, the same data is stored on **more than one server** in case of maintenance/repair — this is called **data redundancy**.

**三种类型（必考"选哪种 + 为什么"）**：

| 类型 | English |
|------|---------|
| **Public cloud** | The client and cloud storage provider are **different companies** |
| **Private cloud** | A **dedicated system behind a firewall** where the client and storage provider **operate as a single entity** |
| **Hybrid cloud** | A **combination of public and private** cloud provider where the **most sensitive data is stored on the private cloud** |

🔧 **答题模板：Which type of cloud storage would be most appropriate? Explain your choice** [2]
> **Private cloud** — because the data is **sensitive/confidential** (client drawings) and **behind a firewall**, so it can only be accessed by the company and its clients; the client and provider operate as a single entity.

🔧 **答题模板：Benefits and drawbacks of cloud storage** [3-4]

**Benefits 好处**
> - Files can be accessed **at any time from any device anywhere in the world**, provided internet access is available
> - **No need to carry an external storage device** or use the same computer
> - Provides **remote back-up of data**, alleviating data loss / aiding disaster recovery
> - If the customer's **hard disk fails**, cloud storage allows **recovery of their data**
> - Offers **almost unlimited storage capacity**

**Drawbacks 坏处**
> - If the customer has a **slow or unstable internet connection**, they would have problems accessing/downloading data
> - **Costs can be high** if large storage capacity is required; expensive data transfer limits with the ISP
> - The **potential failure of the cloud storage company** poses a risk of loss of all back-up data
> - **Data security issues** — how safely is the data protected from hacking, natural disasters and malware?

---

# 第四部分：网络硬件 Network Hardware (3.4)

## 3.4.1 网卡 NIC

**English（背这句）**
> A **network interface card (NIC)** is needed to **allow a device to connect to a network** (for example, the internet). The NIC **contains the Media Access Control (MAC) address, generated at the manufacturing stage**. **Wireless NICs (WNICs)** can also be used; these plug into a USB port or can be part of an internal integrated circuit.

---

## 3.4.2 MAC 地址

**English（背这句）**
> MAC addresses **identify a device connected to a network**. They are made up of **48 bits written in groups of six hex digits**.

```
NN - NN - NN - DD - DD - DD
└─ manufacturer's code ─┘ └─ device serial number ─┘
```

MAC 地址可以是：
- **UAA (Universally Administered MAC address)** — 出厂时设定
- **LAA (Locally Administered MAC address)** — 用户自己改的（如果网络上所有设备需要统一 MAC 格式）

---

## 3.4.3 IP 地址

**English（背这句）**
> When a device connects to a network, a **router** assigns the device an **Internet Protocol (IP) address via a Dynamic Host Configuration Protocol (DHCP) server**, which is unique to that network.

| 版本 | 位数 | 格式 | 例子 |
|------|------|------|------|
| **IPv4** | **32-bit** | A.B.C.D，A/B/C/D 取 **1 到 255** | `215.180.1.80` |
| **IPv6** | **128-bit** | 八组四位十六进制数 | `A8FB:7A88:FFF0:0FFF:3D21:2085:66FB:F0FA` |

**IPv6 的优势**：removes the risk of **IP address collisions**；allows for **more efficient packet switching**；has **built-in authentication checks**。

### 静态 IP vs 动态 IP

| **Dynamic IP** | **Static IP** |
|----------------|---------------|
| **Changes every time** a device connects to a network | **Permanently assigned** |
| **Greater privacy** since it changes each time a user logs on | Since it doesn't change, it allows each device to be **fully traceable** |
| Can be an **issue when using VoIP**, since this type of addressing is less reliable — it can disconnect and change the IP address, causing the VoIP connection to fail | Allows for **faster upload and download speeds** |
| — | **More expensive to maintain** since the device must be constantly running |

---

## MAC vs IP（最经典对比题，几乎每套卷都有）

🔧 **答题模板：Explain the different function of a MAC address and an IP address. Also include any similarities.** [4]

**满分答案（背下来）**：
> A **MAC address identifies the physical address of a device** on the network, whereas the **IP address identifies the device's global address on the internet**.
>
> MAC addresses are **unique for each device**; however, IP addresses are **not necessarily unique**, since all devices on a network share the same part of an IP address.

> ⚠️ **严谨理解**：完整 IP 地址在所属网络内是唯一的；设备共享的是 **network prefix**（网络前缀），host 部分不同。公网 IP 也可能通过 NAT 被多台设备共享。考试按上面的对比点作答即可。
>
> MAC addresses are **set by the manufacturer** but can also be **changed by the user (LAA)**; IP addresses can also be **dynamic or static** (an IP address is usually **assigned by the DHCP server**).
>
> MAC addresses are used to **identify a data packet's sender and recipient**; IP addresses are used in **routing operations** as they specifically identify **where the device is connected to the internet**.

**对比速查表**：

| **MAC address** | **IP address** |
|-----------------|----------------|
| Identifies the **physical address** of a device on the network | Identifies the **global address** on the internet |
| **Unique** for device on the network | **May not be unique** |
| Assigned by the **manufacturer** of the device; part of the **NIC** | **Dynamic** IP assigned by the **ISP using DHCP** each time the device connects |
| Can be **universal or local** | Can be **static or dynamic** |
| Used to identify the **sender's and recipient's devices** in a packet | Used in **routing operations** |
| Uses **48 bits** | Uses **32 bits (IPv4)** or **128 bits (IPv6)** |

⚠️ **失分点（Teacher's comments 原文）**：
> "Avoid giving **opposites** (for example, IP addresses are global, but MAC addresses aren't global) since it is necessary to **explain** what the difference is (for example, MAC addresses can be local or universal)."

❌ **错误说法**："Both MAC and IP addresses are set at the factory and can't be changed." — **两个都错**：IP 地址不是出厂设定的，MAC 地址也可以被用户改（LAA）。

---

## 3.4.4 路由器 Routers

**English（背这句）**
> Routers enable **data packets to be routed between different networks**, for example a **local area network (LAN) to a wide area network (WAN)**. Routers **take data transmitted in one format (protocol) from network "A" and convert the data to another format (protocol) that network "B" understands**. This allows communication between networks to take place.
>
> Routers **inspect data packets** sent to it from another device or network. Every device on the same network has the **same part of an IP address** (for example, `215.164.10.XX`) so the router can send data packets to an **appropriate switch**. The switch then directs the data packet to the **correct device** on the network.

**关键区分**：
- **Router** 连接**不同网络**（LAN ↔ WAN），做协议转换
- **Switch** 在**同一网络内**把数据包送到正确的设备

---

# 📝 考试怎么考（Exam Focus）

## 各题型答题模板

### 模板 1：Describe the role of registers and buses [4]
> 见 §3.1.2。**结构**：先给 registers 的总定义（data holding places），再逐个列出 CIR/ACC/MAR/MDR/PC 各存什么；buses 部分三条总线各一句。
> 💡 **4 分 = 4 个展开的事实**，只列名字不给分。

### 模板 2：Discuss four ways to improve CPU performance [4]
> 见 §3.1.3。**每一条都必须带"为什么能提升性能"或"有什么风险"**。
> ❌ "use more RAM, change clock speed, use bigger buses" = 0 分

### 模板 3：Describe the FDE cycle / three actions in the FDE cycle [3-4]
> 见 §3.1.2。**按 PC → MAR → MDR → CIR → PC+1 → decode → execute 顺序写**。

### 模板 4：Describe how sensors, actuators and a microprocessor interact [5]
> 见 §3.2.3。**固定 5 点**：常发数据 → 比较预设值 → 超范围发信号 → 可能需 DAC → 执行器动作（feedback）。
> 💡 **画流程图能加分**，且能防止漏点。

### 模板 5：Give advantages and disadvantages of [device] [5-6]
> 见 §3.2.1 / §3.2.2。**格式**：每条 "优点 + 一句理由"。
> 💡 **不要只写 "it is faster"**，要写 "it is faster **because there are no moving parts**"。

### 模板 6：Explain the difference between a MAC address and an IP address [4]
> 见 §3.4.3。**必须解释，不能只给对立的形容词**。

### 模板 7：Name/Choose a suitable device for [scenario] [1-8]
> 逐条判断场景需求：
> - **要复制实物/做原型** → 3D printer
> - **大幅面广告、运动会记分牌** → LED screen
> - **可弯曲、超薄、曲面屏** → OLED screen
> - **投影给大观众看** → Light projector
> - **一次性彩色照片 / 少量** → Inkjet printer
> - **1 万份传单 / 大批量** → Laser printer
> - **工业水阀开关控制** → Actuator
> - **视障人士检查文档** → Speakers（语音读出）或 Braille printer

### 模板 8：Explain monitoring vs control [2]
> 见 §3.2.3。**一句 monitoring（只报警）+ 一句 control（改变过程）**。

---

## 📊 真题实证（2024–2026 考频与官方答案）

> 下表基于 **138 份 2024–2026 真题 QP / MS / Examiner Report** 逐题统计。

### 考频总表

| 考点 | 2024 | 2025 | 2026 | 分值 | 结论 |
|------|------|------|------|------|------|
| CPU role / FDE cycle | Mar, Sum, Win | Mar, Sum, Win | Jun ×3 | 1–6 | **每套必考** |
| Registers（PC/MAR/MDR/CIR/ACC） | Mar, Sum, Win | Mar, Sum, Win | Jun ×3 | 1–6 | **每套必考** |
| Buses | Sum, Win | Sum | — | 2 | 常考 |
| Cores / cache / clock speed | Mar, Sum | Mar, Sum, Win | Jun ×3 | 2–5 | **每套必考** |
| Instruction set | Sum | Mar, Sum | Jun | 1 | 常考 |
| Embedded systems | Win | Mar, Sum, Win ×3 | Mar | 2 | **极高频** |
| 输入/输出设备识别 | Sum, Win | Mar | Jun ×3 | 1–3 | **每套必考** |
| Sensors（+microprocessor/actuator） | Mar, Sum, Win | Mar, Sum, Win | Mar, Jun ×3 | 1–6 | **每套必考** |
| 主存 vs 副存 | Mar, Sum | Sum, Win | Jun ×3, Mar | 1–6 | **每套必考** |
| RAM / ROM | Mar, Sum, Win | Sum, Win | Jun | 1–3 | **极高频** |
| Virtual memory | Mar | Sum | Mar | 1–3 | 常考 |
| 磁/光/固存细节 | Sum, Win | Sum, Win | Jun ×2, Mar | 2–6 | **每套必考** |
| Cloud storage | Win | Win | Jun ×2, Mar | 1–4 | 常考 |
| NIC / MAC 地址 | Sum | Mar, Sum, Win | — | 1–5 | 常考 |
| IP 地址（v4/v6, static/dynamic） | Sum | Mar, Win | Mar | 1–3 | 常考 |
| Router | Mar | Mar, Win | Jun | 1–3 | 常考 |
| **触摸屏类型 / 打印机 / 投影仪 / 2D-3D 扫描仪 / QR / LED 屏** | 无 | 无 | 无 | — | ⚠️ **近年少考，但考纲仍列出；掌握用途/适用场景，细节不必全背** |

### 🔑 逐考点官方答案（背这些，不是背教材）

**① CPU role [1]** —— `0478/12 June 2026 Q2(a)`
> ✅ "To process/execute data/instructions" / "To perform/carry out/run/process the **fetch–decode–execute/FDE/FE cycle**"
> ⚠️ MS 判分：**"Tasks/programs/code/information in place of instructions is TV"**
> ❌ ER 2025 Mar: "explaining that it **does the processing**, or that it is **the brain of the computer**" —— 不给分

**② Registers [1-3]** —— 多卷
> ✅ 五个合法答案：**PC / MAR / MDR / CIR / ACC**
> ⚠️ MS: "**Do not accept MAR or MDR as they are given in the question.**"
> ❌ ER 2025 Mar: 编造名字 —— "**a logical register and an arithmetic register**" 是最常见错误答案
> ❌ ER 2025 Jun: "The most common incorrect answer given was the **arithmetic logic unit**"（ALU 是组件，**不是 register**）

**③ Registers 表格题官方描述** —— `0478/12 June 2025 Q4(a)` 6 分
> | 组件 | 官方给分描述（逐字） |
> |------|-------------------|
> | **Control unit (CU)** | "It **sends signals to all the components in the CPU to manage the flow of data** through the CPU." |
> | **ALU** | "It **carries out all the arithmetic and logic operations** in the CPU." |
> | **Cache** | "It **stores frequently used data/instructions**" |
> | **Program counter (PC)** | "It **stores the address of the next instruction to be fetched**" |
> | **Clock** | "It **controls the number of fetch-decode-execute (FDE) cycles that are performed per second**." |
> | **MDR** | "It stores data **immediately before it is transmitted to RAM and immediately after it is received from RAM**." |

> ⚠️ ER 2025 Jun 原话：**"Clock speed is not a component and it is a measure of how many clock cycles are completed and does not control how many clock cycles are completed."**
> ⚠️ ER 2025 Jun: **Cache** 要说"stores **frequently used** data/instructions"，不是"stores the data that has just been used"。
> ⚠️ ER 2025 Jun: **Accumulator** "stores the **result** of a calculation and not the actual calculation itself."

**④ Decode 阶段 [3]** —— `0478/11 June 2026 Q2(a)(ii)` ⭐ 最高价值小分题
> ✅ "The instruction is **sent/copied to the current instruction register/CIR/control unit/CU**"
> ✅ "… **from the memory data register/MDR**"
> ✅ "The **control unit/CU decodes** the instruction"
> ✅ "An **instruction set** is used (to decode the instruction)"
> ✅ "The instruction is **decoded/converted into the Opcode and Operand**"
> ⚠️ MS 原话：**"MP3 – It must clearly state the CU is decoding the instruction"**
> ❌ ER Winter 2024（**同一句话重复警告了两次**）："**Many candidates instead described the execute stage of the cycle.**"

**⑤ Fetch 阶段完整填空（6 分，逐字背）** —— `0478/11 Nov 2025 Q6(a)`
> "The **program counter** stores the address of the next instruction to be processed. This address is then sent to the **memory address register**. This address is the location in RAM where the instruction can be found. The instruction is retrieved from RAM and immediately stored in the **memory data register**. The instruction is then sent to the **current instruction register** where it is decoded by the **control unit**. The instruction is decoded using an **instruction set**."

> ⚠️ ER Summer 2024: **地址走的是 PC → MAR，不是 PC → MDR**。"The address is then sent to the **memory data register**" 是最常错的一空。

**⑥ Clock speed [2]** —— `0478/12 June 2026 Q2(d)` "3 GHz"
> ✅ "**3 billion**" + "… is the **maximum number of instructions / FDE cycles / clock cycles processed per second**"
> ⚠️ MS: "accept **3 × 10⁹ or 3000000000**"
> ❌ ER 2024 Mar: "**A common misconception was that 3.5 GHz is 3.5 million.**"

**⑦ 提升 CPU 性能 [4]** —— `0478/12 Nov 2025 Q4(c)`
> ✅ **MS 原文："MAX 2 if no expansion given"** —— **每一条必须带 expansion！**
> - "The **number of cores** could be increased … **this means that more instructions can be processed simultaneously**"
> - "The **clock speed** could be increased … **this means that more instructions can be processed (by a core) per second**"
> - "The **cache** could be increased … **this means that more frequently used data/instructions can be stored (to be accessed faster than RAM)**"

> ⭐ **铁律（三条不可混用）**：
> - **More cores → more instructions SIMULTANEOUSLY（同时）**
> - **Faster clock → more instructions PER SECOND（每秒）**
> - **More cache → frequently used data accessed FASTER THAN FROM RAM**
> ❌ ER 2025 Jun: "Some candidates incorrectly stated that it would mean that **more FDE cycles could be carried out simultaneously**."
> ❌ ER 2024 Mar: **"did not identify whether this was with more cores or fewer cores"** —— 必须说**增加还是减少**！
> ❌ ER 2024 Mar: 只说 "**because it is faster**" 而不说**比什么快** → 不给分

**⑧ 嵌入式系统 [2]** —— 几乎每套都有，`0478/11 Nov 2025 Q1(g)` 等
> ✅ 任选**两个不同**特征：**single/limited function** / **dedicated hardware** / **has a microprocessor** / **its function is not easily changed (cannot be reprogrammed)** / **uses firmware**
> ❌ ER 2025 Nov: "**Many gave generic statements such as 'it is a combination of hardware and software'. A vague statement like this does not differentiate it from a general-purpose computer.**"
> ⚠️ 一道题 2 分 = **两个不同特征**，同一个特征换个说法只给 1 分。

**⑨ Sensors [1] + 用途 [2]**
> ✅ 必须写**传感器的类型名**：acoustic / accelerometer / light / temperature / proximity / infra-red / magnetic field / moisture / humidity / pressure
> ❌ MS: "**Sound/noise sensor is TV. Microphone is NE.**"（acoustic 才对）
> ❌ MS: "**Motion, sound, touch and heart rate are TV.**"
> ❌ MS: "**Do not accept by description**, for example it measures light."
> ❌ ER 2024: 说用途必须**结合题干场景** —— "**it measures the temperature**" 这种空话不给分。

**⑩ 传感器链条** —— 见模板 4 与新加的 Unit 6 笔记。
> ⚠️ ER 2025 Mar（**跨单元通用铁律**）：**"An actuator converts a digital signal into physical movement … it does NOT display a message on a digital screen."**

**⑪ 主存 vs 副存 [3]** —— `0478/11 June 2025 Q7(b)` "Why is RAM primary and not secondary?"
> ✅ "**RAM is directly accessed by the CPU**" / "**All secondary storage is non-volatile … whereas RAM is volatile**"
> ⚠️ ER 2025 Jun: **"primary storage can also be volatile"** —— 不要说"所有主存都是易失的"
> ⚠️ ER 2024 Jun: ROM 的"非易失"是 ROM 的特征，**不是让它成为主存的特征**

**⑫ Virtual memory [3]** —— `0478/11 June 2025 Q7(c)`
> ✅ 三个**分别给分**的点：① **secondary storage is partitioned** to create the virtual memory ② **pages are transferred from the RAM** ③ it **acts as an extension to the RAM**
> ⚠️ ER 2025 Jun: "**The most common mark awarded was for stating that secondary storage is partitioned**"（另外两点常丢）

**⑬ 存储类型配对 [6]** —— `0478/13 Nov 2025 Q2(d)`
> 看到**关键词**就选：
> - **pits and lands** / **laser** / "read/write arm that moves a **laser** across a disc" → **Optical**
> - **electromagnets** / **platters** / **tracks and sectors** / **read/write head** / "moving parts" → **Magnetic**
> - **NAND or NOR** / **control gates and floating gates** / **transistors** / "**flow of electrons**" → **Solid-state**
> ⚠️ ER 2024: "**Many candidates appeared to have a misconception that an HDD is an example of optical storage** … because it has spinning platters."
> ⚠️ **"floating gates"，绝不是 "flow gates"**（2026 March 干扰项）

**⑭ MAC vs IP [3]**
> ✅ MAC 特征（格式事实，**不是用途**）："**represented in hexadecimal**" / "**numbers separated by colons/hyphens**" / "**six groups of digits**" / "**48 bits / sets of 2-digit hex numbers**" / "**contains manufacturer ID and unique device number**" / "**static address // cannot be changed**"
> ❌ ER 2025 Mar: "Some candidates **described the purpose** of a MAC address … **which are not characteristics**."
> ✅ MAC = **assigned by the manufacturer**；IP 由 **router** 自动分配
> ✅ IPv6 特征：**128-bit** / **hexadecimal** / **separated by colons** / **8 groups of 4 digits** / "consecutive groups of 0s can be represented by **::** once"

**⑮ Router [3]** —— `0478/12 June 2026 Q3(e)(ii)`
> ✅ "It **examines/analyses/searches the packet to find the destination IP address**" / "It **forwards the packet towards its destination**" / "It **determines/assigns/selects the route/path** each packet takes … **which is the fastest/most efficient/shortest route**" / "**Uses/updates a routing table**" / "Checks/updates the packet's **hop count / time to live (TTL)**"
> ⚠️ MS 原话：**"Do not accept generic statement like 'each packet takes a different path' if there is no reference to the router determining/assigning the path."**
> ⚠️ MS 原话：**"best path is TV"** —— 必须说 **fastest / most efficient / least traffic**

### 🎯 Unit 3 高分优先级（按投入产出排序）

1. **Registers + FDE 阶段描述**（必考，1–6 分）—— 把上面第 ④⑤ 两段**默写**
2. **sensor → microprocessor → actuator 链条**（必考，3–6 分）—— 见 Unit 6 模板
3. **cores / clock speed / cache 性能对比**（必考，2–4 分）—— 记住三条**不可混用**的铁律
4. **存储类型配对表**（必考，2–6 分）—— 背关键词
5. **主存 vs 副存 + RAM/ROM + virtual memory**（必考，1–6 分）
6. **embedded system "explain why"**（每套，2 分）—— 背两个不同特征
7. **输入/输出设备识别**（必考，1–3 分）—— ⚠️ **必须符合题干场景**
8. **MAC / IP 格式事实**（多数卷，1–3 分）
9. **打印机 / 投影仪 / 触摸屏类型 / 扫描仪** —— 近年少考，但 2026–2028 考纲仍列出；**至少掌握用途和适用场景**，内部原理不必逐条死背

---

## ⚠️ 高频失分点汇总

| 失分点 | 正确写法 |
|--------|---------|
| "Sensors only send data **when there is a change**" | ❌ 错！Sensors **constantly** send data to the microprocessor |
| "The **sensors control** the process" | ❌ 错！The **microprocessor** controls the process; sensors only provide data |
| "Sensors don't need an ADC" | ❌ 传感器信号通常是**模拟**的，必须经 **ADC** 转换 |
| 只写方法不写理由（Discuss 题） | ✅ 每条方法必须跟 "**which means that...**" |
| "Instruction is fetched from the hard drive" | ✅ 指令从 **RAM（内存）** 取，不是硬盘 |
| 漏掉 "PC is incremented" | ✅ Fetch 阶段**必须**写这一步 |
| 混淆地址总线/数据总线方向 | ✅ Address bus = **单向**；Data bus & Control bus = **双向** |
| "MAC and IP are both set at the factory" | ✅ MAC 出厂设定（但可被用户改）；**IP 由 ISP 通过 DHCP 分配** |
| "Compare" 题只写差异不写共性 | ✅ 两者都要，但 4 分题写满 4 个差异也能满分 |
| Actuator 当成输入设备 | ✅ Actuator 是**输出设备** |
| Virtual memory 说成"硬盘上的 RAM" | ✅ 准确说法：**RAM + swap space on HDD/SSD**，提供 "illusion of unlimited RAM" |
| 说 SSD 也会 thrashing | ✅ **SSD 没有移动部件**，不受同样影响 |
| **Decode 阶段写成了 execute 阶段** | ✅ Decode = 指令送到 **CIR** → **CU 解码** → 用 **instruction set** → 拆成 **opcode + operand**。❌ 这是 Winter 2024 ER **重复警告两次**的头号错误 |
| **地址说成 PC → MDR** | ✅ **PC → MAR → RAM → MDR → CIR**。地址走 MAR，**不走 MDR** |
| 把 **ALU 当成 register** | ✅ ALU 是**组件**，不是 register。五个 register 只有 PC/MAR/MDR/CIR/ACC |
| 编造 register 名字（logical register / arithmetic register） | ✅ 只有 PC / MAR / MDR / CIR / ACC（外加超纲的 IX、SR） |
| 把 **clock speed 当成一个组件** | ✅ 组件是 **clock**；**clock speed 是度量**，不是组件 |
| Cache 说成 "stores data that has just been used" | ✅ **stores FREQUENTLY USED data/instructions** |
| ACC 说成 "stores calculations" | ✅ ACC stores the **RESULT** of a calculation |
| **"more cores = faster"** | ✅ 三条不可混用：**cores → simultaneously；clock → per second；cache → faster than RAM** |
| 性能题不说"增加还是减少" | ✅ 必须写 **if the clock speed is INCREASED / MORE cores / MORE cache** |
| **GHz 说成 million** | ✅ GHz = **billion**（10⁹） |
| Embedded system 只写 "limited function" | ✅ 2 分题必须给 **两个不同特征**。❌ "a combination of hardware and software" 是 **TV** |
| **Actuator 用来显示屏幕信息** ❌ | ✅ Actuator 只引起**物理运动**（motor/valve/brake）。**2025 Mar ER 跨单元点名** |
| Sensor 写 "sound sensor" / "motion sensor" / "touch sensor" | ✅ 必须写类型名：**acoustic** / **accelerometer** / **light** / **proximity** |
| Sensor 用途只写 "it measures the temperature" | ✅ 必须**结合题干场景**说测什么、为了什么 |
| Sensor 答案写成描述（"it measures light"） | ✅ MS: **"Do not accept by description"** —— 必须给**类型名** |
| 输入/输出设备不符合题干设备 | ✅ ⚠️ **手机/手表/平板** 不能答 mouse / keyboard / printer / HDD |
| HDD 说成 optical storage | ✅ **HDD = magnetic**（虽然也有旋转盘片） |
| 说 "floating gates" 写成 "flow gates" | ✅ **floating gates**（2026 March 干扰项设的坑） |
| Cloud storage 优点只写 "accessed anywhere" | ✅ 必须**对比本地存储**：可从**其他设备**访问 / 无需购买维护硬件 / 容量近乎无限 / 设备丢失数据仍在 |
| Virtual memory 只说 "partitioned" | ✅ 三点分别给分：**partitioned** + **pages transferred from RAM** + **extends the RAM** |
| MAC 题问 characteristics 却答 purpose | ✅ 答**格式事实**：hex / colons / 6 groups / 48-bit / manufacturer ID / static |
| Router 说 "each packet takes a different path" | ✅ MS 明确拒绝：必须说 **router determines/assigns the path**。"best path" 也是 **TV**，要说 **fastest / most efficient / least traffic** |
| Secondary storage 说成"为了做备份" | ✅ **Secondary storage 就在计算机内部**，不是外置备份。ER 2024 重复两次 |

---

## 🧠 一页纸速记

```
【CPU 四件套】
CU  —— 取指令、发控制信号、同步
ALU —— 算数 (+−) + 逻辑 (AND/OR)，乘除用 shifting
Registers —— PC / MAR / MDR / CIR / ACC
Clock —— 在 control bus 上发定时信号

【总线】
Address —— 单向，传地址
Data    —— 双向，传数据（可以是地址/指令/数值）
Control —— 双向，CU 发信号

【FDE】
PC →(address bus)→ MAR →(data bus)→ MDR → CIR → PC+1 → decode → execute

【提速 4 招】加 RAM / 加宽总线 / 提时钟（小心 overclocking）/ 多核
【Cache】最常使用的数据/指令的副本，CPU 先查 cache 再查 RAM

【嵌入式】专用单一任务，小、便宜、省电，难升级、难排故、易被扔
【微型控制器】CPU+RAM+ROM+外设 一片；【SoC】CPU+内存+I/O+辅存 一片

【输入】barcode（红光+光电元件）/ QR（相机+app，可 attagging）
       keyboard ASCII / microphone 振膜+线圈 / optical mouse 无移动部件
       2D scanner + OCR / 3D scanner + CAD / tomography
       touchscreen: capacitive / infrared / resistive

【输出】actuator（继电器/螺线管/马达）—— 是输出！
       DLP（微镜,对比度高,有阴影）/ LCD（分RGB,更清晰,寿命短）
       inkjet（少量彩色）/ laser（大量, toner+fuser）
       3D printer = additive, 逐层 0.1mm；binder = 两遍（粉+粘合剂）
       LED（RGB三色,户外大屏）/ LCD（需背光）/ OLED（自发光,可弯曲,真黑）
       speaker 需先过 DAC

【传感器】ADC 进 → 比较预设值 → 超范围 → DAC 出 → actuator → feedback
   监控 = 只报警；控制 = 改变过程
   ⚠ 传感器【持续】发送数据，【不控制】过程

【存储】
RAM: volatile, 可读写, 存OS在用部分, 可扩容
ROM: non-volatile, 不可改, 存BIOS/启动程序
DRAM: 晶体管+电容, 需刷新, 便宜大容量 = 主存
SRAM: flip flop, 不刷新, 快, 贵 = cache
HDD: 盘片+磁头, 约7000RPM（约117转/秒）, 有latency, 会fragmentation
SSD: NAND matrix, floating gate + control gate, 限写入次数
CD 780nm红 / DVD 650nm红双面 / Blu-ray 405nm蓝, 加密, 4K
虚拟内存 = RAM + swap space, paging, disk thrashing
云: public / private / hybrid, data redundancy

【网络硬件】
NIC — 含 MAC 地址, 出厂生成
MAC — 48位6组hex, NN-NN-NN-DD-DD-DD, UAA/LAA
IP  — IPv4 32位 / IPv6 128位, 由 DHCP 分配, static/dynamic
Router — 连接不同网络, 转换协议
```

---

## 🔗 延伸资源

- 课件：[Unit 3 Hardware 课件目录](../csresource/new/Slides/1%20Computer%20Systems/3%20Hardware/)
- 课件：`csresource/.../Slides/` 中的 Unit 3 相关 PPT
- 真题：`csresource/.../Past Exam Papers/Questions by Year/` 中各年份 Paper 1
- 在线练习（按考纲章节分类，与本单元一一对应）：
  - [Save My Exams — 3. Hardware](https://www.savemyexams.com/igcse/computer-science/cie/23/topic-questions/)
  - [PapersDaddy — 0478 Topical Paper 1](https://www.papersdaddy.com/cambridge/igcse/computer-science-0478/resources/topical-past-papers/paper-1)（免费下载）
  - [Physics and Maths Tutor — IGCSE Computer Science](https://www.physicsandmathstutor.com/computer-science-revision/igcse-cie/)

---

**上一单元** ← [Unit 2 - Data transmission](Unit%202%20-%20Data%20transmission.md)
**下一单元** → [Unit 4 - Software](Unit%204%20-%20Software.md)
