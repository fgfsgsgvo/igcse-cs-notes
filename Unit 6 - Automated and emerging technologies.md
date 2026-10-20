# Unit 6 — Automated and Emerging Technologies 自动化与新兴技术

> **考纲**：Cambridge IGCSE Computer Science 0478 / 0984 (2026–2028) — Unit 6 Automated and emerging technologies
> **试卷**：Paper 1 Computer Systems — **75 分 / 1 小时 45 分钟 / 不允许使用计算器**
> **本单元特点**：**每套卷必考，通常占 10–20 分**。题型几乎完全固定：
> ① **「sensor → microprocessor → actuator」链条描述题**（3–7 分，**出现频率最高，是 Paper 1 最值钱的一道题**）
> ② **「Explain why X is / is not an embedded system / a robot」**（2 分）
> ③ **配对/填词题**（robot characteristics、AI 术语、expert system 组件）
> ④ **优缺点讨论题**（Discuss advantages and disadvantages）
>
> ⚠️ **本单元的分数极度依赖"结合题目情境"**。Examiner Report 对 Unit 6 的头号抱怨永远是同一句：
> **"Candidates gave generic answers that were not applied to the context given in the question."**
> 背模板 + **把题目里的数字、传感器名、设备名抄进去** = 满分。

---

## 📋 考纲对照清单

| # | 考纲条目 | 掌握 |
|---|---------|------|
| 6.1.1 | What is meant by an automated system | ☐ |
| 6.1.2 | The role of sensors, microprocessors and actuators in automated systems | ☐ |
| 6.1.3 | Advantages and disadvantages of automated systems | ☐ |
| 6.2.1 | What is meant by robotics | ☐ |
| 6.2.2 | Characteristics of a robot | ☐ |
| 6.2.3 | Advantages and disadvantages of robots | ☐ |
| 6.3.1 | What is meant by artificial intelligence (AI) | ☐ |
| 6.3.2 | Characteristics of AI | ☐ |
| 6.3.3 | Types of AI system: expert systems and machine learning | ☐ |

---

# 第一部分：自动化系统 (6.1)

## 6.1.1 什么是自动化系统

**English（背这句，定义题 1–2 分）**
> An automated system is a **combination of software and hardware** (for example, **sensors, microprocessors and actuators**) that is **designed and programmed to work automatically without the need for any human intervention**. However, such systems **often involve human monitoring**.

🔧 **答题模板：State what is meant by an automated system** [1-2]
> - Software **and** hardware working together
> - … to perform a task **without human intervention / automatically**
> - … **programmed** to do a specific task

⚠️ **判分警告**：❌ "It is a system that is automatic" —— 循环定义，**0 分**。必须提到 **sensors/microprocessor/actuators** 或 **without human intervention**。

---

## 6.1.2 sensor → microprocessor → actuator 链条 ⭐ 最高频、最值钱

**English（把这一段背到能默写）**

```
Sensors  —  输入设备，从环境中读取数据
            (input devices that take readings from their surroundings)
            ↓ 如果数据是 analogue，先经 ADC 转成 digital
            (If the data is analogue, it is first converted into a
             digital format by an analogue-to-digital converter (ADC).)
            ↓
Microprocessor  —  处理数据，根据编程决定要做什么
            (processes the data and takes the necessary action
             based on programming)
            ↓
Actuators  —  输出，控制 motors / wheels / solenoids / valves / pumps
            (control motors, wheels, solenoids, and so on)
```

### 🔧 万能答题模板（任何 "Describe how sensors and a microprocessor..." 题都能套）

> **①** The **sensor** [名称] **continuously sends digitised data** to the **microprocessor**.
> **②** The microprocessor **compares the data to a stored value / a preset value / a range of values**（**把题目给的数字写在这里！**）.
> **③** **If the value is outside the range / greater than / less than** [题目给的数值], the microprocessor **sends a signal**.
> **④** The signal is sent **to an actuator**, which performs the **physical action**（stop / open the valve / apply the brakes / turn on the pump）.
> **⑤** **If the value is within the range, no action is taken.**
> **⑥** The **whole process repeats until it is turned off**.

**这就是官方 Mark Scheme 的得分点清单（2024 June P11 Q8(c) 六分题逐字）**：
> "A proximity sensor is used" / "The sensor continuously sends digitised data to the microprocessor" / "The microprocessor compares the data to a stored value/range of values" / "If the value is within the range/matches the robot continues planting" / "If the value is above/below/outside the range a signal is sent by the microprocessor to turn/stop the robot" / "…using an actuator to turn/stop the robot" / "This process repeats until the robot is turned off"

**另一份官方答案（2024 March P12 Q6(b)(i) 五分题"拖拉机检测到 3 米内有人就停下"）**：
> - "Sensor **continuously** sends the **digitised value / reading / distance** to the microprocessor"
> - "Microprocessor **compares** the data/signal **to the stored data of a person and distance of 3m**"
> - "**If the data/signal is less than (or equal to) a person and within 3m** …"
> - "…**a signal is sent to actuator to make the tractor stop / apply the brakes**"
> - "If the data/signal is greater than 3m **no action is taken**"
> - "**The whole process repeats until turned off**"

### ⚠️⚠️ 三个致命失分点（Examiner Report 逐条点名）

| 失分点 | 正确写法 |
|--------|---------|
| **不写 "compares to a stored value"** | ✅ 必须写 **the microprocessor compares the data to a stored value / preset value / range** —— 这是**最常丢的那 1 分**。ER: "Some of the weaker responses **repeated the question**, for example stating if the data showed that a person was within 1 metre instead of **how** the microprocessor would identify that a person was within 1 metre — through the comparison of the data against a stored value." |
| **只说 "a signal is sent to an actuator"，不说 actuator 干什么** | ✅ 必须说 **the actuator is what is used to trigger the action**（stop the robot / open the valve）。ER: "just reference to an actuator is **NE** here." |
| **说 actuator 用来在屏幕上显示信息** ❌❌ | ✅ **Actuator 引起物理运动（physical movement）—— 电机、阀门、活塞、刹车。它绝不用来显示文字或改变屏幕内容。** ER 2025 March 原文："A common misconception was that an **actuator would be used to change the display on the screen**. An actuator converts a digital signal into **physical movement**, for example to move a motor to open a door; **it does not display a message on a digital screen**." |

⚠️ **还有一个方向性警告**：题目只问 **role of the microprocessor** 时，**不要**把整个系统都描述一遍。
> ER 2024 Nov: "Some candidates **described the operation of the whole system, which was not necessary**. The question only required the role of the microprocessor."
> ER 2025 Nov: "Some candidates tried to give a lot more information about how the whole system would operate. **This was not necessary** and candidates are reminded to **focus on the information requested in the question**."

---

## 6.1.3 自动化系统的应用领域（八大场景）

> 教材原文：题目里出现的工业/科学流程**一定会在题干中完整描述**（甚至配图）。
> 你**不需要**预先懂得那些流程——你需要的只是**看懂 sensor / actuator / microprocessor 三者的互动关系**。

### 各场景速查表（做题时对照查传感器）

| 场景 | Sensors（通常考这几个） | Actuators 做什么 |
|------|----------------------|-----------------|
| **核电站 (DCS)** | temperature / pressure / flow level / gas (escape) / radiation level sensors | 操作 water pumps、valves、gas pumps、紧急停机系统 |
| **制药 / 化工生产** | temperature / pressure / flow / level sensors | 操作 pumps、valves、heaters、stirrers、pistons |
| **自动泊车 (self-parking car)** | 保险杠里的 **ultrasonic / proximity sensors**（发射＋接收，靠回波时间算距离）；cameras | 操作 **steering rack、brakes、throttle** |
| **自适应巡航 (adaptive cruise control)** | **lasers**（保险杠里持续发射，靠回波时间算车距） | **apply the brakes / reduce the throttle / increase the throttle** |
| **农业灌溉 (Brazil irrigation)** | **ultrasonic water level sensors**；weather station（温度/湿度/风速/气压/雨量/光照） | 操作 **water pumps** |
| **自动气象站 (weather station)** | thermometer（温度）、**anemometer**（风速）、**hygrometer**（湿度）、**barometer**（气压）、level sensor（雨量）、light sensor（日照时数） | **tipping bucket rain gauge** —— 到时间间隔就驱动 piston 翻桶泄水 |
| **游戏设备 (gaming)** | **accelerometer**（测加速度/减速度，即倾斜设备）、**proximity sensor**（触控板里的电极检测手指位置） | 无（主要是输入增强沉浸感） |
| **照明系统 (lighting)** | **light sensor**（环境亮度）、**motion sensor**、**infrared sensor**（安防） | 控制 LED 灯阵列、喷泉水泵 |
| **实验室化学过程** | **level detectors**（A 管流出多少液体）、**colorimeter**（测反应后颜色） | 操作 **burette（滴定管）的 tap** |
| **家用/娱乐机器人** | proximity sensors、cameras、microphone、HD camera（computer vision 识别人脸） | 控制 motors（前进/后退/左右）、转向 |

🔧 **答题模板：Describe how sensors, actuators and a microprocessor interact** [5]
> 逐字背下面五句（这是 Unit 6 最标准的答案）：
> 1. The **sensor** takes a reading from its surroundings and **sends digitised data to the microprocessor**.
> 2. The **microprocessor processes the data / compares it to a stored value or range**.
> 3. **If the value is outside the range**, the microprocessor **sends a signal to an actuator**.
> 4. The **actuator operates** [motor / valve / pump / brakes / heater]，which performs the **physical action**.
> 5. **The process repeats continuously / until it is turned off.**

---

## 6.1.4 自动化系统的优缺点（高分值讨论题）

### 通用优点（背 6 条，题目给场景时挑合适的套）

> - **Much faster than a human operator** to take any necessary action
> - **Much safer**（an automated system is **more likely to make timely interventions** than a human; it also **keeps humans away from a dangerous environment**）
> - The process is **more likely to run under optimum conditions** since any small changes needed can be **identified very quickly and action taken**
> - **In the long run, it is less expensive**（replaces most of the workforce who would need to monitor the process 24 hours a day / **reduced labour costs**）
> - **More efficient use of materials / higher productivity / more consistent results**
> - **Works 24/7 without stopping**（不需要休息、不会疲劳）

### 通用缺点

> - **Expensive to set up in the first place** and **needs considerable testing**
> - **Always possible for a set of conditions to occur that were never considered during testing**, which could have **safety implications**（hence the need for a supervisor / monitoring station）
> - **Any computerised system is subject to cyberattacks**, no matter how good the system
> - **Automated systems always need enhanced maintenance**, which can be **expensive**
> - **Risk of deskilling / unemployment**（replaces manual labour）
> - **Over-reliance on automated systems by the user（loss of skills）**
> - **Faulty/dirty sensors can send false data, which could lead to a malfunction**

### 场景特有优缺点（考到就加分）

| 场景 | 特有优点 | 特有缺点 |
|------|---------|---------|
| **自动泊车** | 同样数量车占更少车位；避免城市交通拥堵；能停进更小的车位；**减少刮蹭和凹陷**（reduced insurance claims）；**传感器会监测包括幼儿在内的所有物体**，更安全 | **轮胎蹭到路缘 (kerbing)** 是常见问题，因为传感器可能**检测不到低矮的路缘**；贵但不省钱 |
| **照明系统** | **降低能耗**（只在需要时开灯）；**灯泡寿命更长**；无线连接**更安全**（无拖线）；可编程不同灯光秀 | 初期安装贵；无线连接**不如有线可靠** |
| **实验室化学过程** | **结果更一致（可重复）**；**更安全**（尤其化学品危险时）；**结果更快**（多个实验可同时进行）；可自动分析结果；**需要的高技能人员更少**；实验可在世界任何地方实时监测 | 人来做更灵活；数据全球共享时**有安全风险**；设备贵 |
| **灌溉系统** | 大幅降低人工成本；**对宝贵资源（如水）控制更好**；**比人工巡查几公里渠道快得多**；**更安全**（田间可能 40°C）；**不同作物可以编程不同的灌溉条件**（水稻需淹水，橙树喜干燥） | 初期设备贵；**维护成本极高**，且需要专业技师（在偏远地区是问题）；需要持续维护水渠——**水渠堵塞或坍塌系统检测不到**，会导致部分区域过涝、部分区域缺水 |
| **气象站** | 节省人力；可从**偏远地区**或需要持续数据的地区采集数据；太阳能供电 | 传感器需定期校准维护 |

🔧 **答题模板：Discuss the advantages and disadvantages of using an automated system to ...** [4-6]
> **结构：2 个优点 + 2 个缺点，每个都"点 + 解释"（1 分说点，1 分说为什么/对谁）。**
> ⚠️ 只列 4 个点不解 = 最多 2 分。

---

# 第二部分：机器人技术 (6.2)

## 6.2.1 什么是 robotics 和 robot

**English（背这句）**
> **Robotics** is a **branch of (computer) science** that brings together the **design, construction and operation of robots**.
> A **robot** is a **mechanical device that can carry out tasks normally done by humans**.

⚠️⚠️ **最常考的术语区分**：
| 术语 | 中文 | 定义 |
|------|------|------|
| **Robotics** | 机器人**技术**（学科） | A **branch of computer science** that brings together the **design, construction and operation** of robots |
| **Robot** | 机器人（**设备**） | A **mechanical device** that can carry out tasks normally done by humans |
| **Actuator** | 执行器 | A device, under the control of a microprocessor, which allows it to **operate pumps, wheels, motors and pistons** |
| **End-effector** | 末端执行器 | An **attachment to a robot arm** which allows it to carry out a **specific task, such as spray painting** |
| **Controller** | 控制器 | A **microprocessor that is in control of a process** |
| **Autonomous** | 自主的 | Able to operate **independently without any human input** |

❌ **绝对不能把 robotics 说成 "a robot"**。Robotics 是**学科/领域**，不是机器本身。

---

## 6.2.2 机器人的特征 ⭐ 必考（2–4 分）

**English（背这张表，配对题直接照抄）**

> **要被称为 robot，必须同时具备以下特征：**

| # | 特征 | English |
|---|------|---------|
| **1** | **机械结构 / 框架** | Has a **mechanical structure / framework**（made up of motors, hydraulic pipes, actuators, gears, cogs, pistons, circuit boards） |
| **2** | **电子元件** | Contains **electrical components** to allow it to function |
| **3** | **可编程** | Is **programmable** — it has a 'brain' known as a **controller** that determines the action to be taken（controllers are **programmable to allow the robots to do certain tasks**） |
| **4** | **能移动** | Has the **ability to move** — can use wheels, cogs, pistons, gears to carry out functions such as **turning, twisting, moving backwards/forwards, gripping or lifting** |
| **5** | **能感知环境** | Has the **ability to sense its surroundings** — via **sensors**（light, pressure, temperature, acoustic, etc.）; **sensor data is sent to a microprocessor or computer** |

⚠️⚠️⚠️ **2025 March Examiner Report 标记的年度最高频错误**：
> ❌❌ **"Artificial intelligence (AI) is NOT a characteristic of a robot."** ❌❌
> 很多学生写 "it can think"、"it has AI"、"it is intelligent" —— **不得分**。
> 教材原文也强调："**Many robots don't possess artificial intelligence (AI)** since they tend to do **repetitive tasks** rather than requiring **adaptive human characteristics**."

🔧 **答题模板：Give three characteristics needed to define a machine as a robot** [3]
> 从上面 5 条里任选 3 条，**每条必须至少带一个具体名词**（wheels/gears 或 sensors 或 controller/programmable 或 electrical components/mechanical structure）。

⚠️ **另一条警告**：**Software robots 不是真机器人**（按上面的定义，它们没有机械结构和电子元件）：
> - **Search engine bots / WebCrawlers** — 在互联网上爬行、扫描网站并分类，供搜索引擎使用
> - **Chatbots** — 网站上弹出的程序，看起来能和人对话

---

## 6.2.3 独立机器人 vs 依赖机器人

| | **Independent robot** 独立机器人 | **Dependent robot** 依赖机器人 |
|---|---|---|
| **人机关系** | Has **no direct human control**（is said to be **autonomous**） | Has **a human who is interfacing directly with the robot**（the human interface may be a **computer or a control panel**） |
| **替代程度** | Can **replace the human activity totally**（no human interaction is required for the robot to function fully） | Can **supplement, rather than totally replace, the human activity** |
| **例子** | An autonomous vehicle / autonomous vacuum cleaner | A car assembly plant where both humans and robots work together |

🔧 **答题模板：Explain what is meant by the two types of robot** [4]
> **每个类型 2 分**：① **有没有人在直接控制** ② **是完全取代人还是补充人**。
> - An **independent robot** has **no direct human control** … it can **replace the human activity totally**.
> - A **dependent robot** has **a human who is interfacing directly with the robot** … it **supplements rather than replaces** the human activity.

---

## 6.2.4 机器人的应用领域

### 工业 Industry

**典型任务**：paint spraying of car bodies、welding bodywork、manufacturing of microchips、manufacturing electrical goods、automatic warehouses。

**机器人的两种编程方式（考点）**：
> 1. The robot is **programmed with a sequence of instructions** which allow it to carry out the series of tasks.
> 2. A **human operator manually carries out the series of tasks**; each movement is **stored as an instruction on the computer**. This is done in two ways:
>    i. The robot arm is **guided manually by a worker**; each movement of the arm is **stored as an instruction**.
>    ii. The **worker straps sensors to his own arm** and performs the task; each movement is stored as a set of instructions — sensors send back information such as **position relative to the object, arm rotation**, and so on.

**为什么机器人要装传感器？**（考点）
> Robots are equipped with sensors so they can gather important information about their surroundings and also **prevent them from doing 'stupid things'** — for example, **stopping a robot spraying a car if no car is present**, or **stopping the spraying operation if the supply of paint has run out**.

**⚠️ 什么时候该用人而不是机器人**
> Robots are very good at **repetitive tasks**. However, if there are **specialist tasks that require 'thinking' to cope with variable circumstances**（for example, making specialist glassware）, then it is **often better to still use human operators**.

**工业机器人优缺点表（背下来，配对/讨论题直接用）**

| **Advantages** | **Disadvantages** |
|----------------|-------------------|
| Capable of working in **conditions that may be hazardous to humans** | Can find it **difficult to do 'non-standard' tasks**（例如装挡风玻璃时玻璃裂了） |
| Work **24/7 without the need to stop** | Can lead to **higher unemployment amongst manual labour tasks** |
| **Less expensive in the long run**（fewer salaries to pay） | **Risk of deskilling** when robots take over certain tasks（welding、paint spraying） |
| **More productive than humans**（higher productivity） | Factories can now be moved **anywhere in the world where operation costs are lower**（again leading to unemployment in some countries） |
| Although not necessarily more accurate, robots are **more consistent** | **Expensive to buy and set up in the first place** |
| **Better suited to boring, repetitive tasks**（less likely to make mistakes） | |
| **Less cost in heating and lighting**（robots don't need good light or warmth） | |

### 交通 Transport

**自动驾驶汽车 (Autonomous cars)**
> Autonomous cars use **sensors, cameras, actuators and microprocessors**（together with very complex algorithms）. **Sensors (radar and ultrasonics) and cameras** act as the **'eyes' and 'ears' of the car**. Microprocessors process the data and **send signals to actuators to perform physical actions**, such as: **change gear / apply the brakes / turn the steering wheel**.

**遇到红灯时会发生什么（经典情境题）**：
> The control system needs to **recognise the road sign** and then **check its database as to what action to take**. Since the traffic light shows red, the microprocessor must **send signals to actuators to apply brakes and put the gear into 'park'**. **Constant monitoring must take place until the light changes to green.** When this happens, the microprocessor will again **instruct actuators to put the car into first gear, release the brakes and operate the throttle**.

**自动驾驶汽车优缺点表**

| **Advantages** | **Disadvantages** |
|----------------|-------------------|
| **Safer** since **human error is removed**, leading to fewer accidents | **Very expensive system to set up**（high technology requirements） |
| **Better for the environment** since vehicles will **operate more efficiently** | The **ever-present fear of hacking** into the vehicle's control system |
| **Reduced traffic congestion**（humans cause 'stop-and-go' traffic known as '**the phantom traffic jam**'） | **Security and safety issues**（software glitches could be catastrophic） |
| **Increased lane capacity**（research shows +100% lane capacity and +20% average speeds） | **Cameras need to be kept clean**; sensors could **fail to function in heavy snowfall**（radar/ultrasonic signals could be deflected by snow particles） |
| **Reduced travel times** → less commuting time | **Driver and passenger reluctance** to use the new technology |
| **Stress-free parking**（the car will find parking on its own and then self-park） | **Reduction in the need for taxis could lead to unemployment** |

**自动驾驶火车 (Autonomous trains)**
> 用 **LiDaR (Light Detection and Ranging)** —— 用激光建立周围环境的 **3D 图像**；还有 **proximity sensors on train doors**、cameras（包括 **infrared cameras**）、**GPS** 用于计算速度和方向的精确变化。**Actuators 控制列车的速度、刹车以及车门的开关**。

**无人驾驶飞机 (Pilotless airplanes)** —— 主要特征：
> - Sensors to **detect turbulence** to ensure smooth flights
> - An increase in **self-testing of all circuits and systems**
> - Sensors that would **automatically detect depressurisation** in the cabin
> - Use of **GPS** for navigation and speed calculations
> - Use of **actuators** to control **throttle, flaps (on the wings) and the rudder**

**交通类通用优缺点速记**：
| 优点 | 缺点 |
|------|------|
| 消除人为失误 → **更安全** | **黑客入侵的持续威胁** |
| 减少人力 → **运行成本更低** | **初期资本和运营成本高** |
| **提高准点率 / 可增加班次密度 / 调度更容易** | **软件故障可能是灾难性的** |
| **减少能耗**（更好的速度控制和最优服务） | **乘客对新技术的不信任 / 抵触** |
| 对飞机：**乘客舒适度提升、气动性改善**（前面不用留驾驶舱） | 对飞机：**机上无飞行员时的安保问题**；飞行中的紧急情况难处理 |

### 农业 Agriculture（五大方向）

| 方向 | 关键点 |
|------|-------|
| **Harvesting / picking 采摘** | 更准确（**只摘成熟的果实**）、更快 → **产量更高、浪费更少**；例：**vegebot**（剑桥大学）用 cameras 扫描生菜判断是否可以收割，**第二个 camera 靠近刀片处**引导机械臂无损切下 |
| **Weed control 除草** | 用 **AI 区分杂草和作物**；用 **GPS tracking** 沿藤蔓行前进；**除草刀片由 actuator 在 controller（microprocessor）控制下操作**；常先用 **drone 航拍**葡萄园，生成预设路线发送到除草机器人的内存 |
| **Phenotyping 表型分析** | **表型分析 = 观察植物的物理特征以评估其健康和生长**；机器人装有 **spectral sensors 和 thermal cameras** 生成 **3D 模型**；用 **machine learning** 识别叶片问题（枯斑、颜色异常）并反馈给农民；比人工**更快、更准** |
| **Seed-planting / fertiliser 播种施肥** | Drones 提供航拍"鸟瞰图"；**播种更精准**；**施肥更高效、减少浪费**；可用于 **cloud seeding**（向云中播撒碘化银晶体使其降雨） |
| **Autonomous devices 自主设备** | 割草机、除草/修剪/采摘机器人、播种机器人、施肥机器人；都用 **sensors and cameras 绕开障碍物**，甚至可编程为**天气变坏时"休眠"** |

### 医疗 Medicine

> - **手术 (surgical procedures)**：更安全、更快、成本更低
> - 从**监测病人**到做**小型手术**
> - **病房和手术室的消毒**可由自主机器人完成
> - **采血 (take blood samples)**：对病人**痛苦更小**（机器人更擅长找到 'good vein'）；病人有传染病时对**医护更安全**；**释放医护去做更高技能的工作**
> - **Microbots 靶向治疗**：用微观机械元件（含 microprocessor）把药物**定位到特定部位，减少对周围组织的损伤**
> - **假肢 (prosthetic limbs)**：现在本身就是小型机器人（因为它们**满足机器人的三条特征**）；**bionic skins 和 neural implants** 与受损肢体的**人类神经系统接口**，提供反馈以实现更好的控制（同样用 sensors 和 actuators 给出**类人的反应，如抓握**）

### 家用 Domestic

> - **自主吸尘器**：用 **proximity sensors 和 cameras** 避免撞到障碍物并覆盖整个房间；有 **microprocessor** 控制整体操作并**允许用户编程设备**；**actuators 控制马达**实现前进/后退/左右移动
> - **自动割草机**：使用和吸尘器**相同的 sensor + camera + microprocessor + actuator 组合**
> - **个人助理（如 Vector）**：由 microprocessor 控制，**通过云连接互联网**；用 microphone 理解语音命令并回答问题；用 **HD camera + computer vision 识别人脸**；用 **proximity sensors 和 actuators 导航房间绕过物体**

### 娱乐 Entertainment

> - **主题公园**用自主机器人（常扮成卡通角色）与游客互动，让体验更"真实"
> - **音乐节**：机器人控制**灯光（含激光秀）、视觉特效和动画**（如把演员影像叠加到机器人角色上并同步嘴部动作）
> - **拍摄**：《地心引力》用大量机器人操作**摄像机、道具和演员**；机械臂模拟人类行为，产生逼真的动态影像
> - **特技**：人形机器人（遥控或预编程）做人类不可能完成的动作，用 **CGI 和图像捕捉技术**生成特效
> - 机器人能以**超越人类能力的精度、速度和协调性**产生特效，动作和特效可同步到**毫秒级**

---

# 第三部分：人工智能 AI (6.3)

## 6.3.1 什么是 AI

**English（背这句，定义题必考）**
> **Artificial intelligence (AI)** is a **branch of computer science dealing with the simulation of intelligent human behaviour by a computer**. This is often referred to as the **cognitive functions of the human brain**（the mental process of **acquiring knowledge and understanding through thought, experience and the five senses**）.

**Key term 速记**：
| 术语 | 定义 |
|------|------|
| **AI** | A **collection of rules and data** which gives a computer system the ability to **reason, learn and adapt to external stimuli** |
| **Cognitive** | Relating to the **mental processes of the human brain** involved in **acquiring knowledge and understanding** through thought, experiences and input from the five senses |
| **Deductive reasoning** | Where **a number of correct facts are built up to form a set of rules** which can then be **applied to other problems** |

🔧 **答题模板：State what is meant by artificial intelligence** [1-2]
> - A **branch of computer science** / a **simulation of intelligent human behaviour** by a computer
> - … that gives a computer the ability to **reason, learn and adapt**

---

## 6.3.2 AI 的特征 ⭐ 必考

**English（背这四条）**
> AI is essentially a **collection of rules and data**, and the ability to:
> - **Simulation of intelligent human behaviour**
> - **Collection of rules and data**
> - **Ability to reason**（draw reasoned conclusions based on given data/situations）
> - **Ability to learn and adapt**（to external stimuli）

**AI 的三个类别（可能考配对）**：
| 类别 | 定义 |
|------|------|
| **Narrow AI** 弱人工智能 | A machine has **superior performance to a human when doing ONE specific task** |
| **General AI** 通用人工智能 | A machine is **similar (not superior)** in its performance to a human doing a specific task |
| **Strong AI** 强人工智能 | A machine has **superior performance to a human in MANY tasks** |

**AI 的例子（题目若给情境，直接引用）**：
- **News generation** based on live news feeds
- **Smart home devices**（Alexa / Siri / Google Now / Cortana）：识别语音命令；**从环境和接收的数据中学习**；响应越来越精细，**表现出自动重复学习的能力**
- **Chatbots**：通过与即时通讯交互，**人为复现人类互动模式**；被问到时用**当时已知的信息**回应
- **Autonomous cars**
- **Facial expression recognition**：算法识别关键面部地标（眉毛角、嘴角等），**组合这些地标可以映射情绪**（愤怒、恐惧、喜悦、惊讶）

---

## 6.3.3 两种 AI 系统

### Expert Systems 专家系统

**English（背这句）**
> An **expert system** is a **computer system that mimics the decision-making ability of a human**; it uses AI to **simulate the judgement and behaviour of a human or organisation that has expert knowledge and experience**. They use **knowledge and inference to solve problems or answer questions that would normally require a human expert**.

#### ⭐⭐ 专家系统的四个组件（**必考，背死**）

```
     ┌─────────────────────────────────────────────┐
     │              Expert System                   │
     │  ┌──────────────┐      ┌──────────────────┐  │
user │  │    USER      │      │   EXPLANATION    │  │ Advice
◄────┼──│  INTERFACE   │      │     SYSTEM       │  │
     │  └──────┬───────┘      └──────────────────┘  │
     │         ↓                                    │
     │  ┌──────────────┐      ┌──────────────────┐  │
     │  │  INFERENCE   │◄────►│   KNOWLEDGE      │  │
     │  │    ENGINE    │      │      BASE        │  │
     │  └──────┬───────┘      └──────────────────┘  │
     │         ↓                                    │
     │  ┌──────────────┐                            │
     │  │  RULES BASE  │                            │
     │  └──────────────┘                            │
     └─────────────────────────────────────────────┘
```

| 组件 | English 定义（背这几句） |
|------|----------------------|
| **User interface** 用户界面 | The **method by which the expert system interacts with a user**；交互可通过 **dialogue boxes、command prompts** 或其他输入方式；问题通常只有 **Yes/No 答案**，且**基于对前一个问题的回答** |
| **Inference engine** 推理机 | The **main processing element** of the expert system；**acts like a search engine examining the knowledge base for information/data that matches the queries**；负责**通过问一系列问题从用户处收集信息**，每个问题基于之前的回答；是**问题求解部分**，使用 rules base 里的 **inference rules**；尝试用从用户收集的信息**找出匹配的 object** |
| **Knowledge base** 知识库 | A **repository of facts**；存储从多个专家资源获得的**某领域的全部知识**；本质上是**一堆 objects 及其 attributes** 的集合 |
| **Rules base** 规则库 | A **set of inference rules**；**inference rules 被 inference engine 用来得出结论**（方法**紧密跟随人类推理**）；通常涉及一系列 **'IF' 语句**，例如：`IF continent = "South America" AND language = "Portuguese" THEN country = "Brazil"` |

⚠️⚠️ **判分警告（Examiner Report 点名）**：
> ❌ **"rule data"** —— 错，必须写 **rules base**（或 **knowledge base**，但不能混）
> ❌ **"interface engine"** —— 错，必须是 **inference engine**（把 interface 和 inference 搞混了）
> ✅ 接受的写法：**knowledge base / rule base / rules base / inference engine / interface / user interface**

**补充术语（图里出现，syllabus 不强制但可写）**：
> **Explanation system** — part of an expert system which **informs the user of the reasoning behind its conclusions and recommendations**. 它让用户**判断诊断或建议治疗的有效性**。

#### 专家系统的优缺点

| **Advantages** | **Disadvantages** |
|----------------|-------------------|
| Offer a **high level of expertise** | Users need **considerable training** in its use to ensure the system is being used correctly |
| Offer **high accuracy** | **Set up and maintenance costs are very high** |
| Results are **consistent** | They tend to give very **'cold' responses** that may not be appropriate in certain medical situations |
| Ability to **store vast amounts of ideas and facts** | They are **only as good as the information/facts entered** into the system |
| Can make **traceable logical solutions and diagnostics** | Users sometimes make the **dangerous assumption that they are infallible** |
| Possible to have **multiple expertise** | |
| **Very fast response times**（much quicker than a human expert） | |
| Provide **unbiased reporting and analysis** of the facts | |
| **Indicate the probability** of any suggested solution being correct | |

**应用领域（配对/举例题）**：oil and mineral prospecting、diagnosis of a patient's illness、fault diagnostics in mechanical and electronic equipment、tax and financial calculations、strategy games（如 chess）、logistics（包裹配送的高效路径规划）、identification of plants/animals/chemical compounds。

#### 专家系统怎样建立（4 分流程题）

> 1. Information needs to be **gathered from human experts or from written sources**（textbooks, research papers, internet）
> 2. The information is used to **populate the knowledge base**（which needs to be created first）
> 3. A **rules base needs to be created** — made up of a series of **inference rules** so the inference engine can draw conclusions
> 4. The **inference engine itself needs to be set up**（a complex system since it is the main processing element）
> 5. The **user interface needs to be developed** to allow the user and the expert system to communicate
> 6. Once set up, it **needs to be fully tested** — done by **running the system with known outcomes so results can be compared** and any changes made

#### 专家系统诊断流程（医学诊断例，5 分描述题的完整答案）

> - **First of all, an interactive screen is presented to the user**
> - **The system asks a series of questions about the patient's illness**
> - **The user answers the questions asked**（either as multiple choice or YES/NO questions）
> - **A series of questions are asked based on the user's responses to previous questions**
> - **The inference engine compares the symptoms entered with those in the knowledge base looking for matches**
> - **The rules base (inference rules) is used in the matching process**
> - **Once a match is found, the system suggests the probability of the patient's illness being identified accurately**
> - **The expert system also suggests possible solutions and remedies**
> - **The explanation system will give reasons for its diagnosis** so the user can determine the validity

---

### Machine Learning 机器学习

**English（背这句，定义题必考）**
> **Machine learning** is a **sub-set of artificial intelligence (AI)** in which **algorithms are 'trained' and learn from their past experiences and examples**. It is possible for the system to **make predictions or even take decisions based on previous scenarios**.

⚠️ **另一种官方 Mark Scheme 措辞**（学生答案里出现过，也是给分的）：
> A **program that has the ability to automatically adapt its own data and processes**.

**核心特点**：
> - Can offer **fast and accurate outcomes** due to **very powerful processing capability**
> - Key factor: the ability to **manage and analyse considerable volumes of complex data**
> - Some tasks would **take humans years to complete** without machine learning

#### ⭐ AI vs Machine Learning（必考对比，配对/表格题）

| **AI** | **Machine Learning** |
|--------|---------------------|
| Represents **simulated intelligence in machines** | The practice of **getting machines to make decisions without being programmed to do so** |
| The aim is to build **machines that are capable of thinking like humans** | The aim is to make **machines that learn through data acquisition, so that they can solve new problems** |

#### 机器学习的三个经典例子（考情境题时对照用）

**例 1：把邮件分类为垃圾邮件**
> - An ML algorithm **collects data about emails** — email content, headers, sender's name/email address
> - It carries out a **'cleaning' process by removing stop words**（the, and, a）and punctuation, leaving only the relevant data
> - Certain words/phrases are frequently used in spam（**lottery, earn, full-refund**）and indicate the email is very likely spam
> - The ML model is built and a **'training data set' is used to train the model** using past emails known to be spam
> - Once it is **evaluated, the model is fine-tuned and tested live**

**例 2：识别用户购买历史（推荐系统）**
> - This comes from **collaborative filtering** — the process of **comparing customers who have similar shopping behaviour** to a new customer who has similar behaviour
> - The ML algorithms recommend products based on the **similarities between customer A and customer B's shopping behaviour**

**例 3：检测欺诈活动**
> - **Data collection**（survey 或 **web scraping**）：收集客户信息，如交易类型、购物习惯、特定个人数据
> - **Data cleaning**：移除冗余数据（redundant data），需谨慎操作以避免错误预测
> - **Exploration and analysis** + **Training**：算法通过真实的客户购买行为例子进行训练（**这是最重要的一步**）
> - **Building a model**：基于训练数据建立模型，可用于检测欺诈（如客户在某件珠宝上花了异常金额）
> - **Model evaluation**：用**已知数据和已知结果**充分测试；若未达到检测欺诈的标准则修改系统

🔧 **答题模板：Describe how a search engine might use machine learning to determine the most appropriate results** [4]
> - The search engine **uses search bots to locate websites matching the user's search criteria**
> - **If the user selects one of the websites found on PAGE 1, the search engine classes this as a success**
> - **If the user has to go to PAGES 2, 3 or 4 to find the information, the search engine classes this as a failure**
> - **The search engine learns from its past performance** …
> - … so its ability to carry out searches **becomes more and more sophisticated and accurate**

---

## 6.3.4 Deep Learning（**超纲**，但习题里出现过，了解即可）

> **Deep learning** structures algorithms **in layers**（**input layer, output layer and hidden layer(s)**）to create an **artificial neural network** made up of **'units' or 'nodes'** — essentially **based on the human brain**（其神经元之间的互联）。Neural network systems are able to **process more like a human** and their **performance improves when trained with more and more data**.

| **Machine learning** | **Deep learning** |
|---------------------|-------------------|
| Uses algorithms to enable machines to make decisions on their own based on **past data** | Uses algorithms arranged as an **artificial neural network** |
| Tends to **need less data** | The system **needs large amounts of data** during the training stages |
| Very good at certain **classification tasks** such as spam email | Very good at very **complex non-linear tasks** such as **visual processing** |
| **A modular approach** — each module combined to produce the final model | The problem is solved **from beginning to end as a single entity** |
| Does **not always need a large amount of computing power** | **Requires a large amount of computing power** |
| **Testing takes a long time** | **Testing takes much less time** |
| There are **clear rules which explain why each stage was made** | The reasoning may be **very difficult to understand**（hence **'black box'**） |

---

# 📝 考试怎么考（Exam Focus）

## 各题型答题模板

### 模板 1：sensor → microprocessor → actuator 链条 ⭐⭐⭐ 最高频
> **必写五句**：
> 1. sensor **continuously sends digitised data** to the microprocessor
> 2. microprocessor **compares the data to a stored value / preset value / range of values**
> 3. **if outside the range**, microprocessor **sends a signal**
> 4. **to an actuator**，它执行**物理动作**（stop / open / apply brakes）
> 5. **the process repeats until it is turned off**
>
> 💡 **把题目里的数字和传感器名字抄进去！** 例如题目说 "less than 10 cm"，你就要写 "compares the data to the **stored value of 10 cm**"。

### 模板 2：Explain why X is / is not an embedded system [2]
> **两个不同的特征**（只说一个 = 1 分）：
> - has a **dedicated / single / limited function**（not a general purpose device）
> - has **dedicated hardware**
> - contains a **microprocessor**（not a CPU）
> - **cannot be easily reprogrammed** / function is not easily changed
> - uses **firmware**
> - **is part of / built into a larger device**（vs a computer is standalone）

### 模板 3：Give three characteristics of a robot [3]
> **mechanical structure / electrical components / programmable / ability to move / ability to sense surroundings**
> ❌ **不要写 AI / intelligence / it can think** —— 这是 2025 年最高频错误。

### 模板 4：配对题 / 术语定义题
> 背熟这些定义（逐字）：
> - **robotics** = branch of computer science … design, construction and operation of robots
> - **expert system** = form of AI developed to **mimic human knowledge and expertise**
> - **knowledge base** = a **repository of facts** … a collection of **objects and attributes**
> - **rules base** = a collection of **inference rules** used to draw conclusions
> - **inference engine** = a **kind of search engine** used in an expert system which **examines the knowledge base for information that matches the queries**
> - **machine learning** = a **sub-set of AI** in which **algorithms are trained and learn from past experiences and examples**
> - **AI** = simulated intelligence in machines … building of machines capable of thinking like a human
> - **autonomous** = can move between point A and point B **without the need for any input from a driver or a pilot**
> - **end-effector** = an **attachment to a robot arm** which allows it to carry out a specific task
> - **controller** = a **microprocessor that is in control of a process**
> - **cognitive** = the **mental process of the human brain** whereby it acquires knowledge and understanding

### 模板 5：Discuss advantages and disadvantages [4-6]
> **2 优点 + 2 缺点，每个都必须"点 + 解释"。**
> 用上面的场景专用优缺点表，**不要用通用空话**。

### 模板 6：Describe how a microprocessor would ensure ... [3-4]
> 只写 microprocessor 的动作，**不要描述整个系统**（Examiner Report 反复警告）。
> 标准骨架：**receive data → compare with stored value → send signal → (to actuator) → repeat**

---

## ⚠️ 高频失分点汇总

| 失分点 | 正确写法 |
|--------|---------|
| **不写 "compares the data to a stored value"** | ✅ 这是**最常丢的 1 分**。必须写 microprocessor **compares to a stored/preset value or range** |
| **actuator 用来在屏幕上显示信息** ❌ | ✅ **Actuator 只引起物理运动**（motor/valve/piston/brakes）。**绝不显示文字** |
| **AI 是机器人的一个特征** ❌ | ✅ **AI 不是机器人的特征**。很多机器人只是做重复任务，不具备 AI |
| **robotics 就是 robot** ❌ | ✅ **robotics 是学科/领域**（design, construction and operation of robots） |
| **写 "rule data" 或 "interface engine"** ❌ | ✅ **rules base** 和 **inference engine** |
| 只写 "a signal is sent to an actuator" 就完了 | ✅ 必须说 **actuator 用来触发什么动作** |
| 答 "Describe the role of the microprocessor" 时描述了整个系统 | ✅ **只写 microprocessor 的动作** |
| 用通用答案，不结合题目情境 | ✅ **把题目里的传感器名、数值、设备名抄进答案** |
| 优缺点只列点不解释 | ✅ **每个点后接 "so that / which means / this makes"** |
| 说 automated system "is a system that is automatic" | ✅ 必须提 **hardware + software, sensors/microprocessor/actuators, without human intervention** |
| 只说 "it is more efficient" / "it is faster" | ✅ 必须说**比什么快 / 为什么更高效**（than a human operator / than manual） |

---

## 🧠 一页纸速记

```
【自动化系统定义】
combination of software and hardware (sensors, microprocessors, actuators)
designed and programmed to work automatically WITHOUT human intervention
(often involves human monitoring)
⚠ 不能写 "it is automatic" (循环定义, 0分)

【⭐ sensor → microprocessor → actuator 链条 ★★★★★ 必背】
① sensor 持续把 digitised data 发给 microprocessor
② microprocessor 把 data 和 stored value / preset value / range 比较
③ 如果超出范围 → microprocessor 发信号
④ → 给 actuator，actuator 执行【物理动作】(motor/valve/pump/brakes)
⑤ 如果在范围内 → 不采取行动
⑥ 整个过程重复直到关闭
⚠ actuator 绝不显示屏幕信息
⚠ 必须写"比较"这一步 (最常丢分)
⚠ 题目给的数字要抄进去

【AI vs 机器学习】
AI = simulated intelligence in machines; aim = machines that THINK like humans
     = collection of rules and data + reason + learn + adapt to external stimuli
ML = sub-set of AI; getting machines to make decisions WITHOUT being programmed
     to do so; aim = machines that LEARN through data acquisition
     = algorithms are 'trained' and learn from past experiences and examples
Deep learning(超纲) = artificial neural network (input/hidden/output layers), 需要大量数据

【AI 三类别】
narrow AI = 在【一个】特定任务上超越人类
general AI = 在特定任务上和人类【相似】(不是超越)
strong AI = 在【许多】任务上超越人类

【专家系统 4 组件 ★ 必背】
user interface   — 与用户交互的方式 (dialogue boxes/command prompts, Yes/No 问题)
inference engine — 【主处理元件】, 像 search engine 一样查 knowledge base
                   用 rules base 里的 inference rules 得出结论
knowledge base   — 【存放事实的仓库】, 是 objects 和 attributes 的集合
rules base       — 一组 inference rules, 通常是 IF 语句
+ explanation system — 解释推理过程 (图里有, syllabus 不强制)
⚠ 不写 "rule data" / "interface engine"

【机器人 5 个特征】
mechanical structure/framework ✓
electrical components ✓
programmable (has a controller) ✓
ability to move (wheels/gears/pistons) ✓
ability to sense surroundings (sensors) ✓
❌ AI is NOT a characteristic of a robot (2025年最高频错误)

【independent vs dependent robot】
independent = 无人类直接控制 (autonomous), 完全取代人类活动
dependent   = 有人类直接接口 (computer/control panel), 补充而非完全取代

【不是真机器人】software robots: search engine bots/WebCrawlers, chatbots

【术语表】
robotics    = branch of computer science: design/construction/operation of robots
robot       = mechanical device that carries out tasks normally done by humans
end-effector= attachment to a robot arm for a specific task (spray painting)
controller  = a microprocessor in control of a process
autonomous  = operates independently without human input
LiDaR       = light detection and ranging; lasers build a 3D image
drone       = flying robot, autonomous or remote-controlled
cognitive   = mental process of acquiring knowledge via thought/experience/senses
phenotyping = observing plant physical characteristics to assess health and growth

【自动化优缺点 - 通用】
优: faster than human / safer (timely interventions, keeps humans away from danger) /
    runs under optimum conditions / less expensive long-term / 24-7 / consistent
缺: expensive to set up + needs testing / unforeseen conditions → safety issues /
    subject to cyberattacks / enhanced maintenance costs / deskilling / unemployment

【各场景传感器速查】
核电站   : temperature, pressure, flow level, gas escape, radiation level
灌溉     : ultrasonic water level + weather station
气象站   : thermometer, anemometer(风速), hygrometer(湿度), barometer(气压),
           level sensor(雨量), light sensor(日照)
自适应巡航: lasers (回波时间算车距)
自动泊车 : ultrasonic/proximity sensors in bumpers + cameras
游戏     : accelerometer (倾斜), proximity sensor (触控板)
照明     : light sensor, motion sensor, infrared sensor
实验室   : level detectors, colorimeter
```

---

## 🔗 延伸资源

- 教材：[Cambridge IGCSE Computer Science Textbook — Chapter 6](../csresource/)
- 真题：[Unit 6 按子主题真题 + Answer Key](../csresource/new/Past%20Exam%20Papers/Questions%20by%20Unit/Unit%206%20-%20Automated%20and%20emerging%20technologies%20%28159%20pts%29/)
- 真题：`csresource/.../Past Exam Papers/Questions by Year/` 中各年份 Paper 1
- 在线练习（按考纲章节分类，与本单元一一对应）：
  - [Save My Exams — 6. Automated and emerging technologies](https://www.savemyexams.com/igcse/computer-science/cie/23/topic-questions/)
  - [PapersDaddy — 0478 Topical Paper 1](https://www.papersdaddy.com/cambridge/igcse/computer-science-0478/resources/topical-past-papers/paper-1)（免费下载）
  - [Physics and Maths Tutor — IGCSE Computer Science](https://www.physicsandmathstutor.com/computer-science-revision/igcse-cie/)

> ⚠️ **注意**：本校 slide 只覆盖 Unit 1–5，**Unit 6 没有 slide 材料**；但新资料里有 **Unit 6 按子主题整理的真题 + Answer Key**（6.1 Automation / 6.2 Robotics / 6.3 AI / 6.3 Expert systems）。本单元内容来自教材 Chapter 6 + 这些真题/答案。

---

**上一单元** ← [Unit 5 - The internet and its uses](Unit%205%20-%20The%20internet%20and%20its%20uses.md)
**下一单元** → [Unit 7 - Algorithm design and problem solving](Unit%207%20-%20Algorithm%20design%20and%20problem%20solving.md)　*（Paper 2 从这里开始）*
