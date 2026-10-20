# Unit 4 — Software 软件

> **考纲**：Cambridge IGCSE Computer Science 0478 / 0984 (2026–2028) — Unit 4 Software
> **试卷**：Paper 1 Computer Systems — **75 分 / 1 小时 45 分钟 / 不允许使用计算器**
> **本单元特点**：概念清晰、**答案极其模板化**。OS 的九大功能、编译器 vs 解释器、IDE 的功能几乎年年出现，而且**判分点固定**。属于"背了就有分"的单元，但**拼写错误会直接丢分**。

---

## 📋 考纲对照清单

| # | 考纲条目 | 掌握 |
|---|---------|------|
| 4.1.1 | System software and application software | ☐ |
| 4.1.2 | Role and function of operating systems | ☐ |
| 4.1.3 | Need for hardware, firmware and operating systems when running apps | ☐ |
| 4.1.4 | Role and operation of interrupts | ☐ |
| 4.2.1 | Advantages and disadvantages of high-level and low-level languages | ☐ |
| 4.2.2 | Assembly languages | ☐ |
| 4.2.3 | Advantages and disadvantages of compilers and interpreters | ☐ |
| 4.2.4 | Role and function of IDEs when writing programming code | ☐ |

---

# 第一部分：软件类型与中断 (4.1)

## 4.1.1 系统软件 vs 应用软件

**English（背这句）**
> All computer systems are made up of **hardware, system software and application software**.

```
                    Computer System
        ┌──────────────────┴──────────────────┐
     Hardware                              Software
                                  ┌───────────┴───────────┐
                            System software        Application software
                          ┌───────┼───────┐      ┌────────┼────────┐
                    Operating  Utility  Device  Spreadsheet Word  Database
                    system    programs drivers
```

**对比表（必背）**：

| **System software** 系统软件 | **Application software** 应用软件 |
|------------------------------|-----------------------------------|
| **Controls and manages the operation of the computer hardware** | Used to **perform various tasks** on a computer |
| **Provides a platform on which all software can run properly** | Allows the user to **perform specific tasks** on a computer |
| **Provides a human computer interface (HCI)** | **Meets the requirements of the user** |
| **Controls the allocation and usage of resources** (software and hardware) | — |

⚠️ **最能拉开差距的判断**：给你一个软件，判断它是系统软件还是应用软件。

🔧 **答题模板：Tick whether the named software is system software or application software**

| 软件 | 答案 | 为什么 |
|------|------|--------|
| **Screensaver** | **System**（utility） | 属于安全/维护工具 |
| **Antivirus software** | **System**（utility） | 保护计算机 |
| **Printer driver** | **System**（device driver） | 让硬件与 OS 通信 |
| **Video editing software** | **Application** | 用户完成特定任务 |
| **Compiler** | **System** | 翻译程序，属于系统软件 |
| **QR code reader** | **Application** | 用户任务 |
| **On-screen calculator** | **Application** | 用户任务 |
| **Operating system software** | **System** | 核心系统软件 |
| **Interrupt handling routine** | **System**（OS 的一部分） | 属于 OS 功能 |
| **Photo editing software** | **Application** | 用户任务 |

💡 **判断口诀**：**"管理计算机本身"→ 系统软件；"帮用户干活"→ 应用软件。**

### 应用软件分类（可能考"举例"）

| 类型 | English 描述 |
|------|-------------|
| **Word processor** | Used to **manipulate a text document**. Functions: creating/editing/saving text, copy and paste, **spell checkers and thesaurus**, import photos, translation into a foreign language |
| **Spreadsheet** | Used to **organise and manipulate numerical data**. Numbers organised on a **grid of lettered columns and numbered rows**; each cell is identified by a unique combination (e.g. **B6**). Functions: **formulas** to carry out calculations, produce **graphs**, do **modelling and "what if" calculations** |
| **Database** | Used to **organise, manipulate and analyse data**. Made up of one or more **tables**; tables consist of **rows (records)** and **columns (fields)**. Functions: **queries**, produce **reports**, add/delete/modify data |
| **Control and measuring software** | Designed to allow a computer/microprocessor to **interface with sensors** so that it is possible to measure physical quantities and **control applications** |
| **Photo editing software** | Manipulate digital photographs — change **brightness, contrast, colour saturation, remove "red eye"** |
| **Video editing software** | Manipulate videos — add titles, colour correction, **transitions between clips**, rearrange/add/remove sections |
| **Graphics manipulation software** | Allows **bitmap and vector images** to be changed. Bitmap = made up of **pixels**; Vector = **lines, curves and text** (no pixels) |
| **Apps** | Short for applications — software which runs on **mobile phones or tablets**; normally downloaded from an **app store** |

### 系统软件分类（四类，必背）

| 类型 | English |
|------|---------|
| **Operating system (OS)** | Essentially **software running in the background**. It manages many of the basic functions. Without the OS, most computers would be very user-unfriendly |
| **Utility programs** | Software designed to **carry out specific tasks** — programs that help to **manage, maintain and control computer resources** |
| **Device drivers** | Software that **enables one or more hardware devices to communicate with the computer's operating system** |
| **Compilers / Linkers** | A compiler translates HLL into machine code. A **linker (link editor)** takes one or more **object files** produced by a compiler and **combines them into a single program** which can be run on a computer |

💡 **Linker 考点**：允许程序员把程序**拆成多个 module 分别编写**（简化编程任务），最后由 linker 组装成最终程序。

### 常用工具软件 Utilities（五大类 + 说明）

| Utility | English 说明（背诵） |
|---------|---------------------|
| **Virus checker / Antivirus** | A virus is a small program that **replicates itself** and can **delete or modify important files**. Antivirus software looks for **malware "clues"** or recognises it from a **database of known viruses**. Virus checkers **run in the background** and need to be **regularly updated**. They make use of **heuristic checking** (looks for software behaviour that could indicate a possible virus). Once an infected file is discovered it is **quarantined and then deleted** |
| **Defragmenter** | Tidies up the hard disk drive as it begins to reach its maximum capacity. Works by **rearranging blocks of data** (by removing space left from earlier deletion of data) so that they can become **contiguous** (rather than randomly stored across various sectors). This **frees up disk space** and makes **location of data faster** |
| **Disk repair** | **Verifies if an error has been found in the disk directory**; it will then attempt to correct the error. Removes or bypasses **damaged/corrupted data/disk sectors** and then **links blocks of data together** to allow files to be read (**some data may be lost in the process**) |
| **File compression** | Can be **lossy or lossless**. With lossy, the original file **cannot be reconstructed**; with lossless, the original file **can be reconstructed**. Lossy file sizes are much smaller |
| **Back-up software** | Back-up files are essential in case files/data become **corrupted or lost**. Either done **automatically** or **initiated by the user**. Many OSs offer the ability to **restore a computer status to a point in the past** |
| **Security** | Manages **access control**. Links into virus checkers and **firewalls**, uses a firewall to protect the computer when **automatic software updates** are requested. Makes use of **encryption** to safeguard data |
| **Screensavers** | Moving or still images on a computer screen that are initiated **after a period of inactivity**. Part of the **security system** since screensavers **automatically log out a user** if they have left the computer unlocked and there has been no activity for e.g. 5 minutes |
| **Device drivers** | See above. All **USB device drivers contain information known as descriptors** (these include **vendor ID, product ID and unique serial number**). **If a device has no serial number**, the OS will treat it as a **new device every time** it is plugged in |

---

## 4.1.2 操作系统的功能（最高频大题）

**English（背这句）**
> Operating systems provide both **the environment in which applications can be run** and enable a **human computer interface** to function in a non-complex way. They **disguise the complexity of software and hardware**. Operating systems ensure there is a **platform for running all applications in a safe and secure manner**.

### OS 九大功能总览图（严格按 2026–2028 考纲）

```
┌──────────────────────────────────────────────┐
│                Operating system              │
├──────────────────────────────────────────────┤
│ 1. Managing files                            │
│ 2. Handling interrupts                       │
│ 3. Providing an interface (HCI)              │
│ 4. Managing peripherals and drivers          │
│ 5. Managing memory                           │
│ 6. Managing multitasking                     │
│ 7. Providing a platform for running apps     │
│ 8. Providing system security                 │
│ 9. Managing user accounts                    │
└──────────────────────────────────────────────┘
```

> ⚠️ **考纲的九项就是上面这九项**。`Error handling` 在不少教材里也会提到，但它**不在 2026–2028 考纲列出的九项里**；答题时优先写考纲九项，不要把 `Error handling` 当成第九项。

### 九大功能逐条背诵（按考试出现频率排序）

🔧 **最高频 1：Memory management（内存管理）** [2]
> Memory management is essentially **management of the primary storage (RAM) and the data being moved between RAM and HDD/SSD**. It **keeps track of all the memory locations**. This part of the OS carries out **memory protection** to prevent two competing applications from using the **same memory locations at the same time** — this would otherwise lead to a potential **computer crash, security issues, or loss or corruption of data**.

🔧 **最高频 2：User account management（用户账户管理）** [2]
> User account management allows **more than one user to log into the computer** by ensuring **each user's data is stored in a separate part of memory**. Each user logging on is given a **user account area**, which is protected by a **username and a password**. Each user can **customise their screen layout** and manage their own files and folders. An **administrator** oversees the management of user accounts.
> **Multi-access hierarchy levels** are used to ensure access to certain data is only allowed if a user has the **correct hierarchy clearance level** (e.g. a user with security clearance 2 can access data at levels 2, 3 and 4).

🔧 **最高频 3：Security management（安全管理）** [2]
> Security management ensures the **integrity, confidentiality and availability** of data. This can be achieved by:
> - **overseeing software updates** when they become available
> - ensuring the **latest version of software is always being run** (which often contains revised security fixes)
> - running **antivirus software** and using a **firewall** to check all traffic to and from the computer
> - maintaining **access rights** for all users
> - carrying out **data recovery and system restore**

**其余六个功能**：

| 功能 | English |
|------|---------|
| **Human computer interface (HCI)** | Allows a **human being to communicate with a computer**. The two most common types are the **command line interface (CLI)** and **graphical user interface (GUI)** |
| **Hardware peripheral management** | Uses **device drivers** to allow input and output to take place. It manages the **queues and buffers** to ensure data is being handled correctly and that the CPU performs to its maximum |
| **File management** | Maintains **file directories and file naming conventions**. Performs file maintenance tasks such as **open, close, delete, rename, copy, create, move, save, sort**. Ensures **access rights** are maintained and correct **memory allocation** of the data when read from HDD/SSD and saved temporarily in RAM |
| **Multitasking** | Allows a computer to **carry out more than one task simultaneously**. The OS needs to constantly monitor the status of each process by ensuring: **all resources are allocated specific processor time**; **all processes can be interrupted** as and when necessary; **priorities** are used so that a given resource is used in the most efficient manner |
| **Interrupt handling** | Checks the **priority** of each interrupt and decides whether to **service it now or continue the current task**. Higher-priority interrupts are serviced first using an **interrupt service routine (ISR)**; lower-priority interrupts wait/continue |
| **Platform for running applications** | Provides the **environment and services** that application software needs to run. Applications run **on top of the operating system**, which manages their access to hardware and system resources |

🔧 **答题模板：Apart from HCIs, name three other functions carried out by a typical OS** [3]
> - **Multitasking**
> - **Memory management**
> - **File management**
> - *(也可写：user account management / hardware management / interrupt handling / security / platform for running applications)*

⚠️ **拼写警告**：`user account manager` 与 `user account management` 是两个不同的词，写错会丢分。

**必须拼写正确的术语**：`multitasking` / `memory management` / `file management` / `user account management` / `interrupt handling` / `security` / `hardware management`

---

### HCI：CLI vs GUI

**English（背这句）**

| **Command line interface (CLI)** | **Graphical user interface (GUI)** |
|----------------------------------|-------------------------------------|
| The user is in **direct communication** with the computer | The user is **limited to icons shown on screen** |
| The user is **not restricted to pre-determined actions/options** | There is **no need for the user to learn specific commands** |
| It is possible to **alter computer settings directly** | The user simply needs a **pointing device (such as a mouse)** or a **finger** (touchscreen) |
| Needs **very little memory** requirement | It is an **excellent interface for a novice** or a user with little knowledge of how computers work |
| The user **needs to learn commands** and must type them in using the **correct format** | A GUI has **considerable memory requirements** |
| It is **time-consuming and error-prone** | — |
| The user needs to have **some understanding of how computers work** | — |

### WIMP vs post-WIMP（考过 9 分大题）

**English（背这句）**
> **GUI interfaces are examples of a windows, icons, menu and pointing device (WIMP) environment.** More recently, devices such as smartphones and tablets invariably use touchscreens that require a **post-WIMP interface** — this allows actions such as **pinching and rotating** which would be **impossible in a WIMP environment using a mouse**.

🔧 **答题模板：Explain the difference between WIMP and post-WIMP** [2]
> A **WIMP** environment involves the use of a **pointing device, such as a mouse, to navigate a screen and select options from a menu or "click on" an icon**. With **post-WIMP**, the user **doesn't need a pointing device** since this only works with a **touchscreen** — the user simply uses their **finger or stylus** to carry out movement such as **pinch and rotate**, as well as selections.

🔧 **答题模板：Describe the relative advantages and disadvantages of the two types** [4]
⚠️ **关键**：题目要求"**relative**"，即**两者互相比**。**不要把 GUI 和 CLI 比，也不要和别的界面比——只比 WIMP 和 post-WIMP**。

> **Post-WIMP 优点/缺点**：
> - Advantage: **No input devices are needed**, such as a mouse
> - Disadvantage: Touchscreens can allow the **transfer of viruses and bacteria** between people who touch the same screen
> - Advantage: Allows actions such as **pinch or rotate** which would be **almost impossible using a mouse**
>
> **WIMP 优点/缺点**：
> - Advantage: **Any screen can be used** and it **doesn't require a touchscreen**
> - Disadvantage: Requires a **separate pointing device**, which could equally transfer viruses and bacteria

---

### Screensaver（考过，注意新旧用途变更）

🔧 **答题模板：Explain the term screensaver. Include the reasons why screensavers are used.** [3]
> A screensaver is a **moving or still image which appears on a user's screen following a period of inactivity** (for example, 5 minutes). The screensaver **automatically logs out a user** and is therefore being used as **part of the security system**, since the user will need to supply a **valid username and password** to use the computer again. Some screensavers use **face ID**, which means the computer **unlocks again as soon as a valid user faces the screen**.

⚠️⚠️ **不要写的过时答案（会被判 0 分）**：
> ❌ "Screensavers protect screens from **burning** where a logo is permanently burnt into the screen."

✅ **现代主要用途：安全（自动锁屏/自动登出）**。防烧屏是 CRT 时代的过时答案，写了不给分；省电也不要单独写。

---

## 4.1.3 硬件、固件与操作系统（启动过程）

**English（背这句）**
> When a computer starts up, **part of the operating system is loaded into RAM** (this is called **booting up** the computer). This routine is handled by the **Basic Input Output System (BIOS)**, which is a type of **firmware** — a program that provides **low-level control of devices**. The BIOS is **stored on a flash memory chip called an EEPROM** (electrically erasable programmable ROM) and its task is to **tell the CPU where the operating system can be found**.
>
> Although BIOS is stored on EEPROM, **BIOS settings are stored on a CMOS chip**, which is always connected up to a **power supply (battery)**. The user is allowed to alter the factory settings by **changing CMOS contents, such as changing the clock speed**.

**启动顺序（背）**：
```
开机 → BIOS (在 EEPROM 里) 运行 → BIOS 告诉 CPU 操作系统在哪里
     → 操作系统的一部分被加载进 RAM → 系统启动完成
```

**关键术语对照**：

| 术语 | 内容 |
|------|------|
| **Firmware** 固件 | Software **permanently stored in ROM/hardware** that provides **low-level control of devices** and normally cannot be changed by the user |
| **BIOS** | Stored on **EEPROM**; tells the CPU where the OS can be found |
| **EEPROM** | Electrically erasable programmable ROM — 存 BIOS |
| **CMOS** | 存 **BIOS settings**（如时钟频率）；**靠电池供电** |

**Firmware 的常考作用（按得分点整理）**：
> - **Stored permanently / non-volatile** in ROM or on a chip — not lost when power is switched off
> - Contains the **boot / start-up instructions** (bootstrap / bootloader)
> - Provides a **platform for the operating system** to run
> - Provides **low-level control of hardware** / allows the computer to **communicate with hardware**
> - Can provide **secure storage** (e.g. encryption keys / security routines)
> - Can be **updated** (e.g. flash memory / EEPROM)

**Firmware 的常见例子**：**bootstrap / bootloader**、**BIOS**、**embedded system 中的 OS**、**embedded system 中的程序**。

**答题模板**：*"Firmware is software stored permanently in ROM that provides low-level control of hardware and contains the instructions needed to start the computer, e.g. the BIOS/bootstrap."*

💡 **Apps 与 OS 的关系**：
> Apps are **under the control of the operating system** and need to access **system software, such as device drivers**. Different parts of the operating system may need to be **loaded in and out of RAM** as software runs.

⚠️ **常考判断**：**BIOS 存在 EEPROM 里，BIOS 设置存在 CMOS 里**——这两者经常被混淆。

---

## 4.1.4 中断 Interrupts（最高频，必背）

**English（背这句）** —— 填空高频，**必须背熟**：

> An **interrupt** is a **signal** sent from a hardware device or **software** to the **microprocessor** requesting **attention**. This causes the **microprocessor** to **temporarily** halt what it is doing and to **service** the interrupt.
>
> To determine the order in which an interrupt is dealt with, it is given a **priority**.
>
> When data is sent to a printer, it is first stored in a **buffer** where data is held **temporarily**. This allows the **microprocessor** to get on with other tasks.
>
> If the printer runs out of ink or there is a paper jam, it sends an **interrupt** to the **microprocessor**.
>
> When **streaming** data from the internet, a **buffer** is used to **compensate** for the difference between **download** speeds and the computer's data requirements.

**⚠️ 注意**：上面这些是**给词填空**的标准答案词。**把这段背下来**，这类题就是送分题。

### 中断的五个来源（必背）

| 来源 | English 说明 |
|------|-------------|
| **Timing signal** 定时信号 | All operations are coordinated by **internal clock**; if any operation is **out of sync** (doesn't match timing signal) then an interrupt is sent |
| **Input/output process** 输入输出 | An interrupt can be generated when a **hard disk drive or a printer, for example, are requesting more data to be sent** |
| **Hardware fault** 硬件故障 | An interrupt can occur if, for example, **a printer has a printer jam, or it runs out of paper or ink** |
| **User interaction** 用户交互 | For example, **pressing a key on the keyboard**, **moving the mouse** or **clicking a mouse button** sends an interrupt signal to the microprocessor; pressing the `<BREAK>` key can also generate an interrupt |
| **Software error** 软件错误 | For example, if an **.exe file cannot be found**, or **two processes are trying to access the same memory locations**, or there is a **division by zero error** |

### 中断处理机制

**English（背这句）**
> Once an interrupt signal is received, the microprocessor either **continues with its existing task** or **temporarily pauses the task** in order to service the interrupt. To determine the order of servicing interrupts, each interrupt is given an **interrupt priority**.
>
> If the new interrupt has a **higher priority** than the current task, the processor **finishes the current FE cycle**, pauses the task, services the interrupt using an **ISR**, then **restores the original task**. If it has a **lower priority**, the processor **continues the current task** and the interrupt **waits/is serviced later**.
>
> **Buffers** are also used to allow several tasks to be done at the same time. For example, while printing a document, data is sent to a **buffer** to hold it temporarily. While the buffer contents are emptied to the printer, the **CPU can carry on with other tasks**. Once the buffer is empty, the printer **sends an interrupt to the CPU requesting more data**. The interrupt will then be serviced according to its priority using an **interrupt service routine (ISR)**. This allows the CPU to **stop its existing task, service the interrupt from the printer, and then restore the original task once the interrupt is cleared**.

**Buffer vs Interrupt 的区别（易混！）**

| | **Buffer** | **Interrupt** |
|---|---|---|
| 是什么 | **Areas of memory that hold data temporarily** | **A signal** sent to the microprocessor |
| 作用 | **Prevent slower processes affecting CPU performance**; allow the CPU to carry out several tasks at the same time | Causes the microprocessor to **temporarily stop what it is doing so it can service** it |
| 流程位置 | 数据**先**进 buffer，CPU 继续干别的 | buffer 空了，设备**发中断**要更多数据 |

🔧 **答题模板：Describe how buffers and interrupts are used when data is transferred from a camera to a computer** [3]
> Data from the camera is sent to a **buffer** in the computer, where it is held **temporarily**. The **buffer allows the CPU to continue with other tasks** while the data is being transferred. Once the buffer is **empty**, the camera sends an **interrupt to the microprocessor** requesting more data to be sent. Each interrupt is given a **priority** and is serviced using an **interrupt service routine (ISR)**.

### ISR 关键流程（背这个顺序）

```
设备发中断信号 → CPU 检查中断优先级
    ├─ 更高优先级 → 完成当前 FE cycle → 暂停当前任务
    │                 → 执行 ISR → 清除中断 → 恢复原来的任务
    └─ 更低优先级 → 继续当前任务（中断排队，稍后处理）
```

⚠️ **注意 "restore the original task once the interrupt is cleared"** —— 恢复原任务这一步经常被漏写。
⚠️ **注意 lower-priority 分支**：不是所有中断都会立刻打断当前任务；优先级较低时要写 **continue the current task / the interrupt waits**。
⚠️ 答题写 **`finish the current FE cycle`**（不是 FDE cycle）。

---

# 第二部分：编程语言、翻译程序与 IDE (4.2)

## 4.2.1 高级语言 vs 低级语言（必考对比）

**English（背这句）**
> **High-level languages** are used by the majority of programmers as they make it much **easier and quicker to develop and maintain programs**. Examples: **Visual Basic, Python, Java**.
> **Low-level languages** are used by programmers who need to develop **special routines that make best use of memory, the computer's instruction set and hardware**. Most programs are written in **assembly language**, which is translated into **machine code**.

**HLL 定义（2–3 分模板，背这三句）**：
> - Written using **human-readable / English-like statements**
> - **Independent of the type of computer** (portable / machine-independent)
> - Must be **translated into machine code** before it can be executed

> ⚠️ 如果题目问 "Explain what is meant by a high-level language"，只写 "easy to use" 通常不够；要把 **readable / portable / needs translation** 这三点写出来。

**对比表（背下来，这是送分题）**：

| **High-level languages 高级语言** | | **Low-level languages 低级语言** | |
|---|---|---|---|
| **Advantages** | **Disadvantages** | **Advantages** | **Disadvantages** |
| **Independent of the type of computer being used** | Programs can be **larger** | Can **make use of special hardware** | It takes **longer to write and debug** programs |
| **Easier to read, write and understand** programs | Programs can take **longer to execute** | Can make use of **special machine dependent instructions** | Programs are **more difficult to understand** |
| **Quicker to write** programs | Programs **may not be able to make use of special hardware** | Code **doesn't take up much space in primary memory** | — |
| Programs are **easier and quicker to debug** | — | Code **performs a task very quickly** | — |
| **Easier to maintain** programs in use | — | — | — |

🔧 **答题模板：Explain why you would choose to write a program in a LLL** [2-3]
> A program is written in a low-level language when it **needs to perform a task very quickly**, or **includes special machine dependent instructions to operate hardware**. LLL code also **doesn't take up much space in primary memory**.

⚠️ **答题陷阱**：题目问 **why** 就解释理由，不要写 **how** to write a LLL program。

❌ **错误示范**："Nobody writes programs in a low-level language anymore as it is too hard as you have to learn special commands for each computer." —— 这在解释**为什么不用**，虽然碰巧含一个有效理由，但只得 1 分。

---

## 4.2.2 汇编语言 Assembly Language

**English（背这句）**

| **Assembly language** | **Machine code** |
|-----------------------|------------------|
| Written using **mnemonics and labels** | Written in **binary** |
| **Needs translation before execution** | **Can be executed straight away** |

⚠️ **概念澄清**：
- **Assembly language ≠ machine code**。Assembly 用助记符（mnemonics），需要**汇编器翻译**。
- 有考生选 "A low-level programming language written in **binary**" —— **错**，那是 machine code。

🔧 **选择题标准答案**：
> **"What is meant by the term assembly language?"**
> ✅ A language that is **dependent on computer hardware and needs to be translated into binary before it is executed**.

---

## 4.2.3 翻译程序 Translators（三大类必背）

**English（背这句）**
> A **translator** is a **utility program**. Programs must be translated into binary for the computer to follow them.

| | **Compiler** 编译器 | **Interpreter** 解释器 | **Assembler** 汇编器 |
|---|---|---|---|
| **翻译对象** | Translates a **high-level language** program | Executes a **high-level language** program | Translates a **low-level assembly language** program |
| **方式** | **Into machine code in one go** | **One statement at a time** | Into machine code |
| **产物** | An **executable file of machine code is produced** | **No executable file is produced** | An **executable file of machine code is produced** |
| **对应关系** | **One HLL statement can be translated into several machine code instructions** | **One HLL program statement may require several machine code instructions to be executed** | **One LLL statement is usually translated into one machine code instruction** |
| **运行** | Once compiled, programs are run **without the compiler** | Interpreted programs **cannot be run without the interpreter** | Assembled programs are used **without the assembler** |
| **分发** | A compiled program is usually **distributed for general use** | An interpreter is **often used when a program is being developed** | An assembled program is usually distributed for general use |
| **出错时** | If errors are detected, an **error report is produced** (instead of a compiled program) | If an error is detected in a statement, **execution stops and an error message is output** | — |

🔧 **答题模板：Describe the difference between a compiler and an interpreter** [2]
> A **compiler translates the whole program at once** and produces a **file to be executed later**, whereas an **interpreter translates each statement then executes it before moving on to the next statement**.

⚠️ **注意题目要求**：如果题目说 "**HLL translation programs**"，就**只能**写 compiler 和 interpreter，**写 assembler 不给分**。

### 编译器 vs 解释器 优缺点

| Translator | **Advantages 优点** | **Disadvantages 缺点** |
|---|---|---|
| **Interpreter** | **Easier and quicker to debug, test and edit** programs during development; changes can be tested **immediately without recompiling**; useful for beginners/learning | **Slower to execute** because each statement is translated **every time** it is run; the **interpreter must be present** to run the program; **stops at the first error** (only one error reported at a time); source code must be available |
| **Compiler** | Produces an **executable file** that can be **stored and run without the compiler**; **executes faster**; can **optimise** the code; reports **all errors together** after compilation; the executable can be **tested repeatedly without recompiling**; can be **distributed** for general use | The **whole program must be compiled before it can be run**; **slower to debug/test during development** (edit → recompile → run); any change to the source code requires **recompilation**; errors are only reported **after compilation** |

### 编译器的错误报告与开发优势（常考）

**错误报告**
> - The compiler attempts to translate the **whole program**.
> - If errors are found, it produces an **error report** listing **all the errors** in the code (instead of an executable).
> - The programmer must **correct the errors and recompile** before the program can be executed.

**用编译器开发的好处**
> - **All errors are reported together**, so the programmer can fix several at once.
> - Once compiled, the **executable can be tested many times without translating again**.
> - The compiled program can be **run on another system without the translator** (provided it is compatible).
> - **Optimised code** produced by the compiler can **execute faster**.

🔧 **答题模板：Tick the description — assembler / compiler / interpreter** [5]

| Description | Assembler | Compiler | Interpreter |
|-------------|-----------|----------|-------------|
| Translates a program written in a **LLL** | ✅ | | |
| Translates a program written in a **HLL** | | ✅ | ✅ |
| **Identifies errors** | ✅ | ✅ | ✅ |
| **Does not produce an executable file** | | | ✅ |
| **Allows editing during execution** | | | ✅ |

💡 **记忆要点**：
- **只有 interpreter 不产生可执行文件**
- **只有 interpreter 允许边执行边编辑**
- **三者都能识别错误**

---

## 4.2.4 集成开发环境 IDE（最高频大题）

**English（背这句）**
> An **integrated development environment (IDE)** is a **suite of software development tools** used by programmers to **aid the writing and development of programs**. Examples include **PyCharm (for Python), Visual Studio (for Visual Basic) or BlueJ (for Java)**. IDEs **speed up the development of computer software by providing development tools in one application**.

**IDE 八大功能（必背，考 8 分题的完整答案）**：

| 功能 | English 说明 |
|------|-------------|
| **Code editor** 代码编辑器 | Allows a program to be **written and edited without the need to use a separate text editor**, speeding up the program development process |
| **Translator** 翻译器 | Can be a **compiler and/or an interpreter**. Enables the program to be **executed under the control of the IDE** |
| **Runtime and debugger** 运行时与调试器 | **Runs a program under development**. Allows a programmer to **step through the program a line at a time (single stepping)**. Allows a programmer to **set breakpoints**. A **report window shows the contents of variables and expressions**, which allows the programmer to check for **logic errors** |
| **Error diagnostics** 错误诊断 | **Finds possible errors as the program code is being typed** |
| **Auto-completion** 自动补全 | **Context-sensitive prompts with text completion** for variable names and reserved words |
| **Auto-correction** 自动纠错 | **Alerts the programmer to errors and provides suggested corrections** |
| **Auto-documenter and prettyprinting** 自动文档与美化 | Auto-documenter **explains the function and purpose of key words**. Prettyprinting **colour codes the words** in the program and **lays the program out clearly** |
| **Breakpoints / single stepping** | 见 debugger |

🔧 **答题模板：Explain what is meant by an IDE** [2]
> An IDE is a **suite of software development tools** used by programmers to aid the writing and development of programs; it **provides all the development tools in one application**.

🔧 **答题模板：Describe two features of an IDE** [4]
> **1. Code editor** — allows a program to be written and edited without the need to use a separate text editor, which speeds up the development process.
> **2. Debugger / runtime** — runs the program under development and allows the programmer to **step through the program a line at a time (single stepping)** and **set breakpoints**; a report window shows the contents of variables and expressions so the programmer can check for **logic errors**.

🔧 **答题模板：Explain why an IDE is needed. Identify the features included in an IDE and the reasons why a programmer finds these features useful** [8]
> **结构**：每条 = **feature + 它做什么 + 为什么对程序员有用**（8 分 = 4 条 × 2 分，或 8 条简答）
>
> 1. **Code editor** — 不用另开文本编辑器，**节省时间**
> 2. **Translator (compiler/interpreter)** — 直接运行，**不用切换工具**
> 3. **Debugger with single stepping & breakpoints** — 逐行执行、设置断点、查看变量值，**帮助找逻辑错误**
> 4. **Error diagnostics** — 边打代码边提示错误，**提前发现问题**
> 5. **Auto-completion** — 自动补全变量名和保留字，**减少打字错误、加快输入**
> 6. **Auto-correction** — 提示错误并**建议修改**
> 7. **Auto-documenter** — 解释关键字功能
> 8. **Prettyprinting** — **颜色高亮 + 排版清晰**，方便阅读代码

⚠️ **DE 大题铁律**：**"功能"必须配"为什么有用"**。只写 "it has a code editor" = 0 分。

---

# 📝 考试怎么考（Exam Focus）

## 各题型答题模板

### 模板 1：判断软件类型（Tick 表格）
> **口诀**：管理计算机本身 → **系统软件**；帮用户干活 → **应用软件**。
> 背熟那张 10 个软件的对照表。

### 模板 2：Describe the functions of [X] part of the OS [6]
> **每条 2 分** → 先给定义，再给"为什么这样做/不这样做会怎样"。
> **拼写必须正确**：`user account management` 不是 `user account manager`。

### 模板 3：Explain the term + reasons why it is used [3]
> **格式**：① 定义 → ② 用途 1 → ③ 用途 2
> ⚠️ **注意过时答案**：screensaver 的"防烧屏"是**错的**；现代主要用途是**安全（自动登出）**，省电只是部分教材保留的旧说法。

### 模板 4：Buffer / Interrupt 填空或简答 [3-8]
> **背熟那段标准填空文本**（见 §4.1.4）。
> 答题顺序：**数据进 buffer（临时存放）→ CPU 继续干别的 → buffer 空了 → 设备发中断 → 按优先级 → 执行 ISR → 清除中断 → 恢复原任务**

### 模板 5：Compare HLL and LLL [4-6]
> 用**对比表结构**写，每一条都写清楚是哪个语言的。
> **Explain why → 只写"为什么选它"，不要写"怎么写"**

### 模板 6：Difference between compiler and interpreter [2-4]
> 一句编译器（whole program at once, produces executable file） + 一句解释器（one statement at a time, no executable file）。

### 模板 7：Tick description — assembler/compiler/interpreter [5]
> 背熟那张表。**interpreter 不产可执行文件、可边执行边改**是唯一性特征。

### 模板 8：Explain why an IDE is needed [8]
> **4 条 × (功能 + 为什么有用)**。

---

## 📌 判分规则（精简）

- **OS 功能题**：功能名 **或** role，写对任意一边就得 1 分；描述必须是该功能特有的。
- **中断流程七步**：收到信号 → 检查/设置优先级 → 排队 → **完成当前 FDE 周期** → **寄存器存栈** → 查来源并执行 ISR → **从栈恢复并返回**。只写「暂停 → ISR → 继续」最多 2 分。
- **IDE 题**：只列 feature 封顶 4 分；每条都要写 `feature + so the programmer can…`。
- **HLL vs LLL**：必须成对写（HLL 一句 + whereas + LLL 一句）；只写一边最多一半。
- **Translator 辨析**：one statement at a time / no executable → **interpreter**；whole program / executable → **compiler**；mnemonics → **assembler**。

### 📌 Unit 4 高分优先级

| 优先级 | 考点 | 典型分值 | 说明 |
|--------|------|---------|------|
| ★★★ | **OS 功能** | 4–6 | 每套必考，名称+描述都要会 |
| ★★★ | **Interrupt + Buffer** | 3–8 | 七步流程必须默写 |
| ★★★ | **Compiler / Interpreter / Assembler 对比** | 2–5 | 靠"唯一性特征"秒杀 |
| ★★☆ | **HLL vs LLL** | 4–6 | ⚠️ **必须配对写** |
| ★★☆ | **IDE 功能** | 4–8 | ⚠️ **必须带解释**，封顶 4 分 |
| ★★☆ | **系统软件 vs 应用软件判断** | 2–4 | Tick 表格题，送分 |
| ★☆☆ | **CLI vs GUI / WIMP** | 2–4 | 常和 Unit 5 一起考 |
| ★☆☆ | **Screensaver / BIOS / CMOS** | 1–3 | 记住"防烧屏 = 过时答案" |

---

## ⚠️ 高频失分点汇总

| 失分点 | 正确写法 |
|--------|---------|
| Screensaver 说成"防止屏幕烧屏/phosphor burn" | ❌ **已过时，0 分**。现代主要用途 = **安全（自动登出）**；省电为旧说法 |
| 拼写错误：`user account manager` | ✅ **user account management** |
| WIMP/post-WIMP 题扯到 CLI 比较 | ❌ 题目要求 **relative** = 两者互比，扯 CLI **不给分** |
| "Explain why use LLL" 写成 "how to write LLL" | ✅ 只写**理由**（快、机器相关指令、省内存） |
| Assembly language 说成 "written in binary" | ✅ Assembly 用 **mnemonics and labels**；**machine code** 才是 binary |
| HLL 翻译器题写成 assembler | ✅ HLL 翻译器只有 **compiler** 和 **interpreter** |
| 只写 IDE 功能不写"为什么有用" | ✅ **每个功能必须跟一句"这样程序员就能…"** |
| BIOS 和 BIOS 设置混为一谈 | ✅ BIOS 存 **EEPROM**；BIOS 设置存 **CMOS**（靠电池） |
| OS 功能写成 "controls the computer" | ✅ 必须具体：memory management / multitasking / file management / user account management / security / interrupt handling / hardware management / HCI / error handling |
| Buffer 和 Interrupt 混为一谈 | ✅ Buffer = **内存区域临时存数据**；Interrupt = **送给 CPU 的信号** |

---

## 🧠 一页纸速记

```
【软件分类】
System software:   用 OS / utility / device driver / compiler / linker
Application software: 用 word / spreadsheet / database / photo-video editing / apps

【系统软件特点】控制管理硬件 / 提供运行平台 / 提供 HCI / 分配资源

【OS 九大功能】★ 高频
Managing files / Handling interrupts / Providing an interface (HCI)
Managing peripherals and drivers / Managing memory / Managing multitasking
Providing a platform for running apps / Providing system security / Managing user accounts
  —— Memory management = 管 RAM + RAM↔HDD 数据搬移 + memory protection
  —— User account mgmt = 每用户独立内存区 + 用户名密码 + 权限层级
  —— Security = 更新软件 + 防病毒/防火墙 + 访问权限 + 数据恢复

【HCI】
CLI: 直接通信, 不受限, 可改设置, 省内存 | 需背命令, 费时易错
GUI: 图标, 不用背命令, 适合新手 | 内存需求大
WIMP = windows/icons/menu/pointing device (鼠标)
post-WIMP = 触摸屏, 可 pinch & rotate, 不需指点设备

【Screensaver】非活动后出现 → 自动登出 = 安全（省电为旧说法）
              ⚠ 不要说防烧屏(过时)

【启动】BIOS(存 EEPROM, 是 firmware) → 告诉 CPU OS 在哪
        BIOS 设置存 CMOS, 靠电池供电
        OS 的一部分被载入 RAM = booting

【中断】signal → microprocessor, 请求 attention
   CPU 暂时停止 → 给优先级 → 执行 ISR → 清除 → 恢复原任务
   五个来源: timing / I/O / hardware fault / user interaction / software error
   Buffer = 内存区域临时存数据, 让 CPU 继续干别的
   数据进 buffer → 空了 → 设备发中断要更多数据

【HLL vs LLL】
HLL 优: 与机器无关 / 易读易写 / 写得快 / 易调试 / 易维护
HLL 缺: 程序更大 / 执行更慢 / 用不了特殊硬件
LLL 优: 用特殊硬件 / 机器相关指令 / 省内存 / 执行极快
LLL 缺: 写得慢难调试 / 难理解
Assembly = mnemonics + labels, 需翻译; Machine code = binary, 可直接执行

【翻译程序】
Compiler    — HLL→机器码, 一次性, 产生可执行文件, 出错给 error report
Interpreter — HLL, 一句一句, ★不产生可执行文件, 出错即停
Assembler   — LLL(汇编)→机器码, 产生可执行文件
★只有 interpreter 不产可执行文件 & 可边执行边编辑

【IDE】一套开发工具 (PyCharm/Visual Studio/BlueJ)
  code editor / translator / runtime & debugger (single stepping, breakpoints,
  变量报告窗口) / error diagnostics / auto-completion / auto-correction /
  auto-documenter / prettyprinting
```

---

## 🔗 延伸资源

- 课件：[Chapter 4 课件与反馈材料](../csresource/new/2026_10_19_Common%20Test%20U4%20-%20feedback%20v2/Chapter%204.pdf)
- 练习：[Save My Exams — 4. Software](https://www.savemyexams.com/igcse/computer-science/cie/23/topic-questions/) · [PapersDaddy — 0478 Topical Paper 1](https://www.papersdaddy.com/cambridge/igcse/computer-science-0478/resources/topical-past-papers/paper-1)

---

**上一单元** ← [Unit 3 - Hardware](Unit%203%20-%20Hardware.md)
**下一单元** → [Unit 5 - The internet and its uses](Unit%205%20-%20The%20internet%20and%20its%20uses.md)
